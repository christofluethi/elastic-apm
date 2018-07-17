# Elastic APM 

Application Performance Monitoring with Elastic APM

Elastic APM consists of four components:

* Elasticsearch
* APM agents
* APM Server
* Kibana APM UI

![Elastic APM](https://camo.githubusercontent.com/c4deec730461f148794cf2de2db89b9b389397a5/68747470733a2f2f7777772e656c61737469632e636f2f67756964652f656e2f61706d2f6765742d737461727465642f63757272656e742f61706d2d6172636869746563747572652e706e67)

See
* https://www.elastic.co/solutions/apm
* https://www.elastic.co/blog/elastic-apm-java-agent-beta-released

Start APM Stack
```
docker-compose up -d
```
Run Java Application with Elastic APM Agent. Download Agent from [Maven Central](http://search.maven.org/#search%7Cga%7C1%7Ca%3A%22elastic-apm-agent%22).

```
java -javaagent:/path/to/elastic-apm-agent-<version>.jar \
     -Delastic.apm.server_url=http://localhost:8200 \
     -Delastic.apm.service_name=my-application \
     -Delastic.apm.application_packages=org.myapplication \
     -jar my-application.jar
```

Point your browser to `http://localhost:5601` to get to the kibana UI

