
# Idempotent complete Gogs->Gogs mirror setup

Purpose:

Try to make one Gogs instance contain the exact same git data as a master instance,
using Gogs' "mirror" feature.

Parameters:
 - Leader Gogs API base URL
 - Follower Gogs API base URL
 - Leader auth token
 - Follower auth token

Draft design:
 - Ask leader for a list of repositories.
 - For any organization that does not exist on the follower, create it.
 - For any repository that does not exist on the follower, create it as non-private `mirror`.
 - For any repository that does exist, assert that it has a mirror URL.

Caveats:
 - Only repositories visible to the auth'd user will be mirrored.
 - Stuff like Issues, PRs and Users won't follow. Ideally such stuff would be in git too.

### Example API use

Sources:
 * https://github.com/gogits/go-gogs-client/wiki/Repositories
 * https://github.com/valeriangalliat/gogs-migrate/blob/master/src/index.js
 * https://www.npmjs.com/package/gogs-client

```
curl -H "Authorization: token f0f1948b5492a5961cb18af0698b1aac1168d940" http://192.168.99.101:31299/api/v1/user/repos
```
