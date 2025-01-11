# FFT IMPLEMENTATION USING HLS

## Introduction

The Fast Fourier Transform (FFT) is a powerful mathematical tool that decomposes a signal into its constituent frequencies, making it essential in a wide range of applications, including signal processing, communications, and image analysis. FFT is often used to analyze signals in the frequency domain, allowing for efficient computations and transformations of time-domain signals.

This project aims to design and implement an optimized FFT core using high-level synthesis (HLS) tools, particularly Vivado HLS, to generate a hardware-efficient solution for FPGA deployment. The goal is to translate the mathematical FFT algorithm into hardware, optimizing for performance and resource usage while maintaining flexibility in terms of FFT size and precision.

The design process begins with the development of a high-level C/C++ description of the FFT algorithm, which is validated using Python’s NumPy library. The C/C++ code is then synthesized into hardware description language (HDL) using Vivado HLS, which translates the algorithm into an efficient hardware architecture suitable for FPGA implementation. During this process, optimization techniques such as loop unrolling, pipelining, and dataflow management are employed to improve performance, throughput, and resource utilization.

The project also emphasizes flexibility by allowing the FFT size to be configurable, accommodating various application needs. Additionally, the design supports both fixed-point and floating-point arithmetic, enabling users to choose between higher precision and more efficient resource usage.

After synthesizing the design, it undergoes hardware validation using an FPGA development board, ensuring the implementation works as intended under real-world conditions. The final design is then packaged as an IP core, making it ready for integration into larger systems and allowing for practical deployment in various applications, from wireless communications to real-time signal processing.

---

## Methodology

### Block Diagram and Details

The FFT algorithm was described in C/C++ and synthesized using Vivado HLS, which generated the corresponding hardware description language (HDL) code. The HDL code can then be integrated into a complete system and synthesized using Vivado to create the final FPGA implementation.

