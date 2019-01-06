# Naloga 2

### Zasnova arhitekture
Par requestov:
`GET http://35.204.204.148/users` zlista use userje  
`POST http://35.204.204.148/register` registracija userja  
`POST http://35.204.204.148/login` login  
`GET http://35.204.234.168/song/x_files_x_files_theme.mp3` prestraši userja

Več sodelujočih mikrostoritev:
`http://35.204.59.130/song?id=3` odpre front in kliče media storage  
`GET http://35.204.59.130/admin/createSong` upload pošlje POST na media storage,
ta shrani komad in kliče catalog da shrani metadata (+ kliče auth service, da se 
avtenticira uporabnik)

### Vzpostavitev zvezne integracije
**Travis**:   
https://travis-ci.org/rso9/auth [![Build Status](https://travis-ci.org/rso9/auth.svg?branch=master)](https://travis-ci.org/rso9/auth)  
https://travis-ci.org/rso9/media-storage [![Build Status](https://travis-ci.org/rso9/media-storage.svg?branch=master)](https://travis-ci.org/rso9/media-storage)  
https://travis-ci.org/rso9/catalog-management [![Build Status](https://travis-ci.org/rso9/catalog-management.svg?branch=master)](https://travis-ci.org/rso9/catalog-management)  
https://travis-ci.org/rso9/frontend [![Build Status](https://travis-ci.org/rso9/frontend.svg?branch=master)](https://travis-ci.org/rso9/frontend)  

**Docker Hub**:  
https://hub.docker.com/u/rso9