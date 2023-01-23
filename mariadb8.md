# Exemples MariaDB des de JAVA:

##  Eliminar elements d'una taula:

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
        String sentenciaSQL = "DELETE FROM productes WHERE idProducte=2;";
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

Comprovem que s'han eliminat:

```
use mp03uf6;
select * from productes;
```

![image](https://user-images.githubusercontent.com/110727546/213882480-e58a7e28-4ab4-4732-8722-cf6572ddbca7.png)


