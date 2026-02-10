# Koostetiedosto - Kaikki konfiguraatiot
Päivitetty: Tue Feb 10 18:26:34 UTC 2026

## Tiedosto: configuration.yaml
```yaml

###############################################################################
# Home Assistant – configuration.yaml
# Rakenne: Packages + erillinen YAML-dashboard (Heatpump)
###############################################################################

homeassistant:
  name: Home
  country: FI
  currency: EUR
  time_zone: Europe/Helsinki
  unit_system: metric
  packages: !include_dir_named packages     # Aktivoi /config/packages/

default_config:

# --- LOVELACE ---
# Pidä oletusdashboard UI-tilassa (storage), mutta lisää erillinen YAML-dashboard.

lovelace:
  mode: storage
  dashboards:
    heat-pump:                # <-- url path / sivupalkin tunniste: täytyy sisältää '-'
      mode: yaml
      title: Heat Pump
      icon: mdi:heat-pump
      show_in_sidebar: true
      filename: dashboards/heatpump.yaml   # tiedosto sijaitsee /config/dashboards/heatpump.yaml



# --- LOGGER (valinnainen) ---
# logger:
#   default: info
#   logs:
#     homeassistant.components.template: info
#     homeassistant.components.statistics.sensor: info

# --- TEMPLATE ---
# Pidetään tyhjänä; käytämme trigger-based templateja packages-kansiossa.
template: []

# --- SENSORIT ---
# Jos haluat käyttää erillistä sensors-kansiota, poista kommentti alta
# sensor: !include_dir_merge_list sensors

# --- AUTOMAATIOT / SCRIPTIT / SKENAARIOT ---
# Pidä oletus UI-tiedostot. Halutessasi voit myöhemmin vaihtaa kansiorakenteeseen.
automation: !include automations.yaml
script: !include scripts.yaml
scene: !include scenes.yaml

# --- RECORDER & HISTORY ---
recorder:
  purge_keep_days: 30
  commit_interval: 30
  # Jos et käytä erillistä tietokantaa, poista seuraava rivi tai määritä secrets.yaml:iin.
  # db_url: !secret recorder_db

history:

```
---
