# k8s-labs

The objective is to create a Kubernetes YAML specification for a Deployment, which will execute an application within a Pod, followed by testing the application to ensure it operates as expected. To assist you in getting started, here are a few helpful pointers:

- There is a file named `pod.yaml` that you can utilize. This file launches the application but defines a Pod instead of a Deployment.
- The application container hosts a website that listens on port 80.
- When traffic is directed to the specified port, the web app responds with the hostname of the machine on which it is running.
- The hostname corresponds to the Pod name, which you can confirm using the `kubectl` command.

---
```
kubectl apply -f solution/deployment.yaml

kubectl port-forward deploy/whoami 8080:80

curl http://localhost:8080

> "I'm whoami-687976f48b-tkxp9 running on Linux 4.19.76-linuxkit #1 SMP Thu Oct 17 19:31:58 UTC 2019"

kubectl get pods -o custom-columns=NAME:metadata.name

> whoami-68bf776fd-s6sr9

kubectl exec deploy/whoami -- sh -c 'hostname'

> whoami-687976f48b-tkxp9
```