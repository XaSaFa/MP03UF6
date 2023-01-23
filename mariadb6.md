# Exemples MariaDB des de JAVA:

## Modificar registres d'una taula:

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
        String sentenciaSQL = "UPDATE productes" +
                " SET preu = 3.99 "+
                "WHERE idProducte = 1";
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

![image](https://user-images.githubusercontent.com/110727546/213881887-12e08f33-1b6d-4810-8b25-f9f2d8d73f2d.png)



