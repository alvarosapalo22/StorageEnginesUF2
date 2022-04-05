# StorageEnginesUF2

## Activitat 6. Implementar BD Distribuïdes. (1,5 punts)

Com s'ha vist a classe MySQL proporciona el motor d'emmagatzemament FEDERATED que té com a funció permetre l'accés remot a bases de dades MySQL en un servidor local sense utilitzar tècniques de replicació ni clustering.


### •	Prepara un Servidor Percona Server amb la BD de Sakila
### •	Prepara un segon servidor Percona Server a on hi hauran un conjunt de taules FEDERADES al primer servdor.
### •	Per realitzar aquest link entre les dues BD podem fer-ho de dues maneres:
### •	Opció1: especificar TOTA la cadena de connexió a CONNECTION 
### •	Opció2: especifficar una connexió a un server a CONNECTION que prèviament s'ha creat mitjançant CREATE SERVER
### •	Posa un exemple de 2 taules de cada opció. 
### Tingues en compte els permisos a nivell de BD i de SO així com temes de seguretat com firewalls, etc...

Ho he fet tot en root que es administrador i el Firewall desabilitat.

### •	Detalla quines són els passos i comandes que has hagut de realitzar en cada màquina.

![image](https://user-images.githubusercontent.com/61474765/161723484-e3528f3a-8626-4c44-b302-7f283c289b88.png)

El primer que farem es entrar dintre del arxiu /etc/sysconfig/selinux i la línia on posa SELINUX posar-li un = disabled. Això ho farem en la màquina nova.

![image](https://user-images.githubusercontent.com/61474765/161723519-af7a1899-7280-4767-8e53-47ec557c6654.png)

Ara, entrarem en el arxiu de configuració del my.cnf i escriurem federated.

![image](https://user-images.githubusercontent.com/61474765/161723548-a94b983f-6f32-40ca-8d49-32dd24f9743b.png)

Un cop guardat el arxiu, reiniciem el servei.

![image](https://user-images.githubusercontent.com/61474765/161723581-96a43002-44a2-4fcf-9f39-625088d7be10.png)

I si fem un SHOW STORAGE ENGINES; comprovem que ens apareix correctament el FEDERATED.

***Checkpoint: Mostra al professor la configuració que has hagut de realitzar i el seu funcionament.***
