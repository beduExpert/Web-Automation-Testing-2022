## Sesi贸n 2: Selenium Webdriver: Primeros pasos 馃

<div style="text-align: justify;">

### 1. Objetivos :dart: 

- Utilizar los elementos del IDE de Selenium webdriver para poder encontrar correctamente los elementos de la aplicaci贸n WEB y  poder realizar acciones con ellos,  para lograr scripts automatizados eficientes.
- Utilizar las anotaciones de TestNG para organizar la logica de la ejecuci贸n de los casos de prueba.
- Implementar aserciones para validar los resultados esperados de los casos de pruebas automatizados.

### 2. Contenido :blue_book:

Hasta ahora solo hemos podido realizar las configuraciones necesarias para que Selenium funcione en nuestros equipos, y hemos realizado nuestro primer script de prueba. Ahora nos surgen algunas preguntas 驴Que m谩s podemos hacer con esta poderosa herramienta instalada? 驴Por donde comienzo a automatizar? 驴Tengo algunos casos de prueba, ahora que hago?. Y para darle respuestas a todas estas preguntas tenemos que profundizar en las funcionalidades de Selenium que nos permite convertir eso en casos de pruebas automatizadas. Sin embargo, dado que Selenium no admite la ejecuci贸n de c贸digo en casos de prueba, tenemos que usar TestNG para el mismo. Aqu铆 es donde TestNG encaja en el framework de Selenium. 

Es por ello que en esta sesi贸n nos adentraremos en el uso de TesnNG y Selenium como herramientas para comenzar a automatizar nuestras pruebas sobre plataformas web.  

---

#### <ins>Tema 1: TestNG</ins>

TestNG proviene de las siglas de Test Next Generation y es un framework de automatizaci贸n de pruebas de c贸digo abierto inspirado en JUnit y NUnit que termin贸 siendo una actualizaci贸n de esos dos framework, es decir, se fusionaron para obtener un framework mucho m谩s completo, que resolviera los problemas a los que los 2 anteriores no les daba soluci贸n.

TestNG facilita el desarrollo de pruebas de software en Java, ya que ejecuta las pruebas en clases, es decir, hace clases para las pruebas correspondientes y luego las procesa. Una novedad es que proporciona una funcionalidad adicional como anotaciones de prueba, agrupaci贸n, priorizaci贸n, parametrizaci贸n y t茅cnicas de secuenciaci贸n en el c贸digo que no era posible antes, adem谩s de administrar los casos de prueba, incluso los informes detallados de las pruebas se pueden obtener utilizando TestNG. 

<img src="images/testng.png" width="50%"> 

- [**`EJEMPLO 1 - TestNG`**](./Ejemplo-01)
- [**`RETO 1`**](./Reto-01)

---

#### <ins>Tema 2: Localizaci贸n de elementos con Selenium IDE</ins> 

Para entrar en el mundo de los localizadores de Selenium tenemos que explicar el concepto de WebElement, la misma es una clase creada para los elementos que componen la p谩gina web. Para Selenium WebDriver todos los elementos de una p谩gina web (campos de texto, botones, links, im谩genes, entre otros..) son WebElements.

Para poder encontrar WebElements en la p谩gina web, Selenium utiliza los localizadores que le permite al encontrarlo, ejecutar alguna acci贸n sobre el c贸mo extraer su contenido, hacer un click, revisar si se encuentra disponible, etc..

<img src="images/webelement.png" width="50%"> 

- [**`EJEMPLO 2 - Localizaci贸n de elementos con Selenium IDE`**](./Ejemplo-02)
- [**`RETO 2`**](./Reto-02)
---



#### <ins>Tema 3: Trabajando con Esperas, Condiciones y Manejo de excepciones</ins> 

驴Recuerdas en alg煤n momento haber ingresado en alguna p谩gina web y que la misma se tarde en cargar, o que en vez de eso, se cargue pero observamos que faltan elementos por cargarse?. O que por el contrario la pagina se cierra abruptamente sin tener idea de que sucedio?

En este tema veremos como trabajar con esperas, condiciones para la espera y manejo de excepciones.

- [**`EJEMPLO 3 - Trabajando con Esperas, Condiciones y Manejo de excepciones`**](./Ejemplo-03)
- [**`RETO 3`**](./Reto-03)
---

#### <ins>Tema 4: M茅todos Findelement() y Findelements()</ins>

Para que selenium pueda interactuar con la p谩gina web requiere que un controlador ubique un elemento web y active un evento de JavaScript como por ejemplo hacer un clic, ingresar informaci贸n a un campo de texto, seleccionar un elemento o tomar el valor de un campo. Por lo general, uno comienza la prueba automatizada de cualquier aplicaci贸n web al encontrar elementos web relevantes en la p谩gina web.

Selenium webdriver nos proporciona dos m茅todos para encontrar elementos web en una p谩gina web: driver.findElement() y driver.findElements(). 

- [**`EJEMPLO 4 - Find element Vs Find elements`**](./Ejemplo-04)

---

#### <ins>Tema 5: Clase Webdriver y WebElement</ins>

Selenium WebDriver nos brinda la posibilidad de poder referirnos a estos elementos y ejecutar m茅todos espec铆ficos para realizar las mismas acciones que un humano har铆a sobre los mismos, gracias a las clases WebDriver y WebElement.

Entraremos en m谩s detalle con respecto de que podemos hacer con estas clases ya que ser谩n las m谩s utilizadas para nuestras automatizaciones.

- [**`EJEMPLO 5 - Clase Webdriver y WebElement`**](./Ejemplo-05)

---

#### <ins>Tema 6: Validaciones o Aserciones</ins>

Como 煤ltimo tema de esta sesi贸n veremos lo referente al 煤ltimo paso de nuestras clases de prueba: las validaciones. Sabemos que todo caso de prueba tiene un comportamiento esperado, y que el mismo debe ser validado para saber si nuestro caso de prueba funciona correctamente o seg煤n lo esperado.

Para estas validaciones TestNG nos ofrece lo que se llaman 鈥渁serciones鈥? que se obtienen de la clase Assert.

- [**`EJEMPLO 6  - Validaciones o Aserciones`**](./Ejemplo-06)
- [**`RETO 4`**](./Reto-04)
---

### 3. Postwork :memo:

Encuentra las indicaciones y consejos para reflejar los avances de tu proyecto de este m贸dulo.

- [**`POSTWORK SESI脫N 2`**](./Postwork/)

<br/>


</div>





