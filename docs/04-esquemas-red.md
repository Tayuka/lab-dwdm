\# 4. Esquemas de Red y Flujo de Señal



\## Diagrama de Conexiones Físicas

El siguiente diagrama ilustra la topología física de la maqueta de laboratorio, detallando el cableado entre la instrumentación, los equipos de agregación y la red de transporte DWDM.



\*(Nota: El diagrama de red oficial se encuentra en la carpeta diagramas/imagenes/)\*

!\[Diagrama Físico de la Maqueta](../diagramas/imagenes/diagrama-fisico.png)



\## Mapeo de Puertos

A continuación, se detalla la matriz de interconexión física de los componentes:



\* \*\*Analizador MTX150x (TX/RX)\*\* <--> \*\*Switch CSS610 (Puerto SFP+ 1)\*\*: Enlace Ethernet para inyección de tráfico.

\* \*\*Switch CSS610 (Puerto SFP+ 2)\*\* <--> \*\*Chasis HT6000 (Transponder Slot 1 - Puerto Cliente)\*\*: Enlace de agregación hacia el equipo de transporte.

\* \*\*Chasis HT6000 (Transponder Slot 1 - Puerto Línea DWDM)\*\* <--> \*\*Módulo MUX (Slot 2 - Puerto Canal Específico)\*\*: Patchcord interno para multiplexación de la longitud de onda.

\* \*\*Módulo MUX (Slot 2 - Puerto COM/Line)\*\* <--> \*\*ODF (Puerto 1 In/Out)\*\*: Salida de la señal multiplexada hacia el panel de distribución principal.

\* \*\*ODF (Puerto 1)\*\* <--> \*\*Carrete de Fibra (AB - 25 KM)\*\*: Enlace de fibra óptica monomodo simulando larga distancia.

\* \*\*Carrete de Fibra (AB - 25 KM)\*\* <--> \*\*Atenuador Óptico (OVA JW3303)\*\*: Inserción en línea para control de atenuación.

\* \*\*Atenuador Óptico (OVA JW3303)\*\* <--> \*\*Analizador de Espectro (OSA RXT4510)\*\*: Conexión en el extremo receptor (o puerto de monitoreo) para validación espectral.



\## Flujo de la Señal (Paso a Paso)

1\. \*\*Generación (Cliente):\*\* El analizador VeEX MTX150x genera tramas Ethernet de prueba que ingresan al Switch de agregación CSS610.

2\. \*\*Ingreso a DWDM:\*\* El Switch envía este tráfico cliente hacia el puerto cliente del Transponder (Slot 1) en el chasis HT6000.

3\. \*\*Conversión Electro-Óptica:\*\* El Transponder recibe la señal, la procesa y la retransmite a través de su puerto de línea utilizando un láser sintonizado en una longitud de onda DWDM específica de la banda C.

4\. \*\*Multiplexación:\*\* La señal óptica coloreada ingresa al módulo MUX/DEMUX (Slot 2), donde se combina con otras posibles longitudes de onda en un solo hilo de fibra a través del puerto COM.

5\. \*\*Transmisión de Larga Distancia:\*\* La señal combinada sale del chasis, pasa por el panel pasivo ODF y viaja a través del carrete de fibra óptica de 25 km, experimentando atenuación natural.

6\. \*\*Atenuación Controlada y Monitoreo:\*\* La señal atraviesa el atenuador óptico (donde se añade pérdida manual si la guía de laboratorio lo requiere) y llega a su destino, donde el instrumento OSA RXT4510 lee el espectro y verifica la calidad óptica antes de la demultiplexación final.

