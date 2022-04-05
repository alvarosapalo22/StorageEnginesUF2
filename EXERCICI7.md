# StorageEnginesUF2

## Activitat 7. Storage Engine CSV (0,5  punts)

### •	Documenta i posa exemple de com utilitzar ENGINE CSV.

![image](https://user-images.githubusercontent.com/61474765/161724605-b25db818-ad19-4ee0-a67e-3e03ccc8413e.png)

Com sempre primer de tot, el que haurem de fer es comprovar que el servei que utilitzarem ho tenim actiu, en aquet cas podem comprovar que el CSV ho tenim.

### •	Cal documentar els passos que has hagut de realitzar per preparar l'exemple: configuracions, instruccions DML, DDL, etc....

![image](https://user-images.githubusercontent.com/61474765/161724707-897c61c7-e7e0-4785-af3e-e23cacf7857f.png)

Primer de tot, el que farem es crear una base de dades de prova que en aquet li e anomenat exemple.

![image](https://user-images.githubusercontent.com/61474765/161725307-be2412ed-115d-46e5-97c2-c4417aa9d62e.png)

Un cop creada, seleccionarem la base de dades per utilitzar-la. Un cop seleccionada el que farem es crear-li una taula amb diverses columnes dintre, però al final el que farem es posar un engine=csv; per dir-li que utilitzi aquet motor en aquesta taula.

![image](https://user-images.githubusercontent.com/61474765/161725338-5409c899-4a2e-4671-8cd0-f5224284de95.png)

Des del Workbench podem comprovar que ens a afegit correctament el que hem creat anteriorment.

![image](https://user-images.githubusercontent.com/61474765/161725373-3f136f6e-e850-4d94-987c-1fa1e40b1a0e.png)

Ara, el que farem es insertar registres dintre de les columnes que hem creat. Fent un SELECT * FROM Madrid; comprovem que s’han afegit correctament.

![image](https://user-images.githubusercontent.com/61474765/161725414-76d42da5-3720-41c2-bd6a-11599566d2a7.png)

Si entrem dintre de la ruta de la carpeta de la taula  mysql que vam crear comprovem que al haver- li posat l’opció del CSV ens a creat un arxiu CSV.

![image](https://user-images.githubusercontent.com/61474765/161725444-74f0a997-3e46-42d9-9c91-5fc86ac5d79e.png)

I si fem un cat Madrid.CSV comprovem que ens mostra els registres que hem afegit anteriorment.

***Checkpoint: Mostra al professor la configuració que has hagut de realitzar i el seu funcionament.***
