# Users API Reference

The **Users service** allows you to manage your project users. Use this service to search, block, and view your users' info, current sessions, and latest activity logs. You can also use the Users service to edit your users' preferences and personal info.

## Base URL

```
https://<REGION>.cloud.appwrite.io/v1
```

---

## Endpoints

### 1. Create User

Create a new user with optional email, phone, password, and name.

```js
const sdk = require('node-appwrite');
const client = new sdk.Client()
    .setEndpoint('https://<REGION>.cloud.appwrite.io/v1')
    .setProject('<YOUR_PROJECT_ID>')
    .setKey('<YOUR_API_KEY>');

const users = new sdk.Users(client);
const result = await users.create(
    '<USER_ID>',
    'email@example.com',
    '+12065550100',
    '',
    '<NAME>'
);
```

---

### 2. Create Argon2 User

Create a new user with an Argon2-hashed password.

```js
const result = await users.createArgon2User(
    '<USER_ID>',
    'email@example.com',
    'password',
    '<NAME>'
);
```

---

### 3. Create Bcrypt User

Create a new user with a Bcrypt-hashed password.

```js
const result = await users.createBcryptUser(
    '<USER_ID>',
    'email@example.com',
    'password',
    '<NAME>'
);
```

---

### 4. Create MD5 User

Create a new user with an MD5-hashed password.

```js
const result = await users.createMD5User(
    '<USER_ID>',
    'email@example.com',
    'password',
    '<NAME>'
);
```

---

### 5. Create PHPass User

Create a new user with a PHPass-hashed password.

```js
const result = await users.createPHPassUser(
    '<USER_ID>',
    'email@example.com',
    'password',
    '<NAME>'
);
```

---

### 6. Create Scrypt Modified User

Create a new user with a Scrypt Modified-hashed password.

```js
const result = await users.createScryptModifiedUser(
    '<USER_ID>',
    'email@example.com',
    'password',
    '<PASSWORD_SALT>',
    '<PASSWORD_SALT_SEPARATOR>',
    '<PASSWORD_SIGNER_KEY>',
    '<NAME>'
);
```

---

### 7. Create Scrypt User

Create a new user with a Scrypt-hashed password.

```js
const result = await users.createScryptUser(
    '<USER_ID>',
    'email@example.com',
    'password',
    '<PASSWORD_SALT>',
    null,
    null,
    null,
    '<NAME>'
);
```

---

### 8. Create SHA User

Create a new user with a SHA-hashed password.

```js
const result = await users.createSHAUser(
    '<USER_ID>',
    'email@example.com',
    'password',
    sdk.PasswordHash.Sha1,
    '<NAME>'
);
```

---

### 9. Get User

Get a user by their unique ID.

```js
const result = await users.get('<USER_ID>');
```

---

### 10. Get User Preferences

Get the preferences of a user by their ID.

```js
const result = await users.getPrefs('<USER_ID>');
```

---

### 11. List All Users

Get a list of all users in the project. You can filter results using queries.

```js
const result = await users.list([], '<SEARCH>');
```

---

### 12. Update Email

Update a user's email address.

```js
const result = await users.updateEmail('<USER_ID>', 'email@example.com');
```

---

### 13. Update Email Verification Status

Update the email verification status for a user.

```js
const result = await users.updateEmailVerification('<USER_ID>', false);
```

---

### 14. Enable/Disable MFA

Enable or disable Multi-Factor Authentication for a user.

```js
const result = await users.updateMfa('<USER_ID>', false);
```

---

### 15. Update Name

Update a user's name.

```js
const result = await users.updateName('<USER_ID>', '<NAME>');
```

---

### 16. Update Password

Update a user's password.

```js
const result = await users.updatePassword('<USER_ID>', '');
```

---

### 17. Update Phone Number

Update a user's phone number.

```js
const result = await users.updatePhone('<USER_ID>', '+12065550100');
```

---

### 18. Update Phone Verification Status

Update the phone verification status for a user.

```js
const result = await users.updatePhoneVerification('<USER_ID>', false);
```

