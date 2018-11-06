# Microservices exercises // Kubernetes

## `kubectl` 101

Let's start with some basic commands to see if `kubectl` is installed correctly and your setup is working so you can connecto to the Kubernetes cluster

1. Print the version of your `kubectl` installation
2. Print all nodes of the Kubernetes cluster
3. Print all Pods/Deployments/Services available in the default namespace

Everything can also be done with `kube-prompt` or `click` if you prefer that over the normal `kubectl` CLI.

If you're able to interact with the Kubernetes cluster you can continue with the following tasks:

1. Adapt the Busybox Pod file in `manifets/kubectl-101/busybox.yaml` to get a unique name for your Pod and deploy the Pod to the Kubernetes cluster
2. Use `kubectl exec` to get an interactiv `bash` session in the Kubernetes Pod
3. Check which services are available in the cluster and try to interfact with one of them (Hint: Prometheus might be a good idea as it has a web UI running on port 9090 and the `busybox` image includes `wget`)

## Kubernetes resources 101

To get started with Kubernetes deployments we want to port the previous exercise to deploy a Redis server and the Redis-Commander web UI with Docker-Compose to a Kubernetes based deployment.
The Docker-Compose file can be found at `manifests/k8s-resources-101/redis-cmder-compose.yaml`.

1. Start with the given `01-deployment.yaml` to create a deployment of a single Redis server and a Redis-Commander in every pod
2. Validate with `kubectl get pods` that your deployment is running correctly
3. Connect to your Pod by using `kubectl port-forward` and try to access the web UI to create some keys in the Redis instance
4. Update the tiven `02-service.yaml` to create a Service in Front of your Redis server.
5. Validate if your service is finding at least one Pod to redirect its traffic to
6. Create an Ingress resource with the subdomain `*.mis.inf.fh-rosenheim.de` (e.g. `sINFmamust-redis-cmder.mis.inf.fh-rosenheim.de`) and create an corresponding entry in your `hosts` file as there's unfortunately no DNS resolving the domain correctly. (the last step is already advanced stuff, talk to your lecturer before you start with this task!)