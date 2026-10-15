# MyJotCart

Shared shopping lists for the whole household (per store, live sync) and a home pantry.
Languages: English, Español, Deutsch, Français, Português — chosen from the phone's language, changeable in **Settings → Language**.

## First use
1. Install the add-on, start it and click **Open Web UI** (or enable *Show in sidebar*).
2. Create your user with a 4–8 digit PIN. Then add the rest of the household in **Settings**.

## On your phone
- In the Home Assistant app: side menu → **MyJotCart**.
- Or directly on your home network: `http://<home-assistant-ip>:8210`.
- Live barcode scanning with the camera needs **https** (Nabu Casa or your own domain). Without https you can type the code or use a photo.

## Lists on your dashboard and by voice
Install the **MyJotCart integration** from HACS (custom repository `https://github.com/cleydar-creator/myjotcart-ha`, type Integration) and restart Home Assistant.
**Settings → Devices & services** then shows MyJotCart under *Discovered*: click **Add**. Every list becomes a to-do list
(dashboard card *To-do list*, Assist: *"add milk to my Mercadona list"*) plus the sensors *Pending to buy* and *Running out at home*.

## Kitchen scanner (ESP32)
Create the device code in **Settings → Kitchen scanner**. The device calls
`http://<home-assistant-ip>:8210/api/device/scan`.

## Data
Everything stays in your Home Assistant (the add-on's folder) and is included in its backups.
