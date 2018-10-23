# k8s-crd-controller-example

Based on `https://github.com/resouer/k8s-controller-custom-resource`.

**Note**: the source code is _verbosely_ commented, so the source is meant to be read and to teach.

## What's this?

An example of a custom Kubernetes controller that's only purpose is to watch for the creation, updating, or deletion of all custom resource of type `Network` (in the all namespaces). This was created as an exercise to understand how Kubernetes controllers work and interact with the cluster and resources.

## Running

Clone repo:

```bash
git clone https://github.com/bbbmj/k8s-crd-controller-example
cd k8s-crd-controller-example
```

Build and run:

```bash
go build -o bin/samplecrd-controller ./cmd/
./bin/samplecrd-controller -kubeconfig=$HOME/.kube/config -alsologtostderr=true
```

You can also use `samplecrd-controller` to create a Deployment and run it in Kubernetes. Note in this case, you don't need to specify `-kubeconfig` in CMD as default `InClusterConfig` will be used.

## Usage

You should create the CRD of Network first:

```bash
kubectl apply -f artifacts/network-crd.yaml
```

You can then trigger an event by creating a Network API instance:

```bash
kubectl apply -f artifacts/my-network.yaml
```

CURD the Network API instance, and check the logs of controller.

Enjoy!
