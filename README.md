# graylog-kube
# graylog cluster in kubernetes
# Steps to install graylog cluster 

### 1. Make sure kubectl is up and working , connecting to kubenetes
### 2. Run graylog cluster 
```
 kubectl create ns graylog
 kubectl -n graylog create -f elasticsearch-deployment.yaml,elasticsearch-service.yaml,graylog-service.yaml,graylog-deployment.yaml,mongo-service.yaml,mongo-deployment.yaml
```
### 3. Forward port 9000 
```
 POD=$(kubectl -n graylog get pods --selector=service=graylog -o jsonpath='{.items[*].metadata.name}')
 kubectl -n graylog port-forward $POD 9000:9000
```