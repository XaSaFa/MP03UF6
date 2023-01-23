# Exemples MariaDB des de JAVA:

##  Insertar elements a una taula:

```
package org.example;

import java.sql.*;

public class Main {

    public static Connection conexio() throws SQLException {
        Connection con = null;
        String sURL = "jdbc:mariadb://localhost:3306/mp03uf6";
        con = DriverManager.getConnection(sURL, "estudiant", "Admin1234");
        return con;

    }

    public static void main(String[] args)  {
        Connection con = null;
        Statement stmt = null;
        String sentenciaSQL = "INSERT INTO productes(nom,preu)" +
                " VALUES('pizza prosciutto',3.16)";
        try {
            
            con = conexio();
            stmt = con.createStatement();
            stmt.executeUpdate(sentenciaSQL);
        }catch (Exception e){
            e.printStackTrace();
        }finally{
            try {
                stmt.close();
                con.close();
            }catch (Exception e){
                e.printStackTrace();
            }
        }
    }
}
```

Per veure el resultat anem a mariadb i escrivim:

```
use mp03uf6;
select * from productes;
```

![image](https://user-images.githubusercontent.com/110727546/213881734-a57370f6-9858-4a26-9036-e24c64d50a6b.png)




