# Ejemplo-03# - Instalación y configuración de Selenium Grid 4

## Objetivo

* Agregar los objetivos del ejemplo (Mínimo agregar 2 objetivos y Borrar está linea una vez se hay leido)

## Desarrollo

#### Roles Selenium Grid

Los roles de Selenium Grid depende de las necesidades que se tengan de los componentes que ofrece Selenium Grid, ya que se puede iniciar cada uno de ellos por separado o varios al mismo. Veremos los 3 roles que ofrece Selenium Grid 4:

- `Standalone:` es la unión de todos los componentes y, a los ojos del usuario, se ejecutan como uno solo. Un Grid de uno completamente funcional está disponible después de iniciarlo en el modo `Independiente (independiente)`. De forma predeterminada, el servidor escuchará en http://localhost:4444, y esa es la URL a la que debe apuntar las pruebas de `RemoteWebDriver`. 

> `Pro-tip:` Este es el modo más fácil de hacer girar un Selenium Grid. 

- `Hub and Node(s):` Habilita la configuración clásica de Hub y Node(s). Estos roles son adecuados para Grids pequeños y medianos. Al igual que el rol de `standalone`, dee forma predeterminada el servidor escuchará en http://localhost:4444, y esa es la URL a la que debe apuntar slasus pruebas de `RemoteWebDriver`.

    + Un `Hub` es la unión de los siguientes componentes:
        - Enrutador
        - Distribuidor
        - Mapa de sesión
        - Cola de nueva sesión
        - Autobús de eventos

    Para iniciar el Hub se utilizar el siguiente comando en la terminal de la maquina: `java -jar selenium-server-<version>.jar hub` ejemplo: `java -jar selenium-server-4.1.2.jar hub`


    + Se pueden iniciar `uno o más nodos` en esta configuración, y el servidor detectará los controladores disponibles que puede usar desde la ruta del sistema.

```Java
java -jar selenium-server-<version>.jar hub
```

- `Distributed:` En el modo Distribuido, cada componente debe iniciarse por sí solo. Esta configuración es más adecuada para Grids grandes.

