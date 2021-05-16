## Environment details:
* Host OS: Windows 10 Home
* Docker Docker: 3.3.3
* Docker Engine: 20.10.6
* Kubernetes: v1.19.7
* Kubernetes context: docker-desktop

K8S yaml files are located in the `manifests` directory  

DB schema migrations are started automatically each time when initContainers are created.  

To apply K8S yaml manifests and get running application on your machine:  
1) Go to `/manifests` folder.
2) Run command:  
```sh
kubectl apply -f .
```

Postman collection to test the API endpoints:  
https://www.getpostman.com/collections/34e65c51347657ff1bb5  


### To access database from host machine:  
``` sh
kubectl port-forward postgres-statefulset-0 5432:5432
```