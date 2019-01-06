# Naloga 4

### Kubernetes
- Kubernetes @ Google Cloud
- cluster s 3 nodi
- `kubectl get service`: vidimo da je npr. etcd service tipa **NodePort**
ki je na voljo samo podom znotraj clustra in ni viden navzven, ostali pa 
so **LoadBalancer** ki so vidni na externih ipjih
- odkrivanje storitev imamo narejeno z etcd, ki ga deployamo v kubernetes, 
njegov ip in port pa uporabljamo v configih (KumuluzEE config za node in javo)
- podatkovno bazo imamo gostovano na Heroku