# get-docker-run

`get-docker-run` is a (very) simple bash script that will do it's best to get the original `docker run` command from a running container.

It's using [jq](https://github.com/stedolan/jq) and `sed`. If you are on a mac, you'll need to install GNU sed (`brew install gnu-sed`)

Usage
---

```
$ get-docker-run <ID|name>
```

Example:
```
$ docker run -v "/tmp:/tmp" -e "ENV=ENVVAR" --volumes-from othercontainer --link mydatabase:db.local --dns 10.1.0.1 --name test busybox:latest
$ ./get-docker-run test
docker run -v "/tmp:/tmp" -e "ENV=ENVVAR" --volumes-from othercontainer --link /mydatabase:/test/db.local --dns 10.1.0.1 --name test --hostname a15898e0cd05 busybox:latest
```
