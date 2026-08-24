# Vahnija Global School Website

A responsive school website with online admissions, contact messages, Firebase authentication, Firestore data management, student records, and dynamic school activities.

## Features

- Public school information and responsive layout
- Online admission form
- Contact message storage in Firestore
- Firebase email/password admin login
- Admin dashboard for applications and messages
- Student records with fee tracking
- Dynamic activities carousel
- Activity image uploads up to 1.5 MB
- Netlify Functions support for Firebase configuration

## Local Setup

1. Copy `.env.example` to `.env`.
2. Add the Firebase web configuration values to `.env`.
3. Serve the project with a local web server. For example:

```powershell
python -m http.server 5501
```

Open `http://localhost:5501` in a browser.

The application reads Firebase configuration from the Netlify function first, then from `.env` when the function is unavailable.

## Environment Variables

Required variables:

```text
FIREBASE_API_KEY
FIREBASE_AUTH_DOMAIN
FIREBASE_PROJECT_ID
FIREBASE_STORAGE_BUCKET
FIREBASE_MESSAGING_SENDER_ID
FIREBASE_APP_ID
```

Optional variable:

```text
FIREBASE_MEASUREMENT_ID
```

Never commit `.env`. It is ignored by Git. Use `.env.example` as the template.

## Firebase Setup

- Enable Email/Password authentication in Firebase Authentication.
- Create an admin user in Firebase Authentication.
- Publish the Firestore rules from `firestore.rules`.
- The `activities` collection allows public reads and authenticated writes.

## Netlify Deployment

1. Connect the repository to Netlify.
2. Netlify will use the settings in `netlify.toml`.
3. Add the required `FIREBASE_*` variables in Netlify site environment variables.
4. Deploy or trigger a new deployment.

The Firebase configuration endpoint is available at `/api/firebase-config` and is backed by the Netlify Function in `netlify/functions/firebase-config.js`.

## Project Structure

```text
index.html                 Main website markup
style.css                  Website styles and responsive layout
app.js                     Firebase, forms, dashboard, and carousel logic
firestore.rules            Firestore security rules
netlify.toml               Netlify publish, function, and redirect settings
netlify/functions/         Netlify Functions
.env.example               Firebase environment variable template
```
