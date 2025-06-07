### Account API Reference

The **Account service** allows you to authenticate and manage a user account.

You can use the account service to:
- Update user information
- Retrieve the user sessions across different devices
- Fetch the user security logs with recent activity

#### Overview

Register new user accounts using one of the following endpoints:
- `Create Account`
- `Create Magic URL session`
- `Create Phone session`

Once authenticated, a new session object will be created, allowing the user to access their private data and settings.

This service also exposes an endpoint to save and read the user preferences as a key-value object. This feature is handy if you want to allow extra customization in your app. Common usage includes saving the user's preferred locale, timezone, or custom app theme.

Use the following base URL for all requests:

```
https://<REGION>.cloud.appwrite.io/v1
```

---

## Endpoints

### 1. Create Account

Used to register a new user.

```js
const sdk = require('node-appwrite');
const client = new sdk.Client()
    .setEndpoint('https://<REGION>.cloud.appwrite.io/v1')
    .setProject('<YOUR_PROJECT_ID>');

const account = new sdk.Account(client);
const result = await account.create(
    '<USER_ID>',
    'email@example.com',
    '',
    '<NAME>'
);
```

---

### 2. Get Current User

Fetches details of the currently logged-in user.

```js
const result = await account.get();
```

---

### 3. Get User Preferences

Get the preferences as a key-value object for the currently logged-in user.

```js
const result = await account.getPrefs();
```

---

### 4. Update Email

Update the current user's email address.

```js
const result = await account.updateEmail(
    'email@example.com',
    'password'
);
```

---

### 5. Update Name

Update the current user's name.

```js
const result = await account.updateName('<NAME>');
```

---

### 6. Update Password

Update the current user's password.

```js
const result = await account.updatePassword('', 'password');
```

---

### 7. Update Phone Number

Update the current user's phone number.

```js
const result = await account.updatePhone('+12065550100', 'password');
```

---

### 8. Update Preferences

Update the current user's preferences.

```js
const result = await account.updatePrefs({});
```

---

### 9. Block User

Block the current user account (does not delete it).

```js
const result = await account.updateStatus();
```

---

### 10. Create Anonymous Session

Allow a user to create an anonymous account.

```js
const result = await account.createAnonymousSession();
```

---

### 11. Create Email/Password Session

Log in using email and password.

```js
const result = await account.createEmailPasswordSession(
    'email@example.com',
    'password'
);
```

---

### 12. Create Session via Token

Create a session using a token.

```js
const result = await account.createSession('<USER_ID>', '<SECRET>');
```

---

### 13. Get Session by ID

Retrieve a specific session.

```js
const result = await account.getSession('<SESSION_ID>');
```

---

### 14. List Sessions

List all active sessions for the current user.

```js
const result = await account.listSessions();
```

---

### 15. Delete Session

Logout on a specific device.

```js
const result = await account.deleteSession('<SESSION_ID>');
```

---

### 16. Delete All Sessions

Logout from all devices.

```js
const result = await account.deleteSessions();
```

---

### 17. Create Email Verification Token

Send a verification email to the user.

```js
const result = await account.createVerification('https://example.com');
```

---

### 18. Complete Email Verification

Complete the email verification process.

```js
const result = await account.updateVerification('<USER_ID>', '<SECRET>');
```

---

### 19. MFA (Multi-Factor Authentication)

Add or manage multi-factor authentication methods.

##### Add Authenticator

```js
const result = await account.createMfaAuthenticator(sdk.AuthenticatorType.Totp);
```

##### Begin MFA Challenge

```js
const result = await account.createMfaChallenge(sdk.AuthenticationFactor.Email);
```

##### Complete MFA Challenge

```js
const result = await account.updateMfaChallenge('<CHALLENGE_ID>', '<OTP>');
```

##### Regenerate Recovery Codes

```js
const result = await account.updateMfaRecoveryCodes();
```

##### Delete Authenticator

```js
const result = await account.deleteMfaAuthenticator(sdk.AuthenticatorType.Totp);
```

---

### 20. List Identities

Get the list of identities for the current user.

```js
const result = await account.listIdentities();
```

---

### 21. Delete Identity

Delete an identity by its unique ID.

```js
const result = await account.deleteIdentity('<IDENTITY_ID>');
```

---

## Security Logs

Get the latest security activity logs for the current user.

```js
const result = await account.listLogs();
```

---

## Password Recovery

### Start Recovery Process

```js
const result = await account.createRecovery('email@example.com', 'https://example.com');
```

### Complete Recovery Process

```js
const result = await account.updateRecovery('<USER_ID>', '<SECRET>', '');
```

---

## Phone Verification

### Send SMS Verification Code

```js
const result = await account.createPhoneVerification();
```

### Complete Phone Verification

```js
const result = await account.updatePhoneVerification('<USER_ID>', '<SECRET>');
```

---

