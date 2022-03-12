# Ejemplo-02 # - Desired Capabilities

## Objetivo

- Demostrar el funcionamiento de más propiedades del objeto Desired Capabilities.

## Desarrollo

Como vimos en la sesión anterior las capacidades deseadas son `claves y valores codificados en un objeto JSON`, enviados por los clientes de Appium al servidor cuando se solicita una nueva sesión de automatización.

Estos le dicen a los `controladores (drivers)` de Appium todo tipo de cosas importantes sobre cómo desea que funcione su prueba. Cada cliente de Appium crea capacidades de una manera específica para el idioma del cliente, pero al final del día, `se envían a Appium como objetos JSON`.

Las capacidades deseadas se pueden programar:

- En la prueba de `WebDriver`: 

    ```Java
    import org.openqa.selenium.remote.DesiredCapabilities;
    DesiredCapabilities dCapabilities = new DesiredCapabilities();
    dCapabilities.setCapability(MobileCapabilityType.AUTOMATION_NAME, "uiautomator2");
    dCapabilities.setCapability(MobileCapabilityType.DEVICE_NAME, "emulator-5554");
    dCapabilities.setCapability(MobileCapabilityType.PLATFORM_NAME, "android");
    dCapabilities.setCapability(MobileCapabilityType.PLATFORM_VERSION, "12");
    dCapabilities.setCapability(MobileCapabilityType.BROWSER_NAME, "Chrome");

    ```

- Dentro de la `GUI del servidor Appium (a través de una sesión de Inspector)`

    <img src="assets/appium_inspector.png" width="50%"> 

Existen muchas capacidades compatibles con Appium, las capacidades también `difieren según el driver`, aunque hay un conjunto estándar al que la mayoría de los drivers prestan atención. 

En este tema veremos las capacidades deseadas más utilizadas  `generales (comunes para todos los drivers)` y para `Android versiones de OS mayores 5 (UIAutomator2)`:

#### Capacidades Deseadas Generales para todos los drivers

| Capacidad Deseada | Descripción | Ejemplo de Implementación
| -------- | -------- |------------- |
| `automationName` | Qué motor de automatización usar | 
```Java 
DesiredCapabilities dCapabilities = new DesiredCapabilities();
dCapabilities.setCapability(MobileCapabilityType.AUTOMATION_NAME, "uiautomator2"); 
``` 
        |
| `platformName` | Qué plataforma de sistema operativo móvil usar ||
| `platformVersion` | Versión del sistema operativo móvil ||
| `deviceName` | El tipo de `dispositivo móvil` o `emulador` a usar ||
| `app` | La ruta local absoluta o la URL http remota a un archivo `.ipa` (IOS), o un archivo `.apk` (Android).  Appium intentará instalar primero este binario de la aplicación en el dispositivo adecuado ||
| `browserName` | Nombre del navegador web móvil para automatizar. Debería ser una cadena vacía si se automatiza una aplicación en su lugar ||
| `newCommandTimeout` | Cuánto tiempo (en segundos) Appium esperará un nuevo comando del cliente antes de asumir que el cliente salió y finalizó la sesión ||
| `language` | Idioma a configurar para iOS (solo controlador `XCUITest`) y Android. ||
| `locale` | Configuración regional para iOS (solo controlador `XCUITest`) y Android. Formato `fr_CA` para iOS. Formato `CA` (abreviatura del nombre del país) para Android ||
| `udid` | Identificador de dispositivo único del dispositivo físico conectado ||
| `orientation` | Orientación del Dispositivo (Solo Simuladores/Emuladores) ||
| `noReset` | No reestablece el estado de la aplicación antes de iniciar la sesión. En iOS no destruye ni apaga el `sim` después de la prueba. En ANDROID no detiene la aplicación, no borra los datos de la aplicación y no desinstala la aplicación ||
| `fullReset`| Realiza un reinicio completo, en iOS desinstala la aplicación antes y después de la prueba del dispositivo real, y destruye el simulador antes y después de la prueba de simulación. En Android detiene la aplicación, borra los datos de la aplicación y desistala la aplicación antes de que comience la sesión y después de la prueba ||





























