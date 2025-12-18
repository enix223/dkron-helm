# dkron-helm
Helm chart to install Dkron and other associated components. 

# Publish helm chart

1. Package the chart

    ```shell
    helm package ./dkron
    helm repo index .
    ```

2. login ghcr.io

    ```shell
    helm registry login ghcr.io -u <username> --password <token>
    ```

3. publish the chart

    ```shell
    helm push dkron-2.1.0.tgz.tgz oci://ghcr.io/enix223/dkron-helm
    ```

# Deploy dkron helm chart

```shell
helm upgrade --install dkron oci://ghcr.io/enix223/dkron-helm/dkron \
	--namespace=ishare \
	--version 2.1.0 \
	--set image.tag='4.0.8-light' \
	--set server.replicaCount=3 \
	--set agent.replicaCount=3
```
