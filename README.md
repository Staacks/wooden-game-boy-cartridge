# wooden-game-boy-cartridge
A CNC-machined Game Boy cartridge shell

**:warning: Note: I have also released a [wooden Game Boy](https://github.com/Staacks/wooden-game-boy) and this also contains an optimized version of the cartridge.**

I made this while experimenting with my new CNC router and someone asked me to share the original files, so here they are.

To see the steps (in a time lapse) and the result, check out this clip:

[![Youtube Short Video: Making a wooden Game Boy Cartridge](https://img.youtube.com/vi/ePvpYVNEvzk/0.jpg)](https://youtu.be/ePvpYVNEvzk)

## Important warning

I never planned this project to be properly documented and changed it while machining the one cartridge I made. Therefore, the naming within the files can be off, some parts are designed as fixes for other parts and some parts that were used to generate gcode might have been changed afterwards to create a different part (although I try to avoid this). So, it is very unlikely that you can take these files as they are and just use them on your machine and you should only see them as a starting point to create your own tool paths.

## General parameters and tools I used

* **Wood**: I used walnut wood that I got on ebay as a packet full of cutting remains.
* **Router**: My CNC router is a SainSmart Genmitsu PROverXL 4030 v2 (what a mouth full) with its stock 400W spindle.
* **Bits**: Most steps were done with a 1.5mm diameter **downcut** end mill by Sorotec. Exceptions are the surfacing step which was done with a surfacing bit (not part of the files above) and a 90° V-shaped 1/4 inch chamfering bit by Speed Tiger for chamfering and engraving of the top. (Note, that those are my very first bits of each type I ever bought, so I cannot tell you if these specific models are a good choice.)
* **Speeds**: Sorotec recommends rather high speeds for the 1.5mm end mill, which is not surprising as the tangential velocity is much smaller on small diameters. However, since my stock spindle can only do 10,000 rpm max, I left it at that setting and reduced the feeds accordingly. Since my machine does not have gcode control over the spindle speed, I ignored the setting in the CAM. **Do not just use the speed from the files as it is not the speed I used and does not necessarily match the feeds or your setup!**
* **Feeds**: Those can be found in the CAM files. Generally, I kept it conservative around 150mm/min to 300mm/min.
* **CAD/CAM**: As a cheap and desperate Linux user with Blender experience, I ended up using Blender CAM. Sorry, I know that this is a nightmare for anyone not used to Blender, but it is more powerful than some software that costs hundreds of Euros and runs natively on Linux. A no brainer for someone already familiar with Blender.

## The steps I used to create my cartridge

I also added the original gcode files that I used as reference. However, it is very unlikely that they are usefull on a random machine, so they are probably just useful to be viewed in a gcode viewer.

1. Prepare a 5mm thick board with surfacing bit. This is not in the files above and should match the stock you use. Note, that the typical cartridge bottom is about 5.5mm high and I also designed the bottom around 5.5mm. I just cut away a bit too much and simply adjusted the zero height 0.5mm above the surface of the board to compensate.
2. Run the gcode to drill the pocket and hole for the screw on the outside of the bottom half. Make sure to pick your zero such that the next profile step stays within your material. (gb_bottom_outside_1pocket.gcode, 1.5mm end mill)
3. Run the gcode for the profile cut. Note, that this goes about 1mm below your stock, so make sure to use a spoil board. (gb_bottom_outside_2profile.gcode, 1.5mm end mill)
4. Flip the part you have so far to machine the inside of the bottom half next. Align it such that it is perfectly parallel to your machine's axes and that zero is in the bottom left corner ("bottom left" is a bit vague. Check the upcoming pocketing gcode and compare the corner of the cartridge.)
5. Run the first layer of the pocketing tool path (gb_bottom_1inside_pocket.gcode, 1.5mm end mill)
6. Run the second layer of the pocketing tool path (gb_bottom_2inside_pocket2.gcode, 1.5mm end mill)
7. The bottom part should be done, so remove it and place the remainder of your 5mm board in your machine to cut the top half from it. Again, make sure that the upcoming profile cut fits.
8. Run the gcode for the arrow and label area (gb_top_outside_1label_pocket.gcode, 1.5mm end mill)
9. Run the gcode for the round grip part at the top of the cartridge (gb_top_outside_2grip.gcode, 1.5mm)
10. Run the gcode for the profile cut. Again, note that it will be deeper than your material. (gb_top_outside_3profile.gcode, 1.5mm end mill)
11. Now we switch to the V-shaped bit for chamfering.
12. Run the gcode to create the chamfered sides. Note, that this is a very quick operation and I to my ears the settings sounded a bit more aggressiv than the other ones, so depending on your machine you might want to dial the feed back a little. (gb_top_outside_4chamfer.gcode, 90° V-shaped bit)
13. Run the gcode to carve the lines next to the grip part (gb_top_outside_5sidelines.gcode, 90° V-shaped bit)
14. Run the gcode to carve the label (if you want that label). Note, that I misinterpreted the start height option of Blender CAM, so I adjusted the z height by 0.46mm to actually carve into the grip part. Otherwise it will just run above the material and do nothing. (gb_top_outside_6oughtabe.gcode, 90° V-shaped bit)
15. Now, it's time for the inside of the top half and back to the 1.5mm end mill. Turn around the piece you just cut out and align it perfectly with your machine's axes. Again, align x and y zero with the bottom left corner of the cartridge.
16. Run the gcode to drill a small hole that aids inserting the screw (gb_top_inside_1hole.gcode, 1.5mm end mill)
17. Run the gcode to pocket the inside of the top half (this takes a while). Note that I initially made a mistake here and did not generate a path to cut the top side. Therefore, I later added a toolpath that just cuts the missing part at the top. This is why you find two gcode files for this step and in the Blender files you will find that the work area is still set only to the "fix" part. So, you will have to adjust this to do the entire pocketing step in one go. (gb_top_inside_2pocket.gcode and gb_top_inside_pocket_fix.gcode, 1.5mm end mill)

That's it. I had to do little to no sanding. Most boards from original cartridges or flash cartridges should fit if they have the screw hole in the right place. But also note, that since the machined cartridge does not have any ridges to hold the sides together, that one screw is not enough to keep the sides closed without a gap. You might want to adjust the design a bit or use glue here.

## Licence

I release everything here under the Creative Commons Attribution 4.0 International license (CC-BY 4.0). Enjoy :)

<a href="https://www.buymeacoffee.com/there.oughta.be" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" height="47" width="174" ></a>
