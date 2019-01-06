# Naloga 5

### API za preverjanje vitalnosti in Kubernetes Liveness Probes

### Zbiranje metrik
Na java service (catalog management) je dodanih par čisto osnovnih metrik (število, rate, trajanje klicev na artist 
service).  
Mini "demo" (Java service):  
1. kliči:
- `GET <url>/v1/artist` (uspešen klic),
- `GET <url>/v1/artist/1` (uspešen klic),
- `GET <url>/v1/artist/135` (neuspešen klic)
2. pošlji `GET <url>/metrics`  in poglej vrednosti za metrike (število 404 klicev, 200 klicev, ...)

### Kubernetes in dnevniške datoteke
TODO