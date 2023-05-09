- [Backend As A Service](#backend-as-a-service)
  - [ⓘ Note: This entire page is very "work-in-progress."](#-note-this-entire-page-is-very-work-in-progress)
  - [Links](#links)
  - [Firebase CLI](#firebase-cli)
  - [Firebase Project Setup](#firebase-project-setup)
  - [Firebase Project Setup With Next.js](#firebase-project-setup-with-nextjs)
    - [Firebase Console: Add a **project**](#firebase-console-add-a-project)
    - [Firebase Console: Add an **app**](#firebase-console-add-an-app)
    - [Firebase Console: Add authentication](#firebase-console-add-authentication)
    - [Start the dev server](#start-the-dev-server)

# Backend As A Service

## ⓘ Note: This entire page is very "work-in-progress."

> ⓘ TODO: Fix or delete this page

Offloading functionality for your website, such as analytics, data storage, code hosting, database hosting, etc.

> ⓘ Note: Google Firebase has undergone quite a few changes from v8 to v9, and a lot of the information taught by Odin was incorrect, which slowed me down by quite a bit. I ended up just using google's documentation and trying things. The final key in understanding, for me, was converting my old "Library" project from earlier in the course to use Firebase.

## Links

| Service                                                                          | Company | Description                                       |
| -------------------------------------------------------------------------------- | ------- | ------------------------------------------------- |
| [Firebase Console](https://console.firebase.google.com/)                         | Google  | The place to configure all your firebase projects |
| [Firebase Docs](https://firebase.google.com/docs/build)                          | Google  | Use google's documentation.                       |
| [Firebase Codelab (tutorial)](https://firebase.google.com/codelabs/firebase-web) | Google  | Tutorial showing how to build a chat web app      |
| [AWS Amplify](https://aws.amazon.com/amplify/)                                   | Amazon  |                                                   |
| [Heroku Pricing](https://www.heroku.com/pricing)                                 | Heroku  |                                                   |
| [Firebase Products](https://firebase.google.com/products-build)                  | Google  |                                                   |
| [Firebase Cloud Firestore](https://firebase.google.com/docs/firestore)           | Google  |                                                   |
| [Firebase Hosting](https://firebase.google.com/products/hosting)                 | Google  |                                                   |
| [Firebase Cloud Storage](https://firebase.google.com/products/storage)           | Google  |                                                   |
| [Firebase Authentication](https://firebase.google.com/products/auth)             | Google  |                                                   |

## Firebase CLI

```
firebase deploy --except functions
```

## Firebase Project Setup

See Google Documentation: [Add Firebase to your Javascript Project](https://firebase.google.com/docs/web/setup?hl=en)

1. Create a Firebase project and register your app
2. Install the SDK and initialize Firebase (config copy/paste from console)
3. Access Firebase in your app (write code that utilizes firebase services)
4. Use a modular bundler (webpack/Rollup) for size reduction

Bonus: Ensure permissions for your database support the chosen hosting method.

## Firebase Project Setup With Next.js

> ⓘ Note: This will provide a starting point, and lists a few commands.

```
npx create-next-app@latest <project-name>
```

- typescript: no
- eslint: yes
- tailwindcss: yes
- src-dir: yes
- app-dir: no
- aliases? (enter/no)

```
cd <project-name>
npm install firebase
npm install -g firebase-tools
mkdir firebase
touch firebase/auth.js
touch firebase/firebase.js
```

### Firebase Console: Add a **project**

At the [Google Firebase Console](console.firebase.google.com), choose "Add project." Leave analytics checked or disable it. It doesn't matter.

### Firebase Console: Add an **app**

Add a web app by clicking on the `</>` button, near the iOS+ and android buttons. Give it an alias, like "[project-name] web", just to differentiate it in case you make an ios or android version later. Choose not to set up hosting, for now.

Copy the code snippet for the firebase configuration, and paste it into `firebase/firebase.js`

### Firebase Console: Add authentication

On the left bar, click Build, choose Authentication, and click on Get started. Choose the providers you wish to support. (Ensure you toggle the "Enable" slider, configure any required options, and click "Save")

### Start the dev server

```
npm run dev
```
