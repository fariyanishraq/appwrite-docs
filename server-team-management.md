# Teams API Reference

The **Teams service** allows you to group users of your project and share read and write access to resources like database documents or storage files.

Each user who creates a team becomes the team owner and can delegate the ownership role by inviting a new team member. Only team owners can invite new users to their team.

Base URL:
```
https://<REGION>.cloud.appwrite.io/v1
```

---

## Endpoints

### 1. Create Team

Create a new team. The user who creates the team will automatically be assigned as the owner of the team. Only users with the owner role can invite new members, add new owners, and delete or update the team.

```js
const sdk = require('node-appwrite');
const client = new sdk.Client()
    .setEndpoint('https://<REGION>.cloud.appwrite.io/v1')
    .setProject('<YOUR_PROJECT_ID>')
    .setSession('');

const teams = new sdk.Teams(client);
const result = await teams.create(
    '<TEAM_ID>',
    '<NAME>',
    [] // roles (optional)
);
```

---

### 2. Get Team

Get a team by its ID. All team members have read access for this resource.

```js
const result = await teams.get('<TEAM_ID>');
```

---

### 3. Get Team Preferences

Get the team's shared preferences by its unique ID. If a preference doesn't need to be shared by all team members, prefer storing them in user preferences.

```js
const result = await teams.getPrefs('<TEAM_ID>');
```

---

### 4. List Teams

Get a list of all the teams in which the current user is a member. You can use the parameters to filter your results.

```js
const result = await teams.list([], '<SEARCH>'); 
// queries (optional), search (optional)
```

---

### 5. Update Team Name

Update the team's name by its unique ID.

```js
const result = await teams.updateName('<TEAM_ID>', '<NAME>');
```

---

### 6. Update Team Preferences

Update the team's preferences by its unique ID.  
The object you pass is stored as-is and replaces any previous value. The maximum allowed prefs size is 64kB and throws an error if exceeded.

```js
const result = await teams.updatePrefs('<TEAM_ID>', {});
```

---

### 7. Delete Team

Delete a team using its ID. Only team members with the owner role can delete the team.

```js
const result = await teams.delete('<TEAM_ID>');
```

---

### 8. Invite Member to Team

Invite a new member to join your team. Provide an ID for existing users, or invite unregistered users using an email or phone number.

You only need to provide one of: user ID, email, or phone number. Appwrite will prioritize: `userId > email > phone` if more than one is provided.

Use the `url` parameter to redirect the user from the invitation email to your app.

```js
const result = await teams.createMembership(
    '<TEAM_ID>',
    [], // roles
    'email@example.com', // email (optional)
    '<USER_ID>', // userId (optional)
    '+12065550100', // phone (optional)
    'https://example.com', // url (optional)
    '<NAME>' // name (optional)
);
```

---

### 9. Get Team Membership

Get a team member by the membership unique ID. All team members have read access for this resource.

```js
const result = await teams.getMembership('<TEAM_ID>', '<MEMBERSHIP_ID>');
```

---

### 10. List Team Memberships

List a team’s members using the team’s ID. All team members have read access to this endpoint.

```js
const result = await teams.listMemberships('<TEAM_ID>', [], '<SEARCH>');
// queries (optional), search (optional)
```

---

### 11. Update Team Membership Roles

Modify the roles of a team member. Only team members with the owner role have access to this endpoint.

```js
const result = await teams.updateMembership(
    '<TEAM_ID>',
    '<MEMBERSHIP_ID>',
    [] // roles
);
```

---

### 12. Accept Team Invitation

Allow a user to accept an invitation to join a team after being redirected back to your app from the invitation email.

If successful, a session for the user is automatically created.

```js
const result = await teams.updateMembershipStatus(
    '<TEAM_ID>',
    '<MEMBERSHIP_ID>',
    '<USER_ID>',
    '<SECRET>'
);
```

---

### 13. Delete Team Membership

Allows a user to leave a team or for a team owner to delete the membership of any other team member.

You can also use this endpoint to delete a user membership even if it hasn’t been accepted yet.

```js
const result = await teams.deleteMembership('<TEAM_ID>', '<MEMBERSHIP_ID>');
```
