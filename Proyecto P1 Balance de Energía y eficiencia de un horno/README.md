# Proyecto 1: Balance de energía y eficiencia de un horno

### Especificaciones

1.	Se desea proporcionar 1000 MJ/h de energía a corrientes de proceso
2.	El combustible es Gas Natural
3.	Gas Natural: (30°C, 30 bar) 89.6% mol CH4; 6% mol C2H6; 2.5% mol C3H8; 1.3% mol C4H10; 0.4% mol CO2; 0.2% mol N2.
4.	Aire; (28 °C, 1 bar) 20.9% mol O2; 79.1 % mol N2, Humedad relativa del 70%

### Objetivos a determinar
1.	La Temperatura adiabática de flama
2.	La cantidad de combustible necesario (kmol/h)
3.	La temperatura de los gases de combustión antes de entrar al pre-calentador de aire, cuando sea el caso.
4.	Calcular la eficiencia de primera ley para los gases de combustión, tomando como base el poder calorífico bajo del combustible.

### Reacciones de Combustión del gas natural
Las reacciones que se llevan a cabo en la cámara de combustión, son las siguientes:

![Reacciones](https://user-images.githubusercontent.com/71915068/107081140-daa73780-67b7-11eb-84dd-ef69fa63e854.PNG)

### Consideraciones de entrada al horno, aire con humedad relativa del 70%.

![Tabla Humedad Relativa](https://user-images.githubusercontent.com/71915068/107081388-38d41a80-67b8-11eb-9f8a-e8095355bc53.PNG)

### Simulación del proceso de combustión en Hysys
La simulación del proceso de combustión en un horno se realizó mediante Hysys. Se seleccionó para el cálculo de las propiedades fisicoquímicas el modelo termodinámico Peng Robinson como ecuación de estado. La simulación del proceso usando Hysys se dividió en cuatro etapas: 1) definición del problema a resolver; 2) simulación del problema; 3) casos de sensibilidad; 4) análisis de resultados.

Para generar el proceso de la cámara de combustión en el simulador, se empleó un reactor tipo “bach”, debido a que el simulador Hysys no dispone del módulo de combustión. En la Fig. 1 se muestra el esquema utilizado para la simulación. La segunda parte consiste en simular la corriente de proceso retirando una cantidad fija de calor de 1000 MJ/h, para simular esta parte se empleó un heat exchanger.

En la figura 2 se muestra el esquema utilizado para la simulación con una corriente de precalentamiento. Los hidrocarburos (corriente: Gas) y el aire (corriente: Aire) son combinados en un mezclador y la corriente mezclada es alimentada al reactor que opera a presión de 100kPa, la corriente líquida en nula a la salida del reactor (Líq).

