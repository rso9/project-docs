# Naloga 5

### API za preverjanje vitalnosti in Kubernetes Liveness Probes
Node: `http://35.204.204.148/health`  
Java: `http://35.204.170.47/health`  
Health check na auth tudi deluje s Kubernetes live probes 
(lahko pokazemo loge na K8s ali Kibani).

### Zbiranje metrik
Na java service (catalog management) je dodanih par čisto osnovnih metrik (število, rate, trajanje klicev na artist 
service).  
Mini "demo" (Java service):  
1. kliči:
- `GET <url>/v1/artist` (uspešen klic),
- `GET <url>/v1/artist/1` (uspešen klic),
- `GET <url>/v1/artist/135` (neuspešen klic)
2. pošlji `GET <url>/metrics`  in poglej vrednosti za metrike (število 404 klicev, 200 klicev, ...)

Node metrics: `http://35.204.204.148/metrics`  


### Kubernetes in dnevniške datoteke
`kubectl logs <pod id>`: za loge od poda