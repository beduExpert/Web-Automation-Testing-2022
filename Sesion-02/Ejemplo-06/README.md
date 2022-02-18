# Ejemplo-05: Validaciones o Aserciones

## Objetivo

* Reconocer los tipos de aserciones.
* Implementar la clase Assert de TestNG en los scripts de pueba.

## Desarrollo

Como último tema de esta sesión veremos lo referente al último paso de nuestras clases de prueba: las validaciones. Sabemos que todo caso de prueba tiene un comportamiento esperado, y que el mismo debe ser validado para saber si nuestro caso de prueba funciona correctamente o según lo esperado.

Para estas validaciones TestNG nos ofrece lo que se llaman “aserciones” que se obtienen de la clase Assert. A continuación se muestra la sintaxis genérica de las afirmaciones de TestNG:


```Java
Assert.methodName(actual, esperado);
```

Donde los parámetros:
- `methodName`: es el nombre del método que se puede usar para implementar aserciones de TestNG.
- `actual`: es el primer parámetro que describe el valor que obtiene el usuario durante la ejecución del script de prueba.
- `esperado`: es el segundo parámetro que describe lo que el usuario debe obtener para validar la funcionalidad del caso de prueba.

#### Existen dos tipos se aserciones:

- **Afirmación suave (Soft Assert):** Es un método no estático que cuando la condición de la aserción no coincide no arroja ningún error, y cuando falla la condición de aserción, continúa con el siguiente paso del caso de prueba generando un mensaje de error junto con una excepción de aserción, luego continúa con la misma ejecución del script de prueba.

  En esta asercion se debe usar `assertAll()` al final de los scripts de prueba porque siempre recopila todos los seguimientos de registro y se muestra en la consola.

- **Afirmación dura (Hard Assert):** es un método estático que cuando el caso de prueba falla lanza una `AssertException` . Cuando esto sucede TestNG genera la excepción del mensaje de error, luego detiene la ejecución del script de prueba actual y continúa la implementación con el script de prueba restante.

<img src="assertTypes.png" width="50%"> 

Ahora explicaremos como funcionan las aserciones mas usadas en la actualidad:


- assertNotEquals: es lo opuesto a assertEquals, se compara el parámetro “real” con “esperado”. Si NO son iguales la aserción pasa sin excepción pero si son los mismos, la afirmación falla con una excepción y la prueba se marca como fallida.

```Java
Assert.assertNotEquals (mensaje real, esperado);
```

- assertEquals: este método compara el parámetro “real” con “esperado”. Si son iguales la aserción pasa sin excepción pero si no son los mismos, la afirmación falla con una excepción y la prueba se marca como fallida.

```Java
Assert.assertEquals (real, esperado);
```

- assertFalse: comprueba si el valor devuelto es falso o no. Siempre que pasa el caso de prueba, aborta el método y da una excepción.

```Java
Assert.assertFalse (condición);
```

- assertNull: esta aserción verifica si el objeto es nulo o no. Anula la prueba si el objeto es nulo y da una excepción.

```Java
Assert.assertNull (objeto);
```

- assertNotNull: esta aserción verifica si el objeto es nulo o no. Anula la prueba si el objeto no es nulo, es decir, si el objeto tiene algún valor y da una excepción.

```Java
Assert.assertNotNull (objeto);
```