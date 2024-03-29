---
title: 'webpack / Webpack / 웹팩'
date: 2021-09-21 08:30:39
category: 'javascript'
draft: false
---

## Webpack

Webpack에 대해서 더 자세히 알아보기 위해 webpack docs를 정리한다.

### 핵심 개념
- **Entry** 
- **Output** 
- **Loaders** 
- **Plugins**
- **Mode**
- **Browser Compatibility**(브라우저 호환성)

---

### 1. Entry

**엔트리 포인트(Entry Point)** : webpack이 내부의 디펜던시 그래프를 생성하기 위해 사용해야 하는 모듈
<br>
기본값은 `./src/index.js`.

```js
module.exports = {
    entry: './path/to/my/entry/file.js',
};
```

<br>
디펜던시 그래프(Dependency Graph) : 하나의 파일이 다른 파일에 의존할 때마다, webpack은 의존성으로 취급.
<br>

Application을 처리할 때, 엔트리 포인트에서 시작하여 Application에 필요한 모든 모듈을 포함하는 **디펜던시 그래프**를 
재귀적으로 빌드한 다음, 모든 모듈을 브라우저에 의해 로드되는 하나의 번들로 묶는다.

### 2. Output

**Output** : 생성된 번들을 내보낼 위치와 파일의 이름을 지정하는 방법을 명세</br>
기본 출력파일 : `./dist/main.js`, 생성된 기타 파일 폴더 : `./dist`

```js
const path = require('path');

module.exports = {
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'my-first-webpack.bundle.js',
    },
};
```

### 3. Loaders

**Loader** : webpack이 다른 유형의 파일을 처리하거나, 그들을 유효한 모듈로 변환하여 사용하거나 디펜던시 그래프에 추가할 수 있도록 설정
<br>
Loader는 webpack 설정에 두 가지 속성을 가짐.
1. `test` 속성 : 변환이 필요한 파일들을 식별하는 속성
2. `use` 속성 : 변환을 수행하는데 사용되는 로더를 가르키는 속성

```js
const path = require('path');

module.exports = {
    module: {
        rules: [
            { 
                test: /\.css$i/, 
                use: ['style-loader', 'css-loader'],
            }
        ],
    },
};
```

### 4. Plugins

**플러그인(Plugin)** : 번들을 최적화하거나, 에셋을 관리하고, 환경변수 주입 등과 같은 광범위한 작업을 수행

```js
const HtmlWebpackPlugin = require('html-webpack-plugin');
const webpack = require('webpack')

module.exports = {
    module: {
        rules: [
            {
                test: /\.css$i/,
                use: ['style-loader', 'css-loader'],
            },
        ],
        plugins: [
            new HtmlWebpackPlugin({ template: './src/index.html'})
        ]
    },
};
```

<br>

`html-webpack-plugin` : 생성된 모든 번들을 자동으로 삽입하여 Application용 HTML 파일을 생성

### 5. Mode
`Mode` 파라미터를 `development`, `production`, `none`으로 설정하여 webpack에 내장된 환경별 최적화를 활성화

기본값 : `production`

```js
module.exports = {
    mode: 'production'
};
```

### 6. Browser Compatibility
webpack은 ES5가 호환되는 모든 브라우저를 지원하지만, 구형 브라우저를 지원하려면 **Pollyfill**을 로드해야 한다.

<br>
폴리필(Polyfill) : 기능을 지원하지 않는 웹 브라우저 상의 기능을 구현하는 도구.
<br>

폴리필 플러그인 로드 때문에 시간과 트래픽이 늘어나고, 브라우저별 기능을 추가하는 것 때문에 코드가 길어지고, 성능이 많이 저하된다는
단점이 있다.


**./src/polyfills.js**

```js
import 'babel-polyfill';
import 'whatwg-fetch';
```

**webpack.config.js**

```js
module.exports = {
    entry: {
        polyfills: './src/polyfills',
        index: './src/index.js'
    }
};
```