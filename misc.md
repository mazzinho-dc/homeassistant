# HA MISC

## TTS (Normal)
```yaml
service: notify.alexa_media
data:
  message: "Hey! Habt ihr schon die Tonne für morgen früh herausgestellt?"
  target: media_player.DEINE_ALEXA_HIER
  data:
    type: tts
```

### TTS (Ankündigung)
```yaml
service: notify.alexa_media
title: "Titel für z.B. Echo Show Geräte"
data:
  message: "Lust auf mehr Home Assistant?"
  target: media_player.DEINE_ALEXA_HIER
  data:
    type: announce
    method: all
```

### Sounds abspielen
```yaml
#SoundEffect
service: media_player.play_media
target:
  entity_id: media_player.DEINE_ALEXA_HIER
data:
  media_content_type: sound
  media_content_id: amzn_sfx_doorbell_chime_01
  ```
 # Mehr Sounds: 
 https://github.com/alandtse/alexa_media_player/wiki#known-available-sounds

### Temp disable kiosk mode
```url
add ?disable_km to url
```
