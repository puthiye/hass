
# home assistant dashboard

![Screen Shot 2025-04-10 at 11 48 25 am](https://github.com/user-attachments/assets/0da401e3-62a9-4fef-a754-15a05816b8cf)

# raspberry system monitor 
- Use the homeassistant "System Monitor" integration to track cpu, mem, disk usage: https://www.home-assistant.io/integrations/systemmonitor/

# raspberry fan status
- Add below code in configuration.yaml and restart. The "Command Line" entity will be available to track fan status
  ```
  command_line:
  - binary_sensor:
      command: 'if [ "$( cat /sys/devices/virtual/thermal/cooling_device0/cur_state )" == "0" ]; then echo "off"; else echo "on"; fi'
      name: "rpi_fan"
      device_class: running 
      payload_on: "on"
      payload_off: "off"
  ```
Refer below links for details:
1. https://www.home-assistant.io/integrations/command_line/
2. https://www.home-assistant.io/integrations/binary_sensor/
  

# home assistant - backup restore

- Run docker compose down to stop the container
- Get the backup file core_2023** file, extract and put it the config file path (referenced in the Dockerfile eg: /etc/hass)
```
    volumes:
      - /etc/hass/:/config
```
- home-assistant_v2.db and .storage folder contains almost all user config data.
- use winscp sftp to transfer the files
- Run docker compose up
