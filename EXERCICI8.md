# StorageEnginesUF2

## Activitat 8. Storage Engine MyRocks (1 punt)


A tenir en compte en cas de treballar amb Persona Server 8.x:
*https://www.percona.com/doc/percona-server/8.0/upgrading_guide.html*

### •	Documenta i posa exemple de com utilitzar ENGINE MyRocks. Crea una Base de dades amb 2 o 3 taules i inserta-hi contingut.

![image](https://user-images.githubusercontent.com/61474765/161727065-b61f24ea-8b42-443d-8a67-410878e7fe4c.png)

Igual que al exercici 7 comprovem que tenim el servei instal·lat i activat, en aquet cas això ho hauríem de tenir des del exercici 1.

### •	Cal documentar els passos que has hagut de realitzar per preparar l'exemple: configuracions, instruccions DML, DDL, etc....

![image](https://user-images.githubusercontent.com/61474765/161727133-e13cba01-3d2a-43fb-8938-2d7ad83c6a45.png)

Creem la base de dades, en el meu cas la he anomenat champions.

![image](https://user-images.githubusercontent.com/61474765/161727165-8b842b1b-84cb-4452-af64-b88261c0d02f.png)

Canviem la base de dades, i creem les dues taules que necessitem per aquet exercici.

![image](https://user-images.githubusercontent.com/61474765/161727478-670e68ad-c150-45cd-ad8e-3553e6848283.png)

Insertem alguns registres dintre de les taules que hem creat. També comprovem que s’han creat correctament.

### •	A quin directori es guarden els fitxers de dades? Fes un llistat de a on són els fitxers i què ocupen.

![image](https://user-images.githubusercontent.com/61474765/161727595-8569f875-f930-4e6f-a010-1978a137399a.png)

Entrem dintre de la ruta de la carpeta de la base de dades que hem creat que està dintre de /var/lib/mysql/champions i comprovem que ocupa uns 8,5 i 8,6K mes o menys.

### •	Quina és la compressió per defecte que utilitza per les taules? Com ho faries per canviar-lo. Per exemple utilitza Zlib o ZSTD o sense compressió.

![image](https://user-images.githubusercontent.com/61474765/161727694-5a494623-cf5c-42ec-8879-76caf6810a6d.png)

Podem comprovar que per defecte la compressió que utilitza les taules es kLZ4Compression.

![image](https://user-images.githubusercontent.com/61474765/161727728-925508f8-89a2-4e67-b8f3-ef8625c0f2f5.png)

Per tal de canviar la compressió per defecte a una de les que ens demanen, haurem de afegir aquesta línia en el arxiu de configuració:
	rocksdb_default_cf_options=compression=kZSTD;bottommost_compression=kZSTD

![image](https://user-images.githubusercontent.com/61474765/161727773-054ca6e8-5055-4b79-ac7e-4fa7f6ef254c.png)

Guardem l’arxiu i reiniciem el servei.

![image](https://user-images.githubusercontent.com/61474765/161727801-02130306-12a4-4808-9f5f-1c5d78c4c7d2.png)

I comprovem que se’ns a canviat correctament.

***Checkpoint: Mostra al professor la configuració que has hagut de realitzar i el seu funcionament.***



