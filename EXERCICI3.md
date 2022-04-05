# StorageEnginesUF2

## Activitat 3. INNODB part II. REALITZA ELS SEGÜENTS APARTATS (obligatòria)  (1 punt)

### •	Partint de l'esquema anterior configura el Percona Server perquè cada taula generi el seu propi tablespace en una carpeta anomenada tspaces (aquesta pot estar situada a on vulgueu).
### • Indica quins són els canvis de configuració que has realitzat.

![image](https://user-images.githubusercontent.com/61474765/161711196-7ddad65d-ae48-4af9-b00a-00c0ac1e0263.png)

El primer que farem es tornar a posar el ON el innodb_file_per_table que està en el arxiu de configuració del mysql.

![image](https://user-images.githubusercontent.com/61474765/161711224-1b5ae2be-c1f7-4ada-ae62-599f3d5d93b0.png)

Un cop ho canviem el que farem es reiniciar el servei, amb un status comprovem que tot continua funcionant.

![image](https://user-images.githubusercontent.com/61474765/161711265-6f2f3b33-ebf1-46e8-a3e9-91543b1e4706.png)

També amb un SHOW VARIABLES LIKE ‘%innodb_file_per_table%’’; podem comprovar que està en ON.

![image](https://user-images.githubusercontent.com/61474765/161711299-aa9d380e-c788-4ffc-97c4-9a8bc01db837.png)

Creem la carpeta i li donem permisos.

![image](https://user-images.githubusercontent.com/61474765/161711330-0ae04682-1147-4b4b-9e4f-7a372a971341.png)

Copiem el contingut del directori i el copia a l’arrel.

![image](https://user-images.githubusercontent.com/61474765/161711364-56fd31c5-328a-4bb9-a29b-d9f6be4322d1.png)

Un cop ho fem, aturem el servei per assegurar-nos de que no fem res que faci malbé el mysql. Amb un status comprovem l’estat.

![image](https://user-images.githubusercontent.com/61474765/161711401-84fcbf7e-6d28-408d-a27e-eaf6428c7269.png)
![image](https://user-images.githubusercontent.com/61474765/161711413-e8cbaf7d-7cb1-4ba6-82f3-27e3e88e90a9.png)

Restaurem el context del SELinux adequat al directori nou i amb el semanage informem del context correcte afegint el mysqld_db_t.

![image](https://user-images.githubusercontent.com/61474765/161711460-7ae72d94-fb56-4d78-89ec-4705103e7a57.png)
![image](https://user-images.githubusercontent.com/61474765/161711471-e3266320-4c9f-4864-9b85-adac160375dd.png)

Dintre del datadir haurem de canviar la ruta i posar la carpeta que hem creat. Estem dintre del arxiu de configuració. També afegim un client amb el port i el socket

![image](https://user-images.githubusercontent.com/61474765/161711511-7c959ee6-bef3-4802-ab0c-36e7632c7926.png)

Un cop guardat l’arxiu, tornem a engegar el servei del MySQL

![image](https://user-images.githubusercontent.com/61474765/161711543-5f60300f-68f7-47c9-be38-792ee77fcfea.png)

Si fem un SELECT @@DATADIR; dintre del mysql podem comprovar que ens a agafat bé la configuració.


