---
tags:
  - 디버깅
  - Tailwindcss
  - 스타일링
---
# 오류 내용

템플릿 리터럴을 사용하여 스타일 동적 할당을 진행하는데 스타일 시트에 정상적으로 적용이 되지 않는다.

```tsx
// SVG 컴포넌트 내 path나 rect 요소에 스타일링을 할당하기 위해 작성한 코드
// iconSelectedStyle에는 "fill-white", "stroke-white" 등이 값으로 들어가있다.

const navList = [
	{
		name: "홈",
		route: pageRoute.root,
		icon: HomeIcon,
		iconSelectedStyle: "fill-white",
	},
	{
		name: "스크랩",
		route: pageRoute.scrap,
		icon: ListIcon,
		iconSelectedStyle: "stroke-white",
	},
];

<IconComponent
	className={cn({ [`[&>*]:${nav.iconSelectedStyle}`]: selected })}
/>
```

# 원인 생각해보기

자식 요소에 할당하는 스타일이라 기존에 스타일 시트에 존재하지 않아 발생하는 문제인가?

# 디버깅

> [!QUOTE] 동일 오류 레딧
>  [Next.js and Tailwind can't use template string for applying classes problem - reddit](https://www.reddit.com/r/node/comments/o54avo/nextjs_and_tailwind_cant_use_template_string_for/)

> [!INFO] 문제 원인 요약
> 
> [Tailwindcss : Dynamic class names](https://tailwindcss.com/docs/content-configuration#dynamic-class-names)
> 
> "Tailwind는 사용되지 않는 CSS는 제거합니다. 따라서 당신의 코드가 컴파일링 되는 시점에서, Tailwind는 동적 할당을 인식하지 못하고 stylesheet에서 지워버릴 겁니다."

그렇기에 다음과 같이 언제나 완성된 형태의 클래스 명을 사용 함을 권장한다.

```tsx
<div className="{{ error ? 'text-red-600' : 'text-green-600' }}"></div>
```

```tsx
// 해결 결과

const navList = [
	{
		name: "홈",
		route: pageRoute.root,
		icon: HomeIcon,
		iconSelectedStyle: "[&>*]:fill-white",
	},
	{
		name: "스크랩",
		route: pageRoute.scrap,
		icon: ListIcon,
		iconSelectedStyle: "[&>*]:stroke-white",
	},
];

<IconComponent
	className={cn({ [`${nav.iconSelectedStyle}`]: selected })}
/>
```