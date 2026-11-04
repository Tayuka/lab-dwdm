# 1. Fundamentos Teóricos de DWDM

## Definición de DWDM
La multiplexación por división de longitud de onda densa (DWDM, *Dense Wavelength Division Multiplexing*) es una tecnología que permite transmitir múltiples señales de datos simultáneamente a través de un único hilo de fibra óptica, utilizando diferentes longitudes de onda (colores de luz láser) para cada canal. 
A diferencia de CWDM (*Coarse Wavelength Division Multiplexing*), que tiene una separación amplia entre canales (20 nm) y soporta menos canales, DWDM utiliza un espaciamiento muy reducido, lo que permite multiplexar decenas o incluso cientos de canales en la misma fibra óptica, ideal para transmisiones de altísima capacidad a larga distancia.

## Espectro y Longitudes de Onda
Los sistemas DWDM operan principalmente en la **Banda C** (1530 nm a 1565 nm) debido a que es la región donde la fibra óptica de sílice presenta la menor atenuación (aproximadamente 0.2 dB/km) y es compatible con los amplificadores ópticos EDFA.
La asignación de las longitudes de onda se rige por la grilla espectral definida en la recomendación **ITU-T G.694.1**. El espaciamiento entre canales puede ser de:
* **100 GHz** (aprox. 0.8 nm).
* **50 GHz** (aprox. 0.4 nm).
* **Flexible Grid (Grilla Flexible):** Permite asignar anchos de banda dinámicos a los canales según los requerimientos de la señal (ej. para canales de 400G o superiores).

## Modulación Óptica
Para transmitir información a altas velocidades, las señales eléctricas se convierten en ópticas mediante transpondedores, utilizando distintos formatos de modulación:
* **NRZ (Non-Return-to-Zero):** Modulación de intensidad básica utilizada en velocidades de 10G o inferiores.
* **PAM4 (Pulse Amplitude Modulation 4-level):** Codifica 2 bits por símbolo usando 4 niveles de intensidad, común en transmisiones de 100G a distancias cortas/medias.
* **QPSK (Quadrature Phase Shift Keying) y QAM (Quadrature Amplitude Modulation):** Formatos de modulación coherente que manipulan la fase y amplitud de la luz. Son esenciales para transmisiones de 100G, 200G y 400G a largas distancias.

## Estándares y Normativas
El diseño y operación de las redes de transporte óptico se rigen por los siguientes estándares fundamentales:
* **ITU-T G.694.1:** Define las grillas de frecuencias espectrales para aplicaciones DWDM.
* **ITU-T G.709:** Define las interfaces para la Red de Transporte Óptico (OTN), encapsulando el tráfico del cliente con corrección de errores (FEC) y cabeceras de gestión.
* **ITU-T G.652:** Especifica la Fibra Monomodo Estándar (SMF), la más utilizada en el mundo para transmisión general.
* **ITU-T G.655:** Especifica la fibra monomodo con dispersión desplazada no nula (NZ-DSF), optimizada específicamente para sistemas DWDM al reducir los efectos no lineales.