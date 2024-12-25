<p align="center">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/585101e853b21b8e000c5382b3ad6a1703337a4d/Screenshots/Capture%20-0.JPG" alt="Capture -0">
</p>
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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-2.JPG" alt="Capture -2">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-3.JPG" alt="Capture -3">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-4.JPG" alt="Capture -4">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-5.JPG" alt="Capture -5">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-6.JPG" alt="Capture -6">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-7.JPG" alt="Capture -7">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-8.JPG" alt="Capture -8">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-13.JPG" alt="Capture -13">

<h4>2. Calculate the flop ratio.</h4>
<p>Screenshots of synthesis statistics report file with required values highlighted is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-9.JPG" alt="Capture -9">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-10.JPG" alt="Capture -10">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-11.JPG" alt="Capture -11">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-12.JPG" alt="Capture -12">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-14.JPG" alt="Capture -14">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-15.JPG" alt="Capture -15">

<h4>2. Calculate the die area in microns from the values in floorplan def.</h4>
<p>Screenshots of contents of floorplan def is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-16.JPG" alt="Capture -16">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-17.JPG" alt="Capture -17">

<p>Screenshots of floorplan def in magic is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-18.JPG" alt="Capture -18">

<p>Screenshots of Equidistant placement of ports is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-19.JPG" alt="Capture -19">

<p>Screenshots of Port layer as set through config.tcl is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-20.JPG" alt="Capture -20">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-21.JPG" alt="Capture -21">

<p>Screenshots of Decap Cells and Tap Cells is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-22.JPG" alt="Capture -22">

<p>Screenshots of Diogonally equidistant Tap cells is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-23.JPG" alt="Capture -23">

<p>Screenshots of Unplaced standard cells at the origin is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-24.JPG" alt="Capture -24">

<h4>4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.</h4>
<p>Command to run placement</p>
<dl>  
  <dd>//Congestion aware placement by default</dd>
  <dd>run_placement</dd>
</dl>
<p>Screenshots of placement run is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-25.JPG" alt="Capture -25">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-26.JPG" alt="Capture -26">

<h4>5. Load generated placement def in magic tool and explore the placement.</h4>
<p>Commands to load placement def in magic in another terminal is shown below</p>
<dl>  
  <dd>//Change directory to path containing generated placement def</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-12_14-09/results/placement/</dd>
  <dd>//Command to load the placement def in magic tool</dd>
  <dd>magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &</dd>
</dl>
<p>Screenshots of floorplan def in magic is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-27.JPG" alt="Capture -27">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-28.JPG" alt="Capture -28">

<p>Standard cells legally placed is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-29.JPG" alt="Capture -29">


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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-30.JPG" alt="Capture -30">

<p>Screenshots of terminal after git clone</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-31.JPG" alt="Capture -31">

<p>Screenshots of vsdstdcellesign directory before copying tech file</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-32.JPG" alt="Capture -32">

<p>Screenshots of terminal showing how to copy tech file in vsdstdcelldesign directory</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-33.JPG" alt="Capture -33">

<p>Screenshots of vsdstdcellesign directory after copying tech file</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-34.JPG" alt="Capture -34">

<h4>2. Load the custom inverter layout in magic and explore.</h4>
<p>Command to open custom inverter layout in magic is shown below</p>
<dl>  
  <dd>//Command to open custom inverter layout in magic</dd>
  <dd>magic -T sky130A.tech sky130_inv.mag &</dd>
</dl>
<p>Screenshot of custom inverter layout in magic is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-35.JPG" alt="Capture -35">

<p>Screenshot of NMOS identified is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-36.JPG" alt="Capture -36">

<p>Screenshot of PMOS identified is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-37.JPG" alt="Capture -37">

<p>Screenshot of Output Y connectivity to PMOS and NMOS drain verified is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-38.JPG" alt="Capture -38">

<p>Screenshot of PMOS source connectivity to VDD (here VPWR) verified is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-39.JPG" alt="Capture -39">

<p>Screenshot of NMOS source connectivity to VSS (here VGND) verified is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-40.JPG" alt="Capture -40">

<p>Screenshot of Polysilicon identified is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-41.JPG" alt="Capture -41">

<p>Screenshot of knowingly Deleted part of layout see DRC error is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-42.JPG" alt="Capture -42">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-43.JPG" alt="Capture -43">

<p>Screenshot vsdstdcelldesign directory after each command in tkcon window is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-44.JPG" alt="Capture -44">

<p>Screenshot of created spice file is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-45.JPG" alt="Capture -45">

<h4>4. Editing the spice model file for analysis through simulation.</h4>
<p>Measuring unit distance in layout grid as shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-46.JPG" alt="Capture -46">

<p>Final edited spice file ready for ngspice simulation is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-47.JPG" alt="Capture -47">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-48.JPG" alt="Capture -48">

