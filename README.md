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
<p>The screenshots of above steps is shown below</p>

