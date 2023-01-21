# Exemples MariaDB des de JAVA:

##  Eliminar elements d'una taula:

```
package org.example;

import java.sql.*;
import java.text.MessageFormat;

public class Main {

    public static Connection conexio() throws SQLException {
        Connection con = null;
        String sURL = "jdbc:mariadb://localhost:3306/mp03uf6";
        con = DriverManager.getConnection(sURL, "estudiant", "Admin1234");
        return con;

    }

        public static void main(String[] args) throws SQLException {
            try {
                String sentenciaSQL = "DELETE FROM productes WHERE idProducte=2;";
                Connection con = conexio();
                Statement stmt = con.createStatement();
                ResultSet rs = stmt.executeQuery(sentenciaSQL);
                rs.close();
                stmt.close();
                con.close();
            }catch (Exception e){
                e.printStackTrace();
            }
        }
}
```

Comprovem que s'han eliminat:

```
use mp03uf6;
select * from productes;
```