---

### 19. Update Labels

Update the labels associated with a user (used for resource access control).

```js
const result = await users.updateLabels('<USER_ID>', []);
```

---

### 20. Update Preferences

Update a user’s preferences as a key-value object.

```js
const result = await users.updatePrefs('<USER_ID>', {});
```

---

### 21. Update Status

Update a user's account status (e.g., block/unblock).

```js
const result = await users.updateStatus('<USER_ID>', false);
```

---

### 22. Delete User

Delete a user permanently (releases their ID). Make sure to delete any related resources before deletion.

```js
const result = await users.delete('<USER_ID>');
```

---

### 23. Create Messaging Target

Create a messaging target (e.g., push notification token) for a user.

```js
const result = await users.createTarget(
    '<USER_ID>',
    '<TARGET_ID>',
    sdk.MessagingProviderType.Email,
    '<IDENTIFIER>',
    '<PROVIDER_ID>',
    '<NAME>'
);
```

---

### 24. Get Messaging Target

Get a specific messaging target by its ID.

```js
const result = await users.getTarget('<USER_ID>', '<TARGET_ID>');
```

---

### 25. List Messaging Targets

List all messaging targets associated with a user.

```js
const result = await users.listTargets('<USER_ID>', []);
```

---

### 26. Update Messaging Target

Update a messaging target.

```js
const result = await users.updateTarget(
    '<USER_ID>',
    '<TARGET_ID>',
    '<NEW_IDENTIFIER>',
    '<NEW_PROVIDER_ID>',
    '<NEW_NAME>'
);
```

---

### 27. Delete Messaging Target

Delete a messaging target.

```js
const result = await users.deleteTarget('<USER_ID>', '<TARGET_ID>');
```

---

### 28. Create Session

Create a session for a user.

```js
const result = await users.createSession('<USER_ID>');
```

---

### 29. Create Token

Create a token with a secret key for logging in.

```js
const result = await users.createToken('<USER_ID>', 4, 60);
```

---

### 30. Create JWT

Create a JSON Web Token for authenticating on behalf of the user.

```js
const result = await users.createJWT('<USER_ID>', '<SESSION_ID>', 0);
```

---

### 31. List Sessions

List all active sessions for a user.

```js
const result = await users.listSessions('<USER_ID>');
```

---

### 32. Delete Session

Delete a specific session for a user.

```js
const result = await users.deleteSession('<USER_ID>', '<SESSION_ID>');
```

---

### 33. Delete All Sessions

Delete all sessions for a user.

```js
const result = await users.deleteSessions('<USER_ID>');
```

---

### 34. List Memberships

List all team memberships for a user.

```js
const result = await users.listMemberships('<USER_ID>', [], '<SEARCH>');
```

---

### 35. List Logs

List the latest security logs for a user.

```js
const result = await users.listLogs('<USER_ID>', []);
```

---

### 36. List Identities

List identities for all users.

```js
const result = await users.listIdentities([], '<SEARCH>');
```

---

### 37. Delete Identity

Delete an identity by its unique ID.

```js
const result = await users.deleteIdentity('<IDENTITY_ID>');
```

---

### 38. Generate MFA Recovery Codes

Generate recovery codes for MFA backup.

```js
const result = await users.createMfaRecoveryCodes('<USER_ID>');
```

---

### 39. Get MFA Recovery Codes

Retrieve previously generated MFA recovery codes.

```js
const result = await users.getMfaRecoveryCodes('<USER_ID>');
```

---

### 40. List MFA Factors

List available MFA factors for a user.

```js
const result = await users.listMfaFactors('<USER_ID>');
```

---

### 41. Regenerate MFA Recovery Codes

Regenerate MFA recovery codes.

```js
const result = await users.updateMfaRecoveryCodes('<USER_ID>');
```

---

### 42. Delete MFA Authenticator

Delete an MFA authenticator for a user.

```js
const result = await users.deleteMfaAuthenticator('<USER_ID>', sdk.AuthenticatorType.Totp);
```