<h4>5. Post-layout ngspice simulations.</h4>
<p>Commands for ngspice simulation is shown below</p>
<dl>  
  <dd>//Command to directly load spice file for simulation to ngspice</dd>
  <dd>ngspice sky130_inv.spice</dd>
  <dd>//Now that we have entered ngspice with the simulation spice file loaded we just have to load the plot</dd>
  <dd>plot y vs time a</dd>
</dl>
<p>Screenshots of ngspice run is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-49.JPG" alt="Capture -49">

<p>Screenshots of command to plot graph in ngspice is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-50.JPG" alt="Capture -50">

<p>Screenshot of generated plot is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-51.JPG" alt="Capture -51">

<p>Rise transition time calculation is done as shown below</p>
<p align="center">
Rise transition time = Time taken for output to rise to 80% - Time taken for output to rise to 20%
  20% of output = 0.2 * 3.3V = 660mV
  80% of output = 0.8 * 3.3V = 2.64V
</p>
<p>20% of output screenshot and values of time & voltage is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-52.JPG" alt="Capture -52">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-53.JPG" alt="Capture -53">

<p>80% of output screenshot and values of time & voltage is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-54.JPG" alt="Capture -54">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-55.JPG" alt="Capture -55">

<p align="center">Rise transition time = 2.2458 - 2.18197 = 0.06383 ns </p>
<p>Fall transition time calculation is done as shown below</p>
<p align="center">
Fall transition time = Time taken for output to fall to 20% - Time taken for output to fall to 80%
  20% of output = 0.2 * 3.3V = 660mV
  80% of output = 0.8 * 3.3V = 2.64V
</p>
<p>20% of output screenshot and values of time & voltage is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-56.JPG" alt="Capture -56">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-57.JPG" alt="Capture -57">

<p>80% of output screenshot and values of time & voltage is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-58.JPG" alt="Capture -58">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-59.JPG" alt="Capture -59">

<p align="center">Fall transition time = 4.09512 - 4.05258 = 0.04254 ns</p>
<p>Rise cell delay calculation is done as shown below</p>
<p align="center">
Rise cell delay = Time taken for output to rise to 50% - Time taken for input to fall to 50%
  50% of 3.3V = 0.5 * 3.3V = 2.64V
</p>
<p>50% of input and output screenshot and values of time & voltage is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-60.JPG" alt="Capture -60">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-61.JPG" alt="Capture -61">

<p align="center">Rise cell delay = 2.21091 - 2.15009 = 0.06082 ns </p>
<p>Fall cell delay calculation is done as shown below</p>
<p align="center">
Fall cell delay = Time taken for output to fall to 50% - Time taken for input to rise to 50%
  50% of 3.3V = 0.5 * 3.3V = 2.64V
</p>
<p>50% of input and output screenshot and values of time & voltage is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-62.JPG" alt="Capture -62">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-63.JPG" alt="Capture -63">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-64.JPG" alt="Capture -64">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-65.JPG" alt="Capture -65">

<p>Screenshots of Screenshot of .magicrc file is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-66.JPG" alt="Capture -66">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-67.JPG" alt="Capture -67">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-68.JPG" alt="Capture -68">

<p>Screenshots of command "magic -d XR" is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-69.JPG" alt="Capture -69">

<b>Incorrectly implemented poly.9 simple rule correction</b>
<p>Screenshot of poly rules is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-70.JPG" alt="Capture -70">

<p>Incorrectly implemented poly.9 rule no drc violation even though spacing < 0.48u is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-71.JPG" alt="Capture -71">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-72.JPG" alt="Capture -72">

<p>New commands inserted in sky130A.tech file to update drc is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-73.JPG" alt="Capture -73">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-74.JPG" alt="Capture -74">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-75.JPG" alt="Capture -75">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-76.JPG" alt="Capture -76">

<b>Incorrectly implemented difftap.2 simple rule correction</b>
<p>Screenshot of difftap rules is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-77.JPG" alt="Capture -77">

<p>Incorrectly implemented difftap.2 rule no drc violation even though spacing < 0.42u is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-78.JPG" alt="Capture -78">

<p>New commands inserted in sky130A.tech file to update drc is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-79.JPG" alt="Capture -79">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-80.JPG" alt="Capture -80">

<b>Incorrectly implemented nwell.4 complex rule correction</b>
<p>Screenshot of nwell rules is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-81.JPG" alt="Capture -81">

<p>Incorrectly implemented nwell.4 rule no drc violation even though no tap present in nwell is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-82.JPG" alt="Capture -82">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-83.JPG" alt="Capture -83">

