---
title: 'Roll-up / Roll up / 롤업'
date: 2022-09-17 17:05:18
category: 'Javascript'
draft: false
---

Roll-up
---
<div style="text-align: center;"><img alt="Rollup.JS" src="https://rollupjs.org/logo.svg" style="height: 150px"></div>

### rollup.js 공식 사이트에서 말하는 Roll-up
- 작은 코드를 라이브러리나 응용 프로그램과 같은 더 복잡한 코드로 컴파일 
- JavaScript의 ES6 개정판에 포함된 코드 모듈의 새로운 표준화된 형식을 사용

<br> 

---

<br>

### 다른 Javascript Module Bundler들과의 차이
|                   특징                   | Roll-up                                                                                                                  | Webpack                                                                                                                                                                                                                                                      | Parcel                                                                   |             비교              |
|:--------------------------------------:|--------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------|:---------------------------:|
|             Configuration              | entry, output, loaders, plugins, transformations 등을 설정하는 구성 파일을 필요.<br>상대경로를 지원하며, import/export 를 위한 `node polyfills` 보유  | entry, output, loaders, plugins, transformations 등을 설정하는 구성 파일을 필요.<br>polyfill이 없으며, 상대경로 또한 미지원                                                                                                                                                            | `Zero-configuration`                                                      |  **Parcel>Rollup>Webpack**  |
 |            Transformations             | `플러그인`을 사용                                                                                                                 | `babel-loader`, `css-loader` 등 과 같이 `loader`를 사용                                                                                                                                                                                                             | `zero-configuration`                                                      |  **Parcel>Webpack>Rollup**  |
 |  Tree Shaking (Dead code elimination)  | 코드를 정적으로 분석하고 실제로 사용되지 않는 코드는 제외                                                                                         | Tree shaking을 ES6 모듈에서만 지원하기 때문에 package.json 에서 `SideEffects` 항목을 필요.<br>`UglifyJS`와 같은 minimize tool도 필요                                                                                                                                                   | S6 및 CommonJS 모듈 모두에 대해 Tree shaking을 지원. 대부분의 작업을 캐싱하여 다시 빌드할 경우 속도가 빠름 |  **Parcel>Rollup>Webpack**  |
 |             Code splitting             | 동적 로딩이나 다중 진입점과 같이 Rollup이 코드를 자동으로 청크로 분할하는 경우가 있으며 output.manualChunks 옵션을 통해 별도의 청크로 분할할 모듈을 Rollup에 명시적으로 알려주는 방법 보유 | 최소한의 작업과 로드 시간이 더 빠름.<br>entry 설정을 사용하거나 `CommonChunk` 플러그인을 사용하여 청크를 중복 제거 하고 분할하거나, 모듈 내 인라인 함수를 불러와 동적으로 import 하는 Code Splitting을 활성화 하는 세가지 접근 방식 보유.<br>Rollup과 Parcel은 Code-splitting 하는데에 있어서 유용하지만, 아직까지 이슈들이 보이기 때문에 안정된 상태의 웹팩을 계속 사용하는것이 좋다는 평판. | `Zero-configuration`                                                       | **Webpack>Rollup, Parcel**  |
 |               Dev Server               | `rollup-plugin-serve` 를 제공.<br>live-reload 를 위해서는 추가로 `rollup-plugin-livereload` 설치 필요.                                      | `wepback-dev-server` 를 제공. live-reload를 지원.                                                                                                                                                                                                                  | Dev server 내장.<br>HTTP logging, Hooks, middleware를 사용할 때 이슈가 발생.         | **Webpack>Rollup, Parcel**  |
|         Hot Module Replacement         | `rollup-plugin-hotreload` 를 통해 지원                                                                                                                      | `webpack-dev-server` 를 통해 지원.<br> 안정성이 높음.                                                                                                                                                                                                                   | 기본적으로 HMR을 지원                                                                      | **Webpack>Rollup, Parcel**  |

<br>

### 총평 : 
복잡한 설정을 피하고 간단한 애플리케이션을 빠르게 만들고 싶다 : **Parcel**

최소한의 서드파티로 라이브러리를 만들고 싶다 : **Rollup**

많은 서드파티를 필요로 하는 복잡한 애플리케이션을 개발한다 : **Webpack**

<br>

---

<br>

### Roll-up 설치 방법
1. rollup 글로벌 설치
``` 
npm install -g rollup
```
2. 프로젝트 내부에 rollup 설치
```
npm install rollup
```
3. `rollup.config.js` 파일 생성
4. 기본 config 작성
```js
export default {
    input: './src/index.js',
    output: {
        file: './dist/bundle.js',
        format: 'umd'
    }
}
```
5. `package.json`파일 `scripts` 수정
```json
{
 ...,
 "scripts": {
  "build": "rollup -c -w"
 }   
}
```

<br>

--- 

<br>

#### My Comment
최근 webpack을 토이프로젝트에 적용해보고 있었는데, 많은 기업에서 webpack과 roll-up의 사용 경험을 우대 조건으로 
평가하는 경향이 크다고 느꼈다.<BR>모두 Module Bundler의 종류 인 것은 알고 있었지만 자세히 알아보고 싶어 정리해보있다.<br>
Module Bundler들이 각각 가진 특징이 있다는 것을 자세히 알게되었고 기회가 된다면 Roll-up도 프로젝트에 적용해보고 싶다는
생각이 들었다. ~~(Parcel도..!)~~

<br>

출처: https://rollupjs.org/guide/en/,https://velog.io/@subin1224/Parcel-vs-Rollup-vs-Webpack-%EB%B9%84%EA%B5%90,https://www.js2uix.com/frontend/rollup-study-step1/#:~:text=Rollup%20%EC%9D%B4%EB%9E%80%3F,%EC%9A%A9%20%EB%AA%A8%EB%93%88%20%EB%B2%88%EB%93%A4%EB%9F%AC%EC%9E%85%EB%8B%88%EB%8B%A4.