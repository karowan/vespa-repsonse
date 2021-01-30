Steps to reproduce

```shell
docker run --detach --name vespa-response --hostname vespa-container --volume `pwd`:/app --publish 8080:8080 vespaengine/vespa
```

```shell
docker exec -it vespa-response bash -c '/opt/vespa/bin/vespa-deploy prepare /app/src/main/application && /opt/vespa/bin/vespa-deploy activate'
```

```shell
docker exec vespa-response bash -c 'java -jar /opt/vespa/lib/jars/vespa-http-client-jar-with-dependencies.jar --verbose \
--file /app/feed/data.jl --host localhost --port 8080'
```
