# Why GitHub authorizations

### The overview

It’s not scary, promise. We need the authorizations in order to allow you to have the BEST EXPERIENCE ever on OnlyDust. Or else it’s really limited and actually, not worth it 😟.

<figure><img src="../.gitbook/assets/Screenshot 2025-07-07 at 15.47.05 (1).png" alt=""><figcaption></figcaption></figure>

So why do we ask it:

* We need to ensure that you’re truly owner of the GitHub organization (to avoid scams and unpleasant things). If you’re not, we need to you ask the owner (the admin) to grant the access.
* Github enforces a rate limit on its API \~ 5000 calls/hours. It’s not enough when we have more than 20K repos on our platform that we need to sync, in real time. Hence, to bypass this limitation, we need to use integrations provided by GitHub with the GitHub app.
  * If you’re keen to read more about this our Head of Engineering made a very detailed doc over here.
* By accepting the authorizations, you’ll allow us to have “write rights” (tongue twister there!) so that when you assign/unassign issues on our platform, it shows up directly on GitHub.

So, the best way to do that is through the Oauth token feature from the GH app.

### The details

More info over here written by our Head of Engineering.&#x20;

The Contributor App and Maintainer App have **separate authentication flows**. That’s by design. They need different permissions, and they handle different types of GitHub interactions.

***

### GitHub Authentication Models

#### GitHub OAuth App

Used for logging in with a personal GitHub account.

* The user connects their GitHub account and authorizes the OnlyDust OAuth App.
* This allows us to **act on their behalf** using a personal token.
  * Example: when a contributor applies to an issue, we comment on that issue **as the user**. GitHub shows the user as the comment author.

OAuth App is always linked to the user’s **personal GitHub account**, not an organization.

***

#### GitHub App

Used when someone installs the OnlyDust GitHub App on a GitHub **organization**.

* This grants us access to the selected repos with the permissions defined in our app config.
* We receive a GitHub App installation token, which we use to:
  * Call the GitHub API with the appropriate scope
  * Receive events via GitHub webhooks

This is org-level access, managed through GitHub’s installation and permission flow.

***

#### GitHub App with OAuth Enabled

GitHub lets you enable OAuth on a GitHub App.

* We use this setup to get **both**:
  * Access to act on behalf of the user
  * Access to the organization and its repos

This hybrid approach is used in the Maintainer App.

***

## Maintainer App

Maintainers log in using the **OAuth flow built into our GitHub App**.

#### How it works

1.  **Login via OAuth**

    Maintainer logs in with their personal GitHub account using the GitHub App’s OAuth flow.
2.  **Install the GitHub App**

    After login, they are redirected to GitHub to install the app on an organization where they’re a member.
3. **Request or grant access**
   * If they’re a member (not admin), they request access
   * If they’re an admin, they can grant access immediately
   * They select the repos to grant access to
4.  **Return to Maintainer App**

    Once installation is complete, they’re redirected back to OnlyDust to select which repos to sync.

***

### Why OAuth + GitHub App?

In the past, we used the GitHub App alone. That had problems:

* Users could manage repos without being actual members of the GitHub org
* GitHub’s permission model wasn’t enforced

Now, by adding OAuth:

* We get a user token with the **real permissions** of that user on the org
* GitHub enforces what actions they can and can’t do
  * Example: if a user can’t assign issues in the org, they won’t be able to do it on OnlyDust either

More on [how this works here](https://docs.github.com/en/apps/creating-github-apps/authenticating-with-a-github-app/generating-a-user-access-token-for-a-github-app).\


***

### Permissions Requested by the GitHub App

#### Repo-level permissions (all selected repos, including private)

* Issues
* Pull requests
* Repository metadata
* Collaboration settings

These are visible during installation and defined in the GitHub App config.

#### Organization-level permissions

* Read access to metadata
* Used to verify org membership
* Enforces permission checks through OAuth intersection

***

### Why Maintainers Must Install the GitHub App

#### 1. Enforce org-level access

Only org members (or approved users) can install and manage repos via OnlyDust. One org **owner** needs to install the app and grant access.

#### 2. Avoid GitHub rate limits

GitHub caps API usage at 5000 calls/hour per token. That's not enough for our scale.

Using GitHub App installations:

* Each org gets its own scoped token
* API usage is spread across orgs

#### 3. Real-time events via webhook

We receive webhook events from GitHub:

* Issue creation
* PR activity
* Assignments, etc.

This reduces the number of API calls and keeps data up-to-date.

***

## Contributor App &#x20;

`https://www.onlydust.com/`

Contributors log in via the **OnlyDust OAuth App**. Here's how permissions work:

#### Permissions requested

**`read:user`**

Used to:

* Fetch contributor profile and public GitHub activity
* Feed our recommendation engine and contributor scoring
* Display profile data in the app

We call the GitHub API using the contributor’s token. This avoids rate-limiting issues (5000 req/h per token) that we’d hit using a single platform token.

No GitHub connection = no real login. Contributor gets read-only access.

This is required only when applying to an issue.

* First time: contributor is asked to grant this permission during the application modal
* Later applications: no prompt unless the permission was revoked
* If permission is revoked: we’ll ask again

This permission lets us comment on GitHub issues **as the contributor**.

[GitHub OAuth scopes reference](https://docs.github.com/en/apps/oauth-apps/building-oauth-apps/scopes-for-oauth-apps) over here.\


