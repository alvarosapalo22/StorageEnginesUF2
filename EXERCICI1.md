# StorageEnginesUF2

## Activitat 1. REALITZA I/O RESPON ELS SEGÜENTS APARTATS (obligatòria) (1 punts)

### •	Indica quins són els motors d’emmagatzematge que pots utilitzar (quins estan actius)? Mostra al comanda utilitzada i el resultat d’aquesta.

![image](https://user-images.githubusercontent.com/61474765/161610698-89443b8d-0b9f-4a93-a978-8e930c7a5b4c.png)

Si fem la comanda SHOW ENGINES;, podem veure tots el motors d’emmagatzematge que podem utilitzar. Per defecte només ens ve activat el InnoDB.
Els que podrem utilitzar són el FEDERATED, PERFOMANCE_SCHEMA, InnoDB,Memory, MyISAM,MRG_ MYISAM, BLACKHOLE, CSV i el ARCHIVE.
Podem comprovar que per defecte ens ve amb el InnoDB. 

### •	Com puc saber quin és el motor d’emmagatzematge per defecte? Mostra com canviar aquest paràmetre de tal manera que les noves taules que creem a la BD per defecte utilitzin el motor MyISAM?

![image](https://user-images.githubusercontent.com/61474765/161610830-20778c6a-f265-4606-a51f-da8cb4b64171.png)

Podem comprovar amb el SHOW STORAGE ENGINES; que el motor d’emmagatzematge per defecte es el InnoDB.

![image](https://user-images.githubusercontent.com/61474765/161610876-6b81dad8-5df5-433c-8295-a0448eee97bb.png)

Per tal de canviar el DEFAULT del InnoDB i posar-li al MyISAM, el que farem es executar la següent comanda, SET default_storage_engine=MyISAM;.

![image](https://user-images.githubusercontent.com/61474765/161611004-6e4a0789-a6ce-4fc6-878f-9f5001f1fac3.png)

I si tornem a executar el SHOW STORAGE ENGINES; comprovem que ara ens surt el DEFAULT al MyISAM.

### •	Explica els passos per instal·lar i activar l'ENGINE MyRocks. MyRocks és un motor d'emmagatzematge per MySQL basat en RocksDB (SGBD incrustat de tipus clau-valor). Aquest tipus d’emmagatzematge està optimitzat per ser molt eficient en les escriptures amb lectures acceptables.

![image](https://user-images.githubusercontent.com/61474765/161611484-23755d43-dbf2-4d7a-a34c-f40fc4153214.png)

Amb la comanda sudo yum install percona-server-rocksdb instal·lem el Myrocks. Quan ens demani posar la y, la posem.

![image](https://user-images.githubusercontent.com/61474765/161611650-3ac3c236-6eac-430d-be09-c2c743f4764d.png)

Ara, el que fem amb la comanda sudo ps-admin –enable-rocksdb -u root -p es habilitar el servei RocksDB utilitzant el usuari i contrasenya del MySQL.

![image](https://user-images.githubusercontent.com/61474765/161611690-f74df28f-88d6-4844-af6b-049efd21b7d7.png)

Ara, anem al WorkBench i tornem a fer el SHOW STORAGE ENGINES, podem comprovar que ens surt correctament instal·lat.

***Checkpoint: Mostra al professor que està instal·lat i posa un exemple de com funciona.***


### •	Importa la BD Sakila com a taules MyISAM. Fes els canvis necessaris per importar la BD Sakila perquè totes les taules siguin de tipus MyISAM. 

![image](https://user-images.githubusercontent.com/61474765/161612083-162182da-25f3-4760-8073-44fc0969a276.png)

El primer que farem es substituir la paraula InnoDB per MyISAM així aconseguirem que les taules siguin MyISAM.

![image](https://user-images.githubusercontent.com/61474765/161612144-d8955d7d-0368-426c-95a4-a4ae7e086fa8.png)

El contingut del fitxer importat el podem trobar dintre de /var/lib/mysql/sakila i si fem un ls podem trobar tot el contingut 

![image](https://user-images.githubusercontent.com/61474765/161612187-668ae87f-0a5d-4eca-a92a-1cfe96acebd7.png)

Si entrem dintre del mysql, podem comprovar que la taula s’ha importat correctament, i també que està amb el MyISAM.

### •	Mira quins són els fitxers físics que ha creat, quan ocupen i quines són les seves extensions. Mostra'n una captura de pantalla i indica què conté cada fitxer. Un cop fet això torna a deixar el motor InnoDB per defecte.

![image](https://user-images.githubusercontent.com/61474765/161612315-6bd49b11-c67b-4535-b429-1ddbafa372b7.png)

Fent un ls -l podem comprovar quines extensions hi tenim i quan ocupen cada una.

Fitxers .frm: Són els arxius que contenen informació relacionada amb el format i la estructura de la base de dades del MySQL. En aquet cas el fitxer que estem observant ocupa uns 8694K

![image](https://user-images.githubusercontent.com/61474765/161612397-06076ff7-da7c-4f11-a80a-baa09bec09a6.png)

Fitxers .MYD:  Conte les dades de la taula de la base de dades. Podem observar que tenen una mida de 0.

![image](https://user-images.githubusercontent.com/61474765/161612436-5d231151-caf6-42ac-92c7-ef94f3b74b8d.png)

Fitxers .opt: Ens diu en que esta fet els caràcters de la base de dades. Ocupa uns 65 bytes.

![image](https://user-images.githubusercontent.com/61474765/161612479-21a2ac1a-e2d9-4e3d-adb6-a0f775e5e0a4.png)

Fitxers .TRN:  Serveixen per restaurar la base de dades. Ocupa uns 35 bytes

![image](https://user-images.githubusercontent.com/61474765/161612523-ac6ca3e8-0cef-4981-a171-d81831c18e08.png)



![image](https://user-images.githubusercontent.com/61474765/161612546-05af082b-8d49-48bd-bfb5-fc4221ee8d36.png)

Amb la mateixa comanda que hem posat per defecte el MyISAM, tornarem a posar el InnoDB com default. Amb un SET default_storage_engine = InnoDB;

### •	A partir de MySQL apareixen els schemas de metadades i informació guardats amb InnoDB. Busca informació d'aquests schemas. Indica quin és l'objectiu de cadascun d'ells i posa'n un exemple d'ús.

INFORMATION_SCHEMA: Proporciona accés a les metadades de la base de dades per l’usuari corresponent. Es la base de dades on es guarda la informació sobre totes les demes base de dades, per exemple: noms d’una base de dades o una taula, el tipus de columna... Aquí podem observar amb la informació guardada sobre el InnoDB:

![image](https://user-images.githubusercontent.com/61474765/161612846-49bafc00-f50c-4af9-af96-73d89c8292a4.png)

INNODB_SYS_DATAFILES: Proporciona informació sobre la ruta del arxiu de dades per espais de Innodb taula, equivalent a la informació de la sys_datafiles en el InnoDB diccionari de dades.

InnoDB_SYS_TABLESTATS: Proporciona una vista de la informació de estat de baix nivell sobre les InnoDB taules. El optimitzador de MySQL utilitza aquestes dades per calcular quin index utilitza al consultar un InnoDB taula.

InnoDB_SYS_INDEXES: Proporciona metadades sobre el indexs de InnoDB, equivalents a la informació de la SYS_INDEXES taula interna en el diccionari de dades de InnoDB.

InnoDB_SYS_FOREIGN_COLS: Taula que proporciona informació de estat sobre les columnes de claus foranes de InnoDB, equivalent a la informació de SYS_FOREIGN_COLS taula en el diccionari de dades de InnoDB.

InnoDB_SYS_FOREIGN: Taula que proporciona metadades sobre les claus foranes de InnoDB, equivalents a la informació de la SYS_FOREIGN taula en el diccionari de dades de InnoDB.

InnoDB_SYS_TABLE: Taula que proporciona metadades sobre les taules InnoDB, equivalents a la informació de la SYS_TABLE taula en el diccionari de dades de InnoDB.

InnoDB_SYS_FIELDS: Proporciona metadades sobre les columnes claus dels indexs de InnoDB, equivalents a la informació de la SYS_FIELDS, en el diccionari de dades de InnoDB.

InnoDB_SYS_TABLESPACES: Taula que proporciona metadades sobre espais de la taula InnoDB, equivalents a la informació de la SYS_TABLESPACE en el diccionari de dades de InnoDB.

InnoDB_SYS_COLUMNS: Proporciona metadades sobre les columnes de InnoDB, equivalents a la informació de la SYS_COLUMNS, taula en el diccionari de dades de InnoDB.

InnoDB_SYS_VIRTUAL: Proporciona metadades sobre les columnes de InnoDB, generades virtualment i columnes en les que es basen en columnes generades virtualment, equivalents a la informació de SYS_VIRTUAL taula en el diccionari de dades de InnoDB.

**EXEMPLE D’US:** 

![image](https://user-images.githubusercontent.com/61474765/161612943-723d97d6-d919-4d25-9b8e-48ff5f1b4bef.png)

Primer, el que farem es crear una taula on farem els exemples.

![image](https://user-images.githubusercontent.com/61474765/161612973-59444042-f9d4-4a3d-ba6d-77035ad0f31a.png)

Ara, es tracta de anar localitzant les metadades, aquí podem veure les de la base de dades MADRID.

![image](https://user-images.githubusercontent.com/61474765/161613031-96845dbf-bd30-49a9-8b8f-d183b4ebd486.png)

Aquí, podem veure les metadades de les columnes, L’ID el podem obtenir en la cerca anterior.

![image](https://user-images.githubusercontent.com/61474765/161613066-06857129-f08e-48fa-9cb6-814f8f3852cd.png)

Aquí podem observar les metadades per la cerca de la InnoDB_SYS_TABLESPACES..

Com podem observar, totes les cercas de les information_schema son iguals, només necessitarem tenir una taula per poder anar cercant tota la informació.

### •	Posa un exemple que produeix un DEADLOCK i mostra-ho al professor.

![image](https://user-images.githubusercontent.com/61474765/161613161-b6988f6b-e30b-46ac-9810-34683bcd6d4f.png)

El primer que fem es amb una sessió crrem una taula amb una fila dintre, i comencem la transacció. En la transacció obtenim un bloqueig A, a la fila posant-lo en mode compartit.

![image](https://user-images.githubusercontent.com/61474765/161613217-0c09c4a8-9285-463e-8400-8b3fa850fe62.png)

Ara, el que fem es obrir una altre sessió i començar una nova transacció, una vegada iniciada, el que farem es intentar eliminar la b. Aquesta acció no tindrà èxit, ja que no es pot fer a la vegada que la acció que estem fent a la sessió A. Així doncs aquesta acció es quedà a la cua.

![image](https://user-images.githubusercontent.com/61474765/161613255-a8c67dda-5be1-42a2-b596-6a2f77831e92.png)
![image](https://user-images.githubusercontent.com/61474765/161613275-f24c3ac1-6f16-4a6e-8428-4bd5a7ec4e37.png)

Ara, de nou intentem eliminar la fila en la sessió A, però tampoc te èxit, ja que tenim abans una sol·licitud en la sessió b que està esperant que acabi primer el bloqueig que varen fer al principi amb la sessió A. Així dons tenim un bloqueig tant en la sessió A com en la sessió B.


