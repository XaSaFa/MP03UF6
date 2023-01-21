# MariaDB

## Origen de MariaDB:

![image](https://user-images.githubusercontent.com/110727546/213863455-084cfadd-f6fe-4aef-bf41-49ec93d64894.png)

**MariaDB** és sistema gestor de bases de dades relacionals creat per** Michael "Monty" Widenius**, principal desenvolupador també de **MySQL**.

Quan **Oracle** va adquirir **Sun Microsystems**, incloent MySQL, es va crear el fork MariaDB (2009) per por a que Oracle que també controla el SGBD homònim acabés monopolitzant el mercat de SGBD. 

El nom de la base de dades sembla cosa de Monty, qui té tres fills:

- My (MySQL).
- Max (MaxDB).
- Maria (MariaDB).

Foto de Monty i les seves dues bbdd... filles:

![image](https://user-images.githubusercontent.com/110727546/213863920-a8b0b884-9c13-41ae-8d1e-324d86adc893.png)

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

## Connectar MariaDB amb Java:

Els connectors són peces de software que permeten treballar contra una base de dades implementant mecanismes de connexió amb els programes que els fan servir.

Per connectar Java amb MariaDB utilitzem un software anomenat connector, en el cas de MariaDB el connector rep el nom **MariaDB Connector/J**.

Per a utilitzar-lo en un projecte de Java tenim diverses opcions, veurem com fer-ho utilitzant Maven.

[Com utilitzar MariaDB Connector/J amb Maven](https://mariadb.com/kb/en/java-connector-using-maven/)

Com es veu al tutorial modificarem el fitxer pom.xml per aquest:

```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.mycompany.app</groupId>
    <artifactId>my-app</artifactId>
    <packaging>jar</packaging>
    <version>1.0-SNAPSHOT</version>
    <name>my-app</name>
    <url>http://maven.apache.org</url>

    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>3.8.1</version>
            <scope>test</scope>
        </dependency>
        <dependency>
            <groupId>org.mariadb.jdbc</groupId>
            <artifactId>mariadb-java-client</artifactId>
            <version>2.1.2</version>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.6.0</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>

</project>
```

i a la funció main del projecte escriurem:

```
//create connection for a server installed in localhost, with a user "root" with no password
        try (Connection conn = DriverManager.getConnection("jdbc:mariadb://localhost/", "estudiant", "Admin1234")) {
            // create a Statement
            try (Statement stmt = conn.createStatement()) {
                //execute query
                try (ResultSet rs = stmt.executeQuery("SELECT 'Hello World!'")) {
                    //position result to first
                    rs.first();
                    System.out.println(rs.getString(1)); //result is "Hello World!"
                }
            }

        }
```






