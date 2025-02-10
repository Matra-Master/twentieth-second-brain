---
created: 20240826-1719
status: Done
tags:
  - projects
---

Expected Deadline::forever
Area::Electronics

## Resources

[picocom](https://github.com/npat-efault/picocom) mini serial terminal

### Notes

#### TODO:
- [ ] Reescribir config de kmk sin POG para mejorar uso de la memoria
- [x] Resoldar cable rojo en columna 4 lado izquierdo
- [x] Revisar columnas 1 y 2 en lado derecho
- [x] Cambiar keycaps de lugar: / por =
- [ ] Dibujar el layout real
- [x] Checkear F8 left
- [x] Checkear L right
- [ ] Implementar modulo [Layer](https://github.com/KMKfw/kmk_firmware/blob/main/docs/en/layers.md)
- [ ] Implementar modulo para [homerow mods](https://github.com/KMKfw/kmk_firmware/blob/main/docs/en/holdtap.md)
- [ ] (Optional) LEDs?

List of pins used:

col_pins
  board.GP9
  board.GP8
  board.GP7
  board.GP6
  board.GP5
  board.GP4
  board.GP3
  board.GP2

row_pins
  board.GP15
  board.GP14
  board.GP13
  board.GP12
  board.GP11
  board.GP10

data_pin board.GP1     # RX on the primary board
data_pin2 board.GP0    # TX on the primary board

```
['__class__', '__name__', 'A0', 'A1', 'A2', 'A3',
'GP0', 'GP1', 'GP2', 'GP3', 'GP4', 'GP5', 'GP6', 'GP7', 'GP8', 'GP9', 
'GP10', 'GP11', 'GP12', 'GP13', 'GP14', 'GP15', 'GP16', 'GP17', 'GP18', 'GP19',
'GP20', 'GP21', 'GP22', 'GP26', 'GP26_A0', 'GP27', 'GP27_A1', 'GP28', 'GP28_A2',
'LED', 'SMPS_MODE', 'STEMMA_I2C', 'VBUS_SENSE', 'VOLTAGE_MONITOR', '__dict__', 'board_id']
```


### External links

[[MKII left wiring.jpg]]
[[picow-pinout.svg]]
[[Ergo_S-1_Layout.png]]
[[ErgoS1 MKII Schematics.excalidraw]]

[Alternative QMK pico config from some dude](https://www.vikasraj.dev/blog/qmk-pi-pico-rp2040)

## Planning
Objective:
- Tener un nuevo teclado funcional para el trabajo

Key Results:
- 

obstacles and their solutions:
- 

Timeframe:
- 

## Reflection
Satisfied?:
- 

Improvements and solutions learned for the future:
- 
