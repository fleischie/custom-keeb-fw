# Custom DZ60 Firmware

This project contains the files to customize my DZ60 keyboard.

## Layouts
### Physical

My keyboard is a split space iso layout with some notable differences:
- Split space with a function key in the middle,
- ANSI-style left shift key (2u), and
- split right shift key (1u each) <- by mistake. :/

I thus had to customize a layout definition to my use-case, which is described
by the following patch:
- [custom_layout.patch](./custom_layout.patch)

### Logical
#### Mk. I

As my first custom mechanical keyboard has a 60% form factor I needed to make
some adjustments to the layout in order to provide me with all the necessary
modifiers, media keys, etc. that I use. I also tried to reuse some of vim's
keybindings for which I already developed muscle memory.

Thus I created the following keyboard definition file:
- [dz60-custom_vim_keeb_mk_i.json](./dz60-custom_keep_mk_i.json)

##### Vim mode

The function key between the space bars enters a "vim" mode, which translates
the plain alpha keys into the following keys:
- "h" = ←
- "j" = ↓
- "k" = ↑
- "l" = →
- "g" = Pos1
- "1" - "0" = F1 - F10
- "-" = F11
- "=" = F12
- "`" = Escape
- Ctrl-H = Backspace
- Ctrl-U = Page Up
- Ctrl-D = Page Down
- Ctrl-[ = Escape
- Ctrl-E = ↑
- Ctrl-Y = ↓
- Shift-G = End

##### Keyboard modifier

The physical key right to the split rshift key is now the keyboard modifier key
to interact with the keyboard firmware (as well as some media keys):
- "q" - "[" = RGB modifiers
- "c" - "m" = Backlight modifiers
- "]" = N-key rollover toggle
- "\" = RESET + Bootloader mode
- "1" = Volume mute toggle
- "2" = Volume down
- "3" = Volume up
- "5" = Media previous
- "6" = Media stop
- "7" = Media play/pause toggle
- "8" = Media next
- "-" = Display brightness down
- "=" = Display brightness up

## Documentation

Make sure you have the appropriate qmk drivers and toolkit files installed.

- Clone the qmk firmware: `git clone https://github.com/qmk/qmk_firmware`,
- clone this repo: `git clone https://github.com/fleischie/custom-keeb-fw`,
- go into qmk firmware and patch the layout files: `cd qmk_firmware; git apply
  ../custom-keeb-fw/custom_layout.patch`,
- copy the definition file: `cp ../custom-keeb-fw/*.json .`,
- compile the firmware file: `qmk compile <desired definition file>`,
- put keyboard in bootloader mode, and
- flash the firmware: `qmk flash <desired firmware file>`.
