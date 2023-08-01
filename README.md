# home assistant - backup restore

- Run docker compose down to stop the container
- Get the backup file core_2023** file, extract and put it the config file path (referenced in the Dockerfile eg: /etc/hass)
      volumes:
      - /etc/hass/:/config

- home-assistant_v2.db and .storage folder contains almost all user config data.
- Run docker compose up