![Vivado HLS Design Flow](https://github.com/user-attachments/assets/e9546b93-e6b3-45c6-ab6d-926d74793ddd)

The methodology for developing an FFT design involves initially creating a high-level C/C++ description of the FFT algorithm and validating it with a test bench using Python’s NumPy. To optimize for hardware, the design is optionally refined to use fixed-point arithmetic with `ap_fixed` data types, balancing precision and resource use. The design is then synthesized using Vivado HLS, translating the C/C++ code into HDL. Optimization directives are applied to enhance performance and resource efficiency. Following synthesis, a hardware co-simulation is conducted to ensure functionality. Finally, the design is packaged as an IP core for integration into larger systems, ensuring its portability and readiness for practical deployment.

### FFT Implementation

The FFT design was crafted with a high degree of flexibility, allowing the FFT size \( N \) to be easily configurable. This adaptability was crucial for accommodating various application requirements. The design supported both fixed-point and floating-point arithmetic, allowing users to choose between higher precision with floating-point or more efficient resource usage with fixed-point arithmetic. The emphasis was on developing a generalized FFT implementation rather than adhering to any specific FFT algorithm. This approach ensured that the design could be broadly applicable and adaptable to different scenarios without being constrained by a particular algorithmic structure.

![127676203-d51eab76-11e9-4a71-af22-0a580097acea](https://github.com/user-attachments/assets/ccfc5908-3453-48c6-8b76-046974a046cd)


### Optimization Techniques

Several key optimization techniques were employed to enhance the performance and efficiency of the FFT design:

- **Loop Unrolling:** This technique was used to enable parallel processing of FFT computations. By unrolling loops, multiple iterations of the loop were executed simultaneously, which significantly reduced the overall computation time and increased processing speed.
  
- **Pipelining:** To further enhance performance, pipelining was applied to the FFT computation stages. This optimization technique allowed different stages of the FFT process to be executed concurrently. By overlapping these stages, throughput was increased, leading to faster overall execution of the FFT algorithm.
  
- **Dataflow Management:** Efficient dataflow management was implemented to handle dependencies within the computation process. This approach optimized how data was moved and processed through different stages of the FFT, allowing for parallel execution and reducing potential bottlenecks.

These optimization techniques collectively improved the efficiency, speed, and resource utilization of the FFT design, ensuring that it met performance requirements while maintaining flexibility and adaptability.

---

## Hardware Tools and Components

For the implementation of the FFT core, several hardware tools and components were utilized to ensure a robust and efficient design. These tools and components include both the physical hardware used for testing and validation as well as the software tools required for design synthesis and optimization.

### FPGA Development Board

A Field-Programmable Gate Array (FPGA) development board served as the primary hardware platform for implementing and testing the FFT core. The board used in this project was selected for its compatibility with Vivado Design Suite and its capacity to handle the computational demands of the FFT. The FPGA board provided a reconfigurable environment that allowed for rapid prototyping and testing of the design under real-world conditions.

### Vivado Design Suite

The Vivado Design Suite by Xilinx was the primary software tool used for the synthesis, simulation, and implementation of the FFT design. This comprehensive suite includes Vivado High-Level Synthesis (HLS), which allows the conversion of C/C++ code into a hardware description language (HDL), and the Vivado Integrated Design Environment (IDE) for design verification and hardware implementation. Vivado HLS was essential for translating the high-level FFT algorithm into a hardware architecture, while the Vivado IDE facilitated simulation, debugging, and optimization of the design.

### High-Level Synthesis (HLS) Tools

Vivado HLS was used to generate the hardware design from the C/C++ description of the FFT. This tool provided a higher level of abstraction, enabling rapid development and iteration of the design. HLS tools allowed for the exploration of various design configurations and optimizations, such as adjusting data types, loop unrolling, and pipelining, to achieve the desired performance and resource utilization.

### Test and Measurement Equipment

To validate the performance of the implemented FFT core, various test and measurement tools were employed. Oscilloscopes and logic analyzers were used to monitor signal integrity and timing, while power measurement tools assessed the power consumption of the design. These instruments ensured that the hardware implementation met the performance specifications and operated reliably under different conditions.

### Memory Components

Block RAMs and external memory interfaces were integral to the FFT implementation. These memory components were used to store intermediate results and data during FFT computation. The efficient use of on-chip block RAMs was critical to minimizing latency and optimizing data throughput in the design.

### Clock and Timing Components

Accurate timing and clock management are essential in FPGA designs, especially for high-speed applications like FFT. Clock generators and phase-locked loops (PLLs) were used to provide stable and precise clock signals to the FFT core. Proper clock domain management ensured that the design operated reliably at the required clock frequencies.

### Power Supply and Management

The FPGA development board was powered by a stable and reliable power supply, which is crucial for maintaining the performance and integrity of the design. Power management components ensured that the FPGA and other peripherals operated within their specified voltage and current limits, preventing any potential damage or performance degradation.

### Debugging Tools

In-circuit debugging tools such as JTAG interfaces and embedded logic analyzers were employed to troubleshoot and fine-tune the hardware implementation. These tools allowed for real-time monitoring and modification of the design during operation, making it easier to identify and resolve any issues that arose during testing.

## Software Tools and Languages

The design and implementation of the FFT core for this project involved a variety of software tools and programming languages, each playing a crucial role in the development process. The integration of these tools and languages ensured a seamless workflow from algorithm design to hardware implementation, simulation, and testing.

### Vivado Design Suite

**Vivado HLS (High-Level Synthesis):** This tool from Xilinx allowed for the synthesis of C/C++ code into hardware description languages (HDL) like Verilog or VHDL. Vivado HLS enabled rapid prototyping by converting high-level algorithmic descriptions into optimized hardware architectures. This tool was essential for exploring design optimizations such as pipelining, loop unrolling, and dataflow management.

**Vivado IDE:** The Integrated Design Environment (IDE) within Vivado provided a platform for design entry, simulation, and implementation. It facilitated the synthesis of HDL code, placement and routing on the FPGA, and provided tools for timing analysis and power estimation. The IDE also supported IP core integration and design validation.

### C/C++ Programming

**Algorithm Development:** The FFT algorithm was initially developed and tested in C/C++. This high-level language was chosen for its balance of performance and accessibility. C/C++ enabled the creation of a test bench to validate the functionality of the FFT before moving to hardware synthesis. The flexibility of C/C++ also allowed for easy modifications to the algorithm and data types during the optimization process.

**Fixed-Point Arithmetic:** For applications requiring optimized hardware performance, the C/C++ code was refined to use fixed-point arithmetic. This step involved converting floating-point operations to fixed-point using the `ap_fixed` data type provided by Vivado HLS. This conversion was crucial for reducing resource usage and improving computational speed.

### Python (NumPy)

**Reference Data Generation:** Python, along with its NumPy library, was used to generate input and output data for testing the FFT implementation. NumPy’s FFT functions provided a reliable reference to validate the hardware implementation.

---

## IMPLEMENTATION

### Flow Chart:
![Flow Chart of Implementation of FFT using HLS](https://github.com/user-attachments/assets/cf8669c0-b3f9-4af1-a386-593238c6e75f)

### Reference Generation:
To generate sample input and output data for testing the FFT implementation, the Numeric Python (NumPy) library can be used to create the FFT function. A default approach involves generating a random sequence with a fixed seed to ensure consistent results. The input and output data are saved in files using decimal notation, which can be easily read and processed by the C test bench. Additionally, the data is converted to a 16-bit `ap_fixed<16,8>` data type, where 16 bits are allocated per value with 8 bits for the integer portion and 8 bits for the fractional portion. Adjustments can be made to the data generation process to accommodate different input sequence sizes and bit configurations as needed.

### C/C++ Implementation of FFT:
The first step in the FFT process was to write a high-level description of the FFT algorithm in C/C++. This involved defining the FFT function to handle complex input data and creating a test bench to validate its functionality. The test bench generated input signals using Python’s NumPy library, which were then applied to the C/C++ FFT description. The outputs were compared with the expected results, also calculated using NumPy. This initial step ensured that the FFT algorithm was correctly implemented in a high-level language before proceeding to further design stages. Hence, a 32-point FFT code is implemented with the bit-reversal positions precomputed and stored in the header files.

The Twiddle Factor is decomposed into the following form:
- \( \text{exp}(ia + ib) = \text{exp}(ia) \times \text{exp}(ib) = \text{exp}(ia) + Z \times \text{exp}(ia) \)
- Where \( Z = \text{exp}(ib) - 1 = -(1 - \cos(b)) + i\sin(b) = -2\sin^2(b/2) + i\sin(b) \)
- \( Z \) is precomputed and stored in the header file.

### Fixed-Point Conversion:
To optimize the design for efficient hardware utilization, the system was optionally refined to use fixed-point arithmetic instead of floating-point. This involved converting the data types in the C/C++ description to `ap_fixed`, a data type provided by Vivado HLS for fixed-point arithmetic. The number of bits for both the integer and fractional parts was carefully selected to balance precision with resource utilization. This step is crucial for applications requiring lower power consumption and higher speed, as fixed-point arithmetic generally demands less hardware and is faster to compute compared to floating-point arithmetic.

### C Simulation:
The C simulation of the FFT algorithm using Vivado HLS served as an essential step in verifying the functionality of the design before proceeding to hardware synthesis. By running the FFT algorithm in a high-level simulation environment, the results were compared against expected output values to ensure correctness. This process allowed for early detection and correction of any logical errors, ensuring that the design behaved as intended. The successful simulation results provided confidence in the design's functionality, paving the way for further synthesis and hardware co-simulation.

### C Synthesis:
Once the C/C++ description was verified through the test bench, the next step was to synthesize the design using Vivado HLS. The synthesis process translated the high-level C/C++ code into a hardware description language (HDL), such as Verilog or VHDL. This translation is essential for generating a hardware design that can be implemented on an FPGA. During synthesis, various optimizations were considered, such as adjusting the number of bits used in data types to minimize resource usage and applying directives like loop unrolling, pipelining, and dataflow optimizations to enhance performance metrics like latency and throughput.

### Optimization and Directive Application:
To further refine the hardware design, optional HLS directives were applied. These directives allowed for fine-tuning various parameters such as resource usage, latency, and initiation interval. For instance, loop unrolling was employed to increase parallelism, while pipelining improved overall throughput by overlapping different stages of the FFT computation. These optimizations were iteratively applied and tested until the results were satisfactory, ensuring that the design met performance targets while utilizing resources efficiently.

### Hardware Co-Simulation:
After achieving satisfactory synthesis results, a hardware co-simulation was conducted to verify that the synthesized design functioned correctly. This step was particularly important if any warnings or potential mismatches between the synthesis and simulation phases were detected. The hardware co-simulation involved running the design on a hardware simulator or an actual FPGA to ensure that the netlist matched the expected functionality. Any discrepancies found during this stage were resolved to ensure the design's accuracy.

### IP Core Export:
The final step was to package the verified design as an IP core that can be integrated into larger system designs. This involved exporting the design in a format compatible with Vivado, facilitating its integration into more complex projects. The IP core could then be used as a building block in various applications, ensuring that the FFT design was portable and ready for deployment in practical systems.

---

## RESULTS AND DISCUSSIONS

Test data is generated using a Python script that outputs random complex values for FFT computation. Data is stored in floating-point and hex formats for Vivado testing. Files are prepared for Vivado testing on hardware, including input and output files in floating-point and fixed-point formats. Setting up an FFT project in Vivado HLS involves defining FPGA part number, creating source code and test bench, and running C simulation with a tolerance limit for error checking. The FPGA part number for the project is XC7A35TCPG with 236 pins. The source code includes FFT.cpp file and a test bench that reads input and output data files. A tolerance limit of 0.01 is set to check for errors due to conversion from floating-point to fixed-point. Running a C simulation is essential to check for errors, and the test bench provides error messages if any issues are detected.

### Results of C Synthesis:
After running C synthesis for FFT function in Vivado HLS, the system achieved an estimated 7.3 nanoseconds for a target clock period of 10 nanoseconds. Latency and initiation interval are 833 clock cycles without any optimizations applied. Resource usage and interface details are shown in the synthesis report. Input signals include clock, reset, start signal, while output signals include done, idle, and ready signals.

#### Performance Estimates:

##### Timing Report:
| **CLOCK** | **TARGET** | **ESTIMATED (ns)** | **UNCERTAINTY** |
|-----------|------------|--------------------|-----------------|
| ap_ck     | 10.00      | 7.345              |  1.25           |

##### Latency Report:
| **LATENCY**                 | **INTERVAL**                |       -  |
|-----------------------------|-----------------------------|----------|
|      **MIN** | **MAX**      |      **MIN** | **MAX**      | **TYPE** |
|--------------|--------------|--------------|--------------|----------|
| 83.3         | 83.3         | 83.3         | 83.3         | none     |

#### Utilization Estimates:

##### Resource Utilization Report:
| **NAME**  | **BRAM_18K** | **DSP48E** | **FF** | **LUT** |
|-----------|--------------|------------|--------|---------|
|  DSP      |  -           |    -       |    -   |   -     |
| Expression|     -        |    -       |   0    | 102     |         
| FIFO      |     -        |    -       | 560453 |    -    |         
| Instance  | 0            | 4          | -      | 805     |         
| Memory    | 0            | -          | 197    | 115     |         
| Multiplexer| -           | -          | 1210   | 864     |         
| Register   | -        | -            | 1600       |   -     |         
| Total      | 0        | 4            | 2          | 1886   |         
| Available  | 100      | 90           | 41600      | 20800  |         
| Utilization (%)| 0        | 4            | 2          | 9      |     

#### Interface:

##### Interface Report:
| **RTL PORTS**     | **DIR** | **BITS** | **PROTOCOL** | **SOURCE OBJECT** | **C TYPE** |
|-------------------|---------|------=---|--------------|-------------------|------------|
| ap_clk            | in      | 1        | ap_ctrl_hls  | FFT               | return_value |
| ap_clk_n          | in      | 1        | ap_ctrl_hls  | FFT               | return_value |
| ap_start          | in      | 1        | ap_ctrl_hls  | FFT               | return_value |
| ap_done           | out     | 1        | ap_ctrl_hls  | FFT               | return_value |
| ap_idle           | out     | 1        | ap_ctrl_hls  | FFT               | return_value | 
| ap_ready          | out     | 1        | ap_ctrl_hls  | FFT               | return_value |
| data_IN_TDATA     | in      | 32       | axis         | data_IN           | pointer      |
| data_IN_TVALID    | in      | 1        | axis         | data_IN           | pointer      |
| data_IN_TREADY    | out     | 1        | axis         | data_IN           | pointer      |
| data_OUT_TDATA    | out     | 32       | axis         | data_OUT          | pointer      |
| data_OUT_TVALID   | out     | 1        | axis         | data_OUT          | pointer      |
| data_OUT_TREADY   | in      | 1        | axis         | data_OUT          | pointer      |

### Results of C/RTL Co-simulation:

#### Co-simulation Report:

|         |            | **LATENCY**                   | **INTERVAL**                |
|---------|------------|-------------------------------|-----------------------------|
| **RTL** | **STATUS** | **MIN** | **AVG**  | **MAX**  | **MIN** | **AVG** | **MAX** |
|---------|------------|---------|----------|----------|---------|---------|---------|
|   VHDL  | NA         |    NA   |    NA    |    NA    |   NA    | NA      | NA      |
| VERILOG | PASS       |833      | 833      |   833    |834      | 834     | 834     |

### Simulation result of Waveform Viewer:

![image](https://github.com/user-attachments/assets/ed74c517-f018-4420-8b25-b07d9b48fb84)


---

## CONCLUSION AND FUTURE SCOPE:

Vivado HLS, a tool designed for high-level synthesis, often defaults to a conservative approach regarding resource utilization. This default strategy is geared towards minimizing the use of hardware resources, which can result in increased latency and restricted parallel processing capabilities. In its base configuration, Vivado HLS tends to prioritize safety and simplicity, leading to designs that may not fully exploit the potential of the hardware, particularly in terms of processing speed and concurrency. To overcome these limitations and enhance performance, significant manual intervention is necessary. One of the key strategies to improve performance involves decoupling the stages of butterfly computations within the FFT algorithm. Butterfly computations are fundamental to FFT processing, and by breaking down these stages into independent operations, it is possible to reduce the computational overhead and increase the speed of the entire process. Additionally, optimizing the use of block RAMs, lookup tables (LUTs), and flip-flops is crucial. By strategically balancing these resources, it is feasible to minimize latency. For instance, reducing the dependence on block RAMs in favor of using more LUTs and flip-flops can lead to a more efficient design, cutting down the latency of FFT computation to N log 2 N + N cycles. Despite the advantages of Vivado HLS in simplifying the high-level exploration and synthesis of efficient IP core designs, achieving an optimal hardware implementation typically demands substantial manual adjustments. The process involves fine-tuning various aspects of the design, including memory usage, data flow, and computational efficiency. This level of customization ensures that the final implementation can achieve performance metrics that are on par with or even exceed those of specialized IP cores available from FPGA vendors. The results of this approach illustrate that, with appropriate modifications and directive applications, the performance and cost of the FFT implementation can be competitive with high-end, vendor-specific IP cores. The ability to tailor the synthesis process to meet specific performance goals highlights the flexibility and power of Vivado HLS as a tool for hardware design. Looking forward, there are several promising directions for further enhancing FFT implementations and related DSP modules. One of the key future developments involves creating an advanced guided exploration tool that integrates seamlessly with the current FFT model. This tool aims to streamline the exploration of various design options, making it easier to optimize performance while reducing the need for extensive manual tuning. By providing automated assistance in evaluating different configurations and performance trade-offs, this guided exploration tool could significantly accelerate the design process and improve overall efficiency.

---
