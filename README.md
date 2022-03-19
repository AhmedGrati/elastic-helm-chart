# elastic-helm-chart
This is a helm chart of Elastic that will be used with Graylog and Elastiflow.
# Installing the chart
To install this chart, run the following commands:
1. Create a database namespace, by running this command:
```shell
kubectl create ns database
```
2. Pull the dependencies of this chart, by running this command:
```shell
kubectl dependency update .
```
3. Create a secret that will hold the password of the elasticsearch database(the username could not be changed. It's `elastic` by default). It should look like this:
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: elastic-secret
  namespace: database
data:
  ELASTIC_PASSWORD: ZHVtbXk=
```
4. Install the chart:

`helm install elastic elastic-helm-chart -f elastic-helm-chart/values.yaml -n database`
