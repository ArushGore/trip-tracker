# Raw Source: Initial User Prompt (2026-11-17)

This is trip tracker app, we provide this app for user who travel a lot and want to make sure that they count their days, the backend will be built on go + htmx + postgres, the mobile app will be built on flutter. If user wants they can just use mobile app and connect with their Google Sheets, this app can use trip-tracker backend or google sheets as backend. If user chooses to have google sheet as backend, then we need to add functionality to access google drive from mobile app. but that's phase 2. In Phase 1, app talks to our backend app (app folder). The agent documentation will be in wiki folder - you need to initialise wiki folder from https://github.com/ajeygore/llmwiki and then reprocess this information. 

You need to create a github repo in my account arushgore on github with trip-tracker name, and push all three folders there. This mac will be primary build machine, so we need to setup

1. Flutter SDK
2. Go SDK
3. OrbStack and then use postgres docker container with OrbStack, do NOT install postgres locally
4. Update homebrew and all other dependencies.

Reproces the wiki with everything you know, once you are done, Please let me know.

The way we will do development is 

1. Write an ISSUE in Github on trip-tracker repo
2. Then write tests and acceptance criteria
3. then do 3 lense review as Best SDLC practice for Go (monolith, in memory goroutines, persistence in database if required), product manager review for User Experience and Journey, UI Designer review for minimalist design based on Google Design Guidelines (incorporate all this) and when we ask for review, we create a 3 lense review and post it as comment on Issue and PR
4. once review lands, then only we start coding, a feature that cross cut mobile and app, we will need to refer issue in PR
5. At any time, we will never push to master branch, without review. (this is RED LINE, we never cross that)

The mobile app will talk to app on port 443 when in production, but can talk to non ssl port when in dev phase running locally. we will deploy app inside docker container in orbstack, but open it locally in browser with appropriate port forwarding.

Mobile app talks to app end points, and has same UI functionality.

Please setup this, add all this info to wiki, we will talk about creating first story when you are done.
