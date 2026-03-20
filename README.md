# Cloud vs Edge Kubernetes Performance

## Overview
This project evaluates Kubernetes performance for deploying an Nginx-based Virtual Network Function (VNF) in cloud-like and edge-like environments using Minikube.

## Setup
Two environments were created:
- **Cloud:** Default Minikube configuration  (2 CPU - Dynamic usage with RAM)
- **Edge:** Limited resources (2 CPU, 2GB RAM)

The same Nginx deployment was used in both environments for fair comparison.

## Testing
Performance evaluation was conducted using:
- **ApacheBench (ab):** Throughput, latency, failed requests  
- **iperf3:** Network bandwidth  
- **kubectl top:** CPU and memory usage  
- **Prometheus & Grafana:** Visualization of system metrics  

## Key Findings
- Both environments showed similar performance due to local setup  
- Edge setup used slightly fewer resources  
- Nginx handled load efficiently with low latency  
- Kubernetes ensured consistent deployment across environments  

## Conclusion
The project demonstrates that Kubernetes can effectively run lightweight VNFs in both cloud and edge environments. While differences were minimal in this setup, real-world deployments are expected to show greater variation.

---

## References

- https://minikube.sigs.k8s.io/docs/  
- https://kubernetes.io/docs/  
- https://httpd.apache.org/docs/2.4/programs/ab.html  
- https://iperf.fr/  
- https://prometheus.io/docs/introduction/overview/  
- https://grafana.com/docs/  
- https://helm.sh/docs/  
