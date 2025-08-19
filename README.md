# Enhanced EPG Card for Home Assistant

A beautiful, feature-rich Electronic Program Guide card for Home Assistant Lovelace, based on [yohaybn/lovelace-epg-card](https://github.com/yohaybn/lovelace-epg-card) and extended for advanced TV setups and smart remotes.

---

## ✨ Features

- **Modern, appealing styling and colors** — looks great with dark themes and custom fonts.
- **Channel switching support for Harmony or any remote entity** (with editable/manual channel numbers).
- **Manual override for channel numbers** per sensor for custom setups.
- **One-click channel navigation** — Channel names/logos are buttons to change the TV channel.
- **Live/New episode indicators** (requires custom sensors, e.g., Gracenote).
- **Pop-up program descriptions** — Click on any show for a details overlay.
- **Remote control can be disabled for view-only dashboards**.
- **Logo support** — Place channel logos as PNGs in `/config/www/logo/` (named by channel number, e.g., `114.png`).
- **Visual Editor** — Configure everything directly from the Home Assistant UI.

> **Supports the [Frosted Glass Dark theme](https://github.com/wessamlauf/homeassistant-frosted-glass-themes) and [Quicksand Font](https://fonts.google.com/specimen/Quicksand)** for a sleek, modern look.

---

## 📸 Screenshots

![EPG full width](https://github.com/user-attachments/assets/daaa0f3f-fd35-4018-a930-d7c5963d3bc1)
![EPG channel](https://github.com/user-attachments/assets/15ab85b8-a5f2-4d39-98ce-ee4413609660)
![EPG popout](https://github.com/user-attachments/assets/b68a8fd5-cdd4-40f7-8a35-c6fc8daff2af)

---

## 🛠️ Configuration Examples

### Harmony Remote Integration

```
type: custom:epg-card
entities:
    sensor.101_global_tvlistings
    sensor.102_cbc_tvlistings
    ... more entities
row_height: 40
enable_channel_clicking: true       # Channel logos/names are clickable
harmony_entity_id: remote.harmony_hub
harmony_device_id: "79382863"
channels:                           # (optional) manual override per entity
  sensor.101_global_tvlistings: "101"
  sensor.102_cbc_tvlistings: "102"
```

### View-Only (Disable Remote Control Integration)

```
type: custom:epg-card
entities:
    sensor.101_global_tvlistings
    sensor.102_cbc_tvlistings
    ... more entities
row_height: 40
enable_channel_clicking: false      # Makes the EPG informational only
```

---

## 📂 Channel Logo Placement

Save PNG logos of each channel in the `/config/www/logo/` folder, named with the channel number (e.g., `114.png`, `115.png`).
These are widely available online or from your TV provider.

---

## ℹ️ Additional Notes

- **Live/New Icon Support:** By default, the EPG integration does not supply live or new flags. If you use your own sensors (e.g., with Gracenote or another metadata source), those status indicators will display automatically.
- **Pop-up Descriptions:** Click on any program entry to view episode details in a modal.
- **Works with Any Remote:** Works out of the box with Harmony and may work with other remote entities (e.g., Android TV, Samsung, etc.) if exposed in Home Assistant as a `remote` entity.

---

## 🙏 Credits

- Based on [yohaybn/lovelace-epg-card](https://github.com/yohaybn/lovelace-epg-card)
- Theme: [Frosted Glass Dark](https://github.com/wessamlauf/homeassistant-frosted-glass-themes)
- Font: [Quicksand](https://fonts.google.com/specimen/Quicksand)

---

**Enjoy your beautiful, clickable TV schedule in Home Assistant!**

---

# Original Card Description:

This is a custom Lovelace card for Home Assistant that displays Electronic Program Guide (EPG) data. It is designed to work in conjunction with the custom Home Assistant integration available at [https://github.com/yohaybn/HomeAssistant-EPG](https://github.com/yohaybn/HomeAssistant-EPG).  **You must install this integration for the card to function correctly.** The card fetches program information from the sensors provided by this integration and presents it in a user-friendly timeline format. Please note that the current styling is basic, and contributions to improve its appearance are highly welcome!

## Features

* Displays EPG data for multiple channels.
* Dynamic timeline starting from the current time.
* Configurable row height for program entries.
* Tooltips on program entries showing title, description, and start/end times.
* Easy configuration through the Lovelace UI editor.
![screenshot](/images/screenshot.png)
## Installation

1. **Manual Installation:**
   - Copy the `epg-card.js` file to your `/config/www/` directory (or any other directory served by your Home Assistant frontend).
   - Add the following to your `configuration.yaml` file (adjust the path if necessary):

     ```yaml
     lovelace:
       resources:
         - url: /local/epg-card.js?v=1.0.0 # Add a version number to the URL for cache busting
           type: module
     ```

2. **HACS Installation (Recommended):**
   - Add the following repository to HACS as a custom repository: `https://github.com/evilpig/lovelace-epg-card`
   - Search for "Lovelace EPG Card" in HACS and install it.  HACS will handle the resource inclusion automatically.

## Configuration

You can configure the card through the Lovelace UI editor.  Just add the card to your dashboard and click "Edit".

The following options are available:

* **`entities` (Required):** A list of entity IDs representing your EPG sensors.  These sensors are created and managed by the [HomeAssistant-EPG](https://github.com/yohaybn/HomeAssistant-EPG) integration.
* **`row_height` (Optional):** The height of each program row in pixels. Defaults to 100px.

## Example Card Configuration

```yaml
type: custom:epg-card
entities:
  - sensor.epg_channel_1
  - sensor.epg_channel_2
row_height: 120

```


## Styling

The current styling of the card is quite basic. I apologize for this! I am not a designer. Contributions to improve the look and feel of the card are highly encouraged and very welcome! Please feel free to submit pull requests with CSS improvements or suggestions.



## Troubleshooting

-   **"Error: No entities configured"**: Make sure you have configured at least one entity in the card configuration.
-   **"Error: Entity [entity_id] not found"**: Double-check that the entity ID is correct and that the entity exists in your Home Assistant instance. Ensure the [HomeAssistant-EPG](https://github.com/yohaybn/HomeAssistant-EPG) integration is correctly configured and working.
-   **EPG Data not showing**: Verify the [HomeAssistant-EPG](https://github.com/yohaybn/HomeAssistant-EPG) integration is providing data to the sensors. Check the Developer Tools -> States menu in Home Assistant to inspect the sensor data.



## Contributing

Contributions are welcome! Please submit pull requests for bug fixes, new features, or improvements, especially for styling enhancements!


### Donate
[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/yohaybn)

If you find it helpful or interesting, consider supporting me by buying me a coffee or starring the project on GitHub! ☕⭐
Your support helps me improve and maintain this project while keeping me motivated. Thank you! ❤️
