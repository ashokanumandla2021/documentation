# About Kubernetes Resources, Commands

## Deployment / Job / StatefulSet
- 3 types of resources to deploy the smallest resource Pod to the k8s
- Deployement will come along with Replica Set to maintain the desired no.of Pods
- Job can be run on demand or can be scheduled like CronJob to complete tasks
- StatefulSet requires Persistent Volume and the pods will be indexed with 0,1,2 etc (required for Databases)

## Service with ClusterIP / NodePort / LoadBalancer
- Service is mainly used for exposing Pods outside k8s
- NodePort is generally used for debugging / testing purposes (If node restarts then new Port should be used)
- ClusterIP is the default option which on it's own cannot accessed outside, requires Ingress / LoadBalancer
- LoadBalancer in general exists outside of cluster and a paid offering from cloud provider
- Service solves the problem of dynamic IP addresses of Pods in case of restarts, it uses labels/selectors to identify the pods

## Ingress
 - Ingress as well can be used to access the Pods outside k8s
 - Ingress will have paths to route the traffic to different services unlike LoadBalancer which can route to only one service
 - Ingress requires Ingress Controllers (ex: nginx ingress controller offered by cloud provider)

 ## K9S
  - k9s is a CLI to manage k8s
  - `k9s -n <namespace>` can be used to launch the CLI
  - :svc or :dp or :ingress or :cm or :ns can be used to switch the view
  - /search Enter to filter
  - in :dp, can use r to restart, s to scale, l to logs
  - SHIFT + F can be used for port-forward

## Useful Commands
 - **create** `kubectl apply -f <kubernetes-resource>.yml`
 - **remove** `kubectl delete -f <kubernetes-resource>.yml`
 - **port-forward** `kubectl port-forward svc/<service-name> <local-port>:<container-port> -n <namespace>` to access k8s Pod from local
 - **copy** `kubectl cp <pod-name>:/path/to/file /local/path/to/file -c <container-name>` to copy resource from container to local vice-versa possible
 - **describe** `kubectl get <pod|service|job> <resource-name> -o yaml`

## APIs
 - to get pods `https://<k8s-console-host>/api/v1/pod/<namespace>`
 - to get logs `https://<k8s-console-host>/api/v1/log/<namespace>/<pod-name>`
