# anynines-hw
Home of an example kubernetes operator usin operator-sdk

## Prerequisites
- operator-sdk
- kubectl
- minikube/kind or any other kubernetes cluster running and configured in kubectl
- your cluster must be able to pull images from dockerhub

## How to run
- bring up your kubernetes cluster
- run `make deploy` to deploy the operator to your current kubernetes cluster
- create a custom resource of type 'Dummy' by running `kubectl apply -f config/samples/dummy_v1alpha1_dummy.yaml`
- you can create multiple custom resources of type Dummy by modifying the message and the name in the yaml file.
- make sure to tail the logs from the controller pod by running `kubectl logs -f -n anynines-hw-system $(kubectl get pods -n anynines-hw-system -o name | grep controller-manager)` to see the controller in action
- you can also check the status of the custom resource by running `kubectl get dummy` and `kubectl describe dummy <name>` to see the status of the custom resources