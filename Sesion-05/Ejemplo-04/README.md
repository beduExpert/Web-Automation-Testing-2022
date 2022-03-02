# Ejemplo-04# - Ejemplo de prueba de base de datos con Selenium

## Objetivo

* Adaptar los exemplos entregados en todos los temas de esta sesión a un caso practico con Selenium y una funcionalidad de BEDU (agendar asesoria)

## Desarrollo

Ahora que sabemos como crear bases de datos y tablas, realizar consultas, conexiones, y obtener los resultados de la ejecución de un query en la base de datos,  veamos un caso práctico en selenium de cómo podemos implementar esto en nuestros scripts de pruebas automatizados:


1. Creamos una clase independiente donde crearemos metodos relacionados a la conexion de base de datos, ejección de querys y mas, denominada `connection_database.java`

```Java
package tests;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.ResultSetMetaData;
import java.sql.SQLException;
import java.sql.Statement;

public class connection_database {
	Connection con = null;
	ResultSet res;

	public void Conector() {
		try {
			String DB_URL = "jdbc:mysql://localhost:3306/WebAutomationTesting";
			String DB_USER = "root";
			String DB_PASSWORD = "pass_root";

			con = DriverManager.getConnection(DB_URL, DB_USER, DB_PASSWORD);
			String dbClass = "com.mysql.cj.jdbc.Driver";
			try {
				Class.forName(dbClass);

			} catch (ClassNotFoundException e) {
				e.printStackTrace();
			}

			if (con != null) {
				System.out.println("Conectado a MYSQL");
			}

		} catch (SQLException ex) {
			System.out.println("ERROR: La URL de la conexión no es válida o el usuario y clave de la BD");
			ex.printStackTrace();
		}

	}

	public ResultSet executeQuery(String query) throws SQLException {
		Statement stmt = con.createStatement();
		res = stmt.executeQuery(query);
		return res;

	}

	public void closeConnexion() throws SQLException {
		if (res != null) {
			res.close();
		}

		if (con != null) {
			con.close();
		}
	}
	
	public int getColumnNumber(ResultSet res) throws SQLException{
		ResultSetMetaData rsmd = res.getMetaData();
		return rsmd.getColumnCount();
		
	}
	
}

```

> ¡Cuidado!: Recuerda cambiar el valor de la variable DB_PASSWORD.
2. Creamos nuestra clase de prueba 

```Java
package tests;

import java.sql.ResultSet;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.AfterMethod;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;
import pages.AgendarCitaPage;
import pages.HomePage;

public class DataDrivenTestingUsingDataBase {
	ResultSet res;

	connection_database conect = new connection_database();

	private WebDriver driver;
	private HomePage homePage;
	private AgendarCitaPage agendarCitaPage;

	@BeforeTest
	public void setUp() throws Exception {
		try {
			conect.Conector();
			System.setProperty("webdriver.chrome.driver", "src/test/resources/webdrivers/chromedriver");
			driver = new ChromeDriver();
			driver.manage().window().maximize();
			driver.get("https://bedu.org/");

		} catch (Exception e) {
			e.printStackTrace();
		}

	}

	@BeforeMethod
	public void beforeMethod() {
		homePage = new HomePage(driver);
		agendarCitaPage = new AgendarCitaPage(driver);

		// Validamos que el boton de agendar asesoria este disponible
		if (homePage.isButtonDisplayed()) {
			// Click en boton de agendar asesoria
			try {
				homePage.clickButton();
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}

	}

	@Test

	public void agendarAsesoria() {

		if (agendarCitaPage.btn_CancelIsDispayed()) {

			try {

				// Ejecutar consulta (query) a la BD
				String query = "SELECT * FROM Agendar_Cita";
				res = conect.executeQuery(query);
				System.out.println("res = " + res);
				System.out.println("res.next() = " + res.next());

				while (res.next()) {

					agendarCitaPage.fillName(res.getString(1));
					agendarCitaPage.fillLastname(res.getString(2));
					agendarCitaPage.fillPhone(res.getString(3));
					// agendarCitaPage.fillEmail(res.getString(4));
					agendarCitaPage.fillCompany(res.getString(5));
					agendarCitaPage.fillJobTitle(res.getString(6));
					agendarCitaPage.fillSector(res.getString(7));
					agendarCitaPage.fillCompanySize(res.getString(8));
					agendarCitaPage.fillProgram(res.getString(9));
					Thread.sleep(2000);

				}
			} catch (Exception e) {
				e.printStackTrace();
			}

		}

	}

	@AfterMethod
	public void afterMethod() throws Exception {
		driver.close();
	}

	@AfterTest
	public void tearDown() throws Exception {
		conect.closeConnexion();

	}

}


```

En este ejemplo vemos que se obtuvieron datos de la base de datos para usarlos para completar la información de la funcionalidad `Agendar Asesoría`de la página: https://bedu.org/


De esta manera podemos obtener información de la base de datos y realizar aserciones para validar por ejemplo si la información del registro de un usuario se guardó correctamente a la base de datos, si la actualización de información de una dirección se guardó correctamente, o si se eliminó un usuario correctamente cuando se dio de baja por la página web.


Igualmente podríamos usar la base de datos para obtener información que luego utilizaremos para ingresar el texto en un campo por ejemplo o para tomar variables que no queremos que permanezcan en nuestro código de forma fija.