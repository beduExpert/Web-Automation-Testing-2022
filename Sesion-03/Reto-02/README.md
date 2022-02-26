# Reto 2 # - Mejorar clase agendarCitaPage

## Objetivo

* Mejorar la clase agendarCitaPage para agregar mas localizadores y metodos.

## Desarrollo

Agregar mas metodos y localizadores en la clase `agendarCitaPage`, para incluir mas casos de prueba, ten en cuenta que de esta pagina solo se contemplo el botón de "Cancelar".

<img src="assets/agendar.png" width="80%"> 


Utilizar este codigo de base:

```Java
package pages;

import java.time.Duration;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;

public class agendarCitaPage {
	
	/**
	 * Page Object Model (POM) para página de Agendar cita bedu
	 */
	
	protected WebDriver driver;

	  // Definimos objetos de tipo locator y le asignamos la localización By.
	  private By bnt_cancelar = By.xpath("//button[contains(.,'Cancelar')]");

	  // Creamos el método que recibirá el driver en esta clase
	  public agendarCitaPage(WebDriver driver){
	    this.driver = driver;
	  }

	  /**
	    * Creamos el método de login que cancelara la  asesoria   
	    * y retorna un objeto HomePage
	    */
	  public HomePage cancelarAsesoria() {
	    driver.findElement(bnt_cancelar).click();
	    return new HomePage(driver);
	  }
	  
	  public String btnIsDispayed() {
		    WebElement bnt_cancelar = new WebDriverWait(driver, Duration.ofSeconds(10))
		            .until(ExpectedConditions.elementToBeClickable(By.xpath("//button[contains(.,'Cancelar')]"))); 
		    return bnt_cancelar.getText();
		  }

}

```

<details>
  <summary> Solución </summary>
  
  ```Java
package pages;

import java.time.Duration;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.Select;
import org.openqa.selenium.support.ui.WebDriverWait;

public class agendarCitaPage {

	/**
	 * Page Object Model (POM) para página de Agendar cita bedu
	 */

	protected WebDriver driver;

	// Definimos objetos de tipo locator y le asignamos la localización By.
	private By bnt_cancelar = By.xpath("//button[contains(.,'Cancelar')]");
	private By bnt_agendar = By.xpath("//button[contains(.,'Agendar')]");

	// Método que recibirá el driver en esta clase
	public agendarCitaPage(WebDriver driver) {
		this.driver = driver;
	}

	// Método que realizara un click en bnt_cancelar
	public HomePage cancelarAsesoria() {
		driver.findElement(bnt_cancelar).click();
		return new HomePage(driver);
	}

	// Método que realizara un click en bnt_agendar
	public HomePage agendarAsesoria() {
		driver.findElement(bnt_agendar).click();
		return new HomePage(driver);
	}

	// Método que realizara recibira un localizador e ingresara un texto
	public HomePage fillText(By locator, String text) {
		driver.findElement(locator).sendKeys(text);
		return new HomePage(driver);
	}

	// Métodos que realizara recibiran un texto a llenar en cada campo
	public HomePage fillName(String text) {
		By name = By.id("name");
		driver.findElement(name).sendKeys(text);
		return new HomePage(driver);
	}

	public HomePage fillLastname(String text) {
		By lastname = By.id("lastname");
		driver.findElement(lastname).sendKeys(text);
		return new HomePage(driver);
	}

	public HomePage fillPhone(String text) {
		By phone = By.id("phone");
		driver.findElement(phone).sendKeys(text);
		return new HomePage(driver);
	}

	public HomePage fillEmail(String text) {
		By email = By.id("email");
		driver.findElement(email).sendKeys(text);
		return new HomePage(driver);
	}

	public HomePage fillCompany(String text) {
		By company = By.id("company");
		driver.findElement(company).sendKeys(text);
		return new HomePage(driver);
	}

	public HomePage fillJobTitle(String text) {
		By jobTitle = By.id("jobTitle");
		driver.findElement(jobTitle).sendKeys(text);
		return new HomePage(driver);
	}

	public HomePage fillSector(String text) {
		Select sector = new Select(driver.findElement(By.id("sector")));
		sector.selectByVisibleText(text);
		return new HomePage(driver);
	}

	public HomePage fillCompanySize(String text) {
		Select companySize = new Select(driver.findElement(By.id("companySize")));
		companySize.selectByVisibleText(text);
		return new HomePage(driver);
	}

	public HomePage fillProgram(String text) {
		By program = By.id("program");
		driver.findElement(program).sendKeys(text);
		return new HomePage(driver);
	}

	public String btnIsDispayed() {
		WebElement bnt_cancelar = new WebDriverWait(driver, Duration.ofSeconds(10))
				.until(ExpectedConditions.elementToBeClickable(By.xpath("//button[contains(.,'Cancelar')]")));
		return bnt_cancelar.getText();
	}

}
  ```
</details>

