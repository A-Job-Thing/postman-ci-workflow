## CI Integration for A Job Thing 

Research and development for building resilience and scalable Postman APIs automation test into CI pipeline

- Using TravisCI
- Using Github Actions

#### Design System

![Capture 4](https://user-images.githubusercontent.com/86886088/124476155-b5514080-ddcc-11eb-9ef5-b48ce4f2dcf1.PNG)

Currently, we're only setup using Github Actions due limitations for TravisCI. Note for the build status, if the status is failing there are several reasons why it's happening:

- Internal changes for test script in codebase
- Test scenario for API response time exceeds than limitation (set to 2500ms)
- In postman collection, the failed test still not updated yet
- External changes for API (whether its happen on the payload, endpoint or something else)
- This API will be collected periodically for once per every week (using cronjob), due limitation for hooks the postman collection and TravisCI usage

The CI flow for this API development is straightforward. Every Backend side has been deployed the current features, it will be tracking and triggered with Postman monitor (the feature its the same like cronjob), for the validation itself whether the API that has been deployed by Backend side is fail or not, in Postman collections there will be automation testscript for checking if the APIs endpoint is already on the latest build from Backend side or not. Afterwards, the Postman collections (that bundled as `.json`) will be hooks by Github Actions to proceed the automation test. If the build is **pass**, then it automatically sent a badge status into Postman documentation (like in image below), otherwise if the build is **falling** currently only notified to myself through email.

![Capture 5](https://user-images.githubusercontent.com/86886088/124477249-fe55c480-ddcd-11eb-84db-65824a0c8092.PNG)

#### Caveats

**TBD**

