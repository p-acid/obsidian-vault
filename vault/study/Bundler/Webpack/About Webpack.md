---
tags:
  - bundler
  - webpack
---
> [Webpack 공식 문서](https://webpack.kr/concepts/)를 통해 학습하는 Webpack 정리 문서입니다.
> 번들러 개념에 대한 이해가 필요하면 [[What's Bundler?]] 참고해주세요.

# 정의

> **Webpack**은 모던 JavaScript 애플리케이션을 위한 _정적 [모듈](https://webpack.kr/concepts/modules) 번들러_ 입니다.

# 핵심 개념

## [Entry](https://webpack.kr/concepts/#entry)

- [디펜던시 그래프](https://webpack.kr/concepts/dependency-graph/) 생성을 위한 모듈이며, 일종의 진입점이라고 보면 된다.
- `webpack.config.js` 내 `entry` 필드로 설정 가능하다.

```js
module.exports = {
  entry: './path/to/my/entry/file.js',
};
```

## [Output](https://webpack.kr/concepts/#output)

- 번들을 내보낼 위치 및 파일 이름 지정에 관한 내용이다.
- `webpack.config.js` 내 `output` 필드로 설정 가능하다.
- 엔트리 이름, ID, 해시 등을 사용하여 명칭할 수도 있다.

```javascript
const path = require('path');

module.exports = {
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: '[name].[id].[contenthash].js',
  },
};
```

## [Loaders](https://webpack.kr/concepts/#loaders)

- JavaScript, JSON 외 다른 유형의 파일을 처리할 때 사용한다.
- `webpack.config.js` 내 `module.rules` 필드로 설정 가능하다.

> webpack은 기본적으로 JavaScript, JSON만 처리 가능

```javascript
module.exports = {
  module: {
    rules: [
	    { 
		    test: /\.txt$/, // 변환이 필요한 파일 확장자 식별
		    use: 'raw-loader' // 변환을 수행할 loader에 해당하며 배열로 입력 가능(인덱스 역순으로 적용).
		}
	],
  },
};
```

## [Plugins](https://webpack.kr/concepts/#plugins)

- 번들 최적화, 에셋 관리, 환경 변수 주입 등의 작업을 수행한다.
- `require` 를 통해 요청하여 `webpack.config.js` 내 `plugins` 필드 배열에 할당하여 설정 가능하다.

> 다양한 [plugin 목록](https://webpack.kr/plugins) 확인하기.

```javascript
const HtmlWebpackPlugin = require('html-webpack-plugin');
const webpack = require('webpack'); // 내장 plugin에 접근하는 데 사용

module.exports = {
  plugins: [new HtmlWebpackPlugin({ template: './src/index.html' })],
};
```

## [Mode](https://webpack.kr/concepts/#mode)

- 맞춤별 환경 설정을 위한 모드를 설정한다.
- 할당 가능한 값으로 `none`, `development`,`production` 등이 있다.
- `webpack.config.js` 내 `mode` 필드로 설정 가능하다.

```javascript
module.exports = {
  mode: 'production',
};
```

## [Browser Compatibility](https://webpack.kr/concepts/#browser-compatibility)

> Webpack은 [ES5](https://kangax.github.io/compat-table/es5/)가 호환되는 모든 브라우저를 지원합니다(IE8 이하는 지원되지 않습니다). Webpack은 [`import()` 및 `require.ensure()`](https://webpack.kr/guides/code-splitting/#dynamic-imports)을 위한 `Promise`를 요구합니다. 구형 브라우저를 지원하려면 이러한 표현식을 사용하기 전에 [폴리필을 로드](https://webpack.kr/guides/shimming/)해야 합니다.

## [Environment](https://webpack.kr/concepts/#environment)

> Webpack 5는 Node.js 버전 10.13.0 이상에서 실행됩니다.