# Cloud vs Edge Kubernetes Performance

## Description
This project evaluates Kubernetes performance for deploying an Nginx VNF in cloud-like and edge-like environments using Minikube.


## Commands Used

### 1. Minikube Setup

#### Start Cloud Environment
```bash
minikube start --driver=docker
```

#### Start Edge Environment
```bash
minikube start --profile=edge --driver=docker --cpus=2 --memory=2048
```

#### Check Running Profiles
```bash
minikube profile list
```

### 2. Kubernetes Context Management

#### Switch to Cloud
```bash
kubectl config use-context minikube
```
#### Switch to Edge
```bash
kubectl config use-context edge
```

#### Verify Current Context
```bash
kubectl config current-context
```

### 3. VNF Deployment (Nginx)

#### Create Deployment
```bash
kubectl create deployment nginx --image=nginx
```

#### Expose Service
```bash
kubectl expose deployment nginx --type=NodePort --port=80
```

#### Check Pods
```bash
kubectl get pods
```

#### Check Services
```bash
kubectl get services
```


### 4. Access Service

#### Get URL
```bash
minikube service nginx --url
```


### 5. ApacheBench (Performance Testing)

#### Basic Load Test
```bash
.\ab.exe -n 1000 -c 50 http://127.0.0.1:PORT/
```

#### High Load Test
```bash
.\ab.exe -n 5000 -c 100 http://127.0.0.1:PORT/
```


### 6. Metrics Server (Resource Monitoring)

#### Enable Metrics Server
```bash
minikube addons enable metrics-server
```

#### View Pod Resource Usage
```bash
kubectl top pods
```


### 7. iperf3 (Network Testing)

#### Start Server
```bash
.\iperf3.exe -s
```

#### Run Client
```bash
.\iperf3.exe -c 127.0.0.1
```


### 8. Prometheus & Grafana Setup (Helm)

#### Add Helm Repositories
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```

#### Install Monitoring Stack
```bash
helm install monitoring prometheus-community/kube-prometheus-stack
```

#### Check Pods
```bash
kubectl get pods
```


### 9. Grafana Access

#### Port Forward
```bash
kubectl port-forward svc/monitoring-grafana 3000:80
```

#### Get Grafana Password (PowerShell)
```powershell
[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String((kubectl get secret monitoring-grafana -o jsonpath="{.data.admin-password}")))
```


### 10. Troubleshooting Commands

#### Describe Pod
```bash
kubectl describe pod <pod-name>
```

#### View Logs
```bash
kubectl logs <pod-name>
```
