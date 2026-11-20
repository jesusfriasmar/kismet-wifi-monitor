# Monitoreo de redes Wi-Fi con Raspberry Pi 4 y Kismet
 
Sistema de monitoreo pasivo de redes inalámbricas 802.11 con Raspberry Pi 4, Kismet y un adaptador Wi-Fi en modo monitor. Proyecto personal de aprendizaje en seguridad de redes inalámbricas.
 
## Objetivo
 
Observar de forma pasiva el entorno Wi-Fi (redes, canales, intensidad de señal y paquetes) para entender cómo se comporta el espectro 2.4/5 GHz y practicar análisis de redes inalámbricas.
 
## Hardware y software
 
| Componente | Detalle |
|---|---|
| Equipo | Raspberry Pi 4 Model B, 4 GB RAM |
| Almacenamiento | SSD externa (arranque del sistema desde USB) |
| Alimentación/puertos | Hub USB con alimentación externa (4x USB-A, 3x USB-C) |
| Adaptador Wi-Fi | Alfa AWUS036ACM (MediaTek MT7612U), compatible con modo monitor |
| Sistema operativo | Raspberry Pi OS (Debian 13) |
| Software | Kismet |
 
## Qué hace
 
- Pone la interfaz inalámbrica en modo monitor.
- Captura y muestra redes detectadas, canales, RSSI y paquetes observados.
 
## Instalación y configuración
 
1. Instalar Kismet en Raspberry Pi OS:
   ```bash
   sudo apt update
   sudo apt install kismet
   ```
2. Habilitar SSH para acceder a la Pi desde otro equipo de la red:
   ```bash
   sudo systemctl enable --now ssh
   ```
3. Conectarse desde otro equipo:
   ```bash
   ssh [usuario]@[IP-de-la-Pi]
   ```
4. Iniciar Kismet y agregar la interfaz del adaptador Alfa como fuente de datos (Data Sources) desde la interfaz web.
5. Abrir la interfaz web de Kismet: `http://[IP-de-la-Pi]:2501`
 
## Capturas

<img width="1070" height="806" alt="Setup de hardware" src="https://github.com/user-attachments/assets/63905d6d-e402-48c9-9f6b-18d32378ce09" />
 
<img width="1024" height="546" alt="Kismet: escaneo de canales" src="https://github.com/user-attachments/assets/4d9ea424-6420-4223-bbfe-3c87aa078515" />
 
> Los identificadores de redes de terceros (SSID/MAC) están ocultos por privacidad.
 
## Resultados y aprendizajes
 
- En la sesión del 11/11/2026, Kismet detectó 439 dispositivos con un tráfico de ~324 paquetes/s.
- Escaneo por saltos (hopping) sobre 91 canales en 2.4 y 5 GHz: una pasada tarda 18 s, así que cada canal se escucha solo ~1.1% del tiempo.
- La Raspberry Pi 4 sostuvo la captura con ~6% de CPU, ~95 MB de memoria y 32 °C.
 
## Limitaciones
 
- Solo observación pasiva, no se modifica ni se interfiere con ninguna red.
- Depende del chipset del adaptador y de su soporte de modo monitor.
- Con el hopping en todos los canales, la cobertura por canal es baja; fijar canales (p. ej. 1, 6 y 11) mejora la captura.
 
## Roadmap
 
- [ ] Script para automatizar el arranque en modo monitor
- [ ] Exportar métricas por canal (CSV)
- [ ] Dashboard para visualizar la ocupación de canales
- [ ] Documentación de la metodología
 
## Uso ético
 
Este proyecto se usa únicamente para observación pasiva en entornos propios o con autorización. Usa herramientas de este tipo solo donde tengas permiso.

## Autor
 
Jesus Frias Mariscal, estudiante de Ingeniería en Electrónica y Comunicaciones (FIME-UANL).
[LinkedIn](https://linkedin.com/in/jesus-frias-mariscal)
 
