# Iot-Posters
Proyecto de Internet de las cosas para control de cartelería pública.
El proyecto consiste en módulos periféricos (Los carteles) que ejecutaran las tareas de manera automáticas sin necesidad de estar de manera permanente conectados a un servidor, este se utilizara solo para cuando se necesite consultar el estado o agregar, modificar o eliminar algunas de las tareas que debe ejecutar el cartel.  

# Módulos

## Servidor
En una PC con Windows se instala un servidor MQTT (Protocolo de comunicación ligero y bajo consumo de energía y ancho de banda) que centraliza todos los carteles conectados y a través de una interfaz desarrollada en C# permite la configuración detallada de cada tarea que ejecutará cada cartel.


## (Cliente) Hardware en el cartel
Basado en el módulo NodeMCU ESP8266 como placa controladora dentro de cada cartel, donde funciona un servidor web que nos permite la configuración inicial de conectar el dispositivo a una red wifi una vez configurado ahí que buscar la IP que el router le asigno y se accede a una página web donde se visualiza el estado del letrero (Que tarea esta ejecutado, si esta encendido o apagado, encenderlo o apagarlo).

### Configuración Inicial
- Paso 1: Cuando arranca el cartel los primeros 10 segundos indicados por el parpadeo de un led para presionar un pulsador ubicado en la placa principal para ingresar al modo configuración con la dirección IP 192.168.4.1 (en el navegador web) donde se configura la Red wifi que se debe conectar. Presionamos en guardar el dispositivo se reinicia y repite el proceso, Pasados los 10 segundos se conecta a la red wifi previamente configurada. 
- Paso 2: Buscamos en la red la ip que el router le asigno y accedemos a la página principal.

## (Cliente) MQTT Dashboard
Cliente MQTT disponible en la tienda de aplicaciones de Android [MQTT Dashboard](https://play.google.com/store/apps/details?id=com.app.vetru.mqttdashboard&hl=es_AR&gl=US). La ampliación una vez descargada está en blanco, para configurarla se necesita de otro celular con la aplicación configurada para clonarla siguiendo los pasos que la misma aplicación brida.

<img src="/images/MQTT_Dashboard.png" alt="drawing" width="300"/>


## Configuracion de las Tareas

# Las Tareas consisten en:
1. Nombre de la tarea
2. Fecha y Hora de inicio y fin
3. Habilitación de la para que su ejecución
4. Dentro de ella hay 4 secuencias a definir, sus parámetros son:
    1. Color (Depende si el cartel tiene esa capacidad)
    2. Tipo o efecto de secuencia
    3. Invertir el sentido de la secuencia
    4. Numero de repeticiones antes de pasar a la siguiente secuencia
    5. Tiempo de demora en cada segmento antes de pasar al siguiente


# Conectividad
- El acceso es completo en el nivel de red local (dentro de la conectividad del edificio). 
- Para el acceso desde fuera de la red local (desde celulares, a través de datos, desde otros proveedores de servicios de internet, etc.) es necesario la apertura de puertos, una IP fija o un nombre de dominio en su lugar.


#Estado actual
1. Determinando los mensajes que se enviaran entre los clientes y el servidor.
2. Definiendo los elementos graficos y la manera del manejo de la interfaz del programa cliente desarrollado en C# para la computadora que funcionara como servidor.
3. Verificar el algoritmo que determina la tarea a ejecutar en el cartel. 

#Librerias utilizadas
- Interfaz de estilo web [Material Desing Lite](https://getmdl.io/)
- Protoclo comunicacion MQTT [mqtt.org](https://mqtt.org/)
- Cliente MQTT para Android [MQTT Dashboard](https://play.google.com/store/apps/details?id=com.app.vetru.mqttdashboard&hl=es_AR&gl=US)
- Estructura de mesanjes cliente/serividor [arduinojson](https://arduinojson.org/)
- Plataforma de desarrollo [Arduino](https://www.arduino.cc/)
