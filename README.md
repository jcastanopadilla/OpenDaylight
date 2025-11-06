# Guía paso a paso de configuración de OpenDaylight (ODL) 
# Asignatura: configuración de redes  
# Tema: OpenDaylight (ODL) 
# Jose Miguel Castaño Padilla
# Lugar: Lorica 
# _____________________________________________________________________________________________________________________________________________
# Primera parte: Fundamentos teóricos 
# ¿Qué es OpenDaylight (ODL)? 
# 
El proyecto OpenDaylight es una plataforma de código abierto para redes definidas por software (SDN) que utiliza protocolos abiertos para proporcionar control programático centralizado y monitoreo de dispositivos de red.
# La arquitectura OpenDaylight (ODL) es: 
#<img width="575" height="376" alt="im_1" src="https://github.com/user-attachments/assets/51530c7a-f238-45b9-ac8c-f1c99df2061e" />
# 
#
La arquitectura de OpenDaylight (ODL) está basada en una estructura modular y orientada a servicios. Diseñada para ofrecer flexibilidad, escolaridad y compatibilidad con distintos controladores y dispositivos de red.
# 1. Capa de infraestructura o southbound (Sur). 
- Es la capa que se comunica directamente con los dispositivos de red físicos o virtuales, como switches y routers.
# 2. Capa del Núcleo o control.
- Es el corazón de OpenDaylight.
- Se encarga de recibir la información recibida de los dispositivos y tomar decisiones de control (por ejemplo, rutas, políticas, etc.).
- Está basada en el framework OSGi (Open Services Gateway initiative), que permite que los componentes se instalen o actualicen de forma modular (sin reiniciar el controlador).
# Componentes clave del núcleo: 
- MD-SAL (Model-Driven Service Abstraction Layer): permite la comunicación entre los módulos sin depender directamente entre sí.
- Data Store: base de datos interna que guarda el estado de la red.
- YANG Models: define los datos y servicios de la red de manera estandarizada.
# 3. Capa de Aplicación o Northbound (Norte). 
- Es la capa donde interactúan las aplicaciones SDN y las herramientas externas. 
- Usa APIs Northbound (REST, RESTCONF, JSON, XML) para que las aplicaciones puedan consultar o modificar el estado de la red.
# 4. Capa de servicios (Services Layer). 
- Actúa como intermediario entre las aplicaciones y el núcleo.
# Segunda parte: guía de aplicación 
1. Iniciamos VirtualBox y abrimos mininet
# <img width="535" height="291" alt="im_2" src="https://github.com/user-attachments/assets/4e602e1d-c172-4051-8e66-6b92306136d0" />
2. Iniciamos sesión con:
   - login: mininet
   - password: mininet
   - y mostrara lo siguiente una vez estemos en mininet
# <img width="349" height="302" alt="im_3" src="https://github.com/user-attachments/assets/9efa9b52-205d-41d7-8354-5525b80bc0e0" />
3. escribimos el comando siguiente:
   - ifconfig
   - y mostrara nuestra ip:
# <img width="398" height="421" alt="im_4" src="https://github.com/user-attachments/assets/42a5052e-37cc-4dbf-815e-9a4b63781a0e" />
4. abrimos puTTY y agregamos nuestra ip:
   - 192.168.101.10
# <img width="369" height="361" alt="im_5" src="https://github.com/user-attachments/assets/46b1bbb6-2a81-4723-b346-df4b712612da" />
   - Una vez agregamos la ip vamos a X11 en puTTY y agregamos lo siguiente: 
   - Localhosh.0
   - Y abrimos puTTY  
#  <img width="428" height="419" alt="im_6" src="https://github.com/user-attachments/assets/1222f8ea-ee96-4306-8546-4f16525b1034" />
5. Iniciamos sesión en puTTY con:
   - login: mininet
   - password: mininet 
# <img width="569" height="352" alt="im_7" src="https://github.com/user-attachments/assets/d8f897df-a91d-4307-96a8-1ef4fdae43de" />
# <img width="567" height="462" alt="im_8" src="https://github.com/user-attachments/assets/588e003c-0dd9-4bc9-bf89-c28966db09b1" />
Ahora en puTTY agregamos los siguientes comandos para la instalación de OpenDaylight (ODL).
Paso 1: Actualizar el sistema. 
   - sudo apt update && sudo apt upgrade -y
# <img width="551" height="254" alt="im_9" src="https://github.com/user-attachments/assets/7d0815aa-95d5-4c49-9dce-f36d8b3fc246" />
Paso 2: Instalar jdk 17 (requerimiento de ODL) manualmente desde el repositorio oficial.
   - sudo apt update
   - sudo apt install wget -y
   - sudo apt install software-properties-common –y
   - sudo add-apt-repository ppa:openjdk-r/ppa –y
   - sudo apt update
   - sudo apt install openjdk-17-jdk -y
# <img width="549" height="321" alt="im_10" src="https://github.com/user-attachments/assets/5c448d3e-fe0a-4054-9bfb-b77b192f715c" />
Verificación de la versión instalada. 
   - java -version 
# <img width="548" height="90" alt="im_11" src="https://github.com/user-attachments/assets/9cea9367-8ea3-4d3e-951f-6a27283b96a1" />
Paso 3: descargar OpenDaylight (ODL).
   - Wget 
https://nexus.opendaylight.org/content/repositories/opendaylight.relea
 se/org/opendaylight/integration/karaf/0.19.2/karaf-0.19.2.zip
# <img width="525" height="150" alt="im_12" src="https://github.com/user-attachments/assets/5bf5ca06-73d3-424d-80c8-31cde2cdadc7" />
Paso 4: una vez el archivo descargado descomprimimos e iniciamos OpenDaylight. 
   - Unzip karaf-0.19.2.zip
   - Cd karaf-0.19.2
   - ./bin/karaf
Una vez ejecutamos todos estos comandos tendríamos nuestra instalación de 
OpenDaylight (ODL).
# <img width="523" height="280" alt="im_13" src="https://github.com/user-attachments/assets/1ac2f381-a02e-4bbf-bb53-bb2628869067" />
Para serrar OpenDaylight.
   - Logout 
# <img width="527" height="557" alt="im_14" src="https://github.com/user-attachments/assets/58d8421d-d821-4552-996a-9f911c9f6228" />
Hola respecto al final de OpenDaylight tuve un problema que se me ha bloqueó la máquina virtual y he intentado varias veces arreglarla y no he podido aquí le muestro el final:
# <img width="673" height="706" alt="im_15" src="https://github.com/user-attachments/assets/a242a71e-fa36-4112-8cad-6578743527a3" />
# Conclusión  
En este trabajo se pudo evidenciar que la configuración de OpenDaylight (ODL) es fundamental porque garantiza un control eficiente, seguro y automatizado de toda 
la infraestructura de red, permitiendo aprovechar al máximo la ventaja de la arquitectura SDN. 
#
En esta guía se realizo el paso a paso de la configuración de OpenDaylight, donde 
primero se debe realizar la actualización del sistema para nuestra configuración de 
OpenDaylight, seguidamente nos pide obligatoriamente instalar jdk, posteriormente 
descargamos OpenDaylight y por último una vez descargado descomprimimos nuestro archivo e iniciamos OpenDaylight gracias a todo este proceso se realizó 
correctamente nuestra instalación.  
#
En conclusión, esta guía no solo consolida los fundamentos teóricos, si no también 
ofrece una base practica para futuras implementación y comparaciones con otros 
controladores similares.
















 



 






   
   



 
   
   
