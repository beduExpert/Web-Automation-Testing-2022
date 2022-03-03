# Reto 1 # - Uso de la anotación @parameters

## Objetivo

* Identificar el comportamiento de los niveles `<Suite>` y `<Test>` para el uso de la anotación `@Parameters` en los scripts de pruebas automatizados.

## Desarrollo

Desarrollar el archivo `testng.xml` que contenga la parametrización de casos de prueba a nivel de `<Suite>` y `<Test>`.


<details>
  <summary> Solución </summary>
> testng.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE suite SYSTEM "https://testng.org/testng-1.0.dtd">
<suite name="Suite">

	<parameter name="name" value="Juan"/>
	<parameter name="lastname" value="Gomez"/>
	<parameter name="phone" value="11111111"/>
	<parameter name="email" value="Juan.Gomez@gmail.com"/>
	<parameter name="company" value="bedu"/>
	<parameter name="jobtitle" value="QA"/>
	<parameter name="sector" value="Internet"/>
	<parameter name="company_size" value="1 a 50 empleados"/>
	<parameter name="program" value="Web Automation Testing"/>

  <test name="Test">

	<parameter name="name" value="----"/>
	<parameter name="lastname" value="----"/>
	<parameter name="phone" value="----"/>
	<parameter name="email" value="----"/>
	<parameter name="company" value="----"/>
	<parameter name="jobtitle" value="----"/>
	<parameter name="sector" value="Internet"/>
	<parameter name="company_size" value="1 a 50 empleados"/>
	<parameter name="program" value="----"/>

    <classes>
      <class name="com.bedu.web_automation_course.DataDrivenTestingUsingParameters"/>
    </classes>
  </test> <!-- Test -->
</suite> <!-- Suite -->
```

> testng.xml

```Java
package com.bedu.web_automation_course;

import org.testng.annotations.Test;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.AfterSuite;
import org.testng.annotations.AfterTest;
import org.testng.annotations.BeforeSuite;
import org.testng.annotations.BeforeTest;
import org.testng.annotations.Parameters;
import pages.HomePage;
import pages.AgendarCitaPage;

public class DataDrivenTestingUsingParameters {
	
	private WebDriver driver;
	private HomePage homePage;
	private AgendarCitaPage agendarCitaPage;
	
	
	@BeforeSuite
	@Parameters({"funcionalidad"})
	public void beforeSuite(String funcionalidad) {
		System.out.println("---------------------------------------------------------------------------------");
		System.out.println("-------- INICIO DE LA EJECUCIÓN DE LA FUNCIONALIDAD "+funcionalidad+" -----------");
		System.out.println("---------------------------------------------------------------------------------");
		}

	@BeforeTest
	public void beforeTest() throws InterruptedException {
		System.setProperty("webdriver.chrome.driver", "src/test/resources/webdrivers/chromedriver");
		driver = new ChromeDriver();
		driver.manage().window().maximize();
		driver.get("https://bedu.org/");
	}

	@Test
	@Parameters({"name","lastname","phone","email","company","jobtitle","sector","company_size","program"})	
	
	public void agendarAsesoria(String name, String lastname, String phone, String email, String company,String jobtitle, String sector, String company_size, String program) throws InterruptedException{

		
		homePage = new HomePage(driver);
		// Validamos que el boton de agendar asesoria este disponible
		if (homePage.isButtonDisplayed()) {
			// Clck en boton de agendar asesoria
			try {
				homePage.clickButton();
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
			
		agendarCitaPage = new AgendarCitaPage(driver);
		
		if (agendarCitaPage.btn_CancelIsDispayed()) {
			
			agendarCitaPage.fillName(name);
			agendarCitaPage.fillLastname(lastname);
			agendarCitaPage.fillPhone(phone);
			//agendarCitaPage.fillEmail(email); 
			agendarCitaPage.fillCompany(company);
			agendarCitaPage.fillJobTitle(jobtitle);
			agendarCitaPage.fillSector(sector);
			agendarCitaPage.fillCompanySize(company_size);
			agendarCitaPage.fillProgram(program);
			Thread.sleep(2000);
		}

	}

	@AfterTest
	public void afterTest() {
		driver.close();
	}
	
	@AfterSuite
	public void afterSuite() {
		System.out.println("---------------------------------------------------------------------------------");
		System.out.println("--------------------     FIN DE LA EJECUCIÓN     --------------------------------");
		System.out.println("---------------------------------------------------------------------------------");
	}

}

````

</details>