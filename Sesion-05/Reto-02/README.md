# Reto 2 # - Métodos para procesar los resultados

## Objetivo

* Explicar los métodos avanzados utilizados para procesar los resultados en la clase `DataDrivenTestingUsingDataBase`

## Desarrollo

Siguiendo con métodos explicado en el [**`EJEMPLO 3`**](./Ejemplo-03), explica cuales son los métodos utilizados para procesar los resultados en esta clase:


```Java
package tests;


import static org.testng.Assert.assertTrue;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.ResultSetMetaData;
import java.sql.Statement;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;

public class DataDrivenTestingUsingDataBase {
	int total = 0;
	// Creación del object de conexión
	static Connection con = null;

	// Creación del object Statement
	private static Statement stmt;
	private ResultSet res;

	// Creación de Constantes para la conexión a la Base de Datos
	public static String DB_URL = "jdbc:mysql://localhost:3306/WebAutomationTesting";
	public static String DB_USER = "root";
	public static String DB_PASSWORD = "cmora142";

	@BeforeTest
	public void setUp() throws Exception {
		try {
			// Conexión a la Base de Datos
			String dbClass = "com.mysql.cj.jdbc.Driver";
			Class.forName(dbClass);
			Connection con = DriverManager.getConnection(DB_URL, DB_USER, DB_PASSWORD);

			// Statement object para enviar la declaración SQL a la base de datos
			stmt = con.createStatement();

		} catch (Exception e) {
			e.printStackTrace();
		}
	}

	@Test
	public void test() {

		try {

			// Definir y ejecutar la consulta a la base de datos
			String query = "SELECT * FROM Agendar_Cita";
			res = stmt.executeQuery(query);

			// objeto ResultSetMetaData para obtener el numero de columnas de la tabla
			ResultSetMetaData rsmd = res.getMetaData();
			int columnsNumber = rsmd.getColumnCount();

			System.out.println(query);
			while (res.next()) {

				total++;

				for (int i = 1; i <= columnsNumber; i++) {
					System.out.print(" | " + res.getString(i));
					if (i == columnsNumber) {
						System.out.println(" | " + res.getString(i));
					}
				}
			}
		} catch (Exception e) {
			e.printStackTrace();
		}

		// asersiones
		assertTrue(total >= 1, "No se obtuvieron resultados de la consulta");

	}

	@AfterTest
	public void tearDown() throws Exception {
		if (res != null){
            res.close();
        }
		// Cerrar la conexión a la base de datos
		if (con != null) {
			con.close();
		}
		
	}

}

```


<details>
  <summary> Solución </summary>

- `res.next()`: usado junto el ciclo while para recorrer todos los registros de la colsulta ejecutada.
- `res.getString(i)`: usado para obtener el string del resultado segun la columna indicada con el valor `i`
- `res.close()`: cierra el ResultSet object.

</details>