# HDI-45 Adapters

> [!CAUTION]
> This repo is a work in progress. I have ordered using the PCBs and the HD-15 version of the 3d printed case from JLCPCB, but I have added a new version of the DA-15 adpater 3D case that I have not yet received to verify it fits perfectly.  I have printed both on my local Ender 3D printer and they work very well.  But produce at your own risk and send me feedback if you have to adjust the 3D printer settings on your setup. 

## History
If you want to learn more about why this adapter is needed and how it came to be, take a look at the [history](HISTORY.md). But at a high level, this adapter allows you to replace this: 

<img src="/images/hdi-45_adapter.webp" height="240" />

And, in the case of the HDI-45 to HD-15 adapter, also replaces this additional adapter.

<img src="/images/da-15_to_vga_adapter.jpg" height="240" />

## The Adapters
There are two versions of this adapter, depending on your needs. If your PowerMac x100 machine has a DOS Compatible card or you prefer to use a period-correct CRT, you will need a DA-15 connection (also commonly referred to as a DB-15 connector). In that case, use the DA-15 version, located in the DA-15 directory.

<p float="left">
<img src="/images/hdi-45_adapters-top.jpeg" height="240" />
<img src="/images/hdi-45_adapters-bottom.jpeg" height="240" />
<img src="/images/hdi-45_adapters-standing.jpeg" height="313" />
<img src="/images/hdi-45_adapters-installed_in_6100.jpeg" height="313" />
</p>

This adapter consists of a PCB, long 2.0mm pitch headers, either a straight female HD-15 or DA-15 connector, and a diode (for the VGA version). A 3D-printable case is included, which is crucial for pin alignment and adapter stability. While you could use this as a bare PCB, you would likely need to secure it to the back of the machine with double-sided tape. I highly recommend using the 3D-printed case, which can be inexpensively printed in resin at JLC3DP.

## Components Needed

### PCB
First, you'll need to order the PCB. I use JLCPCB because they are affordable and reliable. Download the Gerber file for the version you want from this repository. Get the ZIP file from either the [DA-15/gerber](DA-15/gerber) or [HD-15/gerber](HD-15/gerber) directory (do not decompress it). Then, go to [JLCPCB](https://jlcpcb.com), click "Add Gerber File," and upload the ZIP. The 2-layer PCB will load automatically. You can leave all settings as defaults (feel free to change the PCB color if you'd like). Place the order, and you should receive your five PCBs quickly and affordably.

### Other Components

