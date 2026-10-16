# MyJotCart — Home Assistant add-on repository

[![Add repository](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fcleydar-creator%2Fmyjotcart-addon)

**The shopping list your whole household actually uses** — shared lists per store and a home pantry that refills itself, running inside your own Home Assistant. No cloud account, no subscription.

| Home pantry | Shopping list |
|---|---|
| <img src="images/home-pantry.png" width="260" alt="Home pantry with stock, minimums and days left"> | <img src="images/shopping-list.png" width="260" alt="Shopping list with items grouped by aisle"> |

## Features

- **One list per store** (supermarket, bakery, pharmacy…). Everyone in the house adds things from their phone and sees changes instantly. Items are grouped by aisle, in the order you walk the shop.
- **Shop mode**: tick items as they go into the cart, with a progress bar. *Finish shopping* moves what you bought into the home pantry.
- **Home pantry**: how much you have of each product, a minimum, and how many days one unit lasts. MyJotCart counts it down by itself and, when something runs low, puts it on its list.
- **Barcode scanner** with the phone camera, or a small ESP32 scanner in the kitchen: scan something when it's used up and it's added to the list.
- **Made for families**: each person has a name and a short PIN. Works for non-admin Home Assistant users too.
- **In the Home Assistant sidebar** and in the Home Assistant app — also from outside home whenever your Home Assistant is reachable. No extra port or login.
- **Your data stays home**: everything is stored in the add-on and included in Home Assistant backups. There's also a backup/restore file in Settings.
- **5 languages**: English, Español, Deutsch, Français, Português.

## Install

Requires **Home Assistant OS or Supervised** (add-ons, called *Apps* in recent versions) on a **64-bit** system (amd64 or aarch64, e.g. a Raspberry Pi 4/5 with the 64-bit OS, a mini PC or a VM).

1. Click the **Add repository** button above, or go to **Settings → Apps → App store → ⋮ → Repositories** (*Add-ons → Add-on store* in older versions) and add
   `https://github.com/cleydar-creator/myjotcart-addon`
2. Find **MyJotCart** in the store, click **Install**, then **Start**.
3. **MyJotCart** appears in the sidebar (cart icon). If it doesn't: MyJotCart's page in Settings → Apps → turn on **Show in sidebar**.
4. Create your user with a 4–8 digit PIN, then add the rest of the household in **Settings**.

On phones, open it from the Home Assistant app's side menu, or add it to the home screen (Safari: Share → *Add to Home Screen*; Chrome: ⋮ → *Add to Home screen*). Live camera scanning needs https — see below.

## Access: http, https and the camera

MyJotCart doesn't need its own certificate or domain. There are two ways in:

| | How | http or https? |
|---|---|---|
| **Through Home Assistant** (sidebar, Home Assistant app, dashboard card) | Home Assistant *ingress*: the app is served inside Home Assistant, at Home Assistant's own address and with its login | Whatever Home Assistant uses. If you open Home Assistant with https (Nabu Casa or your own domain), MyJotCart is https too; also from outside home |
| **Direct, on your home network** | `http://<home-assistant-ip>:8210` (the port in the add-on's *Network* settings; leave it empty to turn it off) | Plain http, only inside your network. Handy as a home-screen app on phones, and it's what the ESP32 kitchen scanner uses |

Everything works over plain http **except the live camera scanner**: browsers only allow the camera on https pages. Without https MyJotCart tells you so and lets you type the barcode number instead. To scan with the camera, open Home Assistant through its https address and use MyJotCart from there.

## Add-on or integration? (you can have both)

| | **MyJotCart add-on** (this repository) | **[MyJotCart integration](https://github.com/cleydar-creator/myjotcart-ha)** (HACS) |
|---|---|---|
| What it is | The app itself: it runs MyJotCart and keeps your data | A connector between MyJotCart and Home Assistant |
| Where you see it | **MyJotCart** in the sidebar (cart icon) | Your lists under **To-do lists**, plus a dashboard card |
| What it adds | Lists, home pantry, barcode scanner, settings | Voice with Assist (*"add milk to my supermarket list"*), sensors for automations, the *MyJotCart* dashboard card |
| Needed? | Yes | Optional |

With the integration installed, Home Assistant finds the add-on by itself: **Settings → Devices & services → Discovered → MyJotCart → Add**.

## Free and Pro

Everything above is **free**. **MyJotCart Pro** unlocks the AI features — for the price of a coffee (**€2.50, one-time, one home**) at [myjotcart.com](https://myjotcart.com/#pro):

- 📷 **Photo → product**: take a picture and it's recognised.
- 🧾 **Receipts and invoices**: a photo or PDF adds what you bought to the pantry and keeps prices per store. The image is not stored.
- 🍳 **Recipes**: checks what you have at home and adds what's missing to your list.
- 🗂️ **Smart aisles**: new products go to the right aisle automatically.

> ⚠️ **You need your own AI API key** from **Anthropic (Claude)**, **OpenAI (ChatGPT)** or **Google (Gemini)** — get one at [console.anthropic.com](https://console.anthropic.com/settings/keys), [platform.openai.com](https://platform.openai.com/api-keys) or [aistudio.google.com](https://aistudio.google.com/apikey). Pro unlocks the features in MyJotCart; the AI usage is billed by that provider on your account (a few cents per receipt). A ChatGPT Plus or Claude Pro subscription is **not** an API key.

In **Settings → Artificial intelligence**: activate your Pro key (needs internet once, then it is checked locally) and paste your AI API key.

## Support

- Bugs and ideas: open an [issue](https://github.com/cleydar-creator/myjotcart-addon/issues) (it's public — never paste keys).
- Your purchase or your Pro key: [myjotcart.com → Help & contact](https://myjotcart.com/#contact).
