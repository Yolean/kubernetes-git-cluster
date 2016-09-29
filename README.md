
# Kubernetes Git Cluster

I have no idea how to accomplish this yet, but git is DVCS so it should be feasible.

Ideas:
 * https://github.com/RalfJung/git-mirror
 * https://github.com/solsson/docker-httpd/tree/master/git
 * https://github.com/kakwa/git-create.cgi

## Gogs

[Gogs](https://gogs.io/) has a [migrate](https://github.com/gogits/go-gogs-client/wiki/Repositories#migrate) with `mirror` feature that could provide basic synchronization. It also supports auto-creating users from proxy headers, https://github.com/gogits/gogs/issues/165, so databases wouldn't have to be in sync. The problem is that "mirror" is one-way, and runs on timer instead of hooks, as tracked in https://github.com/gogits/gogs/issues/3476.

There's an experimental setup in `build-contracts/`:
 * Run `docker-compose up` and check `docker-compose port cluster-perimeter 80`
 * Visit `http://localhost:30080/headerscheck/` to see that your username is passed on as header.
 * Visit `http://gogsleader:30080/` to create a repository on the master (you need a hosts file entry for your docker machine, something like `127.0.0.1	gogsleader`).
 * Visit `http://localhost:30080/` to create a "Migration" with the `mirror` option enabled.
