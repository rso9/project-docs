# Naloga 6

### Implementacija centralnega beleženja dnevnikov
Uporabljen Elastic-Stack-as-a-service (https://logit.io/).  

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

`GET /v1/song/circuit-breaker/1` (Java service)  
- vrača pesem z ID-jem 1
- v ta testni endpoint je vgrajena ~20% možnost, da se sproži napaka
- če 10% requestov (v nekem časovnem obdobju) faila, se krog zapre in ne spusti čez nobenega
zahtevka - takrat uporablja fallback mehanizem, vračanje privzete pesmi