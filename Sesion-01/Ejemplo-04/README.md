# Manual de configuración de Eclipse IDE con Selenium WebDriver

## Objetivo

* Demostrar el proceso de configuración de Eclipse IDE con Selenium WebDriver

## Desarrollo

* Abrir el Eclipse IDE y seleccionar la opcion "Crear nuevo proyecto de Java"
    - Si estas desde la pantalla principal de Bienvenida de Eclipse, se encuentra en esta opcion:
      ><img src="assets/conf_eclipse_1.png" width="400"> 
    - Si no estas desde la pantalla principal de bienvenida, se hace desde esta opción:
      ><img src="assets/conf_eclipse_1b.png" width="400"> 

* En la pantalla de creación de proyecto, colocar la informacion detallada acontinuación:
  ><img src="assets/conf_eclipse_2.png" width="400"> 
  - Nota: el nombre del proyecto puede ser el que deseen, la información de la imagen es solo para indicar que debe colocarse un nombre en ese campo.

* Hacer click en el botón "Finish"
  ><img src="assets/conf_eclipse_3.png" width="400"> 

* Saldra una ventana emergente informando sobre la creación de el modulo, hacemos click en el botón "Create"
  ><img src="assets/conf_eclipse_4.png" width="400"> 

* Se creara un proyecto con los siguientes directorios:
  ><img src="assets/conf_eclipse_5.png" width="400"> 
  
* Realizar click derecho sobre la carpeta "src" y crea un nuevo archivo de clase desde la opción New > Class.
  ><img src="assets/conf_eclipse_6.png" width="400">   
  - Nota: Los scripts de prueba de Selenium siempre se escriben en el archivo ".class" en Java. Aquí, la idea es que esa clase puede contener uno o más casos de prueba/scripts de prueba de Selenium.

* Escribe el nombre que quieras darle a tu clase y selecciona la opcion "Finish"
  ><img src="assets/conf_eclipse_7.png" width="400"> 

* Veras que se crea la clase en la siguiente ventana:
  ><img src="assets/conf_eclipse_8.png" width="400"> 

* Realizar click derecho sobre el nombre del proyecto y hacer click a la opción de propiedades del proyecto:
  ><img src="assets/conf_eclipse_9.png" width="400"> 

* Realizar click en la opción "Java Build Path" del panel izquierdo de la ventana:
  ><img src="assets/conf_eclipse_10.png" width="400"> 

* Ingresar en la sección de "Libraries"
  ><img src="assets/conf_eclipse_11.png" width="400"> 

* Seleccionar la opcion "modulepath" y hacer click en el botón "Add External JARs"
  ><img src="assets/conf_eclipse_12.png" width="400"> 

* Localizar la ruta donde descomprimiste el .zip de selenium que contiene los archivos JARs, seleccionalos y haz click en el botón de "Open"
  ><img src="assets/conf_eclipse_13.png" width="400"> 

* Seleccionar de nuevo la opción "modulepath" y hacer click en el botón "Add External JARs", hacer lo mismo para los archivos JARs que se encuentran dentro de la carpeta "Libs"
  ><img src="assets/conf_eclipse_14.png" width="400"> 

* Una vez que se encuentren todas las librerias de selenium importadas, hacer click en el botón "Apply and Close". Esto creara una sección en nuestro proyecto llamado "Referenced Libraries"
  ><img src="assets/conf_eclipse_15.png" width="400"> 

#### Ahora, estamos listos para escribir nuestros scripts de prueba en Eclipse y ejecutarlos en WebDriver.
