# Ejemplo-03 # - Instalación de Appium & Emuladores.

## Objetivo

- Explicar el proceso de instalación de Appium, Emuladores y variables en entornos requeridas paras las pruebas en plataformas moviles.

## Desarrollo


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
7. Selecciona el dispositivo que quieras emular de la lista (se recomienda los que tienen el simbolo de google play)
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


#### :round_pushpin: ANDROID ADB

El nombre de la variable va a ser “ANDROID_HOME” y el valor va a ser la ruta donde fue instalado nuestras versiones de Andriod, se puede visualizar en el “Android SDK Manager”

#### :round_pushpin: Configuración de Entorno APPIUM
