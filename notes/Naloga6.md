# Naloga 6

### Implementacija centralnega beleženja dnevnikov
Uporabljen Elastic-Stack-as-a-service (https://logit.io/).  

**TODO pred zagovorom**:  
- naredi nov trial account, ker bo ta potekel pred zagovorom vaj,  
- parkrat poženi aplikacije, ki imajo nastavljeno logiranje z 
različnimi verzijami aplikacije, iz različnih naslovov in kaj podobnega
(da se bojo vidli vsaj malo drugačni logsi) - TL;DR: nafilaj LogStash.

**Primeri poizvedb (Kibana Query Language)**:
1. Pridobi logse za zahtevke iz specifičnega IP-ja na specifično instanco mikrostoritve
(specificirano z unique instance ID-jem). Tako IP kot unique ID instance je 
verjetno najlažje najdit v Kibani.  
`host: <zunanji IP uporabnika> && contextMap.uniqueInstanceId: <ID instance>`  

2. Pridobi logse za zahtevke na vse instance mikrostoritve s specifičnim imenom 
(v tem primeru `catalog`), kjer imajo ti logsi "prioriteto" INFO.  
`contextMap.applicationName: catalog && level: INFO`  

3. Pridobi logse za vse klice endpointov iz specifičnega IP-ja 
(tako vhode v endpointe kot tudi izhode iz endpointov).  
`host: <zunanji IP uporabnika> && (marker.name: ENTRY || marker.name: EXIT)`  


### Izolacija in toleranca napak  
TBD