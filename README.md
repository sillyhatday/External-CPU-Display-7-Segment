# External-CPU-Display-7-Segment
An External CPU indicator display - Set up for a 2 digit display - Expandable to VFD tube display

This took me far longer than I want to admit. The electronic side took no time to sort out, the lack of coding knowledge took me around the houses. Trying to get other peoples code adapted to work for my application. Lets talk through it, with various options to get an end result.

I wanted to use some retro VFD tubes to display computers CPU usage in percentage. This was after many other ideas. My first idea to get this to work was with display multiplexing. The standard arduino doesn't have enough I/O for driving 7 display segments x2 plus one for each digit to be controlled on or off. Multiplexing is nothing new, there is enough out there to explain how it works if you do not know. 

Option 1.

This is not the best soultion, you're best skipping to the next one.

This option worked in a fashion. While the Arduino is busy multiplexing the displays, it doesn't have time to run any other code. Well not a lot of code anyhow. This is ok and it does work properly. I found that it refreshes the display too fast making it tough to read, not only that but with the PC software, the CPU readings are up and down all the time. As such the display can totally miss spikes in CPU performance. I realised that readings in monitoring software is averaged out over time. The problems start when writing some code to average a bunch of readings from the serial port. While the Arduino is busy doing that, it's not longer multiplexing and the display freezes on what ever it was just doing. Leaving just one digit on. Once it has done its calculations it gets back to showing the display properly. This gives a much more stable reading that is much more useful. Juist with a horrid flickering display.

I do wonder if someone more experienced can write some more efficient code to allow this to work properly, which is why I included this in here. Possibly editing the PC software to do the work before being sent to the arduino. (I don't know how to do that)

Option 2.

After that I realised that I'd be able to use shift registers to solve the issue. If the hardware you have can't do the job, add more hardware. Simply the shift registers do all the work in the displays, the arduino spends its time reading the serial port and calculating averages. Another bonus is that you can have longer periods of time to take an average. Making a really nice stable display. Downside is that you need more hardware to make it all work.

Included is the schematic for making your own PCB. I have yet to make my own PCB and haven't sorted out a constant current source for driving the VFD heaters. For testing I've been connecting the heaters in series with a 100ohm resistor on 5v. You can use a 120ohm resistor too so you can underdrive the tubes. This will help to make them last longer as they will loose their brightness over time.

The Arduino sketch has inverted hex values to be able to drive either, a common anode or common cathode LED seven segment display. For driving the VFD tubes you need to use the common cathode hex values.
