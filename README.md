# AUX-2 Grove LCD

English | [简体中文](README.zh-CN.md)

Add a Seeed Grove LCD RGB Backlight (16×2) to the Home Assistant Connect AUX-2. The first row shows playback status and progress, for example `PLAY 01:23/04:56`. The second row shows the title and artist and scrolls if the text exceeds 16 characters. Track metadata comes from Sendspin. Unsupported characters appear as `?`.

## Installation

1. Connect the LCD to the AUX-2's Grove port. The configuration enables Grove power and detects the V5 (`0x30`) or V4 (`0x62`) backlight controller. Check [Seeed's power requirements](https://wiki.seeedstudio.com/Grove-LCD_RGB_Backlight/) before connecting it.
2. Put [`aux-2-grove-lcd.yaml`](aux-2-grove-lcd.yaml) next to your device YAML. Add the `grove_lcd` entry below to your existing `packages:` section and keep the original [AUX-2 package](https://github.com/NabuCasa/aux-2/blob/main/packages/aux-2.yaml).

   ```yaml
   packages:
     # Keep your existing AUX-2 package entry.
     grove_lcd: !include aux-2-grove-lcd.yaml
   ```

3. If you use Improv to set up Wi-Fi and your device YAML does not already enable it, add these top-level entries:

   ```yaml
   improv_ble:
     authorizer: none
   improv_serial:
   ```

4. Validate and compile your **device YAML** in ESPHome Builder. This configuration was successfully compiled with ESPHome **2026.11.0-dev**.

## Backlight and status

- **LCD Backlight**: Set the color and brightness, or turn the backlight on or off.
- **LCD Automatic Color**: Blue during playback, amber during pause or announcements, white when idle, and red when a network or device error is detected. Turn this switch off to keep your manual color setting.
- **LCD Status**: View playback or error status in Home Assistant.

## 3D printing

Download [`Grove_LCD_R2_PC.3mf`](3d-print/Grove_LCD_R2_PC.3mf) and open it in a slicer that supports 3MF. The repository includes the original file. Check your printer and material settings before slicing.
