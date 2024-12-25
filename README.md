<h1 align="center">Digital-VLSI-System-Design-and-SoC-Planning</h1>
2 Week workshop on “Digital VLSI System Design and SoC Planning” by Kunal Ghosh, in which picorv32a processor was designed from RTL to GDS-II in OpenLane flow, which comprises of various open source EDA tools for Synthesis and Physical Design. In the design SkyWater SKY130 PDK was used.
<h2>Section 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK</h2>
<h3>Implementation</h3> 
<h4>Task</h4>
<ol>
  <li> Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.</li>
  <li> Calculate the flop ratio.</li>
</ol>
<p align="center">
Flop Ratio = (Number of D Flip Flops) / (Total Number of Cells)<br/>
Percentage of DFF's = Flop Ratio * 100
</p>
<h4>1. Run 'picorv32a' design synthesis using OpenLANE flow and generate necessary outputs.</h4>
<p>Commands to invoke the OpenLANE flow and perform synthesis</p>

<dl>  
  <dd>//Change directory to openlane flow directory</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane</dd>
  <dd>//alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'</dd>
  <dd>//Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command</dd>
  <dd>docker</dd>
  <dd>//Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command</dd>
  <dd>./flow.tcl -interactive</dd>
  <dd>//Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow</dd>
  <dd>package require openlane 0.9</dd>
  <dd>//Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'</dd>
  <dd>prep -design picorv32a</dd>
  <dd>//Now that the design is prepped and ready, we can run synthesis using following command</dd>
  <dd>run_synthesis</dd>
</dl>
<p>The screenshots of above steps and changes in picorv32a directory is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-1.JPG" alt="Capture -1">
Capture -1
Capture -2
Capture -3
Capture -4
Capture -5
Capture -6
Capture -7
Capture -8
Capture -13
<br/>
<br/>
<br/>
<h4>2. Calculate the flop ratio.</h4>
<p>Screenshots of synthesis statistics report file with required values highlighted is shown below</p>
Capture -9
Capture -10
Capture -11
Capture -12
<br/>
<br/>
<br/>
<p>Calculation of Flop Ratio and DFF % from synthesis statistics report file</p>
<p align="center">
Flop Ratio = 1613 / 14876  = 0.108429685<br/>
  Percentage of DFF's = 0.108429685 ∗ 100 = 10.8429685 %
</p>

<h2>Section 2 - Good floorplan vs bad floorplan and introduction to library cells.</h2>
<h3>Implementation</h3>
<h4>Task</h4>
<ol>
  <li> Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.</li>
  <li> Calculate the die area in microns from the values in floorplan def.</li>
  <li> Load generated floorplan def in magic tool and explore the floorplan.</li>
  <li> Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.</li>
  <li> Load generated placement def in magic tool and explore the placement.</li>
<p align="center">
Area of Die in microns = Die width in microns * Die height in microns
</p>
</ol>
<h4>1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.</h4>
<p>Commands to invoke the OpenLANE flow and perform floorplan</p>
<dl>  
  <dd>//Since synthesis is done, now we can run floorplan</dd>
  <dd>run_floorplan</dd>
</dl>
<p>Screenshots of floorplan run is shown below</p>
Capture -14
Capture -15
<br/>
<br/>
<br/>
<h4>2. Calculate the die area in microns from the values in floorplan def.</h4>
<p>Screenshots of contents of floorplan def is shown below</p>
Capture -16
<br/>
<br/>
<br/>
<p>According to floorplan def</p>
<p align="center">
1000 Unit Distance = 1 Micron<br/>
  Die width in unit distance = 660685 - 0 = 660685<br/>
  Die height in unit distance = 671405 - 0 = 671405<br/>
Distance in microns = Value in unit distance / 1000<br/>
  Die width in micron = 660685 / 1000 = 660.685 microns<br/>
  Die height in micron = 671405 / 1000 = 671.405 microns<br/>
  Area of Die in micron = 660.685 * 671.405 = 443587.212425 square microns
</p>
<h4>3. Load generated floorplan def in magic tool and explore the floorplan.</h4>
<p>Commands to load floorplan def in magic in another terminal</p>
<dl>  
  <dd>//Change directory to path containing generated floorplan def</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-12_14-09/results/floorplan</dd>
  <dd>//Command to load the floorplan def in magic tool</dd>
  <dd>magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &</dd>
</dl>
<p>Screenshots of terminal is shown below</p>
Capture -17
<br/>
<br/>
<br/>
<p>Screenshots of floorplan def in magic is shown below</p>
Capture -18
<br/>
<br/>
<br/>
<p>Screenshots of Equidistant placement of ports is shown below</p>
Capture -19
<br/>
<br/>
<br/>
<p>Screenshots of Port layer as set through config.tcl is shown below</p>
Capture -20
Capture -21
<br/>
<br/>
<br/>
<p>Screenshots of Decap Cells and Tap Cells is shown below</p>
Capture -22
<br/>
<br/>
<br/>
<p>Screenshots of Diogonally equidistant Tap cells is shown below</p>
Capture -23
<br/>
<br/>
<br/>
<p>Screenshots of Unplaced standard cells at the origin is shown below</p>
Capture -24
<br/>
<br/>
<br/>
<h4>4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.</h4>
<p>Command to run placement</p>
<dl>  
  <dd>//Congestion aware placement by default</dd>
  <dd>run_placement</dd>
