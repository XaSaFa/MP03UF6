# Exemples MariaDB des de JAVA:

## Crear una taula:

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

        public static void main(String[] args) throws SQLException {
            try {
                String sentenciaSQL = "CREATE TABLE IF NOT EXISTS productes" +
                        "(idProducte INT AUTO_INCREMENT PRIMARY KEY, "+
                "nom VARCHAR(100) NOT NULL, preu FLOAT NOT NULL DEFAULT 0);";

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

Per veure el resultat anem a mariadb i escrivim:

```
use mp03uf6;
show tables;
describe productes;
```

![image](https://user-images.githubusercontent.com/110727546/213881289-af43bfcb-2098-41e9-8510-619b1066525d.png)



