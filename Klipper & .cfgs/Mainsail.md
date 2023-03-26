# Configuring Mainsail
This part is strictly how I did mine and you are more than welcome to modify set up to your liking.

# Printer.cfg
* Select `MACHINE` in menu on the left side
* Find your printer.cfg file and select it
* Below will be what mine looks like, but yours will vary depending on how you set your printer up.
> 
```
# This file contains pin mappings for the Creality Ender 5 Plus.
# Ender 5 Plus stock uses a Creality v2.2 board, similar to CR-20 Pro.
# To use this config, the firmware should be compiled for the AVR
# atmega2560.

# See docs/Config_Reference.md for a description of parameters.



#[include timelapse.cfg] ## uncomment this if you choose to install timelapse feature
#[include macros.cfg] # I use a separate folder for my macros
[include mainsail.cfg]
[virtual_sdcard]
path: /home/ryan/Ender5Plus_data/gcodes ###Change this to your path
on_error_gcode: CANCEL_PRINT

[exclude_object]

######################################################################
# BED LEVELING
######################################################################

[bltouch]
sensor_pin: ^PC13
control_pin: PE5
x_offset:-31
y_offset:-41
#z_offset: 3.380
pin_up_reports_not_triggered: True
pin_up_touch_mode_reports_triggered: False
stow_on_each_sample: False
probe_with_touch_mode: True
speed:10
samples:2

[safe_z_home]
home_xy_position: 175, 175 # Change coordinates to the center of your print bed
speed: 100
z_hop: 10 # Move up 10mm
z_hop_speed: 20

[bed_mesh]
speed: 200
horizontal_move_z: 5
mesh_min: -4, -6
mesh_max: 320, 301
probe_count: 5, 5
mesh_pps: 2,2
fade_start: 1.0
fade_end: 10.0
fade_target: 0.0

[screws_tilt_adjust]
screw1: 58, 74
screw1_name: Front Left screw
screw2: 352, 338
screw2_name: Back Right
screw3: 352,74
screw3_name: Front Right
screw4: 58,338
screw4_name: Back Left
horizontal_move_z: 6
speed: 200
screw_thread: CW-M4

[z_tilt]  ### Will only need this if you connected both z axis motors to their own driver
z_positions: 22, 204
           351, 204
# A list of X,Y coordinates (one per line; subsequent lines
# indented) describing the location of each bed "pivot point". The
# "pivot point" is the point where the bed attaches to the given Z
# stepper. It is described using nozzle coordinates (the XY position
# of the nozzle if it could move directly above the point). The
# first entry corresponds to stepper_z, the second to stepper_z1,
# the third to stepper_z2, etc. This parameter must be provided.
points: 22, 204
      351, 204
          
# A list of X,Y coordinates (one per line; subsequent lines | back |
# indented) that should be probed during a Z_TILT_ADJUST command. | |
# Specify coordinates of the nozzle and be sure the probe is above L z1 z R
# the bed at the given nozzle coordinates. This parameter must be | |
# provided. | front |
speed: 200
horizontal_move_z: 7
retries: 20
# Number of times to retry if the probed points aren't within
# tolerance.
retry_tolerance:0.0025
# If retries are enabled then retry if largest and smallest probed
# points differ more than retry_tolerance. Note the smallest unit of
# change here would be a single step. However if you are probing
# more points than steppers then you will likely have a fixed
# minimum value for the range of probed points which you can learn
# by observing command output.

# This file contains common pin mappings for the BigTreeTech SKR 3.
# To use this config, the firmware should be compiled for the
# STM32H743 with a "128KiB bootloader".

# See docs/Config_Reference.md for a description of parameters.


######################################################################
# X Stepper
######################################################################


[stepper_x]
step_pin: PD4
dir_pin: !PD3
enable_pin: !PD6
microsteps: 16
rotation_distance: 40
endstop_pin: ^PC1
position_endstop: 352
position_max: 352
#position_min:-20  #used for getting my min
homing_speed: 150

[tmc2209 stepper_x]
uart_pin: PD5
run_current: 0.580
diag_pin:
interpolate: False #Comment out if you use stealth shop
#stealthchop_threshold: 999999 #will make your printer quieter, but at a cost to accuracy; this applies to all below

######################################################################
# Y Stepper
######################################################################

[stepper_y]
step_pin: PA15
dir_pin: !PA8
enable_pin: !PD1
microsteps: 16
rotation_distance: 40
endstop_pin: ^PC3
position_endstop: 342
position_max: 342
#position_min:-10
homing_speed: 150

[tmc2209 stepper_y]
uart_pin: PD0
run_current: 0.580
diag_pin:
interpolate: False
#stealthchop_threshold: 999999

######################################################################
# Z & Z1 Stepper
######################################################################

[stepper_z]
step_pin: PE2
dir_pin: !PE3
enable_pin: !PE0
microsteps: 16
rotation_distance: 4
endstop_pin: probe:z_virtual_endstop
#position_endstop: 0.5
position_max: 400
position_min: -6
homing_speed: 10.0

[tmc2209 stepper_z]
uart_pin: PE1
run_current: 0.580
diag_pin:
interpolate: False
#stealthchop_threshold: 999999

[stepper_z1]
step_pin: PD11
dir_pin: !PD10
enable_pin: !PD13
microsteps: 16
rotation_distance: 4
#endstop_pin: PC13
#position_endstop: 0.5
#position_max: 200

[tmc2209 stepper_z1]
uart_pin: PD12
run_current: 0.580
diag_pin:
interpolate: False
#stealthchop_threshold: 999999

######################################################################
# Extruder
######################################################################

[extruder]
step_pin: PD15
dir_pin: PD14
enable_pin: !PC7
microsteps: 16
gear_ratio: 42:12
rotation_distance: 26.4462726999097
nozzle_diameter: 0.400
filament_diameter: 1.750
heater_pin: PB3
sensor_type: EPCOS 100K B57560G104F
sensor_pin: PA2
#control: pid
#pid_Kp: 22.2
#pid_Ki: 1.08
#pid_Kd: 114
min_temp: 0
max_temp: 300
max_extrude_only_distance: 450
min_extrude_temp: 180
#pressure_advance: .1127

[tmc2209 extruder]
uart_pin: PC6
run_current: 0.650
diag_pin:
#stealthchop_threshold: 999999


######################################################################
# Heated Bed
######################################################################

[heater_bed]
heater_pin: PD7
sensor_type: EPCOS 100K B57560G104F
sensor_pin: PA1
#control: watermark
min_temp: 0
max_temp: 130

[fan]
pin: PB7

[heater_fan hotend_fan]
pin: PB6
heater: extruder
heater_temp:50.0

[heater_fan mcu_fan]
pin: PB5
heater_temp: 45.0

[mcu]
serial: /dev/serial/by-id/usb-Klipper_stm32h743xx_400029000B51303138393138-if00

[printer]
kinematics: cartesian
max_velocity: 300
max_accel: 3000
max_z_velocity: 5
max_z_accel: 100



########################################
# EXP1 / EXP2 (display) pins
########################################

[board_pins]
aliases:
    # EXP1 header
    EXP1_1=PC5, EXP1_3=PB1, EXP1_5=PE9,  EXP1_7=PE11, EXP1_9=<GND>,
    EXP1_2=PB0, EXP1_4=PE8, EXP1_6=PE10, EXP1_8=PE12, EXP1_10=<5V>,
    # EXP2 header
    EXP2_1=PA6, EXP2_3=PE7, EXP2_5=PB2, EXP2_7=PC4,   EXP2_9=<GND>,
    EXP2_2=PA5, EXP2_4=PA4, EXP2_6=PA7, EXP2_8=<RST>, EXP2_10=<NC>


[temperature_sensor raspberry_pi]
sensor_type: temperature_host
min_temp: 10
max_temp: 100

[temperature_sensor mcu_temp]
sensor_type: temperature_mcu
min_temp: 0
max_temp: 100

[filament_switch_sensor filament_sensor]
pause_on_runout: True
#runout_gcode: PAUSE
#insert_gcode: RESUME
switch_pin: PC2
```

## Cusomization

From here everything else would be your prefrence. I'll soon add a guide on how I tune my printer. I'll add links for anything I think would be useful in the [Extra](../Extra/Extra.md) section.

<sub>[Extra](../Extra/Extra.md)

<sub>[Main](../readme.md)

<sub> [Top](#configuring-mainsail)