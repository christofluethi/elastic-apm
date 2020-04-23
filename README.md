# Application Performance Monitoring with Elastic APM

Elastic APM consists of four components:

* Elasticsearch
* APM agents
* APM Server
* Kibana APM UI

## Links
* [Elastic APM](https://www.elastic.co/apm)
* [APM Server Reference](https://www.elastic.co/guide/en/apm/server/current/index.html)
* [Elastic APM JavaScript Agent](https://www.elastic.co/guide/en/apm/agent/rum-js/current/index.html)
* [Elastic APM Java Agent](https://www.elastic.co/guide/en/apm/agent/java/current/setup-javaagent.html)


## Quickstart

Start APM Stack
```
docker-compose -p apm up -d
```
Run Java Application with Elastic APM Agent. Download Agent from [Maven Central](http://search.maven.org/#search%7Cga%7C1%7Ca%3Aelastic-apm-agent).


Specify APM Agent with `-javaagent`
```
-XX:+PreserveFramePointer -javaagent:/tmp/apm-agent.jar -Delastic.apm.service_name=SERVICE_NAME -Delastic.apm.application_packages=ch.shaped -Delastic.apm.server_urls=http://localhost:8200 
```

Point your browser to `http://localhost:5601` to get to the kibana UI. 
* Click: Add APM
* Check APM Server status
* Load Kibana objects
* Launch APM

Enjoy

