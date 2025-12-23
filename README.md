# German Translation Patch for Plant Integration

This patch adds full German translation support including German sensor names for the [Plant Integration](https://github.com/Olen/homeassistant-plant).

## Changes

### Modified Files

1. **sensor.py**
   - Added `_attr_translation_key` for all 7 sensor classes
   - Added German `_attr_name` for proper display names
   - Fixed initialization order (super().__init__() before setting attributes)

2. **translations/de.json**
   - Extended with entity translations for sensor names
   - Added German sensor names (Temperature, Soil Moisture, etc.)

## Sensor Names

| English | German |
|---------|--------|
| Illuminance | Helligkeit |
| Conductivity | Leitfähigkeit |
| Soil Moisture | Bodenfeuchtigkeit |
| Temperature | Temperatur |
| Air Humidity | Luftfeuchtigkeit |
| PPFD | PPFD |
| DLI | DLI |

## Installation

1. Replace `custom_components/plant/sensor.py` with the patched version
2. Replace `custom_components/plant/translations/de.json` with the extended version
3. Restart Home Assistant
4. Delete existing plants and recreate them

## Example Result

After applying this patch, sensors will be created with German names:

```
sensor.my_plant_temperatur
sensor.my_plant_bodenfeuchtigkeit
sensor.my_plant_leitfaehigkeit
...
```

Display names:
- "My Plant Temperatur"
- "My Plant Bodenfeuchtigkeit"
- "My Plant Leitfähigkeit"
- etc.

## Technical Details

### Patched Sensor Classes

All 7 sensor classes now use:

```python
super().__init__(hass, config, plantdevice)
self._attr_translation_key = "temperature"  # or other key
self._attr_name = f"{plant_name} Temperatur"  # German name
```

Classes patched:
- PlantCurrentIlluminance
- PlantCurrentConductivity
- PlantCurrentMoisture
- PlantCurrentTemperature
- PlantCurrentHumidity
- PlantCurrentPpfd
- PlantDailyLightIntegral

## Requirements

- Home Assistant 2022.4+ (for translation key support)

## Based On

Original repository: https://github.com/Olen/homeassistant-plant (Master branch, December 2025)

## License

Same as original project
