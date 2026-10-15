# Firebase Security Checklist for Traductorado

## Restrict the API Key
1. Go to Google Cloud Console → APIs & Services → Credentials.
2. Edit the API key.
3. Application restrictions: HTTP referrers (add your deployed domain).
4. API restrictions: Firebase only.

## Firestore Rules (recommended)
```js
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

Replace `YOUR_FIREBASE_API_KEY_HERE` in `plan-estudios.html` with your real key **after** applying restrictions.
