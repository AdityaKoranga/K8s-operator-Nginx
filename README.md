# K8s-operator-Nginx
## Prerequisite:
Make sure a cluster is running.

## Let's start

Operator initialization

```bash
operator-sdk init \
  --domain adityakoranga.com \
  --plugins helm
  ```

  API creation:

  ```bash
operator-sdk create api \
  --group demo \
  --version v1alpha1 \
  --kind Nginx
```

Install CRD:

```bash
make install
```

setting the docker image:

```bash
export IMG=addytiv/nginx-helm-operator:0.0.1
```

Build and Push operator docker image:

```bash
make docker-build docker-push IMG=${IMG}
```
## Time to deploy:

```bash
make deploy IMG=${IMG}
```
Install Custom Resource:

```bash
kubectl apply -f config/samples/demo_v1alpha1_nginx.yaml
```
