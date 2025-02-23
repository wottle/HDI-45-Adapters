# HDI-45-Adapters

## The History
If you want to learn more about why this adapter is needed and how it came to be, take a look at the [history](HISTORY.md).

## The Adapters

There are two version of this adapter, depending on your needs.  If your PowerMac x100 machine has a DOS Compatible card, or you prefer to hook it up to a period correct CRT, those require a DA-15 (also referred to commonly as a DB-15 connector) connection.  You will want to use the DA-15 version, located in the DA-15 

This adapter consists of a PCB, some long 2.0mm pitch headers, either a straight female HD-15 connector or a straight female DA-15 connector, and on the VGA version, a diode.   Included is a 3d printable case for each, which will be important for both alignment of the pins, and stability to the adapter.  Theoretically, you could use this as a bare PCB, but you'd likely need to secure it to the back of the machine with double sided tape.  I highly recommend using the 3d printed case.  You can print these in cheap resin at JLC3DP for a couple of bucks.  It's worth it.

## Components Needed

### The PCB 

First, youll need to order the PCB.  I use JLCPCB because they are cheap and I've had no problems with quality.  To do that, download the gerber for the version you want from this repo.  Download the zip file from either the [DA-15/gerber](DA-15/gerber) or 
[GD-15/gerber](HD-15/gerber) directory (don't decompress, leave it as a zip file).  Then, go to [JLCPCB](https://jlcpcb.com), click the "Add gerber file" button, and upload the zip file.  This will load the 2 layer PCB. You can leave all the defaults as-is (feel free to change the PCB color). Place the order and you should get your 5 PCBs quickly and for relatively cheap. 

### The Header Pins

I recommend using 19mm long 2.0mm pitch header pins.  The horizontal spacing of the HDI-45 pins is 2.0mm, so these headers will allow you to insert some of the pins in bundles.  However, because the vertical spacing is smaller, you cannot leave the plastic spacers in place for all 5 rows.  I've found it best to use strips of headers for rose 1,3,and 5 with 4 pins, 3 pins, and 4 pins respectively. For rows 2 and 4, they only need 2 pins inserted in each row, so I put those in individually.  Here is the source I used for my headers: [eBay](https://www.ebay.com/itm/171495154253)

### Diodes (for HD-15 version only)

There is a single diode needed for the sense lines to set the HD-15 adapter to 21" MultiSync mode.  This will allow you to use 640x480 @67Hz or 832x624 @ 75Hz. I just used some 1N4007 diodes [from Amazon](https://a.co/d/5SRJu1n).

### Connectors

You'll need different connectors for the two different adapters.  For the HD-15 version, I used [this part](https://www.mouser.com/ProductDetail/Amphenol-Commercial-Products/L77HDEH15SOL2RM8?qs=mq7kV%2Fq8lk7g9czTkxkhWQ%3D%3D) from Mouser.  For the DA-15 version, I used [this part](https://www.mouser.com/ProductDetail/Amphenol-Commercial-Products/LD15S24A4GX00LF?qs=tZOhSuJQg1m5NC9di5k5CQ%3D%3D)

I suspect any straight female HD-15 or DA-15 connectors would do. 

### Case

You can either 3d print your own case, or use a service like JLC3DB.  Grab the .obj files from the "case" directory in the folder for the version you are making.  The 3d files are optimized for printing on a flat surface with no (or minimal support).  The only part my slicer added supports were for the dome cutouts in the "bottom" case where the ground pegs are supposed to sit. Your printer may not need that.  Go ahead and start the print so it's ready to go when you're done with the PCB assembly.  I really don't recomment using these without the case. 

### Screws

You'll need one or two M3 x 8 screws to secure the two halves of the case together. 

## Assembly

Assemly is slightly challenging due to trying to solder the long pins. I've found it best to use a HDI-45 port to set the pins, then load them into the PCB and solder them while in the HDI-45 port. This was easy for me because during my development of this, I desoldered a HDI-45 connector off one of my non-functional PM6100 logic boards.  I used this bare port as a jig to solder my PCBs.  You should be able to do the same with the port while it is still on the logic board, it just will be awkward.  

I recommend tackling the soldering in this order (I'll provide the detail steps below.:

1. Solder in the header pins
2. (Only on HD-15 version) solder in the diode
3. Solder in the HD-15 or DA-15 connector.
4. Assemble in 3d printed case.

PCB Detailed steps:

1. There are two approaches for soldering the pins.  If you're trying to knock out many of these, I've found there is a way to do it faster. However, if you struggle with the advanced method, try the simple method and do one row at a time. Fortunately, the holes in the PCB are pretty tight, so they generally keep them plumb to the PCB, but keeping them in the HDI-454 port makes sure they stay spaced properly. Also note that the back of the PCB now has circles around the pins you need to load headers into.  (NOTE: Make sure you load these into the back side of the board (the side that has no labels printed on it except circles around 15 of the pins)!!!
   * (ADVANCED) First, we will try to solder four of the header pin rows (out of 5).  I cut the headers into two 4-pin sections, and one 3-pin section. Then I pull out 4 individual pins - two for row 2, and two for row 4.  When I load the HDI-45 port with the pins, I start with the 4 individual pins in rows 2 and 4.  The I add the header strips, starting with the 3-pin strip in row 3, and then I put the 4 pin strip in row 1 or row 5 (doesn't really matter which one).  Then we need to get the pins into the PCB.  I've found that this is easiest if you start with the 4-pin strip, with the pcb at a slight angle, then wiggle the board and set the next row (2 solo pins), then the next (3 pin strip) and finally the fourth row of 2 individual pins.  With this technique, I can load up all 4 rows, solder them all at once, and save time. Solder the 4 rows, being careful not to bridge any pins (they are supprt tight spacing, so it's easy to do). Finally, pull the PCB wth the 4 rows out of the HDI-45 connector, add a 4 pin header strip for the 5th and final row, insert it into the connector, and solder those 4 pins.  
   * (SIMPLE) If you struggle getting the 4 rows of pins all loaded into the PCB at one time, the simpler, but slower method is to do one row at a time.  Load a 4-pin strip into the first row of the PCB, in holes surrounded by a circle marking on the PCB. Then insert these into the HDI-45 port.  Solder the 4 pins.  Be careful not to get solder into the surrounding holes, they are small and difficult to clear if you do.  Pull the PCB, then insert the two individual pins into the second row.  Because the individual pins can't fit with the plastic spacers, theres nothing keeping these pins from sliding all the way through.  Use your finger to keep them from sliding too far.  Take the PCB and its two rows, and insert it into the HDI-45 port, then solder the two pins.  Do this for each row remaining.
2. (OPTIONAL - only on HD-15 version) Insert the diode into the through holes labeled D1 on the PCB, taking care to get the direction correct.  Solder the pins, clip the excess. Or, if you want this use the 14" MultiSync Mode, you can simply connect a wire in place of this diode.  
3. Insert the appropriate connector, and solder in place.  Also, I have the shielding connected to the ground pins, so I'd recomment adding solder to the shileding connectors for that reason and to add stability.
4. For assembling the case, the tolerances are very tight.  The method I used was to take the bottom case part, lay the PCB down on it with the long header pins in the shroud.  I visually line up where the pins should be to get even spacing on the top and bottom.  Then I insert the shroud and PCB into the HDI-45 port to test the alignment.  You may need to shift the PCB a couple times to get this right.  Then, once the shroud and PCB are correctly inserted into the port, I add on the top case, then secure with one or two M3 x 8 screws.  Once tightened, pull the adapter out and test re-inserting to make sure there are no snags on insertion.  You may need to loosen the screws and adjust to get it right, but when done properly, there should be no resistance or snags when inserting.  



