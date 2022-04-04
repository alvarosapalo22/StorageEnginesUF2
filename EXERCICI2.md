# StorageEnginesUF2

## Activitat 2. INNODB part I. REALITZA ELS SEGÜENTS APARTATS (obligatòria)  (2 punts)

### •	Desactiva l’opció que ve per defecte de innodb_file_per_table

![image](https://user-images.githubusercontent.com/61474765/161614159-5bb00dff-c0ed-4022-afa6-9dafdbfc677c.png)

Per tal de desactivar l’opció del innodb_file_per_table, en el arxiu de configuració que tenim dintre de /etc/my.cnf, farem un innodb_file_per_table=OFF

![image](https://user-images.githubusercontent.com/61474765/161614191-f6799457-32c5-4d3d-95dd-31873370fc18.png)

Una vegada hem guardat la configuració del arxiu, farem un restart del servei per tal de que agafi la nova configuració.

![image](https://user-images.githubusercontent.com/61474765/161614226-84dbe13d-4f97-43fb-9e0c-361714013915.png)

Ara, si anem dintre del MySQL i fem un show variables LIKE ‘%innodb_file_per_table%’’; comprovem que està desactivat perfectament.

### •	Importa la BD Sakila com a taules InnoDB. 

![image](https://user-images.githubusercontent.com/61474765/161614443-d7b99426-2714-48fc-ac95-b21477c00633.png)

Com en el exercici un, ja vam importar una base de dades de sakila amb el MyISAM, el primer que farem es esborrar aquesta data base amb un DROP DATABASE sakila;

![image](https://user-images.githubusercontent.com/61474765/161614494-09410e80-f49a-4a57-9330-d9145abc7fbd.png)
![image](https://user-images.githubusercontent.com/61474765/161614517-cd44e268-b4d6-4f81-8372-d352ea4f28d1.png)

Podem comprovar que la taula sakila, que estem important per defecte ja ens ve amb el InnoDB, és a dir que per aquesta part no haurem de fer cap canvi. Un cop comprovat, la importem sense cap problema.

![image](https://user-images.githubusercontent.com/61474765/161614545-b6a9f204-83a1-44fb-8433-396ce0ba449d.png)

I un cop la hem importat, el que farem es entrar dintre del MySQL, i comprovarem que ens a importat la taula amb el InnoDB perfectament.

### •	Quin/quins són els fitxers de dades? A on es troben i quin és la seva mida?

![image](https://user-images.githubusercontent.com/61474765/161614624-c4fa3639-af89-499f-baae-d16c8be255ec.png)

Els arxius el trobem dintre de la ruta /var/lib/mysql/sakila. Podem observar que posant el innodb_file_per_table=OFF observem que tenim els fitxers .frm, alguns de .TRN i un de .opt. Això ens passa perquè al tenir-lo en OFF, fa que el InnoDB emmagatzema les taules en el espai de taules del sistema InnoDB, que es el fitxer .ibdata1 que trobem dintre de la carpeta mysql. Si tinguessim la opció del ON faria que ens apareguin els arxiu .ibd que son els que falten. També podem veure la mida.

![image](https://user-images.githubusercontent.com/61474765/161614663-33729a24-9c00-4a0b-b977-20d57da905a6.png)

I aquí podem observar el arxiu del que estàvem parlant i el que ocupa.

En aquet cas, només ens quedaria explicar que son els arxius .ibd, i el que ocupen, ja que en el exercici 1 ja vam explicar tot això dels arxius .TRN i .frm.

Fitxers .ibd: és un fitxer d’espai de les taules de les bases de dades del MySQL. Està associada al InnoDB. En el meu cas ocupa uns 80M aproximadament.

![image](https://user-images.githubusercontent.com/61474765/161614756-9cbe2f40-e376-47ea-ae09-abec7def961a.png)

### •	Canvia la configuració del MySQL per:
### •	Canviar la localització dels fitxers del tablespace de sistema per defecte a /discs-mysql/

![image](https://user-images.githubusercontent.com/61474765/161614891-254ffd1c-c3f2-4209-91ba-13a640cf123d.png)

Primerament, amb un SELECT @@DATADIR; dintre del MySQL comprovarem on es guarden el fitxers per defecte ara, comprovem que es dintre del /var/lib/mysql.

![image](https://user-images.githubusercontent.com/61474765/161614943-e6047d16-5c30-49c4-b98d-702124485da3.png)
![image](https://user-images.githubusercontent.com/61474765/161614975-a6998dac-0175-4f49-8134-3c921c71f740.png)

Per estar segurs de que tot funciona correctament, el que farem es aturar el servei, es tan senzill com fer un sudo systemctl stop mysql, i amb un status podem comprovar que esta aturat.

![image](https://user-images.githubusercontent.com/61474765/161615000-99faaa8f-ec81-4332-914f-bee648d8d8d6.png)

Ara, el que fem es crear el directori discs-mysql i li posem com a propietari i l’usuari i el grup del mysql. També li posem permisos.

![image](https://user-images.githubusercontent.com/61474765/161615036-05ed3ae6-0aa5-47eb-ae26-c3b5832598a9.png)
![image](https://user-images.githubusercontent.com/61474765/161615062-d17d1759-412d-4f39-ab9a-fe874aee1f86.png)

Copiem el directori de la base de dades a la arrel.

![image](https://user-images.githubusercontent.com/61474765/161615104-97782128-3546-4c24-b5a6-c3bb937b6c9c.png)

Instal·lem el paquet policycoreutils-python.

![image](https://user-images.githubusercontent.com/61474765/161615145-5646b962-0aa1-4868-a10e-5ea271cf9290.png)

Informem a SELinux el context afegint el tipus mysqld_db_t

![image](https://user-images.githubusercontent.com/61474765/161615209-566ac374-aa9a-4a2e-bb8f-3ecc23bb80d9.png)

Restaurem el context SELinux adequat al directori nou.

![image](https://user-images.githubusercontent.com/61474765/161615236-2a93e5ab-d873-40c3-b7dc-77f6bb4229bb.png)

Dintre del arxiu de configuració l’indiquem el nou directori que hem creat anteriorment i també la nova ubicació del socket.

![image](https://user-images.githubusercontent.com/61474765/161615269-00d85c9d-0bf6-427b-8c43-021a9f252396.png)

Un cop guardat el arxiu, iniciem de nou el servei, podem comprovar que no ens dona cap error, això es una bona noticia.

![image](https://user-images.githubusercontent.com/61474765/161615297-e09369de-d105-4878-b0e3-eced82862bc4.png)

Si entre de nou al mysql i fem de nou un SELECT @@DATADIR; comprovem que ja ens dona la nova ubicació.

### •	Tinguem dos fitxers corresponents al tablespace de sistema.
### •	Tots dos han de tenir la mateixa mida inicial (10MB) 
### •	El tablespace ha de créixer de 5MB en 5MB.
### •	Situa aquests fitxers (de manera relativa a la localització per defecte) en una nova localització simulant el següent:
### •	/discs-mysql/disk1/primer fitxer de dades → simularà un disc dur
### •	/discs-mysql/disk2/segon fitxer de dades → simularà un segon disc dur.

![image](https://user-images.githubusercontent.com/61474765/161615397-433a4267-a10c-450c-9acb-8ef850c87e5c.png)

El primer que farem es crear els directoris disk1 i disk2 dintre de discs-mysql, li assignem permisos i a mysql com propietari.

![image](https://user-images.githubusercontent.com/61474765/161615424-6af75e4c-3710-45fb-9cf1-711e092ad709.png)

Si entrem dintre del directori i fem un ls comprovem que s’han creat correctament.

![image](https://user-images.githubusercontent.com/61474765/161615479-f690eef5-b605-48f7-88d7-f51d6bd1a856.png)

Esborrem els arxius ibd.

![image](https://user-images.githubusercontent.com/61474765/161615504-f8042557-faad-4813-a1ab-08963c0bfbe5.png)

Si fem de nou un ls comprovem que ja no els tenim.

![image](https://user-images.githubusercontent.com/61474765/161615555-9d1a3edb-b05a-4579-9e90-95de608a83cb.png)

Un cop fet això, aturem de nou el servei el mysql, amb un status comprovem que està aturat.

![image](https://user-images.githubusercontent.com/61474765/161615597-b1c29190-4d3e-495f-b1ee-7c387d289984.png)

Un cop apagat el servei, entrarem dintre del arxiu de configuració que està en /etc/my.cnf i escrivim la següent configuració:
innodb_data_home_dir=
innodb_data_file_path=disk1/ibdata1:10M;disk2/ibdata2:10M:autoextend
innodb_autoextend_increment=5M
I guardem la configuració del arxiu.

![image](https://user-images.githubusercontent.com/61474765/161615650-9d178d7d-ca04-4b62-9697-9da663a51d0c.png)

I engeguem de nou el servei, podem comprovar que no ens a donat cap error.

![image](https://user-images.githubusercontent.com/61474765/161615696-9682cd1d-8f74-4e04-ad4d-6d1880b5bb7b.png)

Si entrem en el mysql, i fem un SHOW VARIABLES LIKE ‘innodb_data_file_path%’; podem comprovar que està justament com ho hem configurat.

![image](https://user-images.githubusercontent.com/61474765/161615768-0dc0e843-f40e-43cf-9859-5e20ce6716f1.png)

Si fem un du -s -h ./* podem comprovar la mida dels tablespace que hem configurat.

![image](https://user-images.githubusercontent.com/61474765/161615804-1b549958-539b-41f0-aaed-a504139e8ddb.png)

I amb un tree comprovem com estan creats els tablespaces

***Checkpoint: Mostra al professor els canvis realitzats i que la BD continua funcionant.***

