**Day 0: Important Links**

VSD-IAT (vsdiat.com)

nickson-jose/vsdstdcelldesign: This repository contains all the information needed to run RTL2GDSII flow using openlane flow. Apart from that, it also contain procedures on how to create a custom LEF file and plugging it into an openlane flow. (github.com)


**Day 1:**

Flop ratio = 1613/14876 = 10.84% (visit: Item number 16)

1.	Opened the flow.tcl in vim   
 ![Picture1](https://github.com/user-attachments/assets/60418a76-bdcd-4bb6-ab9e-0e564d94a9e2)

2. Opened the working folder & opened the tech file & checked in vim ![image](https://github.com/user-attachments/assets/3a6006d5-f3e8-4466-ab70-82e1b63f70d7)
![image](https://github.com/user-attachments/assets/f70b2660-c848-44a7-b5c8-95d9eba54e4d)

3. Ran the commands below in with docker in the working directory ![image](https://github.com/user-attachments/assets/44666e68-e232-4dd6-8d89-87927f7a34e9)

4. Opened the working directory designs ![image](https://github.com/user-attachments/assets/a28062da-ecbb-4701-886f-3f2dccd3e9ee)

5. Opened the config.tcl in vim & checked the period other items ![image](https://github.com/user-attachments/assets/94aa6733-bbfb-4c13-98b2-789ee8a062d3)

6. Opened the sky130A_sky130_fd_sc_hd_config.tcl file & checked the period other items ![image](https://github.com/user-attachments/assets/1e5d3b70-68a1-4669-adf9-f25a45a54feb)

7. Ran the command prep -design picorv32a & found that the run folder is created in the picorv32a design folder ![image](https://github.com/user-attachments/assets/404b5418-9339-4a56-a1ca-a9f9f9c57f44)

8. Went to the design folder and did ls -lrt to check the folders created. ![image](https://github.com/user-attachments/assets/e7e07e5a-96dd-4e92-9e8c-412247f19d4a)

9. Opened the merged.lef file in vim & checked the via & metal information in the file ![image](https://github.com/user-attachments/assets/67c44192-4147-4e30-8d5a-a52814b328eb) ![image](https://github.com/user-attachments/assets/0d0c5205-b9c5-47af-b4bd-765056b0d9c7)

 
10. Opened the config.tcl inside runs folder for today’s run in vim ![image](https://github.com/user-attachments/assets/d608fc0a-a8c2-4e82-b1c2-9c20aefd61ac) ![image](https://github.com/user-attachments/assets/f51a9bc1-3634-4993-b6f9-ee0aeb24fc34)


11. Checked the CORE_UTIL parameter which is 35% ![image](https://github.com/user-attachments/assets/480344cf-9540-4210-ab07-590e7ed12ce1)

12. Checked the cmd.log file ![image](https://github.com/user-attachments/assets/2868bd99-acdd-43ed-972b-f0245aaea381)

13. Ran the run_synthesis in the command line ![image](https://github.com/user-attachments/assets/f84851a4-1fd1-442c-9455-b8a107a0e6c6) ![image](https://github.com/user-attachments/assets/b565e351-0f4a-405b-b63a-a7314598f725)


14. Went & checked the openlane website & the youtube video links mentioned in the video lecture ![image](https://github.com/user-attachments/assets/89dc860e-7380-49c4-8315-b4db996dbf21) ![image](https://github.com/user-attachments/assets/0a0a742a-2383-4aa6-8750-be57435d2154)


15. Checked the synthesis & found that is completed successfully ![image](https://github.com/user-attachments/assets/c4d0c388-57ca-4b58-871b-124ddd0b248c)

16. Opened the stat file in the report folder to find out the flop ratio Flop ratio = 1613/14876 = 10.84% ![image](https://github.com/user-attachments/assets/c5596d70-7af4-42a8-944c-acf1455a74b6) ![image](https://github.com/user-attachments/assets/9fb18303-5856-492c-b9e2-0aa2ccdb7253)


17. Opened the timing file checked it in vim ![image](https://github.com/user-attachments/assets/a541f4df-fb56-498d-84a7-79f41a972672) ![image](https://github.com/user-attachments/assets/d8e19a61-0a7f-4438-b2c7-044a9beec05f)


**Day 2:**  

**1.	Chip floor planning considerations**

**a.	Utilization factor & aspect ratio**
  
  i.	Core – inner most area, die – outer area
  
  ii.	Std cell – 1 unit X 1 unit
  
  iii.	All logic cells are converted into rectangular boxes based on the dimensions of the cells & calculate the area occupied by the netlist on a silicon wafer (excluding the wiring area & buffer area requirements)
 
  iv.	utilization factor is Area occupied by the netlist/total core area of the core, usually this is 50%-60% utilization factor, the additional area is used for buffers. 
  
  v.	aspect ratio = Height/Width, 1 = square others rectangle

**b.	concept of preplaced cells**
  
  i.	An example of utilization factor =0.25
  
  ii.	Preplaced cells – an example with a section of combinational logic designed and reused is discussed as an example. It is also divided into two sections (cut1 & cut2) and made two blocks out of it (Block 1 & Block 2). The blocks once implemented can be reused in same or different designs as black boxes later. Each block can be treated as an IP or a module also. Instantiating the same block multiple times in the same design is also possible. Examples of IP include Memory, Clock gating cells, comparator, Mux etc., can be implemented once and can be re-used or instantiated later as a black box modules. The placement of these preplaced cells is fixed in the early design itself and this initial arrangement of these IP’s in a chip is known as Floorplanning. This is done before the automated place & routing. 

**c.	Decaps**
 
  i.	Block a, b, and c are preplaced cells in an example and the requirement for decaps are discussed. Decaps are important to reduce the ground bounce. 
 
  ii.	Supply voltage droop can cause the logic go into undefined regions. In noise margin, if the logic 1 has to be within Voh & Vih and logic 0 voltage has to be within Vil & Vol
  
  iii.	Decaps reduce the voltage drop caused due to high frequency switching of the cells by providing the fast charge near the cells reducing the voltage droop & ground bounce. 

**d.	Power Planning**
 
  i.	A 16 bit bus example is discussed to explain the ground bounce & voltage droop issues
  
  ii.	To avoid these issues, power is routed as a grid for VDD & VSS

**e.	Pin placement & logical cell blockage**
 
  i.	Connectivity information is defined in netlist & coded in VHDL/verilog
 
  ii.	The area between the core and die is filled with IO pins
 
  iii.	Front end team defines the netlist connectivity using VHDL/Verilog, back end team defines the placement of the pin placement. Usually left (input pins), right (output pins), but not a fixed rule, top and bottom can be used for input and output also.
 
  iv.	The pin blocks are bigger than the normal IO pins to make sure that they have the least resistance path
  
  v.	Logical cell placement blockage is added to avoid the automated placement & routing tool not to place any cells there
  
  vi.	Now the floorplan is ready for placement & routing

**f.	Floor planning using OpenLane**
 
 i.	The stage after synthesis is floor planning
 
 ii.	Standard cells placement happens in placement stage

iii.	Went inside the folder for configuration and checked the README.md  

![image](https://github.com/user-attachments/assets/cb0f5453-25f1-4547-8b70-60b78c9d6e80) 
![image](https://github.com/user-attachments/assets/652fd8b3-ff25-4894-83c2-b8fcf0c93902) ![image](https://github.com/user-attachments/assets/e21865b8-1544-44dd-9aca-90976d0d2f0f)

iv.	Opened the floorplan.tcl file to check the settings 

![image](https://github.com/user-attachments/assets/72bd46cf-6542-4e9e-9d80-1e3229ea3dc0)

v.	Opened the design folder and checked the config.tcl file 

![image](https://github.com/user-attachments/assets/7498fa9c-dd49-47b8-ace2-de369af60d7f)

vi.	Opened the design specifi config file, 

![image](https://github.com/user-attachments/assets/ed4b3242-8d8f-43d6-9894-75701a64535e)

vii.	In OpenLane flow the vertical & horizontal metal layers are one more than what we specify

viii.	Ran the command run_floorplan 

![image](https://github.com/user-attachments/assets/be8054a0-ef85-45d5-b23c-ffc9767798fb) 
![image](https://github.com/user-attachments/assets/31c6dabb-1857-4f50-a34f-3cdc15ce0a41)

ix.	Opend the def file after floor plan 

![image](https://github.com/user-attachments/assets/cc4aee73-be27-4ce9-a44a-dd785c8b2302) 
![image](https://github.com/user-attachments/assets/d0262522-4e3d-49f4-bdb5-957b48d7a844)

x.	Opened the def file in magic as shown in the figure below 

![image](https://github.com/user-attachments/assets/9c153e4e-5c07-4971-8ccd-f9ee1f546d70) 
![image](https://github.com/user-attachments/assets/d1a9e194-2978-4362-ae1a-42414a668ad6)

xi.	Zoomed in using left click, right click, then z. Used v to go back 

![image](https://github.com/user-attachments/assets/55e9dcf0-f640-4532-b4a6-3fcb6c7b47ff) 
![image](https://github.com/user-attachments/assets/dffeac63-1123-48d7-ac6c-5aa84e245d46) 
![image](https://github.com/user-attachments/assets/9505c18c-752c-4f6f-8d9c-4137c206acc2)

xii.	Kept the mouse on one of the IO pins and pressed s and typed what in the tcl command window & found that the IO pin is in metal3 layer. 

![image](https://github.com/user-attachments/assets/858e282a-9945-49e2-b452-c0af3a99e7d1)

xiii.	Went to the bottom of the die and selected a bottom IO pin and found that it is connected to metal2 

![image](https://github.com/user-attachments/assets/79f0e56c-4646-4281-bbca-ca9193f6c11b)

xiv.	Selected one of the endcap cells checked the details 

![image](https://github.com/user-attachments/assets/d7cc4a9f-ba3d-4297-b1a2-6ef66ad1976a)

xv.	Checked a tapcell which is used for preventing latchup issues. They connect the p-substrate to VSS & nwell to VDD. 

![image](https://github.com/user-attachments/assets/68640685-7de8-454f-b098-bb617968c820)

xvi.	Checked the standard cells placed at the bottom left corner of the die 

![image](https://github.com/user-attachments/assets/01bd129c-bba9-4bde-8e29-0a823cf9a32e)

**2.	Library Binding & Placement**

**a.	Netlist binding & initial place design**

i.	Library contains the information on the size & timing of the standard cells & IPs/macros

ii.	Same standard cells can have multiple sizes based on the drive strength of the cells

iii.	If we place the cells very close to the others (abutment), the cell delay is minimal, otherwise, we may have to use buffers if the distance between the two cells is big.

**b.	Optimize placement using estimated wire length & capacitance**

i.	So, if two cells are far away from each other, the wire resistance & capacitance is very high causing very high RC delay

ii.	Slew depends upon the capacitance value & high capacitance values will produce bad slew

**c.	Final Optimization**

i.	Abutment is preferred for critical paths since the delay between the cells is negligible and the circuit can work extremely fast.

**d.	Need for libraries & characterization**

i.	Library characterization & modeling: Logic synthesis -> Floorplanning -> Placement -> CTS -> Routing -> STA 

ii.	One thing is common in all these stages – gates/cells

iii.	In each of the ASIC design flow needs to have the library information on the cells

**e.	Congestion Aware placement using RePIAce**

i.	After floorplan, next stage is placement stage

ii.	Two sub-stages for placement: 1. Global placement (coarse & no legalization) 2. Detailed placement (legalization happens in detailed placement)

iii.	Legalization: Cells should be exactly inside the rows, no overlap on other cells, should be abutted, important from timing point of view

iv.	The command run_placement is performed. Wire length reduction is the focus here. 

![image](https://github.com/user-attachments/assets/a91c7011-ee9c-449a-a5df-307084afde9e)
![image](https://github.com/user-attachments/assets/8cdc3978-9687-437f-9bbe-e88c4724fb46)
![image](https://github.com/user-attachments/assets/44a825bc-03e9-43ad-8b28-1fa24c2db36f)
![image](https://github.com/user-attachments/assets/3010019e-1862-4d5f-94c4-f8167fe96b9a)

v.	Opened the def in magic 

![image](https://github.com/user-attachments/assets/6ea9259d-bf41-48ee-80e1-a120883da4a5)
![image](https://github.com/user-attachments/assets/d9424c7d-ebbf-4480-bab8-8f90052c5534)

vi.	Tried select & what on couple of instances 

![image](https://github.com/user-attachments/assets/b6541b08-684b-4e44-810a-23f3d9d009a2)

vii.	Power ground generation will be after CTS


**3.	Cell Design & Characterization Flow**

a.	Inputs for cell design flow

i.	Library is where the information related to standard cells, macros/IPs, decap cells are present

ii.	Biggest buff will have highest drive strength & higher threshold voltage which in turn determines the speed of the cell. Bigger threshold voltage cell will take more time to switch. High Vt (hVt) low Vt (lVt) is based on the threshold voltage.

iii.	Same size cells can have different Vts.

iv.	Cell design flow is divided into 3 parts: 1. Inputs 2. Design steps 3. Outputs

v.	Inputs (PDK, DRC& LVS rules, spice models, library & user-defined specifications)

vi.	Tech file contains all the foundry related rules

vii.	Equations for fermipotential, threshold voltage & IdVDS equation discussed.

**b.	Circuit design specification**

i.	Cell height is defined as the distance between Vdd & Vss line. The cell designers need to make sure that the cell height is exactly fit into the Vdd & Vss distance.

ii.	Cell width depends on the timing information. 

iii.	Metal layers to connect a cell is defined by the user

iv.	Pin location requirements also have to be taken into account by the cell designer

v.	Design steps are three: 1. Ckt design 2. Layout design 3. Characterization

vi.	Ckt Design: Depending on the drive strength, the NMOS & PMOS needs to be sized. It also depends on the technology node too?

**c.	Layout Design: - characterization **

i.	After the PMOS & NMOS network graph is obtained, make an euler’s path. Euler’s path is a path that is traced only once. Place the transistors based on the euler’s path and draw a stick diagram. Poly is vertically placed for each gate input that used in the circuit. The remaining connections are done based on the circuit. 

ii.	Output: CDL, GDSII file, LEF, Extracted parasitics (.cir)  - Timing, power .libs, noise, function

**d.	Typical characterization flow**

i.	Inputs available: subcircuit models, ckt connections, models for NMOS & PMOS

ii.	Flow: 1. Read in the models 2. Read the extracted spice netlist 3. Recognize the behavior of the buffer 4. Read the subcircuit of the inverter 5. Attach the necessary power sources 6. Apply the stimulus 7. Necessary output/load capacitances (max to min range) 8. Provide the necessary simulation commands (.tran, .dc etc.,) 

iii.	Next step is feed in all the 1-8 inputs as a characterization file in Guna which gives the output models – timing, noise, power .libs, function

**4.	Timing Characterization**

**a.	Timing threshold definitions**

i.	slew_low_rise_thr – closer to low voltage and rising, typically 20% above

ii.	slew_high_rise_thr – closer to the high voltage and rising, typically 20% to the high voltage

iii.	slew_low_fall_thr – like above but falling

iv.	slew_high_fall_thr - like above but falling

v.	in_rise_thr – 50% (typical) of the input voltage rise step

vi.	in_fall_thr – 50% of the input voltage fall step

vii.	out_rise_thr – like that for output voltage

viii.	out_fall_thr -  like that for output voltage

ix.	To calculate the delay, 50% input to output can be used

**b.	Propagation Delay & transition time**

i.	Delay is out_*_thr – in_*_thr

ii.	Wrong threshold points taken can produce wrong delay values, in some cases negative numbers which is simply not correct

iii.	Even with proper choice of threshold, it is possible to see negative delays. For e.g., a long line with big capacitance and then a buffer can lead to negative delay

iv.	Transition time: input slew = slew_high_rise_thr - slew_low_rise_thr & output slew = slew_high_fall_thr - slew_low_fall_thr


**Day 3**

**1.	Labs for ngSPICE simulation for CMOS:**
   
**a.	IO placer review:**

i.	Set the FP_IO_MODE to 2  

![image](https://github.com/user-attachments/assets/40492856-93d4-429a-aea6-e19b0761cfe6)

ii.	Run the command run_floorplan  

![image](https://github.com/user-attachments/assets/c578b771-53d5-4bca-8e29-75051f0ad74c)
![image](https://github.com/user-attachments/assets/1d50686b-fed0-4b7f-b6fa-11d5bd6782d7)


iii.	Opening def the pins are not equidistant anymore they are on top of other  

![image](https://github.com/user-attachments/assets/32b544ab-9bd1-45e7-bb38-37905aea625d)


iv.	The values are reset and ran the run_floorplan again & verified the pin mapping   

![image](https://github.com/user-attachments/assets/1062e8a5-c475-470d-9d87-8810f18fdefc)

![image](https://github.com/user-attachments/assets/b20d4505-9e1f-4d61-9ff3-2a9504ff07da)

**b.	SPICE deck creation for COMS inverter**

i.	Node is required to define a component in spice. A component is placed between nodes.

**c.	SPICE simulation lab for CMOS**

i.	Voltage transfer characteristics are obtained for PMOS same size as NMOS & PMOS 2.5 times the size of the NMOS and compared the VTC to see that the one with PMOS 2.5 times the size of NMOS gives the VTC 50% line at half of VDD (2.5V)

**d.	Switching Treshold Vm**

i.	Static behavior of the CMOS inverter: Switching threshold is the voltage at which the inverter switches, Vm is the point where the Vin=Vout. 

ii.	 Short circuit current flows in the region near Vm, both PMOS & NMOS are in saturation

**e.	Static & dynamic simulation of CMOS inverter**

i.	Transient simulations are done with inverter with a pulse to obtain the rise & fall delay for 50% of the VDD 

ii.	Derivation of Vm can be analytically calculated as below:

![image](https://github.com/user-attachments/assets/d7af2cfb-fc83-4391-b1b2-0bc8e88052e7)

iii.	For Wp/Lp = Wn/Ln, we got rise delay = 148ps, fall delay = 71ps, Vm = 0.99V

f.	Lab steps to git clone vsdstdcelldesign

i.	Downloaded the vsdstdcelldesign to openlane working folder

![image](https://github.com/user-attachments/assets/8cc640de-918f-47da-9a75-4de8b0b2499a)

ii.	Copied the tech file to the vsdstdcelldesign folder 

![image](https://github.com/user-attachments/assets/74adfff6-9be8-4091-84fc-ee9db504ca89)

iii.	Opened the inverter in magic 

![image](https://github.com/user-attachments/assets/4095c38d-71b9-4334-a5ab-51b173dcc951)

![image](https://github.com/user-attachments/assets/17cdac63-2be4-4835-b732-57c1985e30f8)



**2.	SKY130_D3_SK2 - Inception of Layout CMOS fabrication process – 16 Mask process**
   
a.	SKY_L1 - Create Active regions 

i.	P type, high resistivity 5 to 50 ohms meter?, doping level, 10^15 per cm^3, orientation 100, substrate doping should be less than well doping

ii.	Each CMOS are in pockets isolated in p substrate

iii.	On p substrate, 40nm SiO2, 80nm Si3N4, 1um photoresist, then mask1, uv light and then wash out the exposed areas, remove the mask1, exposed Si3N4 is etched off, now remove the photo resist (chemical etching) since the Si3N4 areas helps in growing the oxide layer on other areas, grow the SiO2 further in the oxidation furnace which produces exposed regions to grow isolation regions made by SiO2. This process of growing the field oxide is called LOCOS (local oxidation of silicon). The grown SiO2 regions are called Bird’s beak. Now etch out the Si3N4 using hot phosphoric acid. 

**b.	Formation of nwell & pwell**

i.	Nwell – pmos, pwell – nmos

ii.	Photo resist is applied & mask2 is applied to expose the uv light on other regions. The mask is removed, and providing a region to make p-well. It is formed by Boron (p type material) ion implantation through the SiO2 region using ~200keV. Pwell is formed in the exposed regions under the SiO2. Ion implantation process damage the SiO2 regions and will be later repaired. 

iii.	Similarly, nwell region are formed using Mask3. Phosphorous (n type material) is used for ion implantation & it is heavier than Boron. ~400keV is used for this.

iv.	A Drive in furnace (high temperature – 1100 degree C for 4-6 hours) is used to increase the depth of the well regions to at least half of the P-substrate. This is called twin tub process. 

**c.	Formation of Gate**

i.	The threshold voltage & doping relationship is given by the fermi potential equation below 

![image](https://github.com/user-attachments/assets/71e56f4b-0ce6-4f96-b02c-8b35933d2bfc)

ii.	Threshold voltage is controlled by doping concentration (NA) & oxide capacitance

iii.	Mask4 is used expose the pwell regions, now a low energy boron implantation (~60keV) is used to get thin layer of diffusion atoms at the surface just beneath the SiO2. 

iv.	Mask5 is used to expose the nwell regions & repeat the similar process for n-type (Arsenic or Phosphorous) 

v.	Now HF is used to chemically etch out the SiO2 and regrow a good high quality SiO2 (10nm) layer.

vi.	Previous two steps decide the Vt of the transistors.

vii.	~0.4um thick polysilicon layer is formed on top now.

viii.	N type (As or P) ion implants on poly for low gate resistance 

ix.	Mask6 is used to form gate mask, and the remaining sections are etched out to form the polysilicon gate

d.	Lightly Doped Drain (LDD) formation

i.	Mask7 & Mask8 are used for forming N- & P- diffusion

ii.	LDD is required due to two reasons: 1. Hot electron effect 2. Short channel effect

iii.	When the actual S or D is fabricated, the LDD region might get disrupted and we need to protect the LDD region. For this reason, we add spacers for this. SiO2 or Si3N4 (~0.1um) & use anisotropic plasma etching. The sidewall spacer helps to keep the LDD region between heavily doped D region & the N or P well regions getting P+ P- N for pmos & N+N-P for nmos drains

e.	Source & Drain formation

i.	This screen oxide to avoid channeling during implants

ii.	Mask9 is used to make S & D of nmos As is used at 75keV

iii.	This produces N+N- P N- N+ formation for nmos

iv.	Mask10 is used to do the similar process for PMOS using Boron (50keV)

v.	High temperature annealing (like 1000 degree C) in furnace is used to move the source & drain down further into the wells.

f.	Local contact formation

i.	Etch out the thin oxide in HF

ii.	Now deposit Titanium on wafer through sputtering. Ti metal is hit with Argon gases which causes Ti will get sputtered/emitted out and get deposited into the substrate.

iii.	Ti is deposited uniformly everywhere. Now the wafer is heated at about 650 to 700 degrees C in N2 ambient for 60 seconds. TiSi2 is a low resistant material that can be used for connectivity. Also TiN is formed due to the ambient N present, which is used for local connections. It has higher resistivity can be used for nmos & pmos drain connections. 

iv.	Mask11 is used now to etch out the unwanted TiN using RCA cleaning. RCA solution is H2O:NH4OH:H2O2 = 5:1:1  

g.	Higher level metal formation

i.	Deposit a thick (1um) layer of SiO2 doped with P or B, (for protection against Na ions), & polish the surface. The polishing the surface is called as CMP (Chemical Mechanical Polishing)

ii.	Mask12 is used to make connections to the higher metal layer. Drill holes to make connections. ~10nm TiN is deposited on top of it, since it is a good adhesion layer for SiO2 & it is also a barrier layer to protect the bottom layers. Then W is deposited on top of it. 

iii.	Mask13 & 16 to drill holes for higher layers get the pins accessed at the top layer













