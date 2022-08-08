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

![Extracted file ready to simulate.](Day3_9.png)
We modify the extracted file to simulate the circuit by defining correctly the grid, include the libraries, define the analysis and assign values to the sources and ground.

![Ngspice command run.](Day3_10.png)
We run the ngspice command.

![We plot y and a vs time.](Day3_11.png)
Let's plot.

![We identify the time for the 0.66*Vdd.](Day3_12.png)
Follow, we identify the rise time. Above, we see the 0.66*Vdd when the output is changing from gnd to Vdd.

![we get the rise time.](Day3_13.png)
Then we obtain the rise time. We observe that t_rise = 2.20299ns - 2.16162ns = 0.04137ns.

![Plot to get the propagation delay.](Day3_14.png)
We do the same process for the propagation delay(50% of Vdd for both input and output).

![We get the propagation delay.](Day3_15.png)
Then we obtain the rise time. We observe that t_propagation_delay = 2.1844ns - 2.15ns = 0.0344ns.

![Model and setup configuration.](Day3_33.png)
Next, we simulate the spice deck for the different wp and wn values. Above we present the .cir file. 

![Inverter DC simulation.](Day3_34.png)
We observe the DC simulation of the output against the input. 

![We identify the switching threshold voltage .](Day3_35.png)
The switching threshold voltage Vm is approximately 1.288V. 

Next, we present the results for different Wn/Ln to see how the switching threshold voltage changes.

ratio pmos = 1.5; ratio nmos = 1.5 --> Vm = 1.288V

ratio pmos = 1.5; ratio nmos = 3 --> Vm = 1.096V

ratio pmos = 1.5; ratio nmos = 4.5 --> Vm = 1.055V

ratio pmos = 1.5; ratio nmos = 6 --> Vm = 0.97V

ratio pmos = 1.5; ratio nmos = 7.5 --> Vm = 0.93V

![Inverter DC simulation for ratio pmos = 1.5 and ratio pmos = 7.5.](Day3_36.png)
The switching threshold voltage Vm is approximately 0.93V. 

As expected, the Vm value decreases as the nmos ratio increases.

![We download the labs.](Day3_16.png)
Next, we do the lab exercise associated to Magic DRC. We download the labs in the openlane directory.

![Poly file opened.](Day3_17.png)
We open the poly file.

![We look for the "poly.9" in the "SKY130A.tech" and modify it.](Day3_18.png)
Then we open the "SKY130A.tech" and look for the "poly.9"

![We include in the "SKY130A.tech" the "allpolynonres" rule.](Day3_19.png)
We modify the file.

![We observe the implementation of the rule.](Day3_20.png)
We observe in Magic that the rule was correctly implemented.

![Before including the rule.](Day3_21.png)
![After including the rule.](Day3_22.png)
We made the same process for the ppolyres and nsd and psd layer rules.

![Before including the cif.](Day3_23.png)
![After including the cif.](Day3_24.png)
We do the same process for the nwell layer rules.

![Last lab.](Day3_25.png)
Finally, the last error is associated to nwell.4.

![Change 1.](Day3_26.png)
![Change 2.](Day3_27.png)
![Change 3.](Day3_28.png)
We do the respective changes.

![We observe that the errors appear.](Day3_29.png)
We identify the errors in magic ofr the nwell.4.

![DRC(full) style.](Day3_30.png)
We define the drc(full) style.

![We prove that the error modification is verified.](Day3_31.png)
Finally, we verify that the errors are shown.

## Sky130 Day 4 - Pre-layout timing analysis and importance of good clock tree

![Track information of the different layers.](Day4_1.png)
We observe the file associated to the tracks.

![Grid set according to the track infomation.](Day4_2.png)
We set the grid of the inverter magic file according to the track file and we observe that the pins are placed in the intersection between horizontal and vertical tracks.

![Copy of the inverter file.](Day4_3.png)
We make a copy of the inverter file to  incorporate in the physical design flow.

![We open the inverter file.](Day4_4.png)
We open the copied file to verify that it is ok.

![LEF file created.](Day4_5.png)
We create the LEF file.

![LEF file verification.](Day4_6.png)
We verify that the LEF file is created.

![LEF file information.](Day4_7.png)
We open the LEF file.

![Copied files in the src folder.](Day4_9.png)
We copy the .lef and libraries in the src file to be part of the flow.

Then, we modify the config.tcl.

![Before modifications.](Day4_10.png)
The config.tcl before modifications.

![After modifications.](Day4_11.png)
The config.tcl after modifications.

![We run openLANE again with our cell.](Day4_12.png)
We run the openLANE flow and we overwrite the last folder generated by the synthesis.

![We include the two lines.](Day4_13.png)
We include the two lines in the flow.

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]

add_lefs -src $lefs

![Synthesis was successful.](Day4_14.png)
We observe that the synthesis was successful.

![tns and wns values.](Day4_15.png)
We observe the tns and wns values.

![Current chip area.](Day4_15a.png)
The current chip area is 147712.918400 um2.

![Variable modifications.](Day4_16.png)
Then we define the variables to change strategy.

![Skipping synthesis.](Day4_17.png)
We rerun the synthesis but there already exists the ".synthesis.v" file.

![Renaming old "synthesis.v" file.](Day4_18.png)
I rename the ".synthesis.v" file to avoid conflicts.

