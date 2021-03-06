## Sesi贸n 1: Instalaci贸n y configuraci贸n de Selenium 馃


<div style="text-align: justify;">

### 1. Objetivos :dart: 

- Establecer la instalaci贸n y configurar correctamente Selenium

### 2. Contenido :blue_book:
Selenium es un entorno de pruebas que se utiliza para comprobar si el software que se est谩 desarrollando funciona correctamente, cabe acotar que, con selenium solo se pueden probar las aplicaciones web. Esta herramienta permite: grabar, editar y depurar casos de pruebas que se pueden automatizar. Lo interesante de Selenium es que se pueden editar acciones o crearlas desde cero. Tambi茅n ayuda mucho en las pruebas de regresi贸n porque consigue pruebas automatizadas que luego se pueden reutilizar cuando se necesite. 
  
En esta sesi贸n realizaremos todas las instalaciones y configuraciones necesarias para que selenium funcione de forma correcta. 

---


#### <ins>Tema 1: Instalaci贸n de Java Software Development Kit (JDK)</ins>

Un software development kit (SDK) es un conjunto de herramientas que ayudan a desarrollar aplicaciones para hardware o software espec铆ficos o en un lenguaje de programaci贸n concretos. En algunos lenguajes interpretados, el SDK puede ser id茅ntico al sistema en tiempo de ejecuci贸n. Algunos fabricantes utilizan denominaciones alternativas para sus paquetes de software en lugar de SDK.Oracle, por ejemplo, llama JDK (Java (SE) Development Kit) a su paquete para el lenguaje de programaci贸n que distribuye, Java.
  ><img src="./JDK.png" width="360">    
En esta tema realizaremos la instalacion del Java (SE) Development Kit

  [`Ejemplo-01` Instalaci贸n de Java Software Development Kit (JDK)](./Ejemplo-01)
  
---



#### <ins>Tema 2: Instalaci贸n de Eclipse IDE. </ins>
  
Eclipse es un proyecto de c贸digo abierto cuyo principal objetivo es proporcionar una plataforma de desarrollo abierta e independiente de los fabricantes de software adem谩s de una serie de frameworks para construir software.
   ><img src="./eclipse.png" width="360">     
En esta tema realizaremos la instalacion de Eclipse IDE.

  [`Ejemplo-02` Instalaci贸n de de Eclipse IDE](./Ejemplo-02)
  
---


#### <ins>Tema 3: Instalaci贸n de Selenium JAVA Cliente Driver + Webdriver + IDE</ins>

En esta tema realizaremos la instalacion de Selenium JAVA Cliente Driver + Selenium Webdriver + IDE
  ><img src="./arquitectura_selenium.png" width="360">  

#### 驴Qu茅 es JAVA Cliente Driver?
  > Es un controlador que le permite a los comandos de Java crear secuencias de comandos que interact煤en con Selenium Server (Remote WebDriver) o crear secuencias de comandos locales de Selenium WebDriver.
#### 驴Qu茅 es un Selenium Webdriver?
  > Es una herramienta que permite interactuar con los navegadores directamente con la ayuda de scripts de automatizaci贸n. Admite varias plataformas y la ejecuci贸n es m谩s r谩pida que Selenium Remote Control (Selenium RC, que ahora est谩 en desuso) o IDE. Selenium Webdriver proporciona m煤ltiples librer铆as de clientes para lenguajes de programaci贸n como Java, Python, Ruby, C#, etc. para crear los scripts de automatizaci贸n de pruebas de Selenium. 
  
  > La comunicaci贸n entre estos clientes y el servidor ocurre a trav茅s de un protocolo de cable JSON. Por ejemplo: cuando se da un comando para abrir un navegador con una URL espec铆fica, toda la informaci贸n necesaria, como el tipo de navegador, la versi贸n del navegador y las capacidades deseadas, se usar谩 para crear una carga JSON. El cliente enviar谩 esta carga 煤til que contiene toda la informaci贸n requerida a trav茅s del protocolo JSON al cliente HTTP. Luego, el servidor identificar铆a el tipo de navegador en el que se debe ejecutar el comando y ejecutar铆a el comando especificado en ese navegador en particular.
  
  ><img src="./arquitectura_selenium_webdriver.png" width="360">  
 
  #### 驴Qu茅 es un Selenium IDE?
  > Selenium IDE es una extensi贸n de navegador f谩cil de usar que registra las acciones de un usuario en el navegador utilizando los comandos existentes de Selenium, con par谩metros definidos por el contexto de cada elemento, tambi茅n proporciona una excelente manera de aprender la sintaxis de Selenium. 
  
  ><img src="./seleniumIDE.png" width="360">  

  [`Ejemplo-03` Configuraci贸n Selenium JAVA Cliente Driver + Webdriver + IDE](./Ejemplo-03)
  
---



#### <ins>Tema 4: Configuraci贸n de Eclipse IDE con Selenium WebDriver</ins>
Eclipse es un entorno de desarrollo sobre el que se pueden montar mediante plugins herramientas de desarrollo para cualquier lenguaje de programaci贸n.

Pero para poder integrarse correctamente con Selenium requiere de la importaci贸n de sus librer铆as al proyecto en el que se est谩 trabajando, sin esta integraci贸n, el eclipse no ser谩 capaz de interpretar los comandos de selenium y generar谩 errores en el proceso de compilaci贸n.

En esta tema realizaremos la configuraci贸n de Selenium Webdriver en Eclipse IDE.


  [`Ejemplo-04` Configuraci贸n de Eclipse IDE con Selenium WebDriver](./Ejemplo-04)
  
---
#### <ins>Tema 5: Instalaci贸n y Configuraci贸n de Selenium Browser Drivers</ins>
Un browser driver es un componente que necesita tener nuestro proyecto de pruebas automatizadas sobre selenium para ejecutar los scripts en el explorador mientras se ejecuta la prueba. Es necesario tener configurado cada driver dependiendo del explorador en el que queramos ejecutar nuestros scripts.

En esta tema realizaremos la instalaci贸n y configuraci贸n de Selenium Webdriver.

  [`Ejemplo-05` Configuraci贸n Selenium browser Drivers](./Ejemplo-05)

---

### 3. Retos :memo:

Realizar estos retos que te ayudaran a practicar lo que has aprendido del contenido visto en esta sesi贸n: 
  - [`Reto 01:` Dependencias Selenium](./Reto-01)
  - [`Reto 02:` Chromedriver](./Reto-02)
---  
### 4. Postwork :memo:

Este postwork te servira para iniciar con tu proyecto, que poco a poco iremos construyendo en el trasncurso de las sesiones, este es el primer paso:

  [`Postwork`](./Postwork)

<br/>


</div>

