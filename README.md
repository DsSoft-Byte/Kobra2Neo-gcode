# Kobra2Neo-gcode
custom gcodes for my Anycubic Kobra 2 Neo

# START-gcode

G90 ; use absolute coordinates

M83 ; extruder relative mode

M104 S[first_layer_temperature] ; set extruder temp

M140 S[first_layer_bed_temperature] ; set bed temp

M190 S[first_layer_bed_temperature] ; wait for bed temp

M109 S[first_layer_temperature] ; wait for extruder temp

G28 ; move X/Y/Z to min endstops

G1 Z0.28 ; lift nozzle a bit

G92 E0 ; zero the extruded length

G1 Y3 F1800 ; zero the extruded length on Y-axis

G1 X60 E6 F500 ; Extrude 6mm of filament in a 5cm line

G92 E0 ; zero the extruded length again

G1 E-2 F500 ; Retract a little

G1 X70 F4000 ; Quickly wipe away from the filament line

G1 X65 Y5 F3000 ; Move to prime "blob" position

G92 E0 ; zero the extruded length

G1 E4 F500 ; Extrude 4mm of filament for the "blob"

G92 E0 ; zero the extruded length again

M117 ; Display message

# END-gcode

M104 S0 ; Turn off extruder

M140 S0 ; Turn off heatbed

M107 ; Turn off fan

G91 ; Relative positioning

G1 E-5 F3000 ; Retract filament a little bit

G1 Z+0.3 F3000 ; Lift print head

G28 X0 ; Home X-axis

M84 ; Disable stepper motors

# Hope this helps with the nozzle soiling itself at startup!
