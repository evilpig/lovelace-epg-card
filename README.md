I have modified the code by yohaybn to include the following features:

* Appealing styling/colors
* Indicators for Live or New episodes
* Pop up descriptions of episodes when clicked
* Each channel name/logo is a button which can control your harmony remote (if you have one)
* Logos must be placed in the www/logo folder in this format (channel number.png, eg 114.png, 115.png) Easy to find them online.

Original Card: https://github.com/yohaybn/lovelace-epg-card

Screenshots (I am using the theme [Frosted Glass Dark](https://github.com/wessamlauf/homeassistant-frosted-glass-themes)):
<img width="1031" height="634" alt="image" src="https://github.com/user-attachments/assets/daaa0f3f-fd35-4018-a930-d7c5963d3bc1" />
<img width="578" height="255" alt="image" src="https://github.com/user-attachments/assets/15ab85b8-a5f2-4d39-98ce-ee4413609660" />

## Example Card Configuration (with Harmony remote)

```yaml
type: custom:epg-card
entities:
  - sensor.101_global_tvlistings
  - sensor.102_cbc_tvlistings
  # ... more entities
row_height: 40
enable_channel_clicking: true           # Default behavior
harmony_entity_id: remote.harmony_hub
harmony_device_id: "79382863"
```

## Example Card Configuration (no remote)

```yaml
type: custom:epg-card
entities:
  - sensor.101_global_tvlistings
  - sensor.102_cbc_tvlistings
  # ... more entities
row_height: 40
enable_channel_clicking: false          # Disables remote functionality
```

Original Description:
# Lovelace EPG Card

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
