
# Kubernetes Git Cluster

I have no idea how to accomplish this yet, but git is DVCS so it should be feasible.

Ideas:
 * https://github.com/RalfJung/git-mirror
 * https://github.com/solsson/docker-httpd/tree/master/git
 * https://github.com/kakwa/git-create.cgi

## Gogs

[Gogs](https://gogs.io/) has a [migrate](https://github.com/gogits/go-gogs-client/wiki/Repositories#migrate) with `mirror` feature that could provide basic synchronization. The problem is that it's one-way, and runs on timer instead of hooks.
