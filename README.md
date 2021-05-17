## Environment details:
* Host OS: Windows 10 Home
* Docker Docker: 3.3.3
* Docker Engine: 20.10.6
* Kubernetes: v1.19.7
* Kubernetes context: docker-desktop

K8S yaml files are located in the `manifests` directory  

DB schema migrations are started automatically each time when initContainers are created.  

### To apply K8S yaml manifests and get running application on your machine:  
1) Go to `/manifests` folder.
2) Run command:  
```sh
kubectl apply -f .
```

Postman collection to test the API endpoints:  
https://www.getpostman.com/collections/34e65c51347657ff1bb5  

### To install postgres database with `helm`, follow commands below:
1) create a new directory:
```sh
mkdir postgres-chart
```
2) add artifacthub repo:
```sh
helm repo add postgres-db-chart https://timguardian.github.io/
```
3) copy the file dev-values.yaml located in current repository (https://github.com/timguardian/kbtu-masters-sa-hw2/tree/master/db-chart), to the folder you've just created.

4) Install the chart:
```sh
helm install my-db-chart postgres-db-chart/db-chart --values dev-values.yaml
```

Then you can access database using:
* Service's port (`kubectl get svc`), PORT(S) 5432:`*****`/TCP
* Using minikube: `minikube service postgres-service`. It will show you which port is accessible from outside.
* Using port-forwarding, described below.

### To access database from host machine:  
``` sh
kubectl port-forward postgres-statefulset-0 5432:5432
```