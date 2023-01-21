# MariaDB

## Instal·lar MariaDB:

Per instal·lar mariadb anem a un terminal i escrivim:

```
sudo apt install mariadb
```

## Crear una base de dades:

Quan tenim mariadb instal·lat accedim mitjançant:

```
sudo mariadb
```

Dins de mariadb per crear una base de dades anomenada mp03uf6 escrivim:

```
CREATE DATABASE mp03uf6;
```

Per a utilitzar la base de dades creada dins de mariadb escrivim:

```
USE mp03uf6;
```
I podem llistar les taules creades amb:

```
SHOW TABLES;
```

Comprovant que no hi ha cap taula creada.

## Crear un usuari i donar-li accés a la base de dades:

Per crear un usuari entrem a mariadb i escrivim:

```
CREATE USER 'estudiant'@'localhost' IDENTIFIED by 'Admin1234';
```

On estudiant és el nom d'usuari, Admin1234 és la contrasenya per aquell usuari i localhost indica desd d'on es pot connectar l'usuari, si volem que es pugui connectar des d'altres equips s'ha de substituir localhost per la IP de l'equip o per % si preferim que es pugui connectar des de qualsevol equip.

Donar accés a la base de dades:

```
GRANT ALL ON mp03uf6.* TO estudiant@'localhost';
FLUSH PRIVILEGES;
```
## Comprovar estat del servei mariaDB:

Com qualsevol dimoni de Linux, per saber l'estat del servei ho podem fer per terminal escrivint.

```
sudo service mariadb status
```

![image](https://user-images.githubusercontent.com/110727546/213876722-5c3bbd68-5e00-4cc2-99db-759df36fae1b.png)

Per parar el servei substituïm status per stop, per iniciar-lo per start i per reinicar-lo per restart.
