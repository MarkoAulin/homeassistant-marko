# Koostetiedosto - Kaikki konfiguraatiot
Päivitetty: Wed Feb 11 19:35:57 UTC 2026

## Tiedosto: configuration.yaml
```yaml
###############################################################################
# Home Assistant – configuration.yaml
# Rakenne: Packages + erillinen YAML-dashboard (Heatpump) + diag-dashboard
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
# Pidä oletusdashboard UI-tilassa (storage), ja lisää kaksi YAML-dashboardia:
#  - Heat Pump (dashboards/heatpump.yaml)
#  - HP Diagnoosi (dashboards/heatpump_diag.yaml)

lovelace:
  mode: storage
  dashboards:
    heat-pump:                # <— url path / sivupalkin tunniste (sisältää '-')
      mode: yaml
      title: Heat Pump
      icon: mdi:heat-pump
      show_in_sidebar: true
      filename: dashboards/heatpump.yaml
    hp-diag:
      mode: yaml
      title: HP Diagnoosi
      icon: mdi:stethoscope
      show_in_sidebar: true
      filename: dashboards/heatpump_diag.yaml

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
automation: !include automations.yaml
script: !include scripts.yaml
scene: !include scenes.yaml

# --- RECORDER & HISTORY ---
recorder:
  purge_keep_days: 30
  commit_interval: 30
  # db_url: !secret recorder_db

history:
```
---
