## Environment details:
* Host OS: Windows 10 Home
* Docker Docker, 3.3.3
* Docker Engine: 20.10.6
* Kubernetes: v1.19.7
* Kubernetes context: docker-desktop

### To access database from host machine:  
``` sh
kubectl port-forward postgres-statefulset-0 5432:5432
```