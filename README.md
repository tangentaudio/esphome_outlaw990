# Outlaw Audio 990 AV Preamp/Processor Custom ESPHome Component

This custom component will communicate with an Outlaw Audio 990 via RS232 serial port (UART) to provide control and status feedback.

Required additions to your ESPHome `yaml` file below (set rx and tx pins of the UART as needed):

```
external_components:
  - source:
      type: git
      path: github://tangentaudio/esphome_outlaw990

uart:
  rx_pin: GPIO14
  tx_pin: GPIO13
  baud_rate: 9600
  id: uart1

outlaw_990:
  id: outlaw
  uart_id: uart1

binary_sensor:
  - platform: outlaw_990
    sensor_power:
      name: "Outlaw Power Status"
    sensor_mute:
      name: "Outlaw Mute Status"

sensor:
  - platform: outlaw_990
    sensor_volume:
      name: "Outlaw Volume Status"

text_sensor:
  - platform: outlaw_990
    sensor_display:
      name: "Outlaw Display"
    sensor_audio_in:
      name: "Outlaw Audio Input"
    sensor_video_in:
      name: "Outlaw Video Input"
```
