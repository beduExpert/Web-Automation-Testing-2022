# Sesión # 7 Postwork 

## :dart: Objetivos

- Inspeccionar con Appium Inspector los nuevos elementos de la pantalla de una funcionalidad de mercado libre para utilizarlos como insumo en los scripts de pruebas automatizados.
- Adaptar los scripts de pruebas automatizados para ser ejecutado en el navegador google chrome desde un dispositivo virtual de Android (AVD).



## ⚙ Requisitos

- Software de desarrollo
    - Java Software Development Kit (JDK)
- Editor de código
    - Eclipse IDE
- Entorno de pruebas de software
    - Selenium Java Client
    - Selenium Webdriver
    - Selenium Server GRID
    - Appium
    - Appium Inspector
- Navegador App
    - Google Chrome
- Emulador
    - Android Studio


## Desarrollo

+ Selecciona una de las clases de java de tu proyecto donde ya se encuentren automatizados los casos de prueba de alguna funcionalidad de mercado libre.

+ Realiza una nueva clase java donde:

    - Configures el Android Driver
    - Configures los DesiredCapabilities() con los atributos requeridos para abrir el Google Chrome en el dispositivo. Si tienes dudas sobre este punto puedes revisar la documentacion oficial de appium: https://appium.io/docs/en/writing-running-appium/caps/

+ Adaptes al menos 10 test de pruebas que utilicen los localizadores de google chrome en el dispositivo virtual de android.

+ Utiliza Appium Inspector para poder encontrar los localizadores que necesitas de la página web de mercadolibre en el dispositivo virtual.

+ Recuerda utilizar las anotaciones de TestNG.

+ Recuerda hacer uso del Patrón POM si los localizadores cambian o existen nuevos.
