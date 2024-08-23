### Batterien unter 20% außer iPhones und iPads

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
