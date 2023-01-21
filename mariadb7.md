# Exemples MariaDB des de JAVA:

##  Insertar elements a una taula:

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
                String sentenciaSQL = "SELECT * from productes;";
                Connection con = conexio();
                Statement stmt = con.createStatement();
                ResultSet rs = stmt.executeQuery(sentenciaSQL);

                while(rs.next()){
                    String id = rs.getString("idProducte");
                    String nom = rs.getString("nom");
                    String preu = rs.getString("preu");
                    String registre = MessageFormat.format("Producte id: {0}, nom: {1}, preu: {2} euros.", id, nom, preu);
                    System.out.println(registre);
                }

                rs.close();
                stmt.close();
                con.close();
            }catch (Exception e){
                e.printStackTrace();
            }
        }
}
```

Mostrarà el resultat per terminal.

![image](https://user-images.githubusercontent.com/110727546/213882317-54d13be8-b4c5-496a-a795-78ee8dd44ad7.png)



