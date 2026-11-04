# 3. Manual de Configuración y Seguridad

## Medidas de Seguridad Óptica
El trabajo con equipos DWDM implica la manipulación y exposición a radiación láser no visible (Clase 1M / 3R), la cual puede causar daños severos e irreversibles en la retina.
* **Protección Ocular:** Jamás se debe mirar directamente al extremo de una fibra óptica activa, puerto de equipo o conector del transceptor.
* **Manejo de Conectores (APC/UPC):** Es vital identificar el pulido de los conectores. Los conectores APC (Verdes, pulido en ángulo de 8 grados) no deben conectarse directamente con conectores UPC (Azules, pulido plano ultra físico). Hacerlo sin un adaptador destruirá las férulas de vidrio.
* **Limpieza Obligatoria:** Antes de realizar cualquier conexión en el ODF o los equipos, se deben limpiar los conectores con lápices limpiadores o casetes de limpieza óptica. La suciedad genera atenuación y riesgo de quemar la interfaz debido a la alta potencia del láser.

## Configuración del Chasis HT6000
El aprovisionamiento de servicios se realiza accediendo al sistema de gestión de red (NMS) del chasis mediante su interfaz web IP.

1. **Autenticación:** Ingreso con perfil de administrador al portal del HT6000.
2. **Revisión de Alarmas:** Verificar en el log de sistema que las tarjetas y fuentes de alimentación (PSU) operen sin errores críticos antes de provisionar.
3. **Mapeo de Puertos de Cliente a Línea DWDM:** Ingresar a la configuración de la tarjeta Transponder correspondiente. Se debe asignar el tráfico del puerto de cliente (conexión SFP/LAN hacia el Switch) para que sea mapeado y encapsulado hacia la interfaz de línea óptica (puerto DWDM sintonizado en una longitud de onda específica, ej. Canal 21).
4. **Validación de Gestión NMS:** Comprobar el estado de enlace (`Link Status`) de los puertos LAN del sistema de administración, asegurando conectividad con la red de control.

![Gestión NMS y Puertos LAN](/diagramas/imagenes/Esquema8.jpeg)

## Procedimiento de Prueba y Medición
Para validar la operatividad del enlace de transporte, se debe ejecutar la siguiente secuencia con la instrumentación de la maqueta:
1. **Inserción del Atenuador Óptico Variable (OVA JW3303):** Conectar el OVA en el trayecto de fibra entre el transmisor y el receptor. Aumentar progresivamente la atenuación para simular pérdidas de enlace y encontrar el umbral de sensibilidad del equipo remoto.
2. **Medición Espectral (OSA RXT4510):** Conectar el analizador de espectro al puerto de monitoreo (MON) del chasis. Se debe medir la longitud de onda central exacta del láser, la potencia óptica del canal en dBm y calcular la Relación Señal a Ruido Óptica (OSNR).
3. **Pruebas de Tráfico L2/L3 (VeEX MTX150x):** Con el circuito óptico establecido, inyectar tráfico Ethernet desde el analizador MTX150x. Ejecutar pruebas RFC 2544 para evaluar el *Throughput* (ancho de banda), la latencia, el nivel de Jitter, y descartar la pérdida de tramas o errores de bit (BER) en la transmisión.