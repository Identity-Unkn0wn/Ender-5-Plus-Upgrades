# Wiring Sprite Extruder
Firstly, this isn't the only way to do it, just the way I chose to do it. Why? well I didn't want to bend any of the vent ports or drill any holes. 

## Step 1: 
* Crimp Cables to match stock cables
* **You will not need to touch original X, Y, Z-Axis, filimant run out, heated bed themistor, or heated bed power cable.**
* I Just took the cables out one by one, crimped them and placed them in the new one as I got done so I didn't have 5 wires loose and not know what order to put them in.

> ![Wiring](../Files/Wire%20Connections.jpg)
> * Video on how to crimp connections [here](https://www.youtube.com/watch?v=GZOh1NzqzzU).
> * [This is the kit I used.](https://amzn.to/42i6e2O)

* One thing I would like to point out is to verify the ohms on the fans, mine was wired weired and the parts cooling fan caused my [BTT SKR E3 Mini V3](https://amzn.to/3ZG8Rtn) board I was testing with to burn out. you will know which is posititve when you connect the red to the positive and the black to the negative it will give you a reading, if it is reversed then it will read "0". Keep in mind the numbers won't tell you anything meaningful, just an easy way to tell polarity.
> ![Alt text](../Files/Fluke%20multimeter%20marked.jpg)
    > * Green: Mode to test on
    > * Red: Positive Lead
    > * Black: "Negative" lead
    > * [The multimeter I used.](https://amzn.to/3FrEbUu)

## Step 2: Connect Cables
Really not much to say here other than now that you have crimped all the cables with the new connections they should all go into place. 
> **Note:** Remember to note which fan you plug into with fan plug. They are labled Fan and k-fan on the extruder side. I have k-fan connected to the yellow and blue(parts) fan pair and this was the correct.

<sub>[Top](#wiring-sprite-extruder)