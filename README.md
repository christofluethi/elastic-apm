# Application Performance Monitoring with Elastic APM

Elastic APM consists of four components:

* Elasticsearch
* APM agents
* APM Server
* Kibana APM UI

![Elastic APM](https://camo.githubusercontent.com/c4deec730461f148794cf2de2db89b9b389397a5/68747470733a2f2f7777772e656c61737469632e636f2f67756964652f656e2f61706d2f6765742d737461727465642f63757272656e742f61706d2d6172636869746563747572652e706e67)

## Links
* [Elastic APM](https://www.elastic.co/solutions/apm)
* [APM Server Reference](https://www.elastic.co/guide/en/apm/server/6.3/index.html)
* [Elastic APM JavaScript Agent](https://github.com/elastic/apm-agent-js-base)
* [Elastic APM Java Agent](https://www.elastic.co/blog/elastic-apm-java-agent-beta-released)


## Quickstart

Start APM Stack
```
docker-compose -p apm up -d
```
Run Java Application with Elastic APM Agent. Download Agent from [Maven Central](http://search.maven.org/#search%7Cga%7C1%7Ca%3Aelastic-apm-agent).


Allow to specify `JVM_ARGS` using environment variables for your docker container.
```
CMD ["sh", "-c", "java $JVM_ARGS -jar /opt/thorntail.jar $APP_ARGS"]
```

Sample configuration for docker container
```
  info:
    image: docker.shaped.ch/microprofile-info
    hostname: info
    networks:
      - mpdemo
    ports:
      - 8181:8080
    environment:
      - JVM_ARGS=-javaagent:/opt/apm-agent.jar -Delastic.apm.server_urls=http://hostname:8200 -Delastic.apm.service_name=info -Delastic.apm.application_packages=ch.shaped
    volumes:
      - ./elastic-apm-agent-1.0.1.jar:/opt/apm-agent.jar

```

Point your browser to `http://localhost:5601` to get to the kibana UI

