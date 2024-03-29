# Project Status

This is a work in progress Maths Game that will eventually include additional locations & DLC.

# Actions on Google: Trivia Game using Node.js

The Trivia Game lets users play an interactive game with various personas. Includes classic game show sounds and humor, for a touch of nostalgia.

You can also try out a hosted version of this game at [https://triviatemplate.com/](https://triviatemplate.com/).

## Setup Instructions

### Template Adjustment Steps
1. More detials can be found [here](https://medium.com/@leonnicholls/google-assistant-trivia-game-742f38cae5de).

### Deployment Steps
1. Use the [Actions on Google Console](https://console.actions.google.com) to add a new project with a name of your choosing.
    1. When selecting a template click the relevent category for your app.
    2. Under *Build* select *Actions*, *Add your first Action*, *Custom Intent*, *Build*
    3. This will take you to Dialogflow where you will import the intents you need
4. Click on the gear icon next to your project name to see the project settings.
5. Select *Export and Import*.
6. Select *Restore from zip*. Follow the directions to restore from the `TriviaGame.zip` file in this repo.
    1. You may need to download and extract this repo before you get started
7. Deploy the fulfillment webhook provided in the `functions` folder using [Google Cloud Functions for Firebase](https://firebase.google.com/docs/functions/) and the static resources needed by the project using [Firebase Hosting](https://firebase.google.com/docs/hosting/):
    1. Follow the instructions to [install the Firebase CLI](https://firebase.google.com/docs/hosting/quickstart#install-the-firebase-cli).
        1. May need to set the firebase alias using '"alias firebase="`npm config get prefix`/bin/firebase"'
    2. Run `firebase init`, and select to configure `Hosting` and `Functions`. Select the project you've previously created in the Actions on Google Console as default project. In the configuration wizard, accept all the default choices.
       1. Press space to select 'Functions: Configure and deploy Cloud Functions' & Hosting: Configure and deploy Firebase Hosting sites
       2. Select a language to write Cloud Funtiond (Javascript or Typescript) - Select JS
       3. Do you want to use ESLint to catch probable bugs and enforce style y/n? - Select y
       4. File xxx already exists. Overwite? y/n - Select y
       5. Do you want to install dependancies with NPM now? - Select y
       6. What do you want to use as your public directory? - /users/jhowling/firebase
       7. Configure as single-page app? - Select y
    3. Edit the database data with questions (questions.json) and prompts (prompts.json). Generate a private key using Firebase Settings/Service Accounts, and edit `functions/database.js` with the path to the JSON cert file. Now populate the database: `node database.js`
    4. Run `firebase deploy` and take note of the endpoint where the fulfillment webhook has been published. It should look like `Function URL (triviaGame): https://us-central1-YOUR_PROJECT.cloudfunctions.net/triviaGame`. The command will also deploy the static assets at `https://us-central1-YOUR_PROJECT.cloudfunctions.net/`.
8. Go back to the Dialogflow console and select *Fulfillment* from the left navigation menu. Enable *Webhook*, set the value of *URL* to the `Function URL` from the previous step, then click *Save*.
9. Select *Integrations* from the left navigation menu and open the *Settings* menu for Actions on Google.
10. Click *Test*.
11. Click *View* to open the Actions on Google simulator.
11. Type `Talk to my test app` in the simulator, or say `OK Google, talk to my test app` to any Actions on Google enabled device signed into your developer account.

For more detailed information on deployment, see the [documentation](https://developers.google.com/actions/dialogflow/deploy-fulfillment).

## References and How to report bugs
* Actions on Google documentation: [https://developers.google.com/actions/](https://developers.google.com/actions/).
* If you find any issues, please open a bug here on GitHub.
* Questions are answered on [StackOverflow](https://stackoverflow.com/questions/tagged/actions-on-google).

## How to make contributions?
Please read and follow the steps in the [CONTRIBUTING.md](CONTRIBUTING.md).

## License
See [LICENSE](LICENSE).

## Terms
Your use of this sample is subject to, and by using or downloading the sample files you agree to comply with, the [Google APIs Terms of Service](https://developers.google.com/terms/).

## Google+
Actions on Google Developers Community on Google+ [https://g.co/actionsdev](https://g.co/actionsdev).
