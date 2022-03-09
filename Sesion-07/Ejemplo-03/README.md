# Ejemplo-03 # - Instalación de Appium & Emuladores.

## Objetivo

- Explicar el proceso de instalación de Appium, Emuladores y variables en entornos requeridas paras las pruebas en plataformas moviles.

## Desarrollo

#### :round_pushpin: Requisitos para usar APPIUM

Para utilizar Appium requerimos una serie de herramientas, muchas de ellas son con las que venimos trabando hasta el momento como:

- JDK (kit de desarrollo de Java)
- Eclipse
- TestNG
- Selenium Server

y otras explicaremos como instalarlas en este tema:

- ANDROID SDK (Studio)
- Appium Inspector / Appium Desktop
- .APK a testear


#### :round_pushpin: DISPOSITIVO VIRTUAL ANDROID (AVD)

Un `dispositivo virtual de Android (AVD)` es una configuración que define las características de un teléfono o una tablet Android, o de un dispositivo Wear OS, Android TV o Automotive OS, que deseas simular en Android Emulator. 

El Administrador de dispositivos es una interfaz que puedes iniciar desde `Android Studio` y te permite crear y administrar los AVD.

Un AVD contiene un perfil de hardware, una imagen del sistema, un área de almacenamiento y una máscara, entre otras propiedades.

Para crear un dispositivo virtual se debe realizar lo siguiente:

1. Descargar android studio https://developer.android.com/studio
2. Sigue el proceso de instalación

    <img src="assets/android1.png" width="50%"> 

3. Selecciona la opción "custom"

    <img src="assets/android2.png" width="50%"> 

4. En esta pantalla copia el path de la locación de la SDK de android, ya que lo requerirá para configurar la variable de ambiente de `ANDROID_HOME` más adelante.

    <img src="assets/android3.png" width="50%"> 

5. Una vez finalizada en instalación, en la pantalla principal de android seleccionar la opción `“Virtual Device Manager”`

    <img src="assets/android4.png" width="50%"> 

6. Realizar click en `"Create un virtual device"`

    <img src="assets/android5.png" width="50%"> 

7. Selecciona el dispositivo que quieras emular de la lista (se recomienda los que tienen el simbolo de play store)

    <img src="assets/android6.png" width="50%"> 

8. Descarga el la versión de android que quieras tener instalada en el dispositivo virtual

    <img src="assets/android7.png" width="50%"> 
9. Al finalizar la instalación veremos la siguiente pantalla

    <img src="assets/android8.png" width="50%"> 

10. Al clickear en el botón de play se abrirá el AVD creado

    <img src="assets/android9.png" width="50%"> 


#### :round_pushpin: VARIABLES DE ENTORNO (`JAVA_HOME` y `ANDROID_HOME`)

¿Què son variables de entorno?


`Appium necesitará consumir las variables de entorno JAVA_HOME y ANDROID_HOME` por lo que siguiendo estos pasos podrás configurarlas



ANDROID_HOME: android sdk location

El nombre de la variable va a ser “ANDROID_HOME” y el valor va a ser la ruta donde fue instalado nuestras versiones de Andriod, se puede visualizar en el “Android SDK Manager”


#### :round_pushpin: Android Debug Bridge (adb)

`Android Debug Bridge (adb)` es una herramienta de línea de comandos versátil que te permite comunicarte con un dispositivo. El comando adb permite realizar una variedad de acciones en el dispositivo, como instalar y depurar apps, y proporciona acceso a un shell de Unix que puedes usar para ejecutar distintos comandos en un dispositivo. Es un programa cliente-servidor que incluye tres componentes:

- `Un cliente`, que envía comandos. El cliente se ejecuta en tu máquina de desarrollo. Puedes invocar un cliente desde un terminal de línea de comandos emitiendo un comando adb.
- `Un daemon (adbd)`, que ejecuta comandos en un dispositivo. El daemon se ejecuta como un proceso en segundo plano en cada dispositivo.
- `Un servidor`, que administra la comunicación entre el cliente y el daemon. El servidor se ejecuta en tu máquina de desarrollo como un proceso en segundo plano.


`adb` está incluido en el paquete de herramientas de la plataforma de Android SDK. 

<img src="assets/adb.png" width="50%"> 

> para mas información visitar: https://developer.android.com/studio/command-line/adb?hl=es-419

#### :round_pushpin: Configuración de Entorno APPIUM



#### :round_pushpin: Formato de Aplicaciones Moviles (.ipa vs .apk)

Las aplicaciones moviles pueden venir en los siguientes formatos dependiendo del Sistema operativo

`APK = Paquete de aplicaciones de Android`

El paquete de aplicación de Android es el formato de archivo de paquete utilizado para distribuir e instalar aplicaciones en el sistema operativo Android de Google y en otros sistemas operativos, como Blackberry. En pocas palabras, es una aplicación de Android. Cuando crea una aplicación de Android con App Press, exportamos y le enviamos un archivo APK.

`IPA = Archivo de aplicaciones de iPhone`

Un archivo `.ipa` es un archivo de almacenamiento de aplicaciones de iOS que almacena una aplicación de iOS. Por lo general, está encriptado con la tecnología FairPlay DRM de Apple. Cada archivo .ipa se comprime con un binario para la arquitectura ARM y solo se puede instalar en un dispositivo iOS. En pocas palabras, es una aplicación para iOS. Cuando crea una aplicación para iOS con App Press, exportamos y le enviamos un archivo IPA.


<img src="assets/apps.png" width="50%"> 


#### :round_pushpin: Errores comunes y pasos para la resolución de problemas en Appium

1. `error: – Se requieren las siguientes capacidades deseadas, pero no se proporcionan: nombre del dispositivo, nombre de la plataforma`: Agregue las capacidades necesarias: nombre del dispositivo, nombre de la plataforma en el script APPIUM. por ejemplo: dc.setCapability («deviceName», «Emulator»); dc.setCapability («platformName», «Android»);

2. `error: no se pudo encontrar adb. Configure la variable de entorno ANDROID_HOME con la ruta del directorio raíz del SDK de Android.`:Probablemente necesite configurar una ruta de directorio raíz del SDK en el sistema ‘Variables de entorno’ en la columna ‘Ruta’.

3. `error: org.openqa.selenium.SessionNotCreatedException: No se pudo crear una nueva sesión.`: Debe establecer la ruta correcta de la aplicación y reiniciar el servidor de Appium.

#### :round_pushpin: Limitaciones al usar APPIUM

+ Appium no admite pruebas en la versión de Android inferior a 4.2
+ Soporte limitado para pruebas de aplicaciones híbridas. Por ejemplo: la acción de transferencia de la aplicación desde la aplicación web no se puede probar de forma nativa y viceversa.
+ No hay soporte para ejecutar Appium Inspector en Microsoft Windows.