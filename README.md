# Auth in SvelteKit

There are three files that have been modified from the template to showcase authentication.

*Note: this example uses Google authentication because it's easiest with Firebase.*

## database.js

### Setup 

This file contains all of the logic for interacting with the database.

At the start, it imports all the Firebase products that the app uses, as well as the `user` store for keeping track of the user across different pages/components.

The next chunk of code is all for connecting to your Firebase database and setting up the variables that the other functions will use, like `auth` and `db`.

*Most of this code is given to you when you create a new Firebase database in the [Google Console](https://console.firebase.google.com/).

Sources:
 * [Setup](https://firebase.google.com/docs/database/web/start)

### signup()

The `signin` function uses the built-in `signInWithPopup()` function from Firebase to let Google handle the entire login process. This takes all of the pain away from your own app.

Next, it saves some key information from the user's Google login to the `user` store so it can be used anywhere in your app.

Finally, it saves the user into the database so you can later add more info about them, like their orders or preferences.

Sources:
 * [Signin](https://firebase.google.com/docs/auth/web/google-signin#handle_the_sign-in_flow_with_the_firebase_sdk)
 * [Writing to database](https://firebase.google.com/docs/firestore/manage-data/add-data#add_a_document)

### login()

The `login` function uses the same `signInWithPopup()` from Firebase.

The difference is the next step, in which it tries to get the user's info from the data using their `uid` from their Google login.

It checks to see if the database record of the user `exists`. If it does, then the `user` store gets updated with the right information. If not, then it logs an error.

*You may need to add your own error handling code if you want different behaviour, like prompting the user to sign up.*

Sources:
 * [Signin](https://firebase.google.com/docs/auth/web/google-signin#handle_the_sign-in_flow_with_the_firebase_sdk)
 * [Reading from database](https://firebase.google.com/docs/firestore/query-data/get-data#get_a_document)

### logout()

The `logout` function uses the built-in `signOut` function from Firebase, which handles disconnecting the app from the user's Google login.

The second and last step is to reset the `user` store.

Sources:
 * [Signout](https://firebase.google.com/docs/auth/web/google-signin#next_steps)

## stores.js

This file is for the 'store' variables that can be used on any page in the app.

It imports the stores from Svelte and then create a `user` store as an object with two fields: `uid` and `email`.

*Creating these fields at the start helps display them nicer when they're empty.*



## index.svelte

The main page contains basic code for connecting buttons to functions and inputs to variables.