![Error with the "::env(SYNTH_STRATEGY)" variable definition.](Day4_19.png)
I rerun the synthesis but I got an error since the "::env(SYNTH_STRATEGY)" was not correctly defined.

![Correct definition of the "::env(SYNTH_STRATEGY)" variable.](Day4_20.png)
I correctly define "::env(SYNTH_STRATEGY)".

![Synthesis successful.](Day4_21a.png)
Then I rerun the synthesis and it was successful.

![New area for the new strategy.](Day4_22.png)
The new area is 209181.872000 um2.

![Placement command error.](Day4_23.png)
I run the placement and got the error above.

The old command of the flow was: "run_placement", the new sequence is:

init_floorplan

place_io

global_placement_or

detailed_placement

tap_decap_or

detailed_placement

![Check Legality passes.](Day4_24.png)
Once I ran the sequence above, the legality passes completely.

![Verification of the .def file.](Day4_25.png)
We verified the .def file in magic.

![Verification of the sky130_vsdinv cell in the placement.](Day4_26.png)
We identified the sky130_vsdinv cell in the placement.

![Lef view possible with the expand command.](Day4_27.png)
We do the "expand" command in the tkcon to see the lef view.

![The slack is 4.39.](Day4_28.png)
We observe that the slack is positive.

![pre_sta.conf file configured correctly.](Day4_29.png)
We modify the pre_sta.conf file.

![my_base.sdc file configured correctly.](Day4_30.png)
We modify the my_base.sdc file.

![sta pre_sta.conf file run.](Day4_31.png)
We run the "pre_sta.conf" file.

![We obtain the corresponding slack.](Day4_32.png)
We obtain a slack of -2.95.

![Hold slack value.](Day4_33.png)
We show the hold slack of 0.24.

![Fanout information.](Day4_34.png)
We show part of the fanout information.

![SYNTH_MAX_FANOUT = 4.](Day4_35.png)
We set the FANOUT variable to 4.

![New slack value.](Day4_36.png)
We show the new slack value 4.56.

![](Day4_36a.png)
We observe the different cells in the report.

![](Day4_36b.png)
We do a "report_net -connections _18851_" command to see the connections.

![](Day4_36c.png)
We observe a more interesting case with the _42093 instance which is made of mux2_1.

![](Day4_36d.png)
We replace the mux2_1 cell with mux2_4 cell with the command "replace_cell _42093_ sky130_fd_sc_hd_mux2_4" command.

![](Day4_36e.png)
We do "report_checks -fields {net cap slew input_pins} -digits 4" command to generate the new report.

![](Day4_36f.png)
We observe that the slack reduces to -2.1794.

![](Day4_36g.png)
We rewrite the synthesis.v file to include the new changes.

![](Day4_36h.png)
We observe the new intance changes in the rewrite file.

We rerun the following commands (we don not run synthesis because the synthesis.v will be written again and we don't want to lose the changes).

init_floorplan

place_io

global_placement_or

detailed_placement

tap_decap_or

detailed_placement

![](Day4_36i.png)
In the "detailed_placement_or" step we observe that the slack is better.

!["run_cts" command.](Day4_37.png)
Then we run the cts command after second the "detailed_placement_or" command.

![The clock tree synthesis was successful.](Day4_38.png)
We observe that the clock tree synthesis was successful.

![ The picrorv32a.synthesis_cts.v file was created.](Day4_39.png)
We observe that the picrorv32a.synthesis_cts.v file was created.

![ All the .tcl files.](Day4_40.png)
We observe all the .tcl files in the tcl_commands folder.

![ run_cts command procs.](Day4_41.png)
We observe the all the proc for the run_cts command. 

![ .tcl files in the openroad file.](Day4_42.png)
We observe the .tcl files in the openroad folder. 

![ Verification of different variables values.](Day4_43.png)
We verify different variables values after the run_cts command. 

![ We open openroad.](Day4_44.png)
We open openroad for timming analysis just after the openLANE flow. 

![ merged.lef file read.](Day4_45.png)
We read the lef file. 

![ picorv32a.cts.def file read.](Day4_46.png)
We read the def file. 

![ Commands for timming analysis.](Day4_49.png)
We set the commands above for timming analysis.

![ Results of the timming analysis.](Day4_50a.png)
We observe the results of timming analysis.

![ ](Day4_51.png)
We open openroad and set the variables.

![ ](Day4_52.png)
We set the report command.

![ ](Day4_53.png)
We see the associated slack value, which is 3.9317.

![ ](Day4_54.png)
We see the associated slack value for the hold, which is -0.0188.

![ ](Day4_55.png)
We set the variable for the clk buffer list.

![ ](Day4_56.png)
We obtain the error presented in the video.

![ ](Day4_57.png)
We need to configure again the variables.

## Sky130 Day 5 - Final steps for RTL2GDS using TritonRoute and openSTA

![The "gen_pdn" command for PDN generatioN.](Day5_1.png)
We open openlane and run the "gen_pdn" command.

![PDN generation was successful.](Day5_2.png)
We identify the PDN generation was successful.

![The "run_routing".](Day5_3.png)
Finally, we run routing.

![Several iterations for routing.](Day5_4.png)
We observe the some iterations.

![We have 0 violations.](Day5_5.png)
After several minutes and iteratios, we have 0 violations.

![Routing was successfull.](Day5_6.png)
We observed that the routing finished successfully.

![the .spef file was created.](Day5_8.png)
We observed that the .spef file was created.
