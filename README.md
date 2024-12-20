# Digital-VLSI-System-Design-and-SoC-Planning
2 Week workshop on “Digital VLSI System Design and SoC Planning” by Kunal Ghosh, in which picorv32a processor was designed from RTL to GDS-II in OpenLane flow, which comprises of various open source EDA tools for Synthesis and Physical Design. In the design SkyWater SKY130 PDK was used.
## Section 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK
### Implementation 
#### Task
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
<p>The screenshots of above steps and synthes run is shown below</p>
<br/>
<br/>
<br/>
<h4>2. Calculate the flop ratio.</h4>
<p>Screenshots of synthesis statistics report file with required values highlighted is shown below</p>
<br/>
<br/>
<br/>
<p>Calculation of Flop Ratio and DFF % from synthesis statistics report file</p>
<p align="center">
Flop Ratio = 1613 / 14876  = 0.108429685<br/>
  Percentage of DFF's = 0.108429685 ∗ 100
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
<br/>
<br/>
<br/>
<h4>2. Calculate the die area in microns from the values in floorplan def.</h4>
<p>Screenshots of contents of floorplan def is shown below</p>
<br/>
<br/>
<br/>
<p>According to floorplan def</p>
<p align="center">
Flop Ratio = (Number of D Flip Flops) / (Total Number of Cells)<br/>
Percentage of DFF's = Flop Ratio * 100
</p>
<h4>3. Load generated floorplan def in magic tool and explore the floorplan.</h4>
<p>Commands to load floorplan def in magic in another terminal</p>
<dl>  
  <dd>//Change directory to path containing generated floorplan def</dd>
  <dd>--------------------------------------------/openlane</dd>
  <dd>//Command to load the floorplan def in magic tool</dd>
  <dd>-----------------------------------------------</dd>
</dl>
<p>Screenshots of floorplan def in magic is shown below</p>
<br/>
<br/>
<br/>
<p>Screenshots of Equidistant placement of ports is shown below</p>
<br/>
<br/>
<br/>
<p>Screenshots of Port layer as set through config.tcl is shown below</p>
<br/>
<br/>
<br/>
<p>Screenshots of Decap Cells and Tap Cells is shown below</p>
<br/>
<br/>
<br/>
<p>Screenshots of Diogonally equidistant Tap cells is shown below</p>
<br/>
<br/>
<br/>
<p>Screenshots of Unplaced standard cells at the origin is shown below</p>
<br/>
<br/>
<br/>
<h4>4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.</h4>
<p>Command to run placement</p>
<dl>  
  <dd>//Congestion aware placement by default</dd>
  <dd>run_placement/openlane</dd>
</dl>
<p>Screenshots of placement run is shown below</p>
<br/>
<br/>
<br/>
<h4>5. Load generated placement def in magic tool and explore the placement.</h4>
<p>Commands to load placement def in magic in another terminal is shown below</p>
<dl>  
  <dd>//Change directory to path containing generated placement def</dd>
  <dd>--------------------------------------------/openlane</dd>
  <dd>//Command to load the placement def in magic tool</dd>
  <dd>-----------------------------------------------</dd>
</dl>
<p>Screenshots of floorplan def in magic is shown below</p>
<br/>
<br/>
<br/>
<p>Standard cells legally placed is shown below</p>
<br/>
<br/>
<br/>
<h2>Section 3 - Design library cell using Magic Layout and ngspice characterization</h2>
<h3>Implementation</h3>
<h4>Task</h4>
