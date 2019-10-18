## Setup Instructions

This sample demonstrates Actions on Google features for use on Google Assistant -- using the [Node.js client library](https://github.com/actions-on-google/actions-on-google-nodejs) and deployed on [Cloud Functions for Firebase](https://firebase.google.com/docs/functions/).

## Setup Instructions
### Prerequisites
1. Node.js and NPM
    + We recommend installing using [NVM](https://github.com/creationix/nvm)
1. Install the [Firebase CLI](https://developers.google.com/actions/dialogflow/deploy-fulfillment)
    + We recommend using version 6.5.0, `npm install -g firebase-tools@6.5.0`
    + Run `firebase login` with your Google account

### Configuration
#### Actions Console
1. From the [Actions on Google Console](https://console.actions.google.com/), New project (this will become your *Project ID*) > **Create project** > under **More options** > **Conversational**
1. From the top menu under **Develop** > **Actions** (left nav) > **Add your first action** > **BUILD** (this will bring you to the Dialogflow console) > Select language and time zone > **CREATE**.
1. In the Dialogflow console, go to **Settings** ⚙ > **Export and Import** > **Restore from zip** using the `agent.zip` in this sample's directory.

#### Firebase Deployment
1. On your local machine, in the `functions` directory, run `npm install`
1. Run `firebase deploy --project {PROJECT_ID}` to deploy the function
    + To find your **Project ID**: In [Dialogflow console](https://console.dialogflow.com/) under **Settings** ⚙ > **General** tab > **Project ID**.

#### Dialogflow Console
1. Return to the [Dialogflow Console](https://console.dialogflow.com) > select **Fulfillment** > **Enable** Webhook > Set **URL** to the **Function URL** that was returned after the deploy command > **SAVE**.
    ```
    Function URL (googleio): https://${REGION}-${PROJECT_ID}.cloudfunctions.net/googleio
    ```

### Google Sign In (Account Linking)
**Required if testing the personal schedule feature.**
1. Create a copy of default.json in the `functions/config` directory called `dev.json`
1. In the [Actions on Google console](https://console.actions.google.com) > from the top menu **Develop** > **Account Linking** (left nav):
    + **Account Creation**: select `Yes, allow users to sign up for new accounts via voice`
    + **Linking Type**: **Google Sign In**.
    + **Client Information**: copy the **Client ID** and paste into `functions/config/dev.json`

### Cloud Firestore on Firebase
**Required if testing the personal schedule feature.**
1. Log into the [Firebase Console](https://console.firebase.google.com) > select your *Project ID*.
1. Under **Develop** > **Authentication** > **Sign-in Method** tab > for Sign-in provider select **Email/Password** > **Enable** Allow users to sign up using their email address and password > **Save**.
1. From the **Users** tab > select **Add user** > add **Gmail** email address you will use for testing.
    + For testing this sample, the password can be "abc123"
    + Take note of the User UID.
1. Under **Develop** > **Database** > **Create Database** > select **Start in test mode** then > **Enable**.
1. Add some test user data for the User UID created previously. See the
[Firestore Data](DATA.md) format for information on how this data is
organized.
1. From the Firebase console, select ⚙ > **Project settings** >  **Service Accounts** tab > **Generate new private key** to download a service key > save key as `serviceKey.json` into the `functions/config` directory path.
1. From `functions/`, redeploy by running `firebase deploy --project {PROJECT_ID}`

### Running this Sample
+ Return to the [Dialogflow Console](https://console.dialogflow.com) > from the left navigation menu, click **Integrations** > **Integration Settings** under Google Assistant > Enable **Auto-preview changes** >  **Test** to open the Actions on Google simulator then say or type `Talk to my test app`.
+ You can test your Action on any Google Assistant-enabled device on which the Assistant is signed into the same account used to create this project. Just say or type, “OK Google, talk to my test app”.
+ You can also use the Actions on Google Console simulator to test most features and preview on-device behavior.

## References & Issues
+ Questions? Go to [StackOverflow](https://stackoverflow.com/questions/tagged/actions-on-google), [Assistant Developer Community on Reddit](https://www.reddit.com/r/GoogleAssistantDev/) or [Support](https://developers.google.com/actions/support/).
+ For bugs, please report an issue on Github.
+ Actions on Google [Documentation](https://developers.google.com/actions/extending-the-assistant)
+ Actions on Google [Codelabs](https://codelabs.developers.google.com/?cat=Assistant)
+ [Webhook Boilerplate Template](https://github.com/actions-on-google/dialogflow-webhook-boilerplate-nodejs) for Actions on Google

## Make Contributions
Please read and follow the steps in the [CONTRIBUTING.md](CONTRIBUTING.md).

## License
See [LICENSE](LICENSE).

## Terms
Your use of this sample is subject to, and by using or downloading the sample files you agree to comply with, the [Google APIs Terms of Service](https://developers.google.com/terms/).