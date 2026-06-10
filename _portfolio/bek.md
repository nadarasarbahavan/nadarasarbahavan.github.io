---
title: "BEK: FPGA Based Processor for Image Downsampling (Undergrad Coursework-Computer Architecture)"
excerpt: "A custom RISC processor implemented on a DE2-115 FPGA board to down-sample a 256x256 grayscale image to 128x128, using Gaussian pre-filtering to prevent aliasing and JTAG communication to the host PC."
collection: portfolio
date: 2020-01-01
---


This is our implementation of a RISC processor to down-sample a grayscale image of 256x256 dimensions to 128x128 resolution. The processor was implemented on a DE2-115 Development Board using Quartus Prime software, and it involves 12 registers, a control store, and 29 instructions for the ALU to work on 8-bit data.

The processor first pre-processes the data by convolving with a 3x3 Gaussian window to filter out high-frequency spatial information and prevent aliasing, then selectively samples data to reconstruct the down-sampled image. Upon down-sampling, it communicates the image via the JTAG communication protocol to the computer for viewing.

**Control Store:** The control signal of the BEK processor is 30 bits: the first 8 bits for next address, the next 4 bits for ALU operation, the next 10 bits for C bus operation, the next 3 bits for memory signals, the next 1 bit for PC increment, and the last 4 bits for B bus operation. 
![Project screenshot](/images/controlstore.png)

The results were cross-checked with a simulation implemented in MATLAB.
![Project screenshot](/images/result.png)

I was involved in the design of the ISA, matlab testbench.

