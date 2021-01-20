# Klipper Configs

This is a collection of the config files I'm currently using for Klipper. Printer-specific `printer.cfg` files are in folders, but the `.cfg` files in the root are universal.

Note: `include` directives in the printer configs assume that the included files (`menu.cfg`, etc.) are all in the same directory as `printer.cfg`.

## LCD Menu Settings

### BIQU 12864 LCD + MKS Gen L

The following needs to be included in your Klipper config to get a generic 12864 LCD to work with the MKS Gen L. Don't forget that the EXP1 & EXP2 wiring harnesses on this board are reversed, so you have to clip the tabs and flip them around.

```
[display_status]

[board_pins]
aliases:
    # EXP1 header
    EXP1_1=ar37, EXP1_3=ar17, EXP1_5=ar23, EXP1_7=ar27, EXP1_9=<GND>,
    EXP1_2=ar35, EXP1_4=ar16, EXP1_6=ar25, EXP1_8=ar29, EXP1_10=<5V>,
    # EXP2 header
    EXP2_1=ar50, EXP2_3=ar31, EXP2_5=ar33, EXP2_7=ar49, EXP2_9=<GND>,
    EXP2_2=ar52, EXP2_4=ar53, EXP2_6=ar51, EXP2_8=ar41, EXP2_10=<RST>

[display]
lcd_type: st7920
cs_pin: EXP1_4
sclk_pin: EXP1_5
sid_pin: EXP1_3
encoder_pins: ^EXP2_3, ^EXP2_5
click_pin: ^!EXP1_2
#kill_pin: ^!EXP2_8

[output_pin beeper]
pin: EXP1_1
```
