# CSS 및 JS 전처리기 설정

* 전처리기를 사용하면 브라우저에서 기본적으로 지원하지 않는 CSS 및 자바스크립트 기능\(예: CSS 변수\)을 사용할 수 있습니다.
* 전처리기를 사용하면 소스 맵을 사용하여 원본 소스 파일을 렌더링된 출력으로 매핑할 수 있습니다.
* 웹 서버가 소스 맵을 제공할 수 있어야 합니다.
* 지원되는 전처리기를 사용하여 자동으로 소스 맵을 생성합니다.

### 전처리기란? <a id="%EC%A0%84%EC%B2%98%EB%A6%AC%EA%B8%B0%EB%9E%80"></a>

전처리기는 임의의 소스 파일을 가져와서 브라우저가 이해할 수 있는 것으로 변환시켜주는 도구입니다.

CSS를 출력으로 사용하며, \(아직\) 존재하지 않는 기능을 추가하는 데 사용됩니다. 즉 CSS 변수, 중첩 등이 대표적이며 이외에도 많은 가능성이 있습니다. 이 범주에서 특히 눈에 띄는 예로 [Saas](http://sass-lang.com/), [Less](http://lesscss.org/) 및 [Stylus](https://learnboost.github.io/stylus/) 등이 있습니다.

자바스크립트가 출력되는 경우, 이는 완전히 다른 언어로부터 변환\(컴파일\)하거나 언어 상위 집합 또는 새로운 언어 기준을 오늘날의 기준에 맞춰 변환\(트랜스파일\)해주는 역할을 합니다. 이 범주에서 특히 눈에 띄는 예는 [CoffeeScript](http://coffeescript.org/)와 ES6\([Babel](https://babeljs.io/) 사용\) 등입니다.



[https://developers.google.com/web/tools/setup/setup-preprocessors?hl=ko\#debugging-and-editing-preprocessed-content](https://developers.google.com/web/tools/setup/setup-preprocessors?hl=ko#debugging-and-editing-preprocessed-content)