| Component | Needed for HD-15 Version | Needed for DA-15 Version | Source |
| --- | --- | --- | --- |
| 2.0mm Pitch 19mm Length Header Pins | X | X | [eBay](https://www.ebay.com/itm/171495154253) |
| 1N4007 Diode | X | | [Amazon](https://a.co/d/5SRJu1n) |
| Amphenol L77HDEH15SOL2RM8 Female HD-15 Connector | X | | [Mouser](https://www.mouser.com/ProductDetail/Amphenol-Commercial-Products/LD15S24A4GX00LF?qs=tZOhSuJQg1m5NC9di5k5CQ%3D%3D) |
| Amphenol LD15S24A4GX00LF Female DA-15 Connector | | X | [Mouser](https://www.mouser.com/ProductDetail/Amphenol-Commercial-Products/LD15S24A4GX00LF?qs=tZOhSuJQg1m5NC9di5k5CQ%3D%3D) |
| M3 x 8 screws | 2 | 1 | [Amazon](https://www.amazon.com/dp/B0BMQGV4SW?ref=ppx_yo2ov_dt_b_fed_asin_title&th=1) |

#### Header Pins
I recommend using 19mm long 2.0mm pitch header pins. The horizontal spacing of the HDI-45 pins is 2.0mm, allowing you to insert some pins in bundles. However, the vertical spacing is smaller, so plastic spacers cannot remain in place for all five rows. I found that using strips of headers for rows 1, 3, and 5 (with 4, 3, and 4 pins, respectively) works best. Rows 2 and 4 only require two pins each, which should be inserted individually. I sourced my headers from [eBay](https://www.ebay.com/itm/171495154253).

#### Diode (HD-15 Version Only)
A single diode is needed for the sense lines to set the HD-15 adapter to 21" MultiSync mode, enabling resolutions of 640x480 @ 67Hz or 832x624 @ 75Hz. I used 1N4007 diodes from [Amazon](https://a.co/d/5SRJu1n).

#### Connectors
You'll need different connectors for each adapter type:
- **HD-15 version:** [Amphenol L77HDEH15SOL2RM8](https://www.mouser.com/ProductDetail/Amphenol-Commercial-Products/L77HDEH15SOL2RM8?qs=mq7kV%2Fq8lk7g9czTkxkhWQ%3D%3D) (Mouser)
- **DA-15 version:** [Amphenol LD15S24A4GX00LF](https://www.mouser.com/ProductDetail/Amphenol-Commercial-Products/LD15S24A4GX00LF?qs=tZOhSuJQg1m5NC9di5k5CQ%3D%3D) (Mouser)

Any straight female HD-15 or DA-15 connector should work.

### Screws
If using a case, you'll need one or two M3 x 8 screws to secure the case halves together, depending on your version. The link above is for a set of m3 screws in different heads and lengths.  They're useful to have around, so buy yourself a set to keep handy. Or you can likely find a screw in your computer junk drawer that will work.  

### Case
You can 3D print your own case or use a service like JLC3DP. Get the `.obj` files from the "case" directory for your chosen version. The files are optimized for flat-surface printing with minimal support. My slicer only added supports for the dome cutouts in the "bottom" case where the ground pegs sit. Your printer may not need them. Start printing early so the case is ready when your PCB assembly is complete. I strongly recommend using the case with this PCB.

## Assembly
Assembly is slightly challenging due to the long header pins. I recommend using an HDI-45 port to align the pins before soldering them into the PCB. I salvaged an HDI-45 connector from a non-functional PM6100 logic board for this purpose. However, you can also use the port while it's still on the logic board, though it will be more awkward.

### Soldering Order
1. Solder the header pins
2. (HD-15 version only) Solder the diode
3. Solder the HD-15 or DA-15 connector
4. Assemble the 3D-printed case

#### Soldering the Pins

#### Final Assembly
1. First, solder the header pins. There are two approaches:
    - **Advanced method:** Load four of the five rows simultaneously using cut header strips and individual pins. You can insert them all into the PCC and then insert the PCB with headers into the connector.  Or, my prefered method, you can load all the pins into the connector, and then lower the PCB onto the pins to get them in the PCB (wiggling it as you go to load all 4 roes). Then solder all four rows at once. I've found doing this with 4 rows is much easier than all 5. After solding those 4 rows, add and solder the final row. For more details and pictures, see [pin assembly details](PIN_ASSEMBLY_DETAILS.md). 
    - **Simple method:** Solder one row at a time. Insert a 4-pin strip into the PCB, place it into the HDI-45 port, and solder. Repeat for the remaining rows.
2. Insert and solder the diode (HD-15 version only) at the D1 location, ensuring correct orientation. If you prefer 14" MultiSync mode, use a wire instead of a diode.
3. Insert and solder the appropriate connector, making sure to connect the shielding to ground for stability.
4. Assemble the case
    - Place the PCB into the bottom case, aligning the pins evenly. Insert it into the HDI-45 port to confirm alignment.
    - Attach the top case and secure it with M3 x 8 screws.
    - Test the fit by reinserting the adapter into the HDI-45 port. Adjust as needed to prevent snags.

Your adapter is now ready to use. When fitted with the case, it is secure enough without additional attachment, though you can add double-sided tape if needed. Note that PowerMac 7100 and 8100 models have obstructions that prevent full insertion of the adapter, but testing on an 8100 confirmed it still functions correctly. The 7100 should work as well.

## Special Thanks
I'd like to thank the TinkerDifferent forum members who participated in [the discussion](https://tinkerdifferent.com/threads/need-solution-for-hdi-45-to-db-15-connectors-for-video-out.4056/) that led to the creation of this adapter. I couldn't have done it without their help.


