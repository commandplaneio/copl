# How to distribute helm charts centrally?
Centralized helm charts needs to be placed onto s3. The current setup creates a bucket whose name starts with copl. The rest of the word is a timestamp.
Under the topl level copl-XXXX directory, the structure is common/apps/charts and common/apps/dependency-charts

You can see below the directory structure for the centralized copl file sources. Teh examples also displays a successful run of ```helm dependency update``` which creates an archive of dependency chart under the Charts directory of the umbrella chart.

```
|-- common
|   `-- apps
|       |-- charts
|       |   |-- YYYY-air
|       |   |   |-- Chart.yaml
|       |   |   |-- files
|       |   |   |   |-- air-ssl-multiport.conf
|       |   |   |   |-- air-ssl.conf
|       |   |   |   |-- air.conf
|       |   |   |   `-- common.conf
|       |   |   |-- templates
|       |   |   |   |-- _helpers.tpl
|       |   |   |   |-- air-console-service.yaml
|       |   |   |   |-- air-data-master.yaml
|       |   |   |   |-- air-mongodb-server.yaml
|       |   |   |   |-- air-nats-server.yaml
|       |   |   |   |-- air-redis-server.yaml
|       |   |   |   |-- air-web-server.yaml
|       |   |   |   |-- configmap.yml
|       |   |   |   |-- deployment.yaml
|       |   |   |   |-- job-console-setup.yaml
|       |   |   |   `-- statefulset.yaml
|       |   |   `-- values.yaml
|       |   `-- deploy
|       |       |-- Chart.lock
|       |       |-- Chart.yaml
|       |       |-- charts
|       |       |   |-- mariadb-15.2.0.tgz
|       |       |   `-- rails-app-0.1.0.tgz
|       |       `-- values.yaml
|       `-- dependency-charts
|           `-- rails-app
|               |-- Chart.yaml
|               |-- templates
|               |   |-- NOTES.txt
|               |   |-- _helpers.tpl
|               |   |-- deployment.yaml
|               |   |-- env-configmap.yaml
|               |   |-- hpa.yaml
|               |   |-- ingress.yaml
|               |   |-- service.yaml
|               |   |-- serviceaccount.yaml
|               |   `-- tests
|               |       `-- test-connection.yaml
|               `-- values.yaml
`-- demouser
```
