# MusicRhythmGame
  Final Project for the course *Digital Design Laboratory* (ECE 4273) at The University Of Oklahoma where I teamed up as an engineer with Trent Famuliner to design and develop a music rhythm game from scratch. The components we used included LPCXpresso1769, 96BB2-006 4x4 keypad, NOKIA 5110 LCD display, an audio amplifier a speaker, and resistors and capacitors. The software component of the game is stored on the LCPXpresso, and is written in C.  <br>
  
  If you would like to play yourself, follow these steps: <br>
  - Build provided hardware schematic 
  - Download code and load to LCPXpresso 
  - Have fun!


### Directions for use

To play, press the star symbol (‘*’) on the keypad. This will start the game. Next, the graphical LCD display will show a note to play. You can identify this note by observing a black dot traverse to the note identifier starting from the left and traveling right. The black dot will hover over a note identifier until it is pressed: ‘C’, ‘D’, ‘E’, or ‘G’. After you press the correct note, A new dot will appear, and then decide which note to press next. This process will keep going until the whole sequence of notes has been played. Upon completion your score will be shown. The highest possible score is 2600. You will be scored on two criteria: Note accuracy and Time accuracy. Try to not play the note early or late for the highest score possible. Also try to play the right note.  

Playing the game can be outlined into 4 steps:
  1. Press ‘*’ to START. <br>
  2. Press keys ‘**A**’, ‘**B**’, ‘**C**’, ‘**D**’ to select notes ‘**C**’, ‘**D**’, ‘**E**’, ‘**G**’, respectively until the sequence of notes has been played.  <br>
  3. Observe your score and compete with friends! <br>
  4. Should you want to stop the game part way through, the ‘*’ button can also reset the game. <br>

---
### Hardware Schematic
![HardwareSchematic](https://user-images.githubusercontent.com/70310177/213533053-aeab4210-66a9-46cb-8e48-bf2d5e853963.PNG)
### Hardware Design <br>
Consists of an LCD, a keypad, and an audio amp and Speaker. The only component values
needed are a 10μF capacitor across the power rails to keep the amplifier
power stable, a 270Ω resistor to limit current to the Red LED, and a 330Ω
resistor in series with the LCD LEDs to limit the current to them. The
capacitor value was chosen just to be large enough to soak up any
voltage fluctuations on the power rail, the 270Ω resistor was chosen to
limit the Red LED current to 5 mA, and the LCD resistor value was stated
in the documentation for the LCD. The Audio amplifier is just configured in
a voltage follower mode as the speaker is plenty loud enough at the 3.3V
output of the LPC1769 so there is no need for amplification.

### Software Design <br>

The Software will use GPIO functions to read the key matrix from the
keypad to determine the state of the A, B, C, D, and * keys. The ABCD
keys will be used to play the notes, and the * to start and stop the game.
Once the game is started, a sequence of notes will be displayed via the
LCD which will be communicated with using SPI. The user will then have
to press the note keys to match the sequence and then the game will tally
up a score based on how far off from the right time they were which will be
calculated using timers. This will continue until the song is done and then
the score will be tallied and displayed to the LCD. The actual sound
waveforms will be implemented using the PWM system to generate the
square waves at defined frequencies for the notes that the user will play.


## Game Demo
![demo](https://user-images.githubusercontent.com/70310177/213533131-04f041d9-33c7-4a9f-8bc4-6c8c5fa0b44d.jpg)




