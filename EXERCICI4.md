# StorageEnginesUF2

## Activitat 4. INNODB part III. REALITZA ELS SEGÜENTS APARTATS (obligatòria)  (1 punt)

### •	Crea un tablespace anomenat 'ts1' situat a /discs-mysql/disc1/ i col·loca les taules actor, address i category de la BD Sakila.

![image](https://user-images.githubusercontent.com/61474765/161717344-dc1e87cb-1ea4-4757-ad4d-238d50da9972.png)

El primer que farem es crear el tablespace anomenat ts1 i situat dintre de /discs-mysql/disc1, e¡i col·loquem dintre les taules de actor, address i category.

### •	Crea un altre tablespace anomenat 'ts2' situat a /discs-mysql/disc2/ i col·loca-hi la resta de taules.

![image](https://user-images.githubusercontent.com/61474765/161717465-9a003cd8-eb41-47f5-86be-5fdf74274605.png)

Fem el mateix que a l’anterior però amb les taules que ens diuen ara i amb el tablespace creat ara.

![image](https://user-images.githubusercontent.com/61474765/161717506-4b722d92-ac53-46c1-b2d2-96b1ba193152.png)

Si fem un tree dintre de la carpeta podem comprovar que s’han creat correctament.

### •	Comprova que pots realitzar operacions DML a les taules dels dos tablespaces.

Farem dos INSERT, un a la taula actor i un altre a la taula language. Primer ensenyaré que estan buides.

![image](https://user-images.githubusercontent.com/61474765/161717619-5165ddd0-2a63-4ec4-bf2a-7d31f507cb49.png)

Comprovem que la taula actor està buida.

![image](https://user-images.githubusercontent.com/61474765/161717657-f570aa87-d8d5-4b0d-8a33-7c24c79ab652.png)

I que la taula language també està buida.

Un cop comprovats fem els INSERTS.

![image](https://user-images.githubusercontent.com/61474765/161717718-d2f87a95-3071-4b33-a1c0-72334f57518d.png)

INSERT A LA TAULA ACTOR I COMPROVACIÓ

![image](https://user-images.githubusercontent.com/61474765/161717760-4f61255b-f002-4194-a2d5-df9cff91b131.png)

INSERT A LA TAULA LANGUAGE I COMPROVACIÓ

### •	Quines comandes i configuracions has realitzat per fer els dos apartats anteriors?

Les configuracions estan fets en els punts de dalt.

Les comandes utilitzades són: 
-	INSERT INTO: AFEGIR REGISTRES.DML
-	ALTER TABLE: AFEGIR LES TAULES ALS TABLESPACES.DDL
-	CREATE TABLESPACE: CREAR ELS DATASPACES I CREAR EL DIRECTORI. DDL


***Checkpoint: Mostra al professor els canvis realitzats i que la BD continua funcionant***
