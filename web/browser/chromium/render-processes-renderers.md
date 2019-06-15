# Render Processes\(Renderers\)

* Open Source
  * Blink - [https://www.chromium.org/blink](https://www.chromium.org/blink)
* Sharing the Render Process
  * 크롬은 새로운 윈도우나 탭을 열 경우 프로세스를 생성하고 Single Render View를 만든다. 매번 새로 만들기 때문에 프로세스를 재사용하는 것이 필요하고 사용자의 Process의 총 수가 너무 많아 질 경우, 이미 해당 도메인에 접근 해서 Process를 생성해놓은 도메인일때 존재하는 프로세스를 새로운 탭에 할당하는 전력이 필요하다.
  * [https://www.chromium.org/developers/design-documents/process-models](https://www.chromium.org/developers/design-documents/process-models)