<p>New commands inserted in sky130A.tech file to update drc is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-84.JPG" alt="Capture -84">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-85.JPG" alt="Capture -85">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/483d7af70c82a47b1a79e315dd89ff2a9db47392/Screenshots/Capture%20-86.JPG" alt="Capture -86">


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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-87.JPG" alt="Capture -87">

<p>Open tracks.info file as shown in screenshot below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-88.JPG" alt="Capture -88">

<p>Screenshot of tracks.info of sky130_fd_sc_hd is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-89.JPG" alt="Capture -89">

<p>Commands for tkcon window to set grid as tracks of locali layer</p>
<dl>  
  <dd>//Get syntax for grid command</dd>
  <dd>help grid</dd>
  <dd>//Set grid values accordingly</dd>
  <dd>grid 0.46um 0.34um 0.23um 0.17um</dd>
</dl>
<p>Screenshot of commands run is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-90.JPG" alt="Capture -90">

<p>Screenshot of Condition 1 verified is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-91.JPG" alt="Capture -91">

<p>Screenshot of Condition 2 verified is shown below</p>
<p align="center">Horizontal track pitch = 0.46 um<br>
Width of standard cell = 3 * 0.46 = 138 um
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-92.JPG" alt="Capture -92">
</p>

<p>Screenshot of Condition 3 verified is shown below</p>
<p align="center">Horizontal track pitch = 0.34 um<br>
Width of standard cell = 8 * 0.34 = 2.72 um
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-93.JPG" alt="Capture -93">
</p>

<h4>2. Save the finalized layout with custom name and open it.</h4>
<p>Command for tkcon window to save the layout with custom name is shown below</p>
<dl>  
  <dd>//Command to save as</dd>
  <dd>save sky130_vsdinv.mag</dd>
</dl>
<p>Screenshot of tkcon window and terminal with new file created is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-94.JPG" alt="Capture -94">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-95.JPG" alt="Capture -95">

<p>Command to open the newly saved layout is shown below</p>
<dl>  
  <dd>//Command to open custom inverter layout in magic</dd>
  <dd>magic -T sky130A.tech sky130_vsdinv.mag &</dd>
</dl>
<p>Screenshot of newly saved layout is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-96.JPG" alt="Capture -96">

<h4>3. Generate lef from the layout.</h4>
<p>Command for tkcon window to write lef is shown below</p>
<dl>  
  <dd>//lef command</dd>
  <dd>lef write</dd>
</dl>
<p>Screenshot of command run and terminal with new lef file created is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-97.JPG" alt="Capture -97">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-98.JPG" alt="Capture -98">

<p>Screenshot of newly created file is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-99.JPG" alt="Capture -99">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-100.JPG" alt="Capture -100">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-101.JPG" alt="Capture -101">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-102.JPG" alt="Capture -102">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-103.JPG" alt="Capture -103">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-104.JPG" alt="Capture -104">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-105.JPG" alt="Capture -105">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-106.JPG" alt="Capture -106">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-107.JPG" alt="Capture -107">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-108.JPG" alt="Capture -108">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-109.JPG" alt="Capture -109">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-110.JPG" alt="Capture -110">

<h4>7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.</h4>
<p>Noting down current design values generated before modifying parameters to improve timing is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-111.JPG" alt="Capture -111">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-112.JPG" alt="Capture -112">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-113.JPG" alt="Capture -113">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-114.JPG" alt="Capture -114">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-115.JPG" alt="Capture -115">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-116.JPG" alt="Capture -116">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-117.JPG" alt="Capture -117">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-118.JPG" alt="Capture -118">

<p>Screenshot of merged.lef in tmp directory with our custom inverter as macro is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-124.JPG" alt="Capture -124">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-125.JPG" alt="Capture -125">

<p>Comparing to previously noted run values (before and after optimization) it is observed that area has increased and worst negative slack has become 0</p>
<p align="center">
Before Optimization
</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-109.JPG" alt="Capture -109">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-110.JPG" alt="Capture -110">
<p align="center">
After Optimization
</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-117.JPG" alt="Capture -117">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-118.JPG" alt="Capture -118">

<h4>8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.</h4>
<p>Now that our custom inverter is properly accepted in synthesis we can now run floorplan using following command</p>
<dl>  
  <dd>//Now we can run floorplan</dd>
  <dd>run_floorplan</dd>
</dl>
<p>Screenshots of command run is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-119.JPG" alt="Capture -119">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-120.JPG" alt="Capture -120">

<p>Since we are facing unexpected un-explainable error while using run_floorplan command, we can instead use the following set of commands shown below</p>
<dl>  
  <dd>//Follwing commands are alltogather sourced in "run_floorplan" command</dd>
  <dd>init_floorplan</dd>
  <dd>place_io</dd>
  <dd>tap_decap_or</dd>
