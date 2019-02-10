# What's an Exemplary PWA?

### Indexability & Social

* MetaData
  * Site's content is indexed by Google 
  * Schema. org metadata is provided where appropriate
* Social
  * Social metadata is provided where appropriate
  * [Canonical URLs](https://support.wix.com/ko/article/%EC%BA%90%EB%85%B8%EB%8B%88%EC%BB%AC-%ED%83%9C%EA%B7%B8-%EC%B6%94%EA%B0%80%ED%95%98%EA%B8%B0)\(자기 참조 태그\) are provided when necessary
* API
  * Pages use the History API

### User Experience

* Content doesn't jump as the page loads
* Pressing back from a detail page retains scroll position on the previous list page
* when tapped, inputs aren't obscured by the on screen keyboard
* Content is easily shareable from standalone or full screen mode
* Site is responsive across phone, tablet and desktop screen sizes
* Any app install prompts are not used excessively
* The Add to Home Screen prompt is intercepted

### Performance

* First load very fast even on 3G

### Caching

* Site uses cache-first networking
* Site appropriately informs the user when they're offline

### Push Notifications

* Provide context to the user about how notifications will be used
* UI encouraging users to turn on Push Notifications must not be overly aggressive
* Site dims the screen when permission request is showing
* Push notifications must be timely, precise and relevant
* Provides controls to enable and disable notification

### Additional Features

* User is logged in across devices via Credential Management API
* User can pay easily via native UI from Payment Request API

