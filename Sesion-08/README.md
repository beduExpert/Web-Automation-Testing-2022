## Sesi贸n 8 - Appium: Primeros pasos 馃


<div style="text-align: justify;">

### 1. Objetivos :dart: 

- Desarrollar scripts de pruebas automatizados que puedan ser ejecutados en dispositivos m贸viles con Android por medio de la aplicaci贸n del navegador Google Chrome. 
- Demostrar el funcionamiento de m谩s propiedades del objeto Desired Capabilities
- Aplicar los comandos m谩s utilizados de Appium que pueden ser incorporados en los scripts de pruebas automatizados. 
- Comparar c贸mo se obtienen los localizadores en plataformas m贸viles vs los de plataformas web.
- Utilizar los objetos TouchAction/MultiAction para la automatizaci贸n de gestos m贸viles. 


### 2. Contenido :blue_book:

En la sesi贸n anterior aprendimos que es Appium, cual es su arquitectura y todas las configuraciones necesarias para ejecutar con 茅xito nuestro primer script de prueba automatizado en dispositivos m贸viles virtuales bajo la plataforma android. En esta sesi贸n profundizaremos m谩s sobre todas las herramientas que appium nos ofrece para poder interactuar con los dispositivos bien sea f铆sicos o virtuales, veremos como est谩n confirmados los drivers, profundizaremos sobre el objeto desired capabilities, veremos comandos y c贸mo utilizar los localizadores para finalmente aprender sobre uso de los objetos TouchAction/MultiAction utilizados para la automatizaci贸n de gestos m贸viles.

---
#### <ins>Tema 1: Automatizaciones Web M贸viles con Android </ins>

En sesiones anteriores hemos realizado automatizaciones de casos de pruebas que son ejecutados en navegadores web, ahora `驴Es posible ejecutar estos mismos casos de prueba en las p谩ginas web pero en los dispositivos m贸viles?` La respuesta es __S脥!__ :mechanical_arm:

Appium es la herramienta para esto.. B谩sicamente, puedes escribir una prueba normal de WebDriver y usar Appium como el servidor Selenium con un conjunto especial de capacidades deseadas. (Desired Capabilities)

En este tema veremos c贸mo es posible ejecutar los scripts de pruebas que ya tenemos automatizados desde un emulador android.

<img src="assets/chrome.png" width="50%"> 

- [**`EJEMPLO 1 - Automatizaciones Web M贸viles con Android`**](./Ejemplo-01)
- [**`RETO 1`**](./Reto-01)
---
#### <ins>Tema 2: Desired Capabilities</ins> 

Como vimos en la sesi贸n anterior las capacidades deseadas son claves y valores codificados en un objeto JSON, enviados por los clientes de Appium al servidor cuando se solicita una nueva sesi贸n de automatizaci贸n.

En este tema  profundizaremos sobre el objeto desired capabilities.

```Java
    //DesiredCapabilities
    DesiredCapabilities dc = new DesiredCapabilities();
    dc.setCapability(MobileCapabilityType.AUTOMATION_NAME, "uiautomator2");
    dc.setCapability(MobileCapabilityType.DEVICE_NAME, "emulator-5554");
    dc.setCapability(MobileCapabilityType.PLATFORM_NAME, "android");
    dc.setCapability(MobileCapabilityType.PLATFORM_VERSION, "12");
    dc.setCapability(MobileCapabilityType.BROWSER_NAME, "Chrome");

```

- [**`EJEMPLO 2 - Desired Capabilities`**](./Ejemplo-02)
- [**`RETO 2`**](./Reto-02)

---
#### <ins>Tema 3: Comandos</ins> 

Appium ofrece m煤ltiples comandos para interactuar con los dispositivos m贸viles, en este tema veremos los m谩s importantes.


- [**`EJEMPLO 3 - Comandos`**](./Ejemplo-03)
- [**`RETO 3`**](./Reto-03)

---
#### <ins>Tema 4: Localizadores</ins> 

En este tema veremos las estrategias de localizaci贸n de Appium.

<img src="assets/appium_inspector.png" width="50%"> 

- [**`EJEMPLO 4 - Localizadores`**](./Ejemplo-04)

---
#### <ins>Tema 5: Automatizaci贸n de Gestos M贸viles</ins> 

En cuanto a la automatizaci贸n de gestos m贸viles, si bien la especificaci贸n `Selenium WebDriver` es compatible con ciertos tipos de interacci贸n m贸vil, sus par谩metros no siempre se pueden asignar f谩cilmente a la funcionalidad que proporciona la automatizaci贸n del dispositivo, con ese fin, Appium implementa la nueva API `TouchAction/MultiAction` que veremos en este tema.

<img src="assets/gestos.png" width="50%"> 

- [**`EJEMPLO 5 - Automatizaci贸n de Gestos M贸viles`**](./Ejemplo-05)

---
### 3. Postwork :memo:

Encuentra las indicaciones y consejos para reflejar los avances de tu proyecto de este m贸dulo.

- [**`POSTWORK SESI脫N 8`**](./Postwork/)

<br/>


</div>

