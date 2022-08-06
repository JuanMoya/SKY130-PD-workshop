# SKY130-PD-workshop
Here you can find all the material that I developed from the SKY 130 PD workshop.


## Sky130 Day 1 - Inception of open-source EDA, OpenLANE and SKY130 PDK (Lab Instance 1)

![Docker command](step_1.png)
We use the "docker" command to invoke openlane.

![./flow.tcl -interactive command to run the OpenLANE flow.](step_2.png)
We type the "./flow.tcl - interactive" command to run the openLANE flow.

![package require openlane 0.9 command to load all the packages needed.](step_3.png)
We type the "package require openlane 0.9" command to load all the packages needed in the openLANE flow.

The three commands mentioned above must be executed everytime we want to run the openLANE flow.

![prep -design picorv32 command to prepare the design setup stage.](step_4.png)
We prepare the design setup stage with thrv32a-e command "prep -design picorv32a"

![We check the created files.](step_5.png)
![We check the temp directory and the files created inside.](step_6.png)
Then, we review the files after design preparation and run synthesis.

![We run the synthesis.](step_7.png)
Then, we type the "run_synthesis" command.

![Synthesis successfull.](step_8.png)
We observe that the synthesis is completed successfully.

![Flop ratio.](step_9.png)
We look for the flop ratio as presented above. 
We observe that the total number of d flip-flops (dfxtp_2) is: 1613, and the total number of cells is: 14876. Thus the flop ratio is: 1613/14876 = 0.1084. The equivalent percentage is 10.84%. 

![Total chip area.](step_10.png)
The total chip area is 147712.918400.

![Synthesized netlist file.](step_11.png)
We use the command less picorv32a.synthesis.v to open the synthesized netlist file.
![Synthesized netlist.](step_12.png)
Then we observe the synthesized netlist.
To close the file, we click the "q" botton.

![Reports directory.](step_13.png)
Finally we check the reports directory.

## Sky130 Day 2 - Good floorplan vs bad floorplan and introduction to library cells (Lab Instance 1)

![Definition of the variables for the different steps.](Day2_1.png)
In the "/home/jsmoya07/Desktop/work/tools/openlane_working_dir/openlane/configuration" we enter the README.md file and we observe the variables used in each step.

![Default parameters set for the floorplan stage.](Day2_2.png)
Then we open the "floorplan.tcl".

![Default parameters set in the "config.tcl".](Day2_3.png)
Then we open the "config.tcl".

![Default parameters set in the "config.tcl".](Day2_4.png)
Then we open the "sky130A_sky130_fd_sc_hd_config.tcl "

The priority order for the settings is "sky130A_sky130_fd_sc_hd_config.tcl" --> "config.tcl" --> "floorplan.tcl".

![We run the "run_floorplan".](Day2_5.png)
Once the priority is identified, we run the floorplan of the synthesis obtained above. It is important to mention that floorplan must be run after the synthesis command. If we shut down the session or close openlane (close the terminal), the prep and synthesis commands must be run again.

![The "run_floorplan" command ends.](Day2_6.png)
We observe that the floorplan was successfully implemented.

![The "less ioPlacer.log" command.](Day2_7.png)
![The "less ioPlacer.log" file.](Day2_8.png)
We open the "ioPlacer.log" with the "less ioPlacer.log" command.

![The "less picorv32a.floorplan.def" file.](Day2_9.png)
Then we open the "picorv32a.floorplan.def"

![The magic command to open the layout.](Day2_10.png)
The we run the magic command to open the layout in magic.

![The layout in magic.](Day2_11.png)
Then we can observe the floorplan in magic.

![Zoom in to see the pins distribution.](Day2_12.png)
We zoom in the layout to identify the distance between the pins.

![Zoom in to see the i/o horizontal pins in metal 3.](Day2_13.png)
We zoom in the layout to identify the metal for the i/o horizontal pins.

![Zoom in to see the i/o vertical pins in metal 2.](Day2_14.png)
We zoom in the layout to identify the metal for the i/o horizontal pins.

![Zoom in to see the standard cells in the down left corner.](Day2_15.png)
We zoom in the layout to identify the standard cells in the down-left corner. It is importante to mention that the floorplan does not place the standard cells in the core area, that is why we observe them in the down-left corner.

![The "run_placement" command for wire length reduction.](Day2_16.png)
Then we reduce the wire length with the "run_placement" command.

![The "run_placement" process is done.](Day2_17.png)
We verify that the placement process is done.

![Directory placement.](Day2_18.png)
Now we see the design post placement with the following command.

![Standard cell placement in magic.](Day2_19.png)
Finally, in magic we observe the placement of the standard cells.

## Sky130 Day 3 - Design library cell using Magic Layout and ngspice characterization

![Distance of the pins before changes in magic.](Day3_1.png)
We made changes in the configuration of I/O pins file to change the distance between the pins. But let's take a look before.

![We change the distance between pins.](Day3_2.png)
We change the variable FP_IO_MODE to 2 and then we run the "run_floorplan" command.

![We observe that the distance between pins has changed.](Day3_3.png)
We observe the changes in the distance between the pins.

![We observe that the distance between pins has changed.](Day3_4.png)
First of all let's clone the "vsdstdcelldesign" repository.

![We copy the "sky130A.tech" file.](Day3_5.png)
We copy the tech file in the vsdstdcelldesign file.

![We identify the copied "sky130A.tech" file in vsdstdcelldesign.](Day3_6.png)
We observe the copied file in vsdstdcelldesign.

![We open magic with the inverter and technology files.](Day3_7.png)
Then we open the file with technology file included.

![We extract the inverter's parasitics and see the extracted file.](Day3_8.png)
We create an extracted file, we extract all the parasitic capacitances and resistances, and we observe the created extracted file.
