# Ejemplo-02# - Implementación de POM en Selenium

## Objetivo

* 

## Desarrollo


<img src="assets/pom_2.png" width="40%"> 

Repasemos las principales ventajas de este modelo para empezar a pensar cómo se implementaría este modelo en nuestros proyectos:

- Hay una clara separación entre el código de prueba y el código específico de la página, como los localizadores y el diseño.

- Existe un repositorio único para los servicios u operaciones que ofrece la página en lugar de tener estos servicios dispersos a lo largo de las pruebas.

En ambos casos, esto permite que las modificaciones requeridas debido a los cambios en la interfaz de usuario se realicen en un solo lugar. Para comenzar, ilustraremos los objetos de la página con un ejemplo simple.

```Java
package tests;

import static org.testng.Assert.assertNotNull;
import java.time.Duration;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Test;

public class agendarCitaTest {

	/***
	 * Pruebas sobre una funcionalidad de Agendar Cita en web de BEDU
	 */

	private WebDriver driver;
	private WebElement bnt_asesoria;

	  @BeforeTest
	  public void beforeTest() throws InterruptedException {
			System.setProperty("webdriver.chrome.driver", "src/test/resources/webdrivers/chromedriver");
			driver = new ChromeDriver();
			driver.manage().window().maximize();
			driver.get("https://bedu.org/");
			Thread.sleep(2000);	
	  }

	  @Test
	  public void agendarCita() {
	    // Buscar el botón de agendar asesoria
		  bnt_asesoria = driver.findElement(By.xpath("//button[contains(.,'Agendar Asesoría')]"));
	    
	    //realizar click sobre el btn
		  bnt_asesoria.click();

	    // Validar si el formulario esta presente, validando que este desplegado el boton cancelar en la pantalla
	    driver.findElement(By.xpath("//button[contains(.,'Cancelar')]")).isDisplayed();
	    WebElement bnt_cancelar = new WebDriverWait(driver, Duration.ofSeconds(10))
	            .until(ExpectedConditions.elementToBeClickable(By.xpath("//button[contains(.,'Cancelar')]")));
	    
	    // hacemos una aserción para poder validar el resultado esperado de nuestra prueba
	    assertNotNull(bnt_cancelar.getText() ,"Formulario de Agendar asesoria esta desplegado exitosamente");
	    
	  }
	  
	  @AfterTest
	  public void afterTest() {
		  driver.close();
	  }
	}
```
