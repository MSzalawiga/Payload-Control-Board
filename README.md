# Payload Control Board

During the 2023-2024 design cycle I was tasked with updating the Control Board for the Scientific Payload for Queen's Space Engineering Team.

I worked on 2 revisions of the board being Rev2 and Rev3 with Rev3 being the board used at competition.

These boards were created using KiCad 7.0 and were both 4 layer Signal/Ground/Power/Signal stackups.

## Revision 2
Revision 2 was done in a hurry as we needed a working control board for our systems acceptance review in late Feburary 2024, meaning I needed to order the board early December 2023 before exams started. The hurry comes from the fact that I took over this project from scratch in late November 2023.

### Scope and Functional Requirements
The scope and requirements of this control board came from the requirements from the Science and Mechanical team along with the 2024 University Rover Challenge (URC) Science mission rules. The scope and requirements were as follows:
- Control 2 Stepper Motors to raise and lower the payload
- Control up to 6 Servos for collection scoops and an auger
- Be able to toggle and change the brightness of 9 incandescent lights for the on-board spectrometer.
- Interface with the Rover through serial communication
- Interface with Sensors to get scientific measurements
### Reflection
I am content the turnout of this board, although the board was not space efficent it was able to serve its purpose in being able to provide funcionality for the systems acceptance review. 
Also since I was only able to use THT components (annoying I know) I couldn't find a buck converter with an external control pin, thankfully a weird trick I found online (can't find the articel :(  using a dac to influence the reading on the feedback pin worked wonderfully.

## Revision 3
Now having more time I created Revision 3, having mostly the same requirements with some exceptions being no more ethernet module, switch 3 lights for UV lights and the sensors switching it was pretty much the same. Also I could use SMT components (thank god). 

I am going to jump right into the reflection since the requirements were basically the same as revision 2.

### Reflection
Awesome, I am very happy with the turnout of this board. I was able to fit everything on a 100mm x 100mm board with a Teensy 4.1 microcontroller with a footprint of ~ 60mm x 25 mm. Also this was my first time soldering SMT components on a PCB so I chose 0603 (metric) to be my smallest passive size and I think it turned out well.

A new revision will be needed next year to adapt to the changing ruleset of the science mission. Next year I have taken on an executive position so I will be in more of a helper / design verification role for this specific project.

Some improvements I can think of are:
- No teensy 4.1, switch to STM32 they are just better and putting the MCU ourselves results in a smaller footprint and a more professional look
- I accidentally swapped SDA and SCL on the 3V3 I2C line (whoops) but with design verification next year this shouldn't happen
- For controlling light brightness use PWM and Transistors rather than a buck converter, the lights don't draw too much current. or use a newer buck ic with external pwm signal
- get new stepper drivers, current ones ran very hot and weren't very configurable
