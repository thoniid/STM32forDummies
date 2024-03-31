# Hola Mundo
Uno de los ejercicios más prácticos al aprender a programar un nuevo microcontrolador es realizar un "blink". Este ejercicio consiste en hacer parpadear un LED a una frecuencia determinada. De esta manera, podemos familiarizarnos con el entorno de desarrollo integrado, la configuración de un nuevo proyecto y consideraciones al utilizar la tarjeta de desarrollo.

## Blue Pill
La "Blue Pill" es una tarjeta de desarrollo que utiliza el microcontrolador STM32F103C8T6, parte de la familia STM32 de STMicroelectronics. Esta placa es popular entre los aficionados y los desarrolladores debido a su bajo costo y su capacidad para realizar una amplia variedad de tareas en proyectos de electrónica, automatización, robótica y otros.

Es conocida por su capacidad de procesamiento, sus numerosas interfaces (como UART, I2C, SPI, etc.) y su amplia gama de periféricos integrados, lo que la hace ideal para una variedad de aplicaciones en el mundo de la electrónica y la programación de microcontroladores.

<div align="center">
    <img src="https://coytbarringer.com/wp-content/uploads/2017/12/800px-Bluepill_pinout.png" alt="Pinout de la Blue Pill">
</div>

## STM32CubeIDE
STM32CubeIDE es un entorno de desarrollo integrado (IDE) gratuito que está diseñado para simplificar y acelerar el desarrollo de aplicaciones para microcontroladores STM32.

Es recomendado programar los microcontroladores utilizando las herramientas proporcionadas por los fabricantes. No obstante, esto no quita la posibilidad de que la mayoría de ellos puedan ser programados en otros entornos y/o lenguajes.  

Se puede descargar el IDE recomendado en el siguiente enlace:

https://www.st.com/en/development-tools/stm32cubeide.html

## Configuración de proyecto
En primer lugar, vamos a crear un nuevo proyecto. Para ello, debemos buscar el microcontrolador integrado en nuestra tarjeta de desarrollo. En el caso de la Blue Pill es STM32F103C8T6. 

<div align="center">
    <img src="https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/1.png" alt="Nuevo proyecto">
</div>

En segundo lugar, configuramos los parámetros básicos del nuevo proyecto. 

<div align="center">
    <img src="https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/2.png" alt="Parámetros">
</div>

En tercer lugar, se nos cargara una interfaz grafica para configurar los periféricos del microcontrolador. Esta herramienta es muy útil porque luego nos genera el código correspondiente acorde a nuestra configuración. Esto nos permite enfocarnos netamente en el desarrollo del proyecto sin invertir mucho tiempo en la configuración de los registros para que los periféricos se comporten como nosotros lo esperamos. Esto no quita la posibilidad de posteriormente poder cambiar estos ajustes desde la interfaz grafica o por código. 

Ahora vamos a configurar el reloj del sistema. De ello, es importante recordar que los microcontroladores pueden funcionar a diferentes frecuencias dependiendo a su hardware. En este caso, vamos a configurar el cristal externo, el cual es un componente electrónico que nos permitirá alcanzar los 72 Mhz de frecuencia. Es decir, 74 millones de operaciones por segundo.

<div align="center">
    <img src="https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/3.png" alt="Clock1">
</div>

Posterior a la elección del cristal externo, debemos configurar su uso. Nos vamos a la pestaña “Clock Configuration” y empezamos con la ruta de configuración. Aquí podemos elegir la fuente de principal del reloj, en este caso “HSE- High Speed External Oscillator”, también los divisores adecuados para que los perifericos funciones a la frecuencia adecuado ya que no todos pueden trabajar a la frecuencia máxima de 72 MHz. La configuración debería quedar así:

<div align="center">
    <img src="https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/4.png" alt="Clock2">
</div>

En cuarto lugar, como se mencionó anteriormente, una de las principales bondades de STM32CubeIDE es la generación de plantillas de códigos para ahorrar tiempos. Nos vamos hacia “Project Manager” y “Code Generator” para activar la generación de los códigos para cada periférico utilizado. 

<div align="center">
    <img src="https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/5.png" alt="Codigo">
</div>

En quinto lugar, nos toca configurar los periféricos. Para este ejemplo practico utilizaremos uno de los pines GPIO para conectar un LED y poder controlarlo. En esencia, un PIN GPIO (General Purpose Input/Output) puede estar encendido o apagado, en alto o bajo, con 3.3V o 0V.  

Vamos a conectar el LED en el pin PB6, así que con la ayuda de la interfaz gráfica le damos clic derecho y lo configuramos como salida “output”. De acuerdo al pinout mostrado anteriormente de la tarjeta Blue Pill, pude haber elegido cualquier pin de propósito general. 

<div align="center">
    <img src="https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/6.png" alt="PIN1">
</div>

Asimismo, a medida nuestros códigos se hagan mas completos y utilicemos una gran cantidad de pines, es recomendado tener hyperparámetros para hacer referencia a ciertos pines. En este caso, voy a nombrar el pin PB6 como “led” para que cada vez que quiera usarlo baste con llamar a “led” y no PB6. 

<div align="center">
    <img src="https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/7.png" alt="PIN3">
</div>

Por otro lado, al usar un GPIO debemos considerar ciertas características electrónicas. En primer lugar, el estado inicial del GPIO: Low (apagado). En segundo lugar, el modo del GPIO: Push Pull (0V o 3.3V). En tercer lugar, Pull-Up o Pull-Down: ninguno. En cuarto lugar, la velocidad: Low. Finalmente, el label que anteriormente asignamos como “led”.

<div align="center">
    <img src="https://github.com/thoniid/STM32forDummies/blob/main/HelloWorld/images/8.png" alt="PIN3">
</div>
