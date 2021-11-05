# Monitorización de la calidad del agua empleando un sistema de geoposicionamiento e inmersión de sensores
## Introducción
Los países miembros de la Organización de las Naciones Unidas suscribieron en 2015 una agenda de 17 metas (SDGs -Sustainable Development Goals) que ayudarán a alcanzar un desarrollo global sustentable, así como paz y prosperidad para la humanidad y para el planeta. El manejo sustentable del agua y velar por el acceso a este recurso para toda la población es una de estas metas.
De acuerdo con ONU y las SGDs, el agua es fundamental para el desarrollo económico, el desarrollo social y para la sustentabilidad ambiental globa [1]. Sin embargo, este recurso ha sido subvalorado por años, pues ha sido afectado por la sobreexplotación, por el uso ineficiente, por la contaminación y por otros factores que han contribuido a una realidad lacerante y a las alarmantes proyecciones futuras.
Actualmente 2 mil millones de personas en el mundo no tienen acceso al agua potable, mientras que 2.5 mil millones no pueden acceder al agua para actividades de higiene y sanidad. Para los próximos años se proyecta que el agua será un recurso escaso para un 30 %-40% de la población mundial y esto se agravará como consecuencia del cambio climático. En el peor de los escenarios, agencias de inteligencia subrayan que la crisis por el agua elevará la probabilidad de conflictos bélicos por el recurso, pues se proyecta que la demanda superará hasta en un 40% a los suministros de este vital líquido en 2030 [2].
De acuerdo con el reporte IMI-SDG6 [3], monitorizar la calidad del agua es una tarea de enorme importancia, pues coadyuva a la recuperación del recurso natural a través del diseño de políticas públicas, regulaciones, planeación e inversión en todos los niveles involucrados en el manejo del agua.
En este proyecto planteamos que al utilizar la tecnología provista por el IoT (Internet of Things) podemos obtener parámetros físicos y químicos que nos permitan inferir de mejor manera la calidad del agua. Nuestra propuesta tiene por objetivo simplificar la tarea de muestreo de parámetros y además buscamos extender los puntos de muestreo mediante la inmersión de sensores. Planteamos utilizar un sistema capaz de geo posicionar de manera remota los sensores y realizar la monitorización a diferentes profundidades. La información obtenida será almacenada y visualizada en tiempo real en un servidor WEB para hacerla accesible desde cualquier lugar del mundo.

## Objetivos
### Objetivo general
Diseñar e implementar un sistema de transporte acuático para la monitorización remota de
temperatura, acidez y turbiedad del agua empleando sensores y tecnologías del Internet de las cosas
(IoT).
### Objetivos particulares
1. Diseñar y construir el sistema de transporte acuático para los sensores y microcontroladores.
2. Instalar y configurar un Broker MQTT accesible desde Internet.
3. Implementar y configurar el módulo de geo posición con un módulo GPS instalado en el
transporte acuático.
4. Implementar el módulo de comunicaciones para el envío de datos el microcontrolador y el
Broker MQTT empleando la red celular de datos GPRS.
5. Implementar en un microcontrolador ESP32 el sistema de control de motores para el
geoposicionamiento del sistema de transporte acuático empleando puentes H.
6. Interconectar los sensores y el microcontrolador ESP32 e implementar el programa que realiza
el procedimiento de muestreo de los sensores.
7. Diseñar e implementar el sistema de inmersión de sensores empleando un servomotor.
8. Implementar el sistema de captura de datos tomando los parámetros de la posición geográfica
y altitud de la muestra, así como los parámetros de temperatura, acidez y turbiedad del agua.
9. Implementar una base de datos para el almacenamiento de los datos recolectados.
10. Implementar la aplicación WEB que permita la monitorización en tiempo real de los parámetros
observados empleando Node-RED.

## Justificación
Medir parámetros físicos y químicos para determinar la calidad del agua puede llegar a ser una labor
compleja si se realiza en áreas geográficas amplias, tales como lagunas, presas, etcétera. Pues para
poder determinar con precisión la calidad del agua se requieren suficientes muestras que ayuden a
inferir la calidad del recurso natural. De manera tal que existen posiciones geográficas cuyo acceso
puede ser complejo y la toma de muestras en esas regiones puede consumir una mayor cantidad de
tiempo y recursos.
Para facilitar el procedimiento de toma de muestras en regiones remotas planteamos diseñar un sistema
de recolección de información empleando sensores que puedan ser transportados en dispositivos
móviles. Los dispositivos móviles podrán i) posicionarse en un punto geográfico de manera automática,
mientras que los sensores podrán i) medir parámetros físicos de la superficie del agua y iii) también
podrán medir parámetros a diferentes profundidades, lo cual brindará una mayor cantidad de datos que
permitan caracterizar de mejor manera la calidad del agua.

## Operación del sistema
1. Desde el END-DEVICE se define la ruta de muestreo la cual está constituida como una secuencia de
áreas de muestreo. Esta ruta de muestreo se define desde la aplicación WEB
2. El END-DEVICE publica en el Broker MQTT un punto GPS de la ruta de muestreo.
3. El NODO FLOTANTE debe estar suscrito al Broker MQTT de modo tal que puede recibir la publicación
de la posición GPS a través de la red de datos GPRS.
4. El NODO FLOTANTE al recibir desde el Broker MQTT una posición GPS utilizará un algoritmo de
direccionamiento y el control de motores para aproximarse al área de muestreo.
4. Una vez alcanzado el área de muestreo, el NODO FLOTANTE comienza el muestreo de parámetros de
calidad del agua a nivel superficial.
5. El NODO FLOTANTE utiliza el sistema de control de inmersión para que por gravedad los sensores
puedan ser posicionados a distintas profundidades y realicen el proceso de muestreo.
6. Una vez alcanzado el límite de inmersión, el NODO FLOTANTE utiliza el sistema de control de
inmersión para subir los sensores.
7. Una vez que los sensores salen a la superficie, el NODO FLOTANTE debe indicar la finalización del
muestreo e iniciar la transmisión de los datos obtenidos al Broker MQTT empleando la red de datos
GPRS.
9. El NODO FLOTANTE queda en espera de una nueva posición GPS de muestreo.
10. El END-DEVICE almacena los datos recibidos en una base de datos y los publica en una página WEB
para que puedan ser accesibles desde cualquier lugar con acceso a Internet.

## Materiales necesarios
1. 1 Raspberry PI 4
2. 1 módulo de desarrollo con microcontrolador ESP32
3. 2 motores de 12 V
4. 2 propelas para el impulso del barco
5. 2 puente H
6. 1 servomotor
7. 1 batería de 12 volts recargable
8. 1 sensor Aqua TROLL 400 Multiparameter Probe
9. 1 módulo GT-U7 para el geoposicionamiento GPS
10. 1 módulo SIM800L para comunicaciones GPRS
11. 1 módulo magnetómetro HMC5883L

## Referencias
1. United Nations, “The United Nations World Water Development Report 2021 - Valuing Water,”
UNESCO, 2021.
2. J. D. Petersen-Perlman, J. C. Veilleux, and A. T. Wolf, “International water conflict and
cooperation: challenges and opportunities,” Water International, vol. 42, no. 2, pp. 105–120,
Jan. 2017.
3. UN Water, “Monitoring Water and Sanitation in the 2030 Agenda for Sustainable Development,”
January, 2020
