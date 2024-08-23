### Batterien unter 20% außer iPhones und iPads

Sensor-Template
```
{% set sensor_count = states.sensor | selectattr("entity_id", "search", ".*batter*.") 
      | selectattr("state", "le", "20") | rejectattr('state', 'eq', '100')
      | rejectattr("entity_id", "match", ".*iphone*.")
      | rejectattr("entity_id", "match", ".*ipad*.")
      | rejectattr("entity_id", "eq", "sensor.batterie_low")
      | list | count %}
{% set binary_count = states.binary_sensor | selectattr("entity_id", "search", ".*batter*.") 
      | selectattr("state", "eq", "on")
      | list | count %}
{{ sensor_count + binary_count }}
```
### Anzahl eingeschalteter Lampen
```
{{ states.light
    | rejectattr('attributes.entity_id', 'defined')
    | rejectattr('entity_id', 'search', 'dnd')
    | selectattr('state', 'eq', 'on')
    | list | count }}
```
### Media Player playing
```
{{ states.media_player
    | selectattr('state', 'eq', 'playing')
    | list | count }}
```

