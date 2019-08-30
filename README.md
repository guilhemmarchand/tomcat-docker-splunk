# tomcat-docker-splunk

Copyright 2018-2019 Guilhem Marchand

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

## purpose:

Tomcat to Splunk via Telegraf and Jolokia in a massive scale fashion

### Using the templates

Start by cloning the repository:

```
git clone git@github.com:guilhemmarchand/kafka-docker-splunk.git
```

Then to start a template:

```
cd template_docker_splunk_ondocker
./run.sh
```

Docker will download any image required, and the start the full environment.

Splunk requires around 30 seconds to start, you can verify the instance state:

```
docker-compose logs splunk
```

Once Splunk has been started, you can access to Splunk Web:

http://localhost:8000

- login: admin
- password: ch@ngeM3

Verify metrics ingestion in Splunk:

```
| mcatalog values(metric_name) as metric_name, values(_dims) where index=telegraf_kafka
```

#### Metrics Workspace application

Install the Metrics Workspace application in Splunk:

https://splunkbase.splunk.com/app/4192/

#### To destroy the environment:

Finally, you can totally destroy the environment:

```
./destroy.sh
```
