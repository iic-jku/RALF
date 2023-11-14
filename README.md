# RALF - Reinforcement Learning assisted Automated analog Layout design Flow

As part of a master's thesis, developed at the Institute for Integrated Circuits (IIC), Johannes Kepler University, Linz,
a automated analog layout design flow were developed.


## Getting started
### Step 0: Prerequisites
- [SKY130 PDK](https://github.com/google/skywater-pdk)
    - For easy installation check out [volare](https://github.com/efabless/volare)
- [MAGIC](https://github.com/RTimothyEdwards/magic)
- Python >= 3.10
- Path to the sky130A pdk set under `$PDKPATH`, this can look like as follows
```
    export PDKPATH=/home/pdks/sky130A
```
### Step 1: Clone the repository
```
    $ git clone https://github.com/JakobRat/RALF
```

### Step 2: Add your circuits netlist
To design your circuit, add the circuits-netlist (only `.spice` formats are supported) to the `Circuits` folder. 

#### Netlist prerequisites
- The top-circuit isn't a subcircuit. 
- E.g. a valid netlist looks like
```
    x1 Vin Vout1 Vdd Vss inv
    x2 Vout1 Vout Vdd Vss inv
    XC1 Vout1 Vss sky130_fd_pr__cap_mim_m3_1 W=4 L=4 MF=1 m=1

    .subckt inv A Y Vdd Vss
    XM1 Y A Vss Vss sky130_fd_pr__nfet_01v8 L=1 W=1 nf=1
    XM2 Y A Vdd Vdd sky130_fd_pr__pfet_01v8 L=1 W=3 nf=3
    .ends
    .end
```