# External-CPU-Display-7-Segment
An External CPU indicator display - Set up for a 2 digit display - Expandable to VFD tube display

This took me far longer than I want to admit. The electronic side took no time to sort out, the lack of coding knowledge took me around the houses. Trying to get other peoples code adapted to work for my application. Lets talk through it, with various options to get an end result.

I wanted to use some retro VFD tubes to display computers CPU usage in percentage. This was after many other ideas. My first idea to get this to work was with display multiplexing. The standard arduino doesn't have enough I/O for driving 7 display segments x2 plus one for each digit to be controlled on or off. Multiplexing is nothing new and there is enough out there to explain how it works if you do not know. 

