# DevOps Test



## Deployment


To deploy an environment configuration, use [kubectl](https://kubectl.docs.kubernetes.io/installation/kubectl/) and [kustomize](https://kubectl.docs.kubernetes.io/installation/kustomize/).

For the base configuration:
```bash
kubectl kustomize k8s-manifests/base | kubectl apply -f -
```
For the Dev configuration:
```bash
kubectl kustomize k8s-manifests/overlays/dev | kubectl apply -f -
```
For the QA configuration:
```bash
kubectl kustomize k8s-manifests/overlays/qa | kubectl apply -f -
```

## Example

```bash
$ kubectl kustomize overlays/qa | kubectl apply -f -
namespace/devops-test-rod created
configmap/influxdb-config created
configmap/telegraf-config created
secret/influxdb-secrets created
service/grafana created
service/influxdb created
persistentvolume/data-pv created
persistentvolumeclaim/grafana-pvclaim created
persistentvolumeclaim/influx-pvclaim created
deployment.apps/grafana created
deployment.apps/influxdb created
deployment.apps/telegraf created
networkpolicy.networking.k8s.io/tig-net created
```
All k8s objects will be created in the "devops-test-rod" namespace.
```bash
$ kubectl get pods -n devops-test-rod
NAME                        READY   STATUS    RESTARTS   AGE
grafana-78997f8fdd-42jp8    1/1     Running   0          2m29s
influxdb-6dcc7d8976-gn4vp   1/1     Running   0          2m29s
telegraf-57d5cb44c4-qjfkm   1/1     Running   0          2m29s
```