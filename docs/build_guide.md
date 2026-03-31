# Build Guide

## Before You Start

Make sure you have all components from the [BOM](bom.md) and the tools listed there. Read through the entire guide before soldering.

## Step 1: Inspect the PCB

Check both sides of the bare PCB for any defects — scratches on traces, bridged pads, or missing solder mask. The front side has switch holes and the Grogu silkscreen. The back side is where most SMD components go.

![PCB Front](images/board_front.jpeg)
![PCB Back](images/board_back.jpeg)

## Step 2: Solder SMD Components (Back Side)

Work on the **back of the PCB** first. Solder in this order:

### 2a: Diodes (54×)

The 1N4148W SOD-123 diodes have a **polarity line** — match it to the silkscreen marking on the PCB.

Technique:

1. Apply flux to both pads
2. Tin one pad with a small blob of solder
3. Hold the diode with tweezers, reheat the tinned pad, slide the diode in
4. Check alignment, then solder the second pad
5. Reflow the first pad if needed

![Diode Top](images/diode_top.jpeg)
![Diode Bottom](images/diode_bottom.jpeg)

### 2b: Shift Registers (4×)

Three 74HC595 (column drivers) and one 74HC165 (row reader), all SOIC-16.

1. Apply flux along all pads
2. Align pin 1 (dot on chip) with pin 1 marking on PCB
3. Tin one corner pad to tack the chip down
4. Verify all pins are aligned with pads
5. Drag solder across the remaining pins with plenty of flux
6. Clean up any bridges with solder wick

![Shift Register](images/shift_register.jpeg)

### 2c: Resistors (7×)

The 10kΩ 0805 resistors have **no polarity** — orientation doesn't matter. Same technique as diodes.

![Resistor](images/resistor.jpeg)

### 2d: Reset Button

Solder the TL3342 reset button. Align with the pads and solder.

![Reset Button](images/reset_button.jpeg)

### 2e: Hotswap Sockets (54×)

Solder the Kailh Choc hotswap sockets onto the back side. Make sure they're seated flat against the PCB. These have a specific orientation — the socket opening should align with the switch pin holes.

![Hot Swap Socket Top](images/hot_swap_top.jpeg)
![Hot Swap Socket Bottom](images/hot_swap_bottom.jpeg)

## Step 3: Clean the PCB

Scrub all flux residue with a toothbrush and 91% isopropyl alcohol. Let air dry.

![PCB Back](images/board_back_soldered.jpeg)

## Step 4: Solder Headers (Front Side)

Flip the board to the **front side**.

1. Solder two 7-pin female headers to the U3 (XIAO MCU) footprint
2. The XIAO BLE (pre-soldered with male headers) will plug into these later

![XIAO MCU](images/XIAO_BLE.jpeg)

## Step 5: Test Before Proceeding

Before installing switches, plug in the XIAO and flash the test firmware to verify the matrix works. See the firmware repo for the test scanner script. Press each key position with tweezers across the hotswap socket pins to simulate key presses.

## Step 6: Install Switches

Insert all 54 Choc V1 switches into the hotswap sockets from the **front side**. They should click in firmly. Make sure the pins are straight before pressing — bent pins won't seat into the sockets.

![Front Assembled](images/board_assembled_top.jpeg)

## Step 7: Install Keycaps

Press the MBK keycaps onto each switch stem. Place the two homing keycaps on the home row index finger positions (F and J equivalent).

![Board w/ Keys](images/board_top_w_keys.jpeg)

## Step 8: Prepare the Case

### Heat-Set Inserts

1. Heat your soldering iron to ~200-220°C
2. Place an M2 brass insert on each standoff hole in the case
3. Press the hot iron tip onto the insert — it will slowly melt into the plastic
4. Keep it straight and stop when it's flush with the surface
5. Repeat for all 8 mounting holes

![Heat Insert Side](images/heat_insert_1.jpeg)
![Heat Insert Top](images/heat_insert_2.jpeg)
![Case w/ Inserts](images/case_w_inserts.jpeg)

### Install Joysticks

If using the v2 PCB with joystick support, solder the COM-09032 joysticks to the front side of the PCB before mounting in the case.

![Joystick](images/joystick.jpeg)

## Step 9: Mount PCB in Case

1. Place the PCB into the case, aligning the mounting holes with the inserts
2. Secure with M2 × 5mm screws — don't overtighten

![Completed Build](images/completed_build.jpeg)

## Step 10: Plug In MCU and Flash

ZMK firmware lives in a separate repo: **[custom-keyboard ZMK firmware](https://github.com/aidancahill/custom-keyboard-zmk-firmware)**

1. Plug the XIAO BLE into the female headers
2. Connect USB-C cable to computer
3. Double-tap the reset button to enter bootloader mode
4. Drag the `zmk.uf2` firmware file onto the USB drive
5. The board will reboot with the keyboard firmware

## Step 11: Test All Keys

Open a text editor and press every key to verify they all work. If a key doesn't register:

- Check the diode solder joint at that position
- Check the hotswap socket solder joints
- Make sure the switch is fully seated

## Troubleshooting

### All keys in a column don't work

Check the solder joint on the corresponding 74HC595 output pin. Reflow with flux.

### All rows read as pressed

The pull-up resistors R3-R7 need to be removed. The firmware uses internal pull-downs instead.

### No keys register at all

- Verify the XIAO is getting power (LED on)
- Check SCK, MOSI, and RCLK solder joints on both the XIAO and shift registers
- Verify the shift registers have +3.3V and GND

### Single dead key

Reflow the diode at that key position. Add flux, reheat both pads for 2-3 seconds each.

### Solder won't stick to pad

- Add flux to the pad
- Clean the pad with isopropyl alcohol or a pencil eraser
- Make sure the iron tip is clean and tinned
- Heat the pad first, then apply solder to the pad (not the iron)

### Joystick not responding

- Verify the joystick analog signals are routed to XIAO D0-D3 (ADC pins)
- Check the 74HC165 is installed (not another 74HC595)
- Verify D6 connects to the 74HC165 PL pin
- Verify D9 connects to the 74HC165 Q7 pin
