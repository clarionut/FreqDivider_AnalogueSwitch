# Frequency Divider / Analogue Switch

This repository contains details of synthesiser module providing a 4-stage frequency divider linked to three 2-in 2-out analogue changeover switches.

![DividerSwitch](https://github.com/user-attachments/assets/e2518ae7-653d-48fa-aa92-c53b749d4124)

The frequency divider comprises two CD4027B Dual J-K flip-flops with each stage wired as a T-type flip-flop. Each stage toggles its state on the rising edge of its clock signal, converting the incoming pulse train into a square wave of half the incoming frequency. By default the output of each stage is normalled to the input of the next, so a single clock input can give four outputs of 1/2, 1/4, 1/8 and 1/16 the incoming frequency. Multiple input clocks can be processed using the input jacks on the later divider stages, e.g to divide one clock by 2 and a second clock by 2, 4 & 8. The outputs of each stage are 0-9V square waves.

The module also includes three 'two-pole changeover' analogue switches based on two CD4053B 3-channel mux/demux chips. The CD4053Bs are powered by +12 & -6V and consequently can handle Eurorack standard voltages of ±5V or 0-10V (with protection against out-of-range voltages) and will work with both CVs and audio-rate signals. Each of the virtual changeover switches can be connected to any of the four frequency divider stages and multiple switches can be connected to the same divider output. I used red/white bicolor LEDs to indicate the state of each changeover switch; when the control input to a switch is high its LED is white and the two inputs connect straight to the output and when low the LED is red and the outputs cross over.

The original inspiration for this module was to provide a means of using my [ADCequencer](https://github.com/clarionut/ADCequencer) 8-step 2-channel sequencer as a 16-step 1-channel sequencer. Passing the two analogue outputs of the sequencer through a changeover switch clocked at 1/16 the speed of the sequencer swaps between the two outputs every 8 steps creating a 16 step sequence. Interesting variations can also be introduced by changing the relative phasing of the sequencer and the analogue switch. The frequency divider has a manual clock input to allow such changes on the fly.

##Hardware Notes

My synth is Eurorack format and to save space I used small 2-pole 4-way slide switches as the selectors connecting the analogue switches to the divider output stages. Unfortunately these are make-before-break which can cause glitching when switching on the fly. If you build in a larger format like Kosmo it would be better to use small break-before-make rotary switches for these selectors. If you're forced to use make-before-break switches it's best to set them up when all the divider outputs are in the same (high or low) state. Note that it's also extremely fiddly wiring the connections between the switch/LED sub-boards if you use the small slide switches!

##KiCad files

The schematic and PCB files are provided in KiCad 7 format and as PDFs. Note that the front copper ground plane is excluded from the board PDF for clarity but is present in the KiCad files. The schematic uses some custom symbols and the PCB some custom footprints, so you will need to download my [custom KiCad libraries](https://github.com/clarionut/kiCad_libraries) and tell KiCad where to find them. The PCB file is intended to be processed by the KiCad 'Round Tracks' plugin but will work perfectly well without. I've included the Gerber files but these will only be useful if you mount the PCB on brackets behind and perpendicular to the front panel.
