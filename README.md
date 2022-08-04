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
