# Reto 1 # - Uso de la anotación @parameters

## Objetivo

* Identificar el comportamiento de los niveles `<Suite>` y `<Test>` para el uso de la anotación `@Parameters` en los scripts de pruebas automatizados.

## Desarrollo


Copia el contenido de este archivo `testng.xml`y ejecutalo en tu pc:

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

<details>
  <summary>¿Que fue lo que sucedio y porque?</summary>
> Se ejecutaron los parametros que estaban dentro de la etiqueta `Test` y no los que se encuentran dentro de la etiqueta `Suite`, esto se debe a que  el parámetro del nivel de prueba tendrá preferencia sobre el nivel de la suite. 
</details>