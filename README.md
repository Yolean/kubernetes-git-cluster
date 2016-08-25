
# Kubernetes Git Cluster

I have no idea how to accomplish this yet, but git is DVCS so it should be feasible.

Ideas:
 * https://github.com/RalfJung/git-mirror
 * https://github.com/solsson/docker-httpd/tree/master/git
 * https://github.com/kakwa/git-create.cgi

## Building containers locally

Go to your kubernetes host, like minikube, cd to your dev folder, then:
```
docker build -t local/yolean/git-httpd git-httpd/
```
