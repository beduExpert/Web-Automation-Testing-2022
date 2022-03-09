# Ejemplo-02 # - Appium

## Objetivo

- Razonar sobre los conceptos basicos de la herramienta para automatización mobile Appium y su arquitectura.

## Desarrollo

`Appium` es una herramienta de código abierto para automatizar aplicaciones nativas, web móviles e híbridas en plataformas móviles iOS, móviles Android y de escritorio Windows. 

<img src="../assets/tema2.jpeg" width="50%"> 

Es importante destacar que Appium es `"multiplataforma"`, es decir, permite escribir pruebas contra múltiples plataformas (iOS, Android, Windows), utilizando la misma API. Esto permite la reutilización de código entre conjuntos de pruebas de iOS, Android y Windows.

#### :round_pushpin: Filosofía de Appium

Appium fue diseñado para satisfacer las necesidades de automatización móvil de acuerdo con una filosofía descrita por los siguientes cuatro principios:

1. No debería tener que volver a compilar su aplicación o modificarla de ninguna manera para automatizarla.
2. No debe estar encerrado en un idioma o marco específico para escribir y ejecutar sus pruebas.
3. Un marco de automatización móvil no debe reinventar la rueda cuando se trata de API de automatización.
4. Un marco de automatización móvil debe ser de código abierto, tanto en espíritu como en práctica, así como de nombre.


Pero ¿como se cumple con esta filosofia? miremos el diseño de appium para saberlo.

#### :round_pushpin: Diseño de Appium

1. `Cumplimos con el requisito n. ° 1:` mediante el uso de `marcos de automatización` proporcionados por el proveedor. De esta forma, no necesitamos compilar en su aplicación ningún código o framework específico o de terceros de Appium. Esto significa que estás probando la misma aplicación que estás enviando . Los marcos proporcionados por el proveedor que utilizamos son:

+ iOS 9.3 y superior: `XCUITest` de Apple
+ iOS 9.3 y versiones anteriores: `UIAutomation` de Apple
+ Android 4.2+: `UiAutomator / UiAutomator2` de Google
+ Android 2.3+: `Instrumentación de Google` . (El soporte de instrumentación se proporciona agrupando un proyecto por separado, Selendroid )
+ Windows: `WinAppDriver` de Microsoft

2. `Cumplimos con el requisito n. ° 2:` ajustando los marcos proporcionados por el proveedor en una API, la API de `WebDriver`. WebDriver (también conocido como `“Selenium WebDriver”`) especifica un protocolo cliente-servidor (conocido como el protocolo `JSON Wire Protocol`). Dada esta arquitectura cliente-servidor, un cliente escrito en cualquier idioma puede usarse para enviar las solicitudes HTTP apropiadas al servidor. Ya hay clientes escritos en todos los lenguajes de programación populares. Esto también significa que puede utilizar el corrector de prueba y el marco de prueba que desee; las bibliotecas cliente son simplemente clientes HTTP y se pueden mezclar en su código de la forma que desee. En otras palabras, los clientes de Appium & WebDriver no son técnicamente `“frameworks de prueba”`, son `“bibliotecas de automatización”`.

3. `Cumplimos con el requisito n. ° 3:` de la misma manera: `WebDriver` se ha convertido en el estándar de facto para la automatización de navegadores web, y es un borrador de trabajo del `W3C` . `¿Por qué hacer algo totalmente diferente para dispositivos móviles?` En cambio, hemos extendido el protocolo con métodos adicionales de API útiles para la automatización móvil.

4. `Cumplimos con el requisito n. ° 4:`porque Appium es de código abierto.


#### :round_pushpin: Conceptos de Appium




#### :round_pushpin: Funcionamiento de Appium en Android

Para dispositivos Android, Appium utiliza la API de `UI Automator` para interactuar con los componentes de UI de la aplicación a probar.

<img src="assets/appium_android.jpeg" width="50%"> 

1. Las bibliotecas de cliente convierten los comandos escritos por el usuario en solicitudes de `API REST`.
2. Estas solicitudes se envían al servidor de `Appium` mediante el `protocolo de conexión móvil JSON`.
3. El servidor de Appium reenvía estas solicitudes al `dispositivo/emulador` Android de destino.
4. Estos comandos son interpretados por `bootstrap.jar`, que los convierte en un formato `UIAutomator` comprensible para dispositivos móviles.
5. Los comandos de `UIAutomator` ahora se ejecutan en el `dispositivo/emulador`.
6. El `dispositivo/emulador` luego revierte el resultado del comando ejecutado al servidor de Appium a través de `bootstrap.jar`.
7. El servidor de Appium reenvía esta respuesta al cliente.

#### :round_pushpin: Funcionamiento de Appium en iOS

Para dispositivos iOS, Appium utiliza la `API XCUITest` nativa de Apple para interactuar con los componentes de la interfaz de usuario de la aplicación a probar. `XCUITest` es un marco de prueba de interfaz de usuario construido sobre el marco de prueba de unidad de Apple, `XCTest`.

<img src="assets/appium_ios.jpeg" width="50%"> 

1. Las bibliotecas de cliente convierten los comandos escritos por el usuario en solicitudes de `API REST`.
2. Estas solicitudes se envían al servidor de `Appium` mediante el `protocolo de conexión móvil JSON`.
3. El servidor de Appium reenvía estas solicitudes al `dispositivo/simulador` iOS de destino.
4. Estos comandos son interpretados por `WebDriverAgent.app`, que los convierte en un formato comprensible para dispositivos móviles llamando a la `API XCUITest` de Apple.
5. Los comandos ahora se ejecutan en el `dispositivo/simulador`.
6. El `dispositivo/simulador` luego revierte el resultado del comando ejecutado al servidor de Appium a través de `WebDriverAgent.app`.
7. El servidor de Appium reenvía esta respuesta al cliente.