</dl>
<p>Screenshots of placement run is shown below</p>
Capture -25
Capture -26
<br/>
<br/>
<br/>
<h4>5. Load generated placement def in magic tool and explore the placement.</h4>
<p>Commands to load placement def in magic in another terminal is shown below</p>
<dl>  
  <dd>//Change directory to path containing generated placement def</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-12_14-09/results/placement/</dd>
  <dd>//Command to load the placement def in magic tool</dd>
  <dd>magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &</dd>
</dl>
<p>Screenshots of floorplan def in magic is shown below</p>
Capture -27
capture -28
<br/>
<br/>
<br/>
<p>Standard cells legally placed is shown below</p>
Capture -29
<br/>
<br/>
<br/>

<h2>Section 3 - Design library cell using Magic Layout and ngspice characterization</h2>
<h3>Implementation</h3>
<h4>Task</h4>
<ol>
  <li> Clone custom inverter standard cell design from github repository: [Standard cell design and characterization using OpenLANE flow](https://github.com/nickson-jose/vsdstdcelldesign).</li>
  <li> Load the custom inverter layout in magic and explore.</li>
  <li> Spice extraction of inverter in magic.</li>
  <li> Editing the spice model file for analysis through simulation.</li>
  <li> Post-layout ngspice simulations.</li>
  <li> Find problem in the DRC section of the old magic tech file for the skywater process and fix them.</li>
</ol>
<h4>1. Clone custom inverter standard cell design from github repository</h4>
<p>Commands to copy inverter standard cell design from github repository is shown below</p>
<dl>  
  <dd>//Change directory to openlane</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane</dd>
  <dd>//Clone the repository with custom inverter design</dd>
  <dd>git clone https://github.com/nickson-jose/vsdstdcelldesign</dd>
  <dd>//Change into repository directory</dd>
  <dd>cd vsdstdcelldesign</dd>
  <dd>//Copy magic tech file to the vsdstdcelldesign directory for easy access</dd>
  <dd>//Open new terminal and change directory to magic</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic</dd>
  <dd>//Now copy file as shown below</dd>
  <dd>cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign</dd>
  <dd>//Go back to previous terminal and check whether file is copied or not</dd>
  <dd>ls -ltr</dd>
</dl>
<p>Screenshots of above steps is shown below</p>
<p>Screenshots of terminal before git clone</p>
Capture -30
<br/>
<br/>
<br/>
<p>Screenshots of terminal after git clone</p>
Capture -31
<br/>
<br/>
<br/>
<p>Screenshots of vsdstdcellesign directory before copying tech file</p>
Capture -32
<br/>
<br/>
<br/>
<p>Screenshots of terminal showing how to copy tech file in vsdstdcelldesign directory</p>
Capture -33
<br/>
<br/>
<br/>
<p>Screenshots of vsdstdcellesign directory after copying tech file</p>
Capture -34
<br/>
<br/>
<br/>
<h4>2. Load the custom inverter layout in magic and explore.</h4>
<p>Command to open custom inverter layout in magic is shown below</p>
<dl>  
  <dd>//Command to open custom inverter layout in magic</dd>
  <dd>magic -T sky130A.tech sky130_inv.mag &</dd>
</dl>
<p>Screenshot of custom inverter layout in magic is shown below</p>
Capture -35
<br/>
<br/>
<br/>
<p>Screenshot of NMOS identified is shown below</p>
Capture -36
<br/>
<br/>
<br/>
<p>Screenshot of PMOS identified is shown below</p>
Capture -37
<br/>
<br/>
<br/>
<p>Screenshot of Output Y connectivity to PMOS and NMOS drain verified is shown below</p>
Capture -38
<br/>
<br/>
<br/>
<p>Screenshot of PMOS source connectivity to VDD (here VPWR) verified is shown below</p>
Capture -39
<br/>
<br/>
<br/>
<p>Screenshot of NMOS source connectivity to VSS (here VGND) verified is shown below</p>
Capture -40
<br/>
<br/>
<br/>
<p>Screenshot of Polysilicon identified is shown below</p>
Capture -41
<br/>
<br/>
<br/>
<p>Screenshot of knowingly Deleted part of layout see DRC error is shown below</p>
Capture -42
<br/>
<br/>
<br/>
<h4>3. Spice extraction of inverter in magic.</h4>
<p>Commands for spice extraction of the custom inverter layout to be used in tkcon window of magic is shown below</p>
<dl>  
  <dd>//Check current directory</dd>
  <dd>pwd</dd>
  <dd>//Extraction command to extract to .ext format</dd>
  <dd>extract all</dd>
  <dd>//Before converting ext to spice this command enable the parasitic extraction also</dd>
  <dd>ext2spice cthresh 0 rthresh 0</dd>
  <dd>//Converting to ext to spice</dd>
  <dd>ext2spice</dd>
</dl>
<p>Screenshot of tkcon window after running above commands is shown below</p>
Capture -43
<br/>
<br/>
<br/>
<p>Screenshot vsdstdcelldesign directory after each command in tkcon window is shown below</p>
Capture -44
<br/>
<br/>
<br/>
<p>Screenshot of created spice file is shown below</p>
Capture -45
<br/>
<br/>
<br/>
<h4>4. Editing the spice model file for analysis through simulation.</h4>
<p>Measuring unit distance in layout grid as shown below</p>
Capture -46
<br/>
<br/>
<br/>
<p>Final edited spice file ready for ngspice simulation is shown below</p>
Capture- 47
Capture -48
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<h4>5. Post-layout ngspice simulations.</h4>
<p>Commands for ngspice simulation is shown below</p>
<dl>  
  <dd>//Command to directly load spice file for simulation to ngspice</dd>
  <dd>ngspice sky130_inv.spice</dd>
  <dd>//Now that we have entered ngspice with the simulation spice file loaded we just have to load the plot</dd>
  <dd>plot y vs time a</dd>
</dl>
<p>Screenshots of ngspice run is shown below</p>
Capture -49
<br/>
<br/>
<br/>
<p>Screenshots of command to plot graph in ngspice is shown below</p>
Capture -50
<br/>
<br/>
<br/>
<p>Screenshot of generated plot is shown below</p>
Capture -51
<br/>
<br/>
<br/>
<p>Rise transition time calculation is done as shown below</p>
<p align="center">
Rise transition time = Time taken for output to rise to 80% - Time taken for output to rise to 20%
  20% of output = 0.2 * 3.3V = 660mV
  80% of output = 0.8 * 3.3V = 2.64V
</p>
<p>20% of output screenshot and values of time & voltage is shown below</p>
Capture -52
Capture -53
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>80% of output screenshot and values of time & voltage is shown below</p>
Capture -54
Capture -55
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p align="center">Rise transition time = 2.2458 - 2.18197 = 0.06383 ns </p>
<p>Fall transition time calculation is done as shown below</p>
<p align="center">
Fall transition time = Time taken for output to fall to 20% - Time taken for output to fall to 80%
  20% of output = 0.2 * 3.3V = 660mV
  80% of output = 0.8 * 3.3V = 2.64V
</p>
<p>20% of output screenshot and values of time & voltage is shown below</p>
Capture -56
Capture -57
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>80% of output screenshot and values of time & voltage is shown below</p>
Capture -58
Capture -59
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p align="center">Fall transition time = 4.09512 - 4.05258 = 0.04254 ns</p>
<p>Rise cell delay calculation is done as shown below</p>
<p align="center">
Rise cell delay = Time taken for output to rise to 50% - Time taken for input to fall to 50%
  50% of 3.3V = 0.5 * 3.3V = 2.64V
</p>
<p>50% of input and output screenshot and values of time & voltage is shown below</p>
Capture -60
Capture -61
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p align="center">Rise cell delay = 2.21091 - 2.15009 = 0.06082 ns </p>
<p>Fall cell delay calculation is done as shown below</p>
<p align="center">
Fall cell delay = Time taken for output to fall to 50% - Time taken for input to rise to 50%
  50% of 3.3V = 0.5 * 3.3V = 2.64V
</p>
<p>50% of input and output screenshot and values of time & voltage is shown below</p>
Capture -62
Capture -63
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p align="center">Fall cell delay = 4.00763 - 4.05006 = 0.02757 ns</p>
<h4>6. Find problem in the DRC section of the old magic tech file for the skywater process and fix them.</h4>
<p>Commands to download and view the corrupted skywater process magic tech file and associated files to perform drc corrections is shown below</p>
<dl>  
  <dd>//Change to home directory</dd>
  <dd>cd</dd>
  <dd>//Command to download the lab files</dd>
  <dd>wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz</dd>
  <dd>//Since lab file is compressed,so the command to extract it</dd>
  <dd>tar xfz drc_tests.tgz</dd>
  <dd>//Change directory into the lab folder</dd>
  <dd>cd drc_tests</dd>
  <dd>//List all files and directories present in the current directory</dd>
  <dd>ls -al</dd>
  <dd>//Command to view .magicrc file</dd>
  <dd>gvim .magicrc</dd>
  <dd>//Command to open magic tool in better graphics</dd>
  <dd>magic -d XR</dd>
</dl>
<p>Link to Sky130 Periphery rules: https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html</p>
<p>Screenshots of commands run is shown below</p>
Capture -64
Capture -65
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Screenshots of Screenshot of .magicrc file is shown below</p>
Capture -66
Capture -67
Capture -68
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Screenshots of command "magic -d XR" is shown below</p>
Capture -69
<br/>
<br/>
<br/>
<b>Incorrectly implemented poly.9 simple rule correction</b>
<p>Screenshot of poly rules is shown below</p>
Capture -70
<br/>
<br/>
<br/>
<p>Incorrectly implemented poly.9 rule no drc violation even though spacing < 0.48u is shown below</p>
Capture -71
Capture -72
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>New commands inserted in sky130A.tech file to update drc is shown below</p>
Capture -73
Capture -74
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Commands to run in tkcon window after making changes in "sky130A.tech" file are shown below</p>
<dl>  
  <dd>//Loading updated tech file</dd>
  <dd>tech load sky130A.tech</dd>
  <dd>//Must re-run drc check to see updated drc errors</dd>
  <dd>drc check</dd>
  <dd>//Selecting region displaying the new errors and getting the error messages</dd>
  <dd>drc why</dd>
</dl>
<p>Screenshot of magic window with rule implemented is shown below</p>
Capture -75
Capture -76
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<b>Incorrectly implemented difftap.2 simple rule correction</b>
<p>Screenshot of difftap rules is shown below</p>
Capture -77
<br/>
<br/>
<br/>
<p>Incorrectly implemented difftap.2 rule no drc violation even though spacing < 0.42u is shown below</p>
Capture -78
<br/>
<br/>
<br/>
<p>New commands inserted in sky130A.tech file to update drc is shown below</p>
Capture -79
<br/>
<br/>
<br/>
<p>Commands to run in tkcon window after making changes in "sky130A.tech" file are shown below</p>
<dl>  
  <dd>//Loading updated tech file</dd>
  <dd>tech load sky130A.tech</dd>
  <dd>//Must re-run drc check to see updated drc errors</dd>
  <dd>drc check</dd>
  <dd>//Selecting region displaying the new errors and getting the error messages</dd>
  <dd>drc why</dd>
</dl>
<p>Screenshot of magic window with rule implemented is shown below</p>
Capture -80
<br/>
<br/>
<br/>
<b>Incorrectly implemented nwell.4 complex rule correction</b>
<p>Screenshot of nwell rules is shown below</p>
Capture -81
<br/>
<br/>
<br/>
<p>Incorrectly implemented nwell.4 rule no drc violation even though no tap present in nwell is shown below</p>
Capture -82
Capture -83
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>New commands inserted in sky130A.tech file to update drc is shown below</p>
Capture -84
Capture -85
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Commands to run in tkcon window after making changes in "sky130A.tech" file are shown below</p>
<dl>  
  <dd>//Loading updated tech file</dd>
  <dd>tech load sky130A.tech</dd>
  <dd>//Change drc style to drc full</dd>
  <dd>drc style drc(full)</dd>
  <dd>//Must re-run drc check to see updated drc errors</dd>
  <dd>drc check</dd>
  <dd>//Selecting region displaying the new errors and getting the error messages</dd>
  <dd>drc why</dd>
</dl>
<p>Screenshot of magic window with rule implemented is shown below</p>
Capture -86
<br/>
<br/>
<br/>

<h2>Section 4 - Pre-layout timing analysis and importance of good clock tree</h2>
<h3>Implementation</h3>
<h4>Task</h4>
<ol>
  <li> Clone custom inverter standard cell design from github repository: [Standard cell design and characterization using OpenLANE flow](https://github.com/nickson-jose/vsdstdcelldesign).</li>
  <li> Fix up small DRC errors and verify the design is ready to be inserted into our flow.</li>
  <li> Save the finalized layout with custom name and open it.</li>
  <li> Generate lef from the layout.</li>
  <li> Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.</li>
  <li> Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.</li>
  <li> Run openlane flow synthesis with newly inserted custom inverter cell.</li>
  <li> Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.</li>
  <li> Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.</li>
  <li> Do Post-Synthesis timing analysis with OpenSTA tool.</li>
  <li> Make timing ECO fixes to remove all violations.</li>
  <li> Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.</li>
  <li> Post-CTS OpenROAD timing analysis.</li>
  <li> Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.</li>
</ol>
<h4>1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.</h4>
<p>Conditions to be verified before moving forward with custom designed cell layout are shown below</p>
<dl>  
  <dd>Condition 1: The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.</dd>
  <dd>Condition 2: Width of the standard cell should be odd multiples of the horizontal track pitch.</dd>
  <dd>Condition 3: Height of the standard cell should be even multiples of the vertical track pitch.</dd>
</dl>
<p>Commands to open the custom inverter layout is shown below</p>
<dl>  
  <dd>//Change directory to vsdstdcelldesign</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign</dd>
  <dd>//Command to open custom inverter layout in magic</dd>
  <dd>magic -T sky130A.tech sky130_inv.mag &</dd>
</dl>
<p>Screenshot of sky130_inv.mag is shown below</p>
Capture -87
<br/>
<br/>
<br/>
<p>Open tracks.info file as shown in screenshot below</p>
Capture -88
<br/>
<br/>
<br/>
<p>Screenshot of tracks.info of sky130_fd_sc_hd is shown below</p>
Capture -89
<br/>
<br/>
<br/>
<p>Commands for tkcon window to set grid as tracks of locali layer</p>
<dl>  
  <dd>//Get syntax for grid command</dd>
  <dd>help grid</dd>
  <dd>//Set grid values accordingly</dd>
  <dd>grid 0.46um 0.34um 0.23um 0.17um</dd>
</dl>
<p>Screenshot of commands run is shown below</p>
Capture -90
<br/>
<br/>
<br/>
<p>Screenshot of Condition 1 verified is shown below</p>
Capture -91
<br/>
<br/>
<br/>
<p>Screenshot of Condition 2 verified is shown below</p>
<p align="center">Horizontal track pitch = 0.46 um<br>
Width of standard cell = 3 * 0.46 = 138 um
Capture -92
</p>
<br/>
<br/>
<br/>
<p>Screenshot of Condition 3 verified is shown below</p>
<p align="center">Horizontal track pitch = 0.34 um<br>
Width of standard cell = 8 * 0.34 = 2.72 um
Capture -93
</p>
<br/>
<br/>
<br/>
<h4>2. Save the finalized layout with custom name and open it.</h4>
<p>Command for tkcon window to save the layout with custom name is shown below</p>
<dl>  
  <dd>//Command to save as</dd>
  <dd>save sky130_vsdinv.mag</dd>
</dl>
<p>Screenshot of tkcon window and terminal with new file created is shown below</p>
Capture -94
Capture -95
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Command to open the newly saved layout is shown below</p>
<dl>  
  <dd>//Command to open custom inverter layout in magic</dd>
  <dd>magic -T sky130A.tech sky130_vsdinv.mag &</dd>
</dl>
<p>Screenshot of newly saved layout is shown below</p>
Capture -96
<br/>
<br/>
<br/>
<h4>3. Generate lef from the layout.</h4>
<p>Command for tkcon window to write lef is shown below</p>
<dl>  
  <dd>//lef command</dd>
  <dd>lef write</dd>
</dl>
<p>Screenshot of command run and terminal with new lef file created is shown below</p>
Capture 97
Capture -98
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Screenshot of newly created file is shown below</p>
Capture -99
<br/>
<br/>
<br/>
<h4>4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.</h4>
<p>Commands to copy necessary files to 'picorv32a' design 'src' directory is shown below</p>
<dl>  
  <dd>//Copy lef file</dd>
  <dd>cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/</dd>
  <dd>//List and check whether it's copied</dd>
  <dd>ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/</dd>
  <dd>//Copy lib files</dd>
  <dd>cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/</dd>
  <dd>//List and check whether it's copied</dd>
  <dd>ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/</dd>
</dl>
<p>Screenshot of commands run is shown below</p>
Capture -100
Capture -101
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<h4>5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.</h4>
<p>Commands to be added to config.tcl to include our custom cell in the openlane flow is shown below</p>
<dl>  
  <dd>set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"</dd>
  <dd>set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"</dd>
  <dd>set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"</dd>
  <dd>set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"</dd>
  <dd>set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]</dd>
</dl>
<p>Edited config.tcl to include the added lef and change library to ones we added in src directory is shown below</p>
Capture -102
Capture -103
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<h4>6. Run openlane flow synthesis with newly inserted custom inverter cell.</h4>
<p>Commands to invoke the OpenLANE flow include new lef and perform synthesis is shown below</p>
<dl>  
  <dd>//Change directory to openlane flow directory</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane</dd>
  <dd>//alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'</dd>
  <dd>//Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command</dd>
  <dd>docker</dd>
  <dd>//Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command</dd>
  <dd>./flow.tcl -interactive</dd>
  <dd>//Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow</dd>
  <dd>package require openlane 0.9</dd>
  <dd>//Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'</dd>
  <dd>prep -design picorv32a -tag 20-12_14-09 -overwrite</dd>
  <dd>//Adiitional commands to include newly added lef to openlane flow</dd>
  <dd>set lefs [glob $::env(DESIGN_DIR)/src/*.lef]</dd>
  <dd>add_lefs -src $lefs</dd>
  <dd>//Now that the design is prepped and ready, we can run synthesis using following command</dd>
  <dd>run_synthesis</dd>
</dl>
<p>Screenshot of command run is shown below</p>
Capture -104
Capture -105
Capture -105
Capture -106
Capture -107
Capture -108
Capture -109
Capture -110
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<h4>7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.</h4>
<p>Noting down current design values generated before modifying parameters to improve timing is shown below</p>
Capture -111
Capture -112
Capture -113
Capture -114
Capture -115
Capture -116
Capture -117
Capture -118
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Screenshot of merged.lef in tmp directory with our custom inverter as macro is shown below</p>
Capture -124
Capture -125
<br/>
<br/>
<br/>
<p>Comparing to previously noted run values (before optimization) area has increased and worst negative slack has become 0</p>
Capture -109
Capture -110
Capture -117
Capture -118
<br/>
<br/>
<br/>
<h4>8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.</h4>
<p>Now that our custom inverter is properly accepted in synthesis we can now run floorplan using following command</p>
<dl>  
  <dd>//Now we can run floorplan</dd>
  <dd>run_floorplan</dd>
</dl>
<p>Screenshots of command run is shown below</p>
Capture -119
Capture -120
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Since we are facing unexpected un-explainable error while using run_floorplan command, we can instead use the following set of commands shown below</p>
<dl>  
  <dd>//Follwing commands are alltogather sourced in "run_floorplan" command</dd>
  <dd>init_floorplan</dd>
  <dd>place_io</dd>
  <dd>tap_decap_or</dd>
</dl>
<p>Screenshots of command run is shown below</p>
Capture -121
Capture -122
Capture -123
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Now that floorplan is done we can do placement using following command</p>
<dl>  
  <dd>//Now we are ready to run placement</dd>
  <dd>run_placement</dd>
</dl>
<p>Screenshots of command run is shown below</p>
Capture -126
Capture -127
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Commands to load placement def in magic in another terminal</p>
<dl>  
  <dd>//Change directory to path containing generated placement def</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-12_14-09/results/placement/</dd>
  <dd>//Command to load the placement def in magic tool</dd>
  <dd>magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &</dd>
</dl>
<p>Screenshot of terminal is shown below</p>
Capture -128
<br/>
<br/>
<br/>
<p>Screenshot of placement def in magic is shown below</p>
Capture -129
<br/>
<br/>
<br/>
<p>Screenshot of custom inverter inserted in placement def with proper abutment is shown below</p>
Capture -130
<br/>
<br/>
<br/>
<p>Command for tkcon window to view internal layers of cells</p>
<dl>  
  <dd>//Command to view internal connectivity layers</dd>
  <dd>expand</dd>
</dl>
<p>Abutment of power pins with other cell from library clearly visible is shown below</p>
Capture -131
Capture -132
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<h4>9. Do Post-Synthesis timing analysis with OpenSTA tool.</h4>
<p>Since we are having 0 wns after improved timing run we will not do Post Synthesis timing analysis</p>
<p>If we want we can do Post Synthesis timing analysis but for that we should do another synthesis i.e. we will not use previous directory created in runs directory of picorv32a directory.</p>
<p>We will be creating another synthesis file  because we don't want to disturb our flow till now</p>
<h4>11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.</h4>
<p>Since we are not doing Post Synthesis timing analysis and we have not created new synthesis file.</p>
<p>So we don't need to replace new synthesis file as our old synthesis file is intact.</p>
<p>Now, we will continue from CTS</p>
<dl>  
  <dd>//Command to run cts</dd>
  <dd>run_cts</dd>
</dl>
<p>Screenshot of cts is shown below</p>
Capture -133
Capture -134
Capture -135
Capture -136
<br/>
<br/>
<br/>
<h4>12. Post-CTS OpenROAD timing analysis.</h4>
<p>Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD</p>
<dl>  
  <dd>//Command to run OpenROAD tool</dd>
  <dd>openroad</dd>
  <dd>//Reading lef file</dd>
  <dd>read_lef /openLANE_flow/designs/picorv32a/runs/20-12_14-09/tmp/merged.lef</dd>
  <dd>Command to run cts</dd>
  <dd>//Reading def file</dd>
  <dd>read_def /openLANE_flow/designs/picorv32a/runs/20-12_14-09/results/cts/picorv32a.cts.def</dd>
  <dd>//Creating an OpenROAD database to work with</dd>
  <dd>write_db pico_cts.db</dd>
  <dd>//Loading the created database in OpenROAD</dd>
  <dd>read_db pico_cts.db</dd>
  <dd>//Read netlist post CTS</dd>
  <dd>read_verilog /openLANE_flow/designs/picorv32a/runs/20-12_14-09/results/synthesis/picorv32a.synthesis_cts.v</dd>
  <dd>//Read library for design</dd>
  <dd>read_liberty $::env(LIB_SYNTH_COMPLETE)</dd>
  <dd>//Link design and library</dd>
  <dd>link_design picorv32a</dd>
  <dd>//Read in the custom sdc we created</dd>
  <dd>read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc</dd>
  <dd>//Setting all cloks as propagated clocks</dd>
  <dd>set_propagated_clock [all_clocks]</dd>
  <dd>//Check syntax of 'report_checks' command</dd>
  <dd>help report_checks</dd>
  <dd>//Generating custom timing report</dd>
  <dd>report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4</dd>
  <dd>//Exit to OpenLANE flow</dd>
  <dd>exit</dd>
</dl>
<p>Screenshots of commands run and timing report generated is shown below</p>
Capture -137
Capture -138
Capture -139
Capture -140
Capture -141
Capture -142
Capture -143
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<h4>13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.</h4>
<p>Commands to be run in OpenLANE flow to do OpenROAD timing analysis after changing CTS_CLK_BUFFER_LIST</p>
<dl>  
  <dd>//Checking current value of 'CTS_CLK_BUFFER_LIST'</dd>
  <dd>echo $::env(CTS_CLK_BUFFER_LIST)</dd>
    <dd>//Removing 'sky130_fd_sc_hd__clkbuf_1' from the list</dd>
  <dd>set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]</dd>
    <dd>//Checking current value of 'CTS_CLK_BUFFER_LIST'</dd>
  <dd>echo $::env(CTS_CLK_BUFFER_LIST)</dd>
    <dd>//Checking current value of 'CURRENT_DEF'</dd>
  <dd>echo $::env(CURRENT_DEF)</dd>
    <dd>//Setting def as placement def</dd>
  <dd>set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/20-12_14-09/results/placement/picorv32a.placement.def</dd>
    <dd>//Run CTS again</dd>
  <dd>run_cts</dd>
    <dd>//Checking current value of 'CTS_CLK_BUFFER_LIST'</dd>
  <dd>echo $::env(CTS_CLK_BUFFER_LIST)</dd>
    <dd>//Command to run OpenROAD tool</dd>
  <dd>openroad</dd>
    <dd>//Reading lef file</dd>
  <dd>read_lef /openLANE_flow/designs/picorv32a/runs/20-12_14-09/tmp/merged.lef</dd>
    <dd>//Reading def file</dd>
  <dd>read_def /openLANE_flow/designs/picorv32a/runs/20-12_14-09/results/cts/picorv32a.cts.def</dd>
    <dd>//Creating an OpenROAD database to work with</dd>
  <dd>write_db pico_cts1.db</dd>
    <dd>//Loading the created database in OpenROAD</dd>
  <dd>read_db pico_cts.db</dd>
    <dd>//Read netlist post CTS</dd>
  <dd>read_verilog /openLANE_flow/designs/picorv32a/runs/20-12_14-09/results/synthesis/picorv32a.synthesis_cts.v</dd>
    <dd>//Read library for design</dd>
  <dd>read_liberty $::env(LIB_SYNTH_COMPLETE)</dd>
    <dd>//Link design and library</dd>
  <dd>link_design picorv32a</dd>
    <dd>//Read in the custom sdc we created</dd>
  <dd>read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc</dd>
    <dd>//Setting all cloks as propagated clocks</dd>
  <dd>set_propagated_clock [all_clocks]</dd>
    <dd>//Generating custom timing report</dd>
  <dd>report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4</dd>
    <dd>//Report hold skew</dd>
  <dd>report_clock_skew -hold</dd>
    <dd>//Report setup skew</dd>
  <dd>report_clock_skew -setup</dd>
      <dd>//Exit to OpenLANE flow</dd>
  <dd>exit</dd>
      <dd>//Checking current value of 'CTS_CLK_BUFFER_LIST'</dd>
  <dd>echo $::env(CTS_CLK_BUFFER_LIST)</dd>
      <dd>//Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list</dd>
  <dd>set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]</dd>
      <dd>//Checking current value of 'CTS_CLK_BUFFER_LIST'</dd>
  <dd>echo $::env(CTS_CLK_BUFFER_LIST)</dd>
</dl>
<p>Screenshots of commands run and timing report generated is shown below</p>
Capture -144
Capture -145
Capture -146
Capture -147
Capture -148
Capture -149
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>

<h2>Section 5 - Final steps for RTL2GDS using tritonRoute and openSTA</h2>
<h3>Implementation</h3>
<h4>Task</h4>
<ol>
  <li> Perform generation of Power Distribution Network (PDN) and explore the PDN layout.</li>
  <li> Perfrom detailed routing using TritonRoute.</li>
  <li> Post-Route parasitic extraction using SPEF extractor.</li>
  <li> Post-Route OpenSTA timing analysis with the extracted parasitics of the route.</li>
</ol>
<h4>1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.</h4>
<p>Commands to perform all necessary stages up until now</p>
<dl>  
  <dd>//Change directory to openlane flow directory</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane</dd>
    <dd>//alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'</dd>
    <dd>//Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command</dd>
  <dd>docker</dd>
    <dd>//Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command</dd>
  <dd>./flow.tcl -interactive</dd>
    <dd>//Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow</dd>
  <dd>package require openlane 0.9</dd>
    <dd>//Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'</dd>
  <dd>prep -design picorv32a</dd>
    <dd>//Addiitional commands to include newly added lef to openlane flow merged.lef</dd>
  <dd>set lefs [glob $::env(DESIGN_DIR)/src/*.lef]</dd>
  <dd>add_lefs -src $lefs</dd>
    <dd>//Command to set new value for SYNTH_STRATEGY</dd>
  <dd>set ::env(SYNTH_STRATEGY) "DELAY 3"</dd>
    <dd>//Command to set new value for SYNTH_SIZING</dd>
  <dd>set ::env(SYNTH_SIZING) 1</dd>
    <dd>//Now that the design is prepped and ready, we can run synthesis using following command</dd>
  <dd>run_synthesis</dd>
    <dd>//Following commands are alltogather sourced in "run_floorplan" command</dd>
  <dd>init_floorplan</dd>
  <dd>place_io</dd>
  <dd>tap_decap_or</dd>
    <dd>//Now we are ready to run placement</dd>
  <dd>run_placement</dd>
    <dd>//Incase getting error</dd>
  <dd>unset ::env(LIB_CTS)</dd>
      <dd>//With placement done we are now ready to run CTS</dd>
  <dd>run_cts</dd>
      <dd>//Now that CTS is done we can do power distribution network</dd>
  <dd>gen_pdn</dd>
</dl>
<p>Screenshots of power distribution network run is shown below</p>
Capture -150
Capture -151
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Commands to load PDN def in magic in another terminal</p>
<dl>  
  <dd>//Change directory to path containing generated PDN def</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-12_14-09/tmp/floorplan/</dd>
  <dd>//Command to load the PDN def in magic tool</dd>
  <dd>magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 21-pdn.def &</dd>
</dl>
<p>Screenshots of terminal is shown below</p>
Capture -152
Capture -153
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Screenshots of PDN def is shown below</p>
Capture -154
Capture -155
Capture -156
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<h4>2. Perfrom detailed routing using TritonRoute and explore the routed layout.</h4>
<p>Command to perform routing</p>
<dl>  
  <dd>//Check value of 'CURRENT_DEF'</dd>
  <dd>echo $::env(CURRENT_DEF)</dd>
    <dd>//Check value of 'ROUTING_STRATEGY'</dd>
    <dd>echo $::env(ROUTING_STRATEGY)</dd>
  <dd>//Command for detailed route using TritonRoute</dd>
    <dd>run_routing</dd>
</dl>
<p>Screenshots of routing run is shown below</p>
Capture -157
Capture -158
Capture -159
Capture -160
Capture -161
Capture -162
Capture -163
Capture -164
Capture -165
Capture -166
Capture -167
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Commands to load routed def in magic in another terminal</p>
<dl>  
  <dd>//Change directory to path containing routed def</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-12_14-09/results/routing/</dd>
  <dd>//Command to load the routed def in magic tool</dd>
  <dd>magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &</dd>
</dl>
<p>Screenshots of terminal is shown below</p>
Capture -168
<br/>
<br/>
<br/>
<p>Screenshots of routed def is shown below</p>
Capture -169
Capture -170
Capture -171
Capture -172
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<p>Screenshot of fast route guide present in openlane/designs/picorv32a/runs/20-12_14-09/tmp/routing directory is shown below</p>
Capture -173
Capture -174
<br/>
<br/>
<br/>
<h4>3. Post-Route parasitic extraction using SPEF extractor.</h4>
<p>We don't need to follow this step</p>
<h4>4. Post-Route OpenSTA timing analysis with the extracted parasitics of the route.</h4>
<p>Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD</p>
<dl>  
  <dd>//Command to run OpenROAD tool</dd>
  <dd>openroad</dd>
  <dd>//Reading lef file</dd>
  <dd>read_lef /openLANE_flow/designs/picorv32a/runs/20-12_14-09/tmp/merged.lef</dd>
    <dd>//Reading def file</dd>
  <dd>read_def /openLANE_flow/designs/picorv32a/runs/20-12_14-09/results/routing/picorv32a.def</dd>
    <dd>//Creating an OpenROAD database to work with</dd>
  <dd>write_db pico_route.db</dd>
    <dd>//Loading the created database in OpenROAD</dd>
  <dd>read_db pico_route.db</dd>
    <dd>//Read netlist post CTS</dd>
  <dd>read_verilog /openLANE_flow/designs/picorv32a/runs/20-12_14-09/results/synthesis/picorv32a.synthesis_preroute.v</dd>
    <dd>//Read library for design</dd>
  <dd>read_liberty $::env(LIB_SYNTH_COMPLETE)</dd>
    <dd>//Link design and library</dd>
  <dd>link_design picorv32a</dd>
    <dd>//Read in the custom sdc we created</dd>
  <dd>read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc</dd>
    <dd>//Setting all cloks as propagated clocks</dd>
  <dd>set_propagated_clock [all_clocks]</dd> 
    <dd>//Read SPEF</dd>
  <dd>read_spef /openLANE_flow/designs/picorv32a/runs/20-12_14-09/results/routing/picorv32a.spef</dd>
      <dd>//Generating custom timing report</dd>
  <dd>report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4</dd>
      <dd>//Exit to OpenLANE flow</dd>
  <dd>exit</dd>
</dl>
<p>Screenshots of commands run and timing report generated is shown below</p>
Capture -175
Capture -176
Capture -177
Capture -178
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
