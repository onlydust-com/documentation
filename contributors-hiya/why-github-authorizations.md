# Why GitHub authorizations

### In a few words

We need the authorizations in order to allow you to have the BEST EXPERIENCE ever on OnlyDust. Or else it’s really limited and actually, not worth it 😟.&#x20;

Contributors log in via the **OnlyDust OAuth App**. This is required only when applying to an issue.

Here's how permissions work:

#### Permissions requested

**`read:user`**

Used to:

* Fetch contributor profile and public GitHub activity
* Feed our recommendation engine and contributor scoring
* Display profile data in the app

We call the GitHub API using the contributor’s token. This avoids rate-limiting issues (5000 req/h per token) that we’d hit using a single platform token.

No GitHub connection = no real login. Contributor gets read-only access.



* First time: contributor is asked to grant this permission during the application modal
* Later applications: no prompt unless the permission was revoked
* If permission is revoked: we’ll ask again

This permission lets us comment on GitHub issues **as the contributor**.

[GitHub OAuth scopes reference](https://docs.github.com/en/apps/oauth-apps/building-oauth-apps/scopes-for-oauth-apps) over here.
