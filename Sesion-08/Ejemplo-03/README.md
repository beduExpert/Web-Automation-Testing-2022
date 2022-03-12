# Ejemplo-03 # - Comandos

## Objetivo

- Descubrir los comandos mas utilizados de Appium que pueden ser incorporados en los scripts de pruebas automatizados.

## Desarrollo

Appium ofrece múltiples comandos para interactuar con los dispositivos móviles, en este tema veremos los más importantes:

- `Status`: Devuelve información sobre si un extremo remoto se encuentra en un estado en el que puede crear nuevas sesiones y, además, puede incluir metainformación arbitraria que es específica de la implementación.

```Java
driver.getStatus();
```

- `Ejecutar Script`: Ejecuta una variedad de comandos móviles nativos que no están asociados con un endpoint específico. La sintaxis es `execute("mobile: <commandName>", <argumento JSON serializable>)``

```Java
driver.executeScript("mobile: scroll", ImmutableMap.of("direction", "down"));
```

- __Sesiones__:
    - `Crear`: crea una nueva sesión, es decir, el servidor debe intentar crear una sesión que coincida lo más posible con las capacidades deseadas y requeridas.
    ```Java
    String sessionId = driver.getSessionId().toString();
    ```

    - `Terminar`: termina la sesión en ejecución.
    ```Java
    driver.quit();
    ```

    - `Obtener capacidades de sesión`: recupera las capacidades de la sesión especificada.
    ```Java
    Map<String, Object> caps = driver.getSessionDetails();
    ```

    - `Tomar captura de pantalla`: toma una captura de pantalla de la vista/ventana/página actual, es decir, toma una captura de pantalla de la ventana gráfica en un contexto nativo (iOS, Android) y toma una captura de pantalla de la ventana en contexto web

    ```Java
    File scrFile = ((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
    ```

    - `Obtener la fuente de la página`: obtiene la jerarquía de aplicaciones actual XML (aplicación) o fuente de página (web). En un contexto web, la fuente devuelve el HTML fuente de la ventana actual. En un contexto nativo (iOS, Android, etc...) devolverá el XML de jerarquía de la aplicación.

    ```Java
    String pageSource = driver.getPageSource();
    ```

    - `Tiempos de espera`: configura la cantidad de tiempo que se puede ejecutar un tipo particular de operación antes de que se cancele. Los tipos de tiempos de espera son 'carga de página', 'script' e 'implícito'.

    ```Java
    driver.manage().timeouts().pageLoadTimeout(30, TimeUnit.SECONDS);
    ```

    - `Espera implícita`: establece la cantidad de tiempo que el conductor debe esperar al buscar elementos. Al buscar un solo elemento, el controlador debe sondear la página hasta que encuentre un elemento o expire el tiempo de espera, lo que ocurra primero. Es decir, al buscar varios elementos, el controlador debe sondear la página `hasta que encuentre al menos un elemento o expire el tiempo de espera`, momento en el que debe devolver una lista vacía. Si nunca se envía este comando, el driver debe tener una `espera implícita de 0 ms por defecto`.

    ```Java
    driver.manage().timeouts().implicitlyWait(30, TimeUnit.SECONDS);
    ```

    - `Tiempo de espera del script`: establece la cantidad de tiempo, en milisegundos, que los scripts asincrónicos pueden ejecutarse antes de que se anulen (solo contexto web).

    ```Java
    driver.manage().timeouts().setScriptTimeout(30, TimeUnit.SECONDS);
    ```

    - __Orientación__:
        - `Obtener orientación`: obtiene la orientación actual del dispositivo/navegador

        ```Java
        ScreenOrientation orientation = driver.getOrientation();
        ```

        - `Establecer orientación`: establece la orientación actual del dispositivo/navegador

        ```Java
        driver.rotate(ScreenOrientation.LANDSCAPE);
        ```
    - `Obtener registros`: obtiene los logs (registros) para un tipo de log determinado. El búfer de log se restablece después de cada solicitud.

    ```Java
    LogEntries logEntries = driver.manage().logs().get("driver");
    ```

    - `Instalar aplicación`: instala la aplicación dada en el dispositivo.

    ```Java
    driver.installApp("/Users/johndoe/path/to/app.apk");
    ```

    - `Ejecutar aplicación`: inicia la aplicación bajo prueba en el dispositivo.

    ```Java
    driver.launchApp();
    ```

    - Cerrar aplicación: cierra la aplicación bajo prueba en el dispositivo.
    
    ```Java
    driver.closeApp();
    ```

    - `Bloquear`: bloquea el dispositivo.
    ```Java
    driver.lockDevice();            
    ```

    - `Desbloquear`: desbloquea el dispositivo.
    ```Java
    driver.driver.unlockDevice();
    ```

    - `Presionar el código clave`: presiona una tecla en particular en un dispositivo Android.

    ```Java
    driver.pressKeyCode(AndroidKeyCode.SPACE, AndroidKeyMetastate.META_SHIFT_ON);
    ```

    - `Ocultar el teclado`: oculta el teclado del dispositivo.
    ```Java
    driver.hideKeyboard();
    ```

    - `Grabación de Pantalla`: graba la pantalla del dispositivo.

    ```Java
    driver.startRecordingScreen();
    driver.startRecordingScreen(new BaseStartScreenRecordingOptions(....));
    ```

    - __Elementos__:
    
        - `Encontrar elemento`: encuentra el elemento en la pantalla del dispositivo. Es decir, obtiene el primer elemento que coincida con una estrategia de localización

        ```Java
        MobileElement elementOne = (MobileElement) driver.findElementByAccessibilityId("SomeAccessibilityID");
        MobileElement elementTwo = (MobileElement) driver.findElementByClassName("SomeClassName");
        ```
 
        - `Encontrar elementos`: encuentra los elementos en la pantalla del dispositivo. Es decir, obtiene los elementos que coincidan con una estrategia de localización.

        ```Java
        List<MobileElement> elementsOne = (List<MobileElement>) driver.findElementsByAccessibilityId("SomeAccessibilityID");
        List<MobileElement> elementsTwo = (List<MobileElement>) driver.findElementsByClassName("SomeClassName");
        ```








































