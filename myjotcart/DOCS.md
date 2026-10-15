# MyJotCart

Listas de la compra compartidas por toda la casa (por supermercado, en vivo) e inventario de casa.

## Primer uso
1. Instala el add-on, actívalo y pulsa **Abrir interfaz web** (o *Mostrar en la barra lateral*).
2. Crea tu usuario con una clave de 4 a 8 números. Después, en **Ajustes**, añade al resto de la casa.

## Desde el móvil
- Dentro de la app de Home Assistant: menú lateral → **MyJotCart**.
- O directamente en la red de casa: `http://<ip-de-home-assistant>:8210`.
- La cámara para escanear códigos necesita **https** (Nabu Casa o tu dominio). Sin https puedes escribir el código o usar la foto.

## Escáner de cocina (ESP32)
En **Ajustes → Escáner de la cocina** se crea el código del aparato. El aparato llama a
`http://<ip-de-home-assistant>:8210/api/device/scan`.

## Datos
Todo se guarda en tu Home Assistant (carpeta del add-on) y entra en sus copias de seguridad.
