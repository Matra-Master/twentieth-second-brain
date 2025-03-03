---
created: 20240407-1037
tags:
  - nvim
  - arduino
---

Qué cosas hace el Arduino IDE que deba hacer mi Neovim para considerarse un reemplazo adecuado?
- Serial Monitor
- Librería de ejemplos a la mano
- Elegir board y cambiar settings
- Compilar y buildear
- Syntax highlight

Parece que la mayoría las resuelve el Arduino CLI

Resolver de a una:

- [ ] Syntax highlight
- [ ] Compilar y buildear
- [ ] Elegir board y cambiar settings
- [ ] Librería de ejemplos a la mano
- [ ] Serial Monitor

### Temporal Hacky solution

Por casualidad me enteré que el Arduino IDE 2 está hecho a base del vscode, lo que me hizo pensar que tal vez soporta plugins, y dicho y hecho luego de copiar y pegar el plugin vim de vscode en arduino IDE **vim funciona en el IDE!**


---
## Related Ideas:
* [[fleeting]]
* [Hands-on with the Arduino CLI](https://blog.arduino.cc/2020/04/23/hands-on-with-the-arduino-cli/)
* [Arduino and vim no IDE required](https://forum.arduino.cc/t/arduino-and-vim-no-ide-required/882004)
