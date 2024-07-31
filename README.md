
# Todo

Convert panel holes to NPTH to avoid maximum plated hole size

# Inspiration

https://llllllll.co/t/exits-a-4hp-mixer-line-headphone-output-module/52221
https://github.com/forestcaver/Analog-Voice/tree/master/AJH_Headphone_Amp - not kicad
https://www.ericasynths.lv/shop/diy-kits-1/edu-diy-output/
https://busycircuits.com/alm019/
https://nwavguy.blogspot.com/2011/07/o2-headphone-amp.html
https://github.com/russellmcc/eurorack_headphones - kicad
https://github.com/ramphands/Exits - kicad, SMT, op amp available on ali but not common
https://github.com/wntrblm/Speak_to_Me - kicad, headphone amp with inbuilt speaker
https://github.com/tkilla64/eurorack/tree/main/output

# Features

- left and right mono jack 3.5mm inputs - mono sums over when only left plugged
- stereo volume pot
- L and R mono jack 3.5mm outputs (line level)
- stereo 3.5mm jack output

# Circuit explanation

- Audio comes in on 3.5mm mono jacks (L and R)
- The switched input of the R jack takes audio from the L jack, so that when R is not plugged in we get a copy of the L signal in the R output
- Audio level is dropped to line level for L and R channels by two LME49720 audio op amps
- Audio goes out to L and R 3.5mm line level jacks
- A stereo potentiometer attentuates the line level signal for both channels equally
- Two NJM4556 chips drive the headphones
- Audio op amps are needed (LME49720) and an amplifier chip capable of driving (low impedence) headphones

# How It Will Be Used in Our Rack

- two of these will be installed in our rack
- the buff mult can duplicate the final output signal
- we can send this independently to two separate headphone amps

# Notes

- The large amount of 100n decoupling caps is because we need 1 pair per chip, which on the PCB should be placed as close to chip power pins as possible
- I removed the ADP0204 dip switch in the original circuit
    - when switched on, engages an extra 100K resistor between input and output of the opamp on each channel
    - I guess to further attentuate the input signal perhaps to allow for line-level input
    - I will just experiment with different resistor values here instead
- is there any THT alternative to NJM4556AV-TE1? Yes NJM4556AD DIP with same pinout
- symbol pins 7 and 8 on dual pot are just mount points

# Switched plugs explained simply

- Switched plugs have a switch contact/pin
- When there is no plug inserted into the jack the tip contact is touching the switch contact
- This creates a closed circuit between the input signal and the output path through the switch contact
- When a plug is inserted into the jack the signal now flows through the plug instead of the switch contact
- In the case of my headphone amp, I want L input to connect (normal over) to the R when no plug is inserted in the R
- This means that the tip output of the L jack is connected to the switch contact of the R jack