# StorageEnginesUF2

## Activitat 5. REDOLOG. REALITZA ELS SEGÜENTS APARTATS. (2 punt)

### •	Com podem comprovar (Innodb Log Checkpointing):
### •	LSN (Log Sequence Number)
### •	L'últim LSN actualitzat a disc
### •	Quin és l'últim LSN que se li ha fet Checkpoint

![image](https://user-images.githubusercontent.com/61474765/161720108-654cb878-ca97-410e-a170-458dded7cb20.png)

Per comprovar-ho haurem de fer la comanda SHOW ENGINE INNODB STATUS\G

![image](https://user-images.githubusercontent.com/61474765/161720152-0ead0040-0ab8-40dc-b7bc-d9572c4bfdcb.png)

Haurem de buscar un apartat on ens posa LOG i podem comprovar el LSN.

### •	Proposa un exemple a on es vegi l'ús del redolog

![image](https://user-images.githubusercontent.com/61474765/161720228-31ac53aa-2357-45e7-b36d-019ecd16ceea.png)

El primer que farem es aturar el servei, amb un status podrem comprovar l’estat.

![image](https://user-images.githubusercontent.com/61474765/161720259-edfbe17c-e8e0-4f43-9d13-381c41641f0c.png)

El que farem ara, es esborrar els logs amb un sudo rm -f ib_logfile0

![image](https://user-images.githubusercontent.com/61474765/161721566-9faa554f-652f-482b-a2fb-072de357db4a.png)

Dintre del arxiu de configuració my.cnf modificarem la mida dels logs_file

![image](https://user-images.githubusercontent.com/61474765/161721609-189812c0-6f26-4280-9eae-b4b6a04ba868.png)

Un cop hem guardat la configuració, haurem de tornar a engegar el servei del mysql. Amb un status ho podem comprovar.

![image](https://user-images.githubusercontent.com/61474765/161721651-4db41430-8aad-4c1c-bd36-158d425ba686.png)

Si entrem dintre de /var/lib/mysql també tenim dos fitxers logs, aquí podem comprovar que tenim la mida tal i com la hem posada.

### •	Com podem mirar el número de pàgines modificades (dirty pages)? I el número total de pàgines?

![image](https://user-images.githubusercontent.com/61474765/161721747-a2d8db33-feac-4768-9065-b0db1566151e.png)

Amb la comanda SHOW ENGINE INNODB STATUS\G, podem comprovar en el apartata de BUFFER POOL AND MEMORY el numero de pagines modificades que no ens surt cap ja que no hem modificat cap i el numero total de pàgines.

***Checkpoint: Mostra al professor els canvis realitzats i que la BD continua funcionant.***
