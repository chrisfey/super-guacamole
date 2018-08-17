# Static Site

A simple nginx container for serving static html

## Build and run locally
docker build -t "gcr.io/chrisfey-super-guacamole/static-site" .
docker run -d -p 8888:80 "gcr.io/chrisfey-super-guacamole/static-site"


## Push to GCP registry

gcloud auth configure-docker
docker push gcr.io/chrisfey-super-guacamole/static-site


## Deploy to kubernetes cluster

Create the cluster (See ../kubernetes-cluster/README.md)
```
kubectl run static-site --image=gcr.io/chrisfey-super-guacamole/static-site --port 80
kubectl get pods
kubectl expose deployment static-site --type=LoadBalancer --port 80 --target-port 80
kubectl get service
```

## Deleteing kubernetes stuff

Deleteing the pod wont work:
`kubectl delete pods static-site-7466f665c4-swnfn` 
Because the deployment will restart it
You need to delete the deployment
`kubectl delete deployment static-site` 

kubectl delete service static-site 
kubectl get deployments 
kubectl delete deployment static-site 