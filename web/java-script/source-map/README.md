# Source Map

#### 소스 맵이란? <a id="%EC%86%8C%EC%8A%A4_%EB%A7%B5%EC%9D%B4%EB%9E%80"></a>

소스 맵이란 일종의 JSON 기반 매핑 형식으로, 축소된 파일과 그 소스 사이의 관계를 만들어주는 역할을 합니다. 프로덕션용으로 빌드하면 자바스크립트 파일을 축소하고 조합하는 작업 외에도 원본 파일에 대한 정보를 담은 소스 맵을 만들게 됩니다.

#### 소스 맵의 작동 원리 <a id="%EC%86%8C%EC%8A%A4_%EB%A7%B5%EC%9D%98_%EC%9E%91%EB%8F%99_%EC%9B%90%EB%A6%AC"></a>

CSS 전처리기는 CSS 파일을 만들 때마다 컴파일된 CSS에 더하여 소스 맵 파일\(.map\)도 생성합니다. 이 소스 맵 파일은 JSON 파일로 각각의 생성된 CSS 선언과 소스 파일에서 해당 줄 사이의 매핑을 정의합니다.

각 CSS 파일에는 자신의 소스 맵 파일을 지정하는 주석이 포함되어 있고, 이는 파일의 마지막 줄에 달린 특별 주석\(special comment\)에 포함됩니다.

[https://developers.google.com/web/tools/setup/setup-preprocessors?hl=ko\#debugging-and-editing-preprocessed-content](https://developers.google.com/web/tools/setup/setup-preprocessors?hl=ko#debugging-and-editing-preprocessed-content)