![Esquema de simulación del Proceso de combustión](https://user-images.githubusercontent.com/71915068/107081518-7173f400-67b8-11eb-9ad8-504cd4315e18.PNG)

### Reactor simulación del proceso de combustión

Se utilizó el “reactor de conversión” disponible en el simulador. El reactor de conversión es un tanque agitado discontinuo en el cual ocurren reacciones de conversión; reacciones que proceden hasta que alcanza una conversión especificada o hasta que desaparece el reactivo limitante. No es necesario el uso de expresiones cinéticas. Dado que para las reacciones de combustión la constante de equilibrio es sumamente grande, puede considerarse las reacciones (1) a (4) como irreversibles y de primer orden. Este tipo de simulación nos permitirá conocer la temperatura adiabática de flama, de acuerdo a las cantidades estequiometrias que se ingresan de aire y gas.

![Esquema de simulación del Proceso de combustión](https://user-images.githubusercontent.com/71915068/107081518-7173f400-67b8-11eb-9ad8-504cd4315e18.PNG)

### Resultados y discusión

```Sin precalentamiento```

Considerando una temperatura de entrada de aire de 28°C y de gas de 30°C. Se trabajó variando el exceso de aire desde 10%, hasta un 30%. El cálculo de los flujos de aire estequiométrico y el exceso se realizó utilizando la relación estequiométrico de las reacciones. 
En la Fig. 3 se muestran las temperaturas de los gases de combustión generadas en función del porcentaje de exceso de aire utilizado sin precalentar.

![Efecto del exceso de aire en la temperatura de gases de combustión](https://user-images.githubusercontent.com/71915068/107082011-2e665080-67b9-11eb-8adc-844a9e6457cb.PNG)

Mientras más exceso de aire se tenga, mayor cantidad de gas se necesita para cumplir la carga térmica requerida de 1000 MJ/h, y entre más baja sea la temperatura de los gases combustión el consumo de gas va a empezar a disminuir ya que el gas transfiera energía a costa de su temperatura. 
En la Fig. 4 se muestran las temperaturas de flama adiabática generadas en función del porcentaje de distintos excesos de aire utilizados, sin precalentar. Se observa que, al mantener la temperatura de gases de entrada constante, la temperatura de flama adiabática disminuye con el exceso de aire. 

![Temperatura adiabatica de flama](https://user-images.githubusercontent.com/71915068/107082453-cf550b80-67b9-11eb-937c-130dbd1763a6.PNG)

![Eficiencia del proceso en función del flujo de gas](https://user-images.githubusercontent.com/71915068/107082502-e5fb6280-67b9-11eb-8049-070eabd4abad.PNG)

![Eficiecia en función de la temperatra de los gases de combustion](https://user-images.githubusercontent.com/71915068/107082551-f6abd880-67b9-11eb-9779-65b98c455c39.PNG)

La eficiencia de forma general, sin precalentamiento de aire, aumenta entre más frio salgan los gases de combustión ya que se aprovecha más el calor disponible de los gases de combustión. El efecto del exceso de aire disminuye la eficiencia ya que se ingresa más aire frio que no tiene influencia en el proceso y solo se caliente provocando que se pierda energía y salga a temperatura de gases de chimenea. 

![Eficiencia tabla](https://user-images.githubusercontent.com/71915068/107082649-1f33d280-67ba-11eb-81d3-3daab0d30c79.PNG)

```Con precalentamiento```

En la Fig. 5 se muestra la eficiencia del proceso llevado a cabo en el horno en función del precalentamiento a distintos excesos de aire, utilizando 1.2 kgmol/h de gas combustible constante. De manera general se observa que la eficiencia aumenta con el precalentamiento, la eficiencia va a subir ya que la temperatura de los gases de salida que sin el precalentamiento es elevada, con el aire precalentado estamos haciendo que se enfríen más los gases de salida y el calor de los gases se aprovecha y se regresa al proceso. Entre más frio salgan los gases de combustión la eficiencia empieza a subir y el consumo de combustible va disminuir, la temperatura adiabática de flama solo es función entre la relación de aire/combustible y la temperatura de precalentamiento.

![Eficiencia del gas natural en función del precalentamiento de gas natural](https://user-images.githubusercontent.com/71915068/107082978-90738580-67ba-11eb-80b2-33b6f381cf3b.PNG)

El efecto neto del precalentamiento, es permitir que una de las corrientes entre más caliente, provocando que la temperatura adiabática de flama aumente, disminuyendo el consumo de combustible.

![Precalentamiento Temperatura adiabatica de flama](https://user-images.githubusercontent.com/71915068/107083090-c0bb2400-67ba-11eb-8d62-cd11cb169218.PNG)

En el precalentamiento, se da un poco más de energía a la corriente de aire aumentando la temperatura adiabática de flama, dependiendo de la temperatura de salida de los gases de combustión deseada se podrá disminuir el consumo de gas natural, en general disminuirá mientras más frio salgas los gases de combustión.
Mientras más exceso de aire se tiene, mayor cantidad de combustible se requiere para alcanzar la misma temperatura.

![Fig 8  Temperatura adiabática de flama en función del exceso de aire](https://user-images.githubusercontent.com/71915068/107083336-14c60880-67bb-11eb-8fff-d521f48428c9.PNG)

![Fig 9  Temperatura gases de chimenea en función del exceso de aire](https://user-images.githubusercontent.com/71915068/107083440-3d4e0280-67bb-11eb-8471-3e6c0e45cc33.PNG)

### Coclusiones

-	La eficiencia con el precalentamiento de manera general aumenta, aunque no siempre es factible precalentar debido a los cruces de temperatura.
-	La eficiencia más alta corresponde al exceso de aire más bajo.
-	La temperatura adiabática de flama va a disminuir a medida que aumente el exceso de aire.
-	El exceso de aire a utilizar debe ser el mínimo posible, compatible con la combustión completa del combustible, ya que el mismo diluye los gases de combustión y consume calor. Este calor perdido aumenta el consumo de combustible, por lo que el uso de exceso de aire correcto conlleva un ahorro de combustible, con la consiguiente disminución de emisión de dióxido de carbono a la atmósfera.
-	Conviene aprovechar el calor de los gases de combustión, para precalentar el aire, disminuyendo la temperatura de salida de los gases de chimenea.
-	Las variables significativas del proceso de combustión de gas natural son: Exceso de aire, temperatura del aire (con precalentamiento utilizando el calor sensible de los gases de chimenea) y temperatura de los gases de salida de chimenea


### Bibliografía

Gloria Villaflor , Graciela V. Morales y Jorge Velasco. (2008). Variables Significativas del Proceso de Combustión del Gas Natural. Información Tecnológica, Vol.19, paginas (57-67).De Dianlet Base de datos.
