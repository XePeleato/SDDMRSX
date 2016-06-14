# SDDMRSX
FPGA X11 miner project.

Due to the huge increment of Dash's hashrate experimented weeks ago, this project aims to achieve a cheap yet powerful FPGA mining solution. 
Here there are some of the FPGA Advantages:
- No huge NRE costs
- It can be reprogrammed to mine another cryptocurrency
- It's easier to work with

##Hardware

In order to start, I'll use the Digilent Arty board, because it's cheap and I like its DDR3 memory, however I fear it's not going to run as fast as I'd like. I don't expect much from a $99 board.
If I had more money to spend, I'd buy a better FPGA, so if you have any suggestion let me know.

##Software

I'll try to adapt my modified cgminer to handle the communications with the FPGA.

##Firmware

This is what this repo is all about, In order to code the firmware I'll use the Vivado tools released by Xilinx.

So here's the plan:ho

The board (the one We will develop) will have a USB - UART convertor, and cgminer will talk to the miner that way.
In order to send some work to the FPGA, We'll do it like this:

Cgminer detects a new block and sends a 512bits package formatted like this:

Start[Midstate(256bits), Fill bits (160bits), Last 96 bits of the last block header (96 bits)]

Whenever the nonce (32bits) is calculated, it will be sent back to cgminer and the FPGA will stop working.
I took the idea from the FPGA Icarus bitcoin miner.

About X11, I guess I need some help to decide what parts of X11 (if any) can be setup as a common routine (something present at all of the 11 algorithms) in order to optimize the miner.

By now, if nobody jumps in, getting it to mine (no matter how slow) is the priority.
