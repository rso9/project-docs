# Naloga 3

### Upravljanje s konfiguracijo

##### Konfiguracija mikrostoritev z uporabo okoljskih spremenljivk
> Kdaj uporabimo ta način konfiguracije?  

Ko nočemo, da gesla ali pa kakšne zaupne informacije pišemo direktno v kodo 
in jih dajemo v repozitorij ali pa ko se ključi oz. naslovi, ki jih potrebujemo 
za delovanje mikrostoritve spreminjajo čez čas oz. odvisno od okolja (npr. 
production vs. development).  
Pri tem moramo paziti, da orodja (npr. Travis), ki uporabljajo okoljske spremenljivke, le teh ne
izpisujejo na stdout (oz. vsaj ne v plain-text obliki).  

> Kakšna je podpora s strani izbranega mikrostoritvenega ogrodja? Zakaj je pomembna?

V `config.yaml` lahko vključujemo okoljske spremenljivke, ki jih nato beremo s ConfigurationUtil 
razredom ali pa injectamo s CDI.  
```
Integer port = ConfigurationUtil.getInstance().getInteger("kumuluzee.server.http.port");
```  
(source: [Configuration management with KumuluzEE](https://github.com/kumuluz/kumuluzee/wiki/Configuration))  

> Kakšna je prioriteta okoljskih spremenljivk v izbranem mikrostoritvenem ogrodju in zakaj?  

Okoljske spremenljivke imajo 2. najvišjo prioriteto (višjo prioriteto imajo sistemske lastnosti 
(*system properties*), nižjo pa konfiguracijske datoteke).  

Sistemske lastnosti so vnaprej definirane lastnosti (npr. `kumuluzee.server.base-url`), ki so 
pomembne za delovanje sistema, zato imajo višjo prioriteto kot okoljske spremenljivke.  

##### Definiranje okoljskih spremenljivk ob zagonu vsebnikov Docker
> Preučite in testiranje načine definiranja okoljskih spremenljivk v okoljih Docker in Docker compose.  

**Docker** podpira flag `-e`, kjer lahko podamo okoljske spremenljivke v obliki ključa in vrednosti.  
Primer:  
```
docker run -d --name catalog -e POSTGRES_PASSWORD=admin -e POSTGRES_DB=catalog -p 5432:5432 postgres:latest
```

**Docker Compose** v svoji konfiguracijski datoteki podpira definicijo okoljskih spremenljivk v razdelku *environment*.  
Primer:  
```
    ...
    environment:
    - CONNECTION_URL=jdbc:postgresql://db:5432/catalog
    - DB_USER=postgres
    - DB_PASS=admin
    ...
```

### Odkrivanje storitev
> Odkrivanje vsebnikov znotraj namestitve Docker compose

Lahko uporabljamo npr. `db` namesto podajanja eksplicitnega IP naslova baze (s tem, da mora biti `db` definiran
v `docker-compose.yml`).  
Primer: https://github.com/rso9/catalog-management/blob/master/docker-compose.yml