# Proyecto 2: Ciclos de vapor para generación de potencia

### Especificaciones

1.	Se desea proporcionar 1000 MJ/h de energía a corrientes de proceso
2.	El combustible es Gas Natural
3.	Gas Natural: (30°C, 30 bar) 89.6% mol CH4; 6% mol C2H6; 2.5% mol C3H8; 1.3% mol C4H10; 0.4% mol CO2; 0.2% mol N2.
4.	Aire; (28 °C, 1 bar) 20.9% mol O2; 79.1 % mol N2, Humedad relativa del 70%

### Objetivos a determinar

1.  Efectuar el balance de energía y calcular la eficiencia de primera ley en un horno que utiliza gas natural como combustible. 
2.  Calcular la influencia del exceso de aire, la temperatura de los gases de chimenea y la inclusión de un pre-calentador de aire.

### Reacciones de Combustión del gas natural
Las reacciones que se llevan a cabo en la cámara de combustión, son las siguientes:

![Reacciones](https://user-images.githubusercontent.com/71915068/107081140-daa73780-67b7-11eb-84dd-ef69fa63e854.PNG)

### Consideraciones de entrada al horno, aire con humedad relativa del 70%.

![Tabla Humedad Relativa](https://user-images.githubusercontent.com/71915068/107081388-38d41a80-67b8-11eb-9f8a-e8095355bc53.PNG)

### [Simulación del proceso de combustión en Hysys](https://github.com/CristopherCano/Proyectos-ASPEN-HYSYS/edit/main/Proyecto%20P1%20Balance%20de%20Energ%C3%ADa%20y%20eficiencia%20de%20un%20horno/README.md)
La simulación del proceso de combustión se abordo en el proyecto 1. A continuación se mestra el procedimeinto para simular un ciclo de vapor.

### Simulación del ciclo del vapor características y especificaciones de trabajo.

Para la simulación del ciclo de vapor, fue necesario agregar un paquete termodinámico nuevo “IAPWS-IF97”, la ventaja de trabajar con este paquete termodinámico es el ajuste de las propiedades predichas por el simulador, la ventaja del simular el proceso en HYSYS es la posibilidad de trabajar con dos paquetes termodinámicos distintos a la vez, por un lado la combustión del gas natural se simulo con “Peng-Robinson” y por el ciclo de vapor se utilizo IAPWS-IF97 que son tablas de vapor. También se puede observa la necesidad de utilizar la herramienta “Recycle”, esto es útil cuando tenemos ciclos en un proceso, este equipo itera las corrientes deseadas hasta lograr que ambas lleguen a un mismo punto en el que converjan.

![image](https://user-images.githubusercontent.com/71915068/107086233-535dc200-67bf-11eb-8cf8-fb434224881a.png)\
Figura 3. Diagrama de Flujo de Proceso del ciclo de vapor acoplado al proceso de combustión

### Irreversibilidad, trabajo equivalente mínimo y entropía.

La eficiencia basada en la primera ley de la termodinámica se puede dividir en dos, una energía que tiene el proceso más las perdidas en la atmosfera. La eficiencia basada en la primera ley de la termodinámica expresa cuanta es la energía que utiliza el proceso con respecto a la energía que se suministra al proceso, lo ideal seria que todo lo que se suministra se aproveche. 

La delta de exergías resulta ser el trabajo equivalente mínimo que requiere el sistema, es la mínima cantidad de energía en forma de trabajo que requiere un sistema para funcionar, si el proceso fuera reversible, es decir no hay irreversibilidades y no hay generación de entropía, y por consecuencia no hay trabajo perdido y todo se utiliza para que el proceso opere, este será la cantidad necesaria de trabajo, esto significa que es mínimo permitido y no se puede consumir menos que esta cantidad ya que el proceso no se llevaría a cabo, este será el trabajo contra el cual nos vamos a medir. 

La cantidad de trabajo que se está dando al proceso se compara con el trabajo equivalente mínimo, siendo deseable que sean lo mas cercano y las diferencia se dan por las irreversibilidades y por trabajo perdido, esta diferencia entre el consumo de energía en forma de trabajo real respecto al mínimo es la medida de nuestras irreversibilidades en el proceso y el área de oportunidad para mejorar el proceso.

Cada una de las contribuciones puede ser positiva o negativa, dependiendo del signo las consideraremos como un consumo o como un efecto útil. Si el trabajo es positivo se considera como un consumo de energía, el sistema está consumiendo el trabajo para llevar a cabo el proceso. Pero si es negativo resulta ser un efecto útil ya que en este caso el proceso está entregando energía.

La exergía es como un potencial energético, cuando la delta de exergía es positiva, significa que las corrientes de salida tienen mayor exergía que las corrientes de entrada, entonces fue un efecto útil, ya que se aumenta el potencial energético de las corrientes de salida, por el contrario, si la delta de exergía es negativa implica un consumo de la exergía de las corrientes para producir algo.

La eficiencia basada en la segunda ley de la termodinámica se medirá, como el efecto útil entre el consumo. Parte de la energía suministrada se pierde como trabajo perdido por las irreversibilidades en el sistema.


### [Análisis de resultados](https://github.com/CristopherCano/Proyectos-ASPEN-HYSYS/blob/main/Proyecto%20P2%20%20Ciclos%20de%20vapor%20para%20generaci%C3%B3n%20de%20potencia/Proyecto_2%20Cr%20Balance%20de%20Energ%C3%ADa%20y%20eficiencia%20de%20un%20horno_Cristopher%20Arvizu%20Cano.pdf)
- Turbina
- Bomba
- Condensador
- Evaporador
- Intercambiadores Q1 y Q2
- Separador
- CONSUMO DE GAS NATURAL CASO A1

![image](https://user-images.githubusercontent.com/71915068/107087692-70939000-67c1-11eb-8b59-7f113341bd38.png)\
Fig.1 Ciclo de vapor operando a 100 bar con dos mezcladores, dos bombas, dos compresores Caso D1

### Conclusiones
-	La eficiencia es el consumo asociado al efecto útil, es una medida de que tan bien están siendo aprovechada la energía por el equipo.
-	La evolución en el domo a sido principalmente en el aumento de presión, con una presión inicial de 10 bar, 20 bar, 50 bar y finalmente 100 bar, provocando una disminución en el consumo de gas.
-	El trabajo perdido disminuyo debido a que se acercaron las temperaturas, provocando una disminución del consumo de gas.
-	El trabajo perdido es mayor en una expansión súbita que en lugar de dos etapas de expansión. 
-	El mezclado de corrientes, a medida que se aumentaba la presión en el domo asociado al aumento de presión en la bomba provoco que la diferencia de temperaturas en el mezclado de corrientes aumentara, provocando que en las primeras modificaciones el trabajo perdido aumentara. El problema se corrigió con la extracción de una corriente de la primera turbina y se aumentó la temperatura.
-	En el caso del condensador la carga térmica fue disminuyendo. La máquina térmica recibe calor de los gases de combustión, produciendo 1000kW y el resto se desecha como calor, a lo largo de las modificaciones se logró disminuir la cargar del condensador de los 3125 en el primer caso y se terminó con menos de 2000 kW, un ahorro considerable de energía.
-	Puntos donde se generan irreversibilidades
-	Transferencia de calor por gradientes de calor

### Referencia
Gloria Villaflor , Graciela V. Morales y Jorge Velasco. (2008). Variables Significativas del Proceso de Combustión del Gas Natural. Información Tecnológica, Vol.19, paginas (57-67).De Dianlet Base de datos.


