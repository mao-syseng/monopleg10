# cat⋅toes20
cat⋅toes20 – A sculpted, one-handed keyboard with 10 keys. Designed for individuals with limited hand mobility or those who use only one hand, including those with monoplegia, hemiparesis, amputations, or other conditions. Its ergonomic design ensures comfort and accessibility for efficient, one-handed input.

https://mao-syseng.github.io/cattoes20/

## Parts
- 10x choc switches
- 10x 1N4148 Signal Diodes
- seeed studio xiao rp2040 mcu
- 22AWG solid core wire
- 3D printed case - I would recommend using 100% infill to add some weight to it.
- Some rubber tabs on the bottom of the case to avoid slipping.


## Layout
- Taipo https://inkeys.wiki/en/keymaps/taipo
- There is interactive version of the layout here: https://mao-syseng.github.io/monopleg10/


## Site notes
- https://news.ycombinator.com/item?id=42814110
- Make something to show how to use the layout

## soldering notes
- solder columns first
- columns should be low and rows high, no need for much insulation due to low amount of wires.

## V1.1
- 5mm walls instead of 2mm
- 100% infill to add weight
- skip the bottom plate and add dutter on the case edges.
- use seeed studio xiao rp2040, Pi Pico was too big.
- add hole for wire

## Firmware notes
- hold boot button while plugging in to laptop
- drag and drop CircuitPython to the microcontroller. Remember to get correct circuitpython version for the board.
- Drag and drop KMK folder to the board.
- Edit code.py accordingly

## KMK Notes
First working version of simple KMK config!! has all base chords
```
import board

from kmk.kmk_keyboard import KMKKeyboard
from kmk.keys import KC
from kmk.scanners import DiodeOrientation
from kmk.modules.combos import Combos, Chord, Sequence

keyboard = KMKKeyboard()
combos = Combos()
keyboard.modules.append(combos)

keyboard.col_pins = (board.D4, board.D5, board.D9, board.D8)
keyboard.row_pins = (board.D1, board.D10, board.D3)
keyboard.diode_orientation = DiodeOrientation.ROW2COL

keyboard.keymap = [
    [KC.I, KC.N, KC.S, KC.R,
     KC.E, KC.T, KC.O, KC.A,
     KC.BSPC, KC.SPC, KC.NO, KC.NO]
]

combos.combos = [
    Chord((KC.R, KC.S), KC.B),
    Chord((KC.N, KC.I), KC.Y),
    Chord((KC.T, KC.E), KC.H),
    Chord((KC.A, KC.O), KC.L),
    Chord((KC.S, KC.N), KC.P),
    Chord((KC.O, KC.T), KC.U),
    Chord((KC.R, KC.I), KC.G),
    Chord((KC.A, KC.E), KC.D),
    Chord((KC.R, KC.N), KC.Z),
    Chord((KC.S, KC.I), KC.F),
    Chord((KC.A, KC.T), KC.Q),
    Chord((KC.O, KC.E), KC.C),
    Chord((KC.R, KC.T), KC.X),
    Chord((KC.O, KC.I), KC.K),
    Chord((KC.S, KC.E), KC.V),
    Chord((KC.N, KC.A), KC.J),
    Chord((KC.R, KC.E), KC.M),
    Chord((KC.A, KC.I), KC.W),
]

if __name__ == '__main__':
    keyboard.go()



```

## Cosmos 
V2 cosmos config: https://ryanis.cool/cosmos/beta#cm:Cn8KHhIJEKCABCAJSIACEgUQMEiAAjgTQMSWMUicg7iobwoWEgYQoIAGIAkSAhAwOABA0l5IgICMPAoZEgYQoIAIIAkSAhAwOBRArqaKOEibg7SobwocEgYQoIAKIAkSAhAwOChAgJKTkAJIg4uMjZDZARgAQMjQj/grSOKY1tADCj0KKhISEEAgAEDi6obIHUjTg6SP0PoBEg0gAECjhYyM0D9IgsIiOABAlIOQAxgCQPuLhJzwN0ifh6TN4fsDEAMYhiAiCQi0ARCqARiEBzAyOAOCAQBIAFgAaAByAiAF 

V3 : https://ryanis.cool/cosmos/beta#cm:CnkKGxIIEKBPIAlIgAISA0iAAjgTQMSWMUicg7iobwoWEgUQoFsgCRIDELAvOABA0l5IgICMPAoZEgUQoGcgCRIDELA7OBRArqaKOEibg7SobwoZEgUQoHMgCRIAOChAgqaTkAJIlYmIj7DXARgAQMbQj/grSOiY1qADCj0KKhISEEAgAEDi6obIHUjTg6SP0PoBEg4gAEC1hYyMkFBI2oeERTgAQOSwChgCQP2LhJzwN0ifh6TN4fsDEAMYhiAiCQi0ARCqARiEBzA8OAOCAQcAAGTIAXgASABQYlgKaAByAiAU

V3 MX: https://ryanis.cool/cosmos/beta#cm:CnkKGxIIEKBPIAlIgAISA0iAAjgTQMSWMUicg7iobwoWEgUQoFsgCRIDELAvOABA0l5IgICMPAoZEgUQoGcgCRIDELA7OBRArqaKOEibg7SobwoZEgUQoHMgCRIAOChAgqaTkAJIlYmIj7DXARgAQMbQj/grSOiY1qADCkAKLRISEEAgAEDi6obIHUjTg6SP0PoBEg4gAEC1hYyMkFBI2oeERTgAQIyDkI/AChgCQP2LhJzwN0ifh6TN4fsDGIQgIgkIvgEQvgEYhAcwPIIBBwAAZMgBeABIAFBiWApoAHICICg=

V4 MX from 30 to 25 tenting, lower pinkie, higher thumb, with screw for plate: https://ryanis.cool/cosmos/beta#cm:CngKGxIIEKBPIAlIgAISA0iAAjgTQMSWMUicg7iobwoWEgUQoFsgCRIDELAvOABA0l5IgICMPAoZEgUQoGcgCRIDELA7OBRArqaKOEibg7SobwoYEgUQoHMgCRIAOChAiZqW0AJI24mMu9kBGABAxtCP+CtI5JTH0AIKPQoqEhIQQCAAQOLqhsgdSNODpI/Q+gESDiAAQLeFjIyQUEjah4RFOABAnJQHGAJA/YuEnPA3SJ+HpM3h+wMQAiIJCL4BEL4BGIQHOAKCAQEDSAVYSWADaAByAiAZ

V5, improved spacing, optimized for MOG profile keycaps: https://ryanis.cool/cosmos/beta#cm:CngKGxIIEKBPIAlIgAISA0iAAjgTQMSWMUicg7iobwoWEgUQoFsgCRIDELAvOABA0l5IgICMPAoZEgUQoGcgCRIDELA7OBRArqaKOEibg7SobwoYEgUQoHMgCRIAOChAo+6WgANI24mMu9kBGABAxtCP+CtI5JTH0AIKPwosEhIQQCAAQOLqhsgdSNODpI/Q+gESDiAAQLeFjIyQUEjah4RFOABAwriH4BkYAkD9i4Sc8DdIn4ekzeH7AxACIgwIvgEQvgEYhAcg7Ak4AoIBAQNIBVhJYANoAHICIBk=
