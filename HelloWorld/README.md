# Hola Mundo
Uno de los ejercicios más prácticos al aprender a programar un nuevo microcontrolador es realizar un "blink". Este ejercicio consiste en hacer parpadear un LED a una frecuencia determinada. De esta manera, podemos familiarizarnos con el entorno de desarrollo integrado, la configuración de un nuevo proyecto y consideraciones al utilizar la tarjeta de desarrollo.

## Blue Pill
La "Blue Pill" es una tarjeta de desarrollo que utiliza el microcontrolador STM32F103C8T6, parte de la familia STM32 de STMicroelectronics. Esta placa es popular entre los aficionados y los desarrolladores debido a su bajo costo y su capacidad para realizar una amplia variedad de tareas en proyectos de electrónica, automatización, robótica y otros.

Es conocida por su capacidad de procesamiento, sus numerosas interfaces (como UART, I2C, SPI, etc.) y su amplia gama de periféricos integrados, lo que la hace ideal para una variedad de aplicaciones en el mundo de la electrónica y la programación de microcontroladores.

![Pinout de la Blue Pill](https://coytbarringer.com/wp-content/uploads/2017/12/800px-Bluepill_pinout.png)

## STM32CubeIDE
STM32CubeIDE es un entorno de desarrollo integrado (IDE) gratuito que está diseñado para simplificar y acelerar el desarrollo de aplicaciones para microcontroladores STM32.

Es recomendado programar los microcontroladores utilizando las herramientas proporcionadas por los fabricantes. No obstante, esto no quita la posibilidad de que la mayoría de ellos puedan ser programados en otros entornos y/o lenguajes.  

Se puede descargar el IDE recomendado en el siguiente enlace:

https://www.st.com/en/development-tools/stm32cubeide.html

## Configuración de proyecto
En primer lugar, vamos a crear un nuevo proyecto. Para ello, debemos buscar el microcontrolador integrado en nuestra tarjeta de desarrollo. En el caso de la Blue Pill es STM32F103C8T6. 

![Nuevo proyecto](https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/1.png)

En segundo lugar, configuramos los parámetros básicos del nuevo proyecto. 

![Parámetros](https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/2.png)

En tercer lugar, se nos cargara una interfaz grafica para configurar los periféricos del microcontrolador. Esta herramienta es muy útil porque luego nos genera el código correspondiente acorde a nuestra configuración. Esto nos permite enfocarnos netamente en el desarrollo del proyecto sin invertir mucho tiempo en la configuración de los registros para que los periféricos se comporten como nosotros lo esperamos. Esto no quita la posibilidad de posteriormente poder cambiar estos ajustes desde la interfaz grafica o por código. 

Ahora vamos a configurar el reloj del sistema. De ello, es importante recordar que los microcontroladores pueden funcionar a diferentes frecuencias dependiendo a su hardware. En este caso, vamos a configurar el cristal externo, el cual es un componente electrónico que nos permitirá alcanzar los 72 Mhz de frecuencia. Es decir, 74 millones de operaciones por segundo.

![Clock](https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/3.png)

Posterior a la elección del cristal externo, debemos configurar su uso. Nos vamos a la pestaña “Clock Configuration” y empezamos con la ruta de configuración. Aquí podemos elegir la fuente de principal del reloj, en este caso “HSE- High Speed External Oscillator”, también los divisores adecuados para que los perifericos funciones a la frecuencia adecuado ya que no todos pueden trabajar a la frecuencia máxima de 72 MHz. La configuración debería quedar así:

![Clock](https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/4.png)

En cuarto lugar, como se mencionó anteriormente, una de las principales bondades de STM32CubeIDE es la generación de plantillas de códigos para ahorrar tiempos. Nos vamos hacia “Project Manager” y “Code Generator” para activar la generación de los códigos para cada periférico utilizado. 

![Codigo](https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/4.png)

