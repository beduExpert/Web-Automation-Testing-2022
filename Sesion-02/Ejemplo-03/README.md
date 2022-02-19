# Ejemplo-03: Trabajando con Esperas, Condiciones y Manejo de excepciones

## Objetivo

* Agregar los objetivos del ejemplo (Mínimo agregar 2 objetivos y Borrar está linea una vez se hay leido)

## Desarrollo

#### ¿Cuáles son las excepciones en Selenium?

Las excepciones no son más que eventos debido a los cuales el programa java finaliza abruptamente sin dar el resultado esperado. 

- __ElementNotVisibleException:__ a pesar de que el elemento está presente en el DOM, no es visible. Por ejemplo, elementos definidos en HTML con type = «hidden»
ElementNotSelectableException: un elemento está deshabilitado (no se puede hacer clic / seleccionar) a pesar de estar presente en el DOM
- __NoSuchElementException:__ Webdriver no puede determinar los elementos durante el tiempo de ejecución, es decir, el método FindBy no puede encontrar un componente en particular
- __NoSuchFrameException:__ Webdriver intenta cambiar a un frame no válido, que no está disponible
- NoAlertPresentException: Webdriver está intentando cambiar a una alerta no válida, que no está disponible
- __NoSuchWindowException:__ Webdriver está intentando cambiar a una ventana no válida, que no está disponible
- __StaleElementReferenceException:__ el elemento referenciado ya no está presente en la página DOM (una referencia a un componente ahora es obsoleta). Por ejemplo, el elemento pertenece a un frame diferente al actual o el usuario se ha desplazado a otra página
- __SessionNotFoundException:__ Webdriver está actuando inmediatamente después de «salir» del navegador
- __TimeoutException:__ el comando no se completó en el tiempo especificado. Por ejemplo, el elemento no se mostró en el tiempo especificado. Esto se encuentra especialmente cuando se trabaja con esperas de selenium webdriver
- __WebDriverException:__ Webdriver está actuando inmediatamente después de ‘cerrar’ el navegador

>**💡 Pro-tip**
>La mejor manera de manejar estas excepciones es usando varias técnicas como Try/catch, Múltiple bloques de catch, Finally y otras dependiendo de los requisitos de los scripts

#### ¿Qué son las esperas (waits) en Selenium Webdriver y cómo se manejan?

¿Recuerdas en algún momento haber ingresado en alguna página web y que la misma se tarde en cargar, o que en vez de eso, se cargue pero observamos que faltan elementos por cargarse?. 

Esto nos ha pasado muchas veces, ya que la mayoría de las aplicaciones web se desarrollan utilizando Ajax y JavaScript. Cuando una página es cargada por el navegador, los elementos con los que queremos interactuar pueden cargarse a intervalos de tiempo diferentes.


No sólo hace que esto sea difícil de identificar el elemento, sino también si el elemento no está situado, se producirá una excepción «ElementNotVisibleException». 

Usando las esperas, podemos resolver este problema. Existen 2 tipos de esperas:

#### __Espera Implícita (Implicit Wait):__
Se utiliza para establecer el tiempo de espera predeterminado. Este tipo de espera le dirá al WebDriver que espere cierta cantidad de tiempo (por defecto es 0) antes de que lance una excepción de «No Such Element Exception». Una vez que configuremos el tiempo, el WebDriver esperará ese tiempo antes de lanzar una excepción. Por ejemplo:

```Java
WebDriver driver = new FirefoxDriver();
driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(10));
driver.get("http://google.com");
WebElement googleSearch = driver.findElement(By.name("q"));
```
 
#### __Espera Explícita (Explicit Wait):__
Este tipo de espera, a diferencia de la espera implícita, se utiliza para decirle al WebDriver que espere ciertas condiciones (Expected Conditions) o el tiempo máximo excedido antes de lanzar una excepción «ElementNotVisibleException». La condición se llama con cierta frecuencia hasta que transcurre el tiempo de espera. Esto significa que mientras la condición devuelva un valor falso, seguirá intentándolo y esperando. Se podría decir que es un tipo inteligente de espera. Por ejemplo:

```Java
WebDriver driver = new ChromeDriver();
driver.get("https://google.com");
driver.findElement(By.name("q")).sendKeys("bedu" + Keys.ENTER);
// Inicializar y esperar hasta que se pueda hacer clic en el elemento (enlace): tiempo de espera en 10 segundos

WebElement firstResult = new WebDriverWait(driver, Duration.ofSeconds(10))
     .until(ExpectedConditions.elementToBeClickable(By.xpath("//button[contains(.,'Agendar Asesoría')]")));
```
 
En la espera explícita también podemos configurar con qué frecuencia queremos comprobar la condición con Fluent Wait.

```Java
// Esperar 30 segundos para que un elemento esté presente en la página, verificando su presencia una vez cada 5 segundos.
Wait<WebDriver> wait = new FluentWait<WebDriver>(driver)
  .withTimeout(Duration.ofSeconds(30))
  .pollingEvery(Duration.ofSeconds(5))
  .ignoring(NoSuchElementException.class);

WebElement foo = wait.until(new Function<WebDriver, WebElement>() {
  public WebElement apply(WebDriver driver) {
    return driver.findElement(By.id("foo"));
  }
});
```
  
__ :bangbang: Error:__ no se debe mezclar las esperas implícitas y explícitas. Esto se debe a que puede causar tiempos de espera impredecibles. Por ejemplo, establecer una espera implícita de 10 segundos y una espera explícita de 15 segundos podría causar un tiempo de espera después de 20 segundos.


#### ¿Qué son las condiciones o `ExpectedConditions`?
Las condiciones o condiciones esperadas se utilizan para realizar esperas explícitas (como lo vimos anteriormente) en una determinada condición. 

Las siguientes son las condiciones esperadas que se pueden utilizar en la espera explícita:

- alertIsPresent()
- elementSelectionStateToBe()
- elementToBeClickable()
- elementToBeSelected()
- frameToBeAvaliableAndSwitchToIt()
- invisibilityOfTheElementLocated()
- invisibilityOfElementWithText()
- presenceOfAllElementsLocatedBy()
- presenceOfElementLocated()
- textToBePresentInElement()
- textToBePresentInElementLocated()
- textToBePresentInElementValue()
- titleIs()
- titleContains()
- visibilityOf()
- visibilityOfAllElements()
- visibilityOfAllElementsLocatedBy()
- visibilityOfElementLocated()
