# MariaDB

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

A la funció main del projecte escriurem:

```
public static void main(String[] args) throws SQLException {
        Connection con = null;
        String sURL = "jdbc:mariadb://localhost:3306/mp03uf6";
        con = DriverManager.getConnection(sURL, "estudiant", "Admin1234");
        Statement stmt = con.createStatement();
        ResultSet rs = stmt.executeQuery("SELECT 'Hello World!'");
        rs.first();
        System.out.println(rs.getString(1)); //result is "Hello World!"        
        rs.close();
        stmt.close();
        con.close();
    }
```

El resultat serà Hello World!

### Analitzem el codi:

#### Connection con = null

Aqui creem un objecte Connection que farem servir després.

#### String sURL = "jdbc:mariadb://localhost:3306/mp03uf6";

Aquesta cadena de connexió indica que faraà servir una connexió amb mariadb a la màquina local, el port 3306 és el port per defecte i es pot obviar, i la connexió serà contra la bbdd mp03uf6. 

#### con = DriverManager.getConnection(sURL, "estudiant", "Admin1234");

Aquesta línia crea un objecte DriverManager amb la cadena de connexió, el nom d'usuari i el seu password.

#### Statement stmt = con.createStatement();

Aqui creem un objecte [Statement](https://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html) que s'utilitzarà per passar una sentencia SQL a la BBDD.

#### ResultSet rs = stmt.executeQuery("SELECT 'Hello World!'");

executeQuery executa una sentencia SQL i el resultat es guarda a un objecte ResultSet.

#### rs.first();

Agafem el primer resultat retornat de la consulta.

#### System.out.println(rs.getString(1)); //result is "Hello World!"  

Mostrem el resultat.