</dl>
<p>Screenshots of command run is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-121.JPG" alt="Capture -121">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-122.JPG" alt="Capture -122">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-123.JPG" alt="Capture -123">

<p>Now that floorplan is done we can do placement using following command</p>
<dl>  
  <dd>//Now we are ready to run placement</dd>
  <dd>run_placement</dd>
</dl>
<p>Screenshots of command run is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-126.JPG" alt="Capture -126">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-127.JPG" alt="Capture -127">

<p>Commands to load placement def in magic in another terminal</p>
<dl>  
  <dd>//Change directory to path containing generated placement def</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-12_14-09/results/placement/</dd>
  <dd>//Command to load the placement def in magic tool</dd>
  <dd>magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &</dd>
</dl>
<p>Screenshot of terminal is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-128.JPG" alt="Capture -128">

<p>Screenshot of placement def in magic is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-129.JPG" alt="Capture -129">

<p>Screenshot of custom inverter inserted in placement def with proper abutment is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-130.JPG" alt="Capture -130">

<p>Command for tkcon window to view internal layers of cells</p>
<dl>  
  <dd>//Command to view internal connectivity layers</dd>
  <dd>expand</dd>
</dl>
<p>Abutment of power pins with other cell from library clearly visible is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-131.JPG" alt="Capture -131">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-132.JPG" alt="Capture -132">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x133.JPG" alt="Capture -133">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x134.JPG" alt="Capture -134">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x135.JPG" alt="Capture -135">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x136.JPG" alt="Capture -136">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x137.JPG" alt="Capture -137">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x138.JPG" alt="Capture -138">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x139.JPG" alt="Capture -139">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x140.JPG" alt="Capture -140">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x141.JPG" alt="Capture -141">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x142.JPG" alt="Capture -142">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x143.JPG" alt="Capture -143">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x144.JPG" alt="Capture -144">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x145.JPG" alt="Capture -145">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x146.JPG" alt="Capture -146">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x147.JPG" alt="Capture -147">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x148.JPG" alt="Capture -148">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x149.JPG" alt="Capture -149">


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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x150.JPG" alt="Capture -150">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x151.JPG" alt="Capture -151">

<p>Commands to load PDN def in magic in another terminal</p>
<dl>  
  <dd>//Change directory to path containing generated PDN def</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-12_14-09/tmp/floorplan/</dd>
  <dd>//Command to load the PDN def in magic tool</dd>
  <dd>magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 21-pdn.def &</dd>
</dl>
<p>Screenshots of terminal is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x152.JPG" alt="Capture -152">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x153.JPG" alt="Capture -153">

<p>Screenshots of PDN def is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x154.JPG" alt="Capture -154">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x155.JPG" alt="Capture -155">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x156.JPG" alt="Capture -156">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x157.JPG" alt="Capture -157">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x158.JPG" alt="Capture -158">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x159.JPG" alt="Capture -159">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x160.JPG" alt="Capture -160">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x161.JPG" alt="Capture -161">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x162.JPG" alt="Capture -162">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x163.JPG" alt="Capture -163">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x164.JPG" alt="Capture -164">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x165.JPG" alt="Capture -165">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x166.JPG" alt="Capture -166">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x167.JPG" alt="Capture -167">

<p>Commands to load routed def in magic in another terminal</p>
<dl>  
  <dd>//Change directory to path containing routed def</dd>
  <dd>cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/20-12_14-09/results/routing/</dd>
  <dd>//Command to load the routed def in magic tool</dd>
  <dd>magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &</dd>
</dl>
<p>Screenshots of terminal is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x168.JPG" alt="Capture -168">

<p>Screenshots of routed def is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x169.JPG" alt="Capture -169">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x170.JPG" alt="Capture -170">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x171.JPG" alt="Capture -171">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x172.JPG" alt="Capture -172">

<p>Screenshot of fast route guide present in openlane/designs/picorv32a/runs/20-12_14-09/tmp/routing directory is shown below</p>
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x173.JPG" alt="Capture -173">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x174.JPG" alt="Capture -174">

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
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x175.JPG" alt="Capture -175">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x176.JPG" alt="Capture -176">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x177.JPG" alt="Capture -177">
<img src="https://github.com/saurabhsharma-gh/Digital-VLSI-System-Design-and-SoC-Planning-Images/blob/78eddd78b009df6049ae4c08a09d0257a35803d4/Screenshots/Capture%20-x178.JPG" alt="Capture -178">

<h2>Certificate</h2>
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
<h2>Acknowledgements</h2>
<ul>
  <li> Kunal Ghosh : Co-founder, VSD Corp. Pvt. Ltd.</li>
  <li> Nickson P Jose : Physical Design Engineer, Intel Corporation</li>
  <li> R Timothy Edwards : Senior Vice President of Analog and Design, efabless Corporation</li>
</ul>
