# Guía paso a paso de configuración de OpenDaylight (ODL) 
# Asignatura: configuración de redes  
# Tema: OpenDaylight (ODL) 
# Jose Miguel Castaño Padilla
# _____________________________________________________________________________________________________________________________________________
# Primera parte: Fundamentos teóricos 
# ¿Qué es OpenDaylight (ODL)? 
# El proyecto OpenDaylight es una plataforma de código abierto para redes definidas por software (SDN) que utiliza protocolos abiertos para proporcionar control programático centralizado y monitoreo de dispositivos de red.
# La arquitectura OpenDaylight (ODL) es: 
#<img width="575" height="376" alt="im_1" src="https://github.com/user-attachments/assets/51530c7a-f238-45b9-ac8c-f1c99df2061e" />
# La arquitectura de OpenDaylight (ODL) está basada en una estructura modular y orientada a servicios. Diseñada para ofrecer flexibilidad, escolaridad y compatibilidad con distintos controladores y dispositivos de red.
# 1. Capa de infraestructura o southbound (Sur). 
- Es la capa que se comunica directamente con los dispositivos de red físicos o virtuales, como switches y routers.
# 2. Capa del Núcleo o control.
- Es el corazón de OpenDaylight.
- Se encarga de recibir la información recibida de los dispositivos y tomar decisiones de control (por ejemplo, rutas, políticas, etc.).
- Está basada en el framework OSGi (Open Services Gateway initiative), que permite que los componentes se instalen o actualicen de forma modular (sin reiniciar el controlador).    
