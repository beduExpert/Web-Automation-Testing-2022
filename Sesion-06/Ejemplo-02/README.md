# Ejemplo-02 # Qué es Selenium Grid y su Arquitectura

## Objetivo


* Identificar el uso de Selenium Grid y cuando es requerida su implementación.
* Hacer uso de la arquitectura de Selenium Grid para elaborar estrategias de ejecución de pruebas.

## Desarrollo

Selenium Grid es un aherramienta que forma parte de la suite de Selenium, y permite la `ejecución de scripts de WebDriver en máquinas remotas (virtuales o reales)` mediante el `enrutamiento` de comandos enviados por el cliente a `instancias de navegador remotas`. Su objetivo es proporcionar una manera fácil de ejecutar `pruebas en paralelo` en varias máquinas.

De igual forma nos permite ejecutar pruebas en paralelo en varias máquinas y administrar diferentes versiones y configuraciones del navegador de forma centralizada (en lugar de en cada prueba individual).

#### Propósitos y funcionalidades principales:
- Punto de entrada central para todas las pruebas.
- Gestión y control de los nodos/entorno donde se ejecutan los navegadores.
- Escalada de pruebas..
- Ejecución de pruebas en paralelo.
- Pruebas multiplataforma.
- Balanceo de carga.

#### ¿Cuándo usar Selenium Grid?

En términos generales, hay dos razones por las que podría querer usar Grid.

1. Para ejecutar sus pruebas en múltiples navegadores, múltiples versiones del navegador y navegadores que se ejecutan en diferentes sistemas operativos.
2. Para reducir el tiempo que tarda el conjunto de pruebas en completar un pase de prueba.

Grid se utiliza para acelerar la ejecución de un caso de prueba mediante el uso de varias máquinas para ejecutar pruebas en paralelo. Por ejemplo, si tiene un conjunto de 100 pruebas, pero configura Grid para admitir 4 máquinas diferentes (VM o máquinas físicas separadas) para ejecutar esas pruebas, su conjunto de pruebas se completará en (aproximadamente) una cuarta parte del tiempo que tarda si se ejecutan las pruebas secuencialmente en una sola máquina. 

Para conjuntos de pruebas grandes y conjuntos de pruebas de ejecución prolongada, como los que realizan grandes cantidades de validación de datos, esto puede suponer un importante ahorro de tiempo. Algunos conjuntos de pruebas pueden tardar horas en ejecutarse. 

Otra razón para aumentar el tiempo dedicado a ejecutar la suite es acortar el tiempo de respuesta de los resultados de las pruebas.

Selenium Grid también se utiliza para admitir la ejecución de pruebas en varios entornos de tiempo de ejecución, específicamente, en diferentes navegadores al mismo tiempo. Por ejemplo, se puede configurar un "Grid" de máquinas virtuales, cada una de las cuales admite un navegador diferente que debe admitir la aplicación que se va a probar. Entonces:


- Máquina 1: tiene Internet Explorer 8
- Máquina 2: tiene Internet Explorer 9
- Máquina 3: tiene el Chrome más reciente.
- Máquina 4: tiene el Firefox más reciente. 

Cuando se ejecuta el conjunto de pruebas, Selenium-Grid recibe cada combinación de navegador de prueba y asigna cada prueba para que se ejecute en su navegador requerido.

Una configuración como esta proporciona una ejecución paralela para completar rápidamente el plan de pruebas y soporte para múltiples tipos de navegador y versiones simultáneamente.


#### Arquitectura de Selenium Grid 4

Selenium Grid 2  constaba de dos procesos: `Hub y Nodes`. Pero actualmente la versión de Selenium 4 admite cuatro procesos distintos: `enrutador`, `mapa de sesión`, `distribuidor` y `nodo`.

<img src="assets/arquitectura_selenium_grid.png" >

+ `Enrutador (Router)`: El enrutador se encarga de `reenviar la solicitud` al componente correcto. Es el punto de entrada del Grid, todas las solicitudes externas serán recibidas por él. 

    Se comporta de manera diferente según la solicitud: 

        1. Si se trata de una solicitud de sesión nueva, el enrutador la agregará a la cola de sesión nueva. 
        2. El Distribuidor comprueba regularmente si hay un espacio libre. Si es así, la primera solicitud coincidente se elimina de la cola de nueva sesión. recibirá el evento y sondeará la Cola de Nueva Sesión para obtener la nueva solicitud de sesión. 
        3. Si la solicitud pertenece a una sesión existente, el enrutador enviará la identificación de la sesión al mapa de sesión, y el mapa de sesión devolverá el nodo donde se está ejecutando la sesión. 
        4. Después de esto, el enrutador reenviará la solicitud al nodo.

    El Router tiene como objetivo `equilibrar la carga` en el Grid enviando las solicitudes al componente que puede manejarlas mejor, sin sobrecargar ningún componente que no sea necesario en el proceso.




