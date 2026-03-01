**PART ONE** INTRODUCTION 

**CHAPTER** 

BASIC CONCEPTS AND COMPUTER EVOLUTION 

**1.1 Organization and Architecture** 

**1.2 Structure and Function** 

**1.3** 

**1.4** 

**1.5** 

**1.6**   
Function 

Structure 

**A Brief History of Computers** 

The First Generation: Vacuum Tubes 

The Second Generation: Transistors 

The Third Generation: Integrated Circuits Later Generations 

**The Evolution of the Intel x86 Architecture** 

**Embedded Systems** 

The Internet of Things 

Embedded Operating Systems 

Application Processors versus Dedicated Processors Microprocessors versus Microcontrollers 

Embedded versus Deeply Embedded Systems 

**ARM Architecture** 

ARM Evolution 

Instruction Set Architecture 

ARM Products 

**1.7 Cloud Computing** 

Basic Concepts 

Cloud Services 

**1.8 Key Terms, Review Questions, and Problems** 

1 

**2** CHAPTER 1 / BASIC CONCEPTS AND COMPUTER EVOLUTION 

**LEARNING OBJECTIVES** 

After studying this chapter, you should be able to: 

Explain the general functions and structure of a digital computer. 

Present an overview of the evolution of computer technology from early 

digital computers to the latest microprocessors. 

Present an overview of the evolution of the x86 architecture. 

Define embedded systems and list some of the requirements and constraints that various embedded systems must meet. 

**1.1 ORGANIZATION AND ARCHITECTURE** 

In describing computers, a distinction is often made between *computer architec- ture* and *computer organization.* Although it is difficult to give precise definitions for these terms, a consensus exists about the general areas covered by each. For example, see \[VRAN80\], \[SIEW82\], and \[BELL78a\]; an interesting alternative view is presented in \[REDD76\]. 

**Computer architecture** refers to those attributes of a system visible to a pro- grammer or, put another way, those attributes that have a direct impact on the logical execution of a program. A term that is often used interchangeably with com- puter architecture is **instruction set architecture (ISA)**. The ISA defines instruction formats, instruction opcodes, registers, instruction and data memory; the effect of executed instructions on the registers and memory; and an algorithm for control- ling instruction execution. **Computer organization** refers to the operational units and their interconnections that realize the architectural specifications. Examples of architectural attributes include the instruction set, the number of bits used to repre- sent various data types (e.g., numbers, characters), I/O mechanisms, and techniques for addressing memory. Organizational attributes include those hardware details transparent to the programmer, such as control signals; interfaces between the com- puter and peripherals; and the memory technology used. 

For example, it is an architectural design issue whether a computer will have a multiply instruction. It is an organizational issue whether that instruction will be implemented by a special multiply unit or by a mechanism that makes repeated use of the add unit of the system. The organizational decision may be based on the anticipated frequency of use of the multiply instruction, the relative speed of the two approaches, and the cost and physical size of a special multiply unit. 

Historically, and still today, the distinction between architecture and organ- ization has been an important one. Many computer manufacturers offer a family of computer models, all with the same architecture but with differences in organization. Consequently, the different models in the family have different price and perform- ance characteristics. Furthermore, a particular architecture may span many years and encompass a number of different computer models, its organization changing with changing technology. A prominent example of both these phenomena is the IBM System/370 architecture. This architecture was first introduced in 1970 and 

1.2 / STRUCTURE AND FUNCTION **3** 

included a number of models. The customer with modest requirements could buy a cheaper, slower model and, if demand increased, later upgrade to a more expensive, faster model without having to abandon software that had already been developed. Over the years, IBM has introduced many new models with improved technology to replace older models, offering the customer greater speed, lower cost, or both. These newer models retained the same architecture so that the customer's soft- ware investment was protected. Remarkably, the System/370 architecture, with a few enhancements, has survived to this day as the architecture of IBM's mainframe product line. 

In a class of computers called microcomputers, the relationship between archi- tecture and organization is very close. Changes in technology not only influence organization but also result in the introduction of more powerful and more complex architectures. Generally, there is less of a requirement for generation\-to\-generation compatibility for these smaller machines. Thus, there is more interplay between organizational and architectural design decisions. An intriguing example of this is the reduced instruction set computer (RISC), which we examine in Chapter 15. 

This book examines both computer organization and computer architecture. The emphasis is perhaps more on the side of organization. However, because a computer organization must be designed to implement a particular architectural specification, a thorough treatment of organization requires a detailed examination of architecture as well. 

**1.2 STRUCTURE AND FUNCTION** 

A computer is a complex system; contemporary computers contain millions of elementary electronic components. How, then, can one clearly describe them? The key is to recognize the hierarchical nature of most complex systems, including the computer \[SIMO96\]. A hierarchical system is a set of interrelated subsystems, each of the latter, in turn, hierarchical in structure until we reach some lowest level of elementary subsystem. 

The hierarchical nature of complex systems is essential to both their design and their description. The designer need only deal with a particular level of the system at a time. At each level, the system consists of a set of components and their interrelationships. The behavior at each level depends only on a simplified, abstracted characterization of the system at the next lower level. At each level, the designer is concerned with structure and function: 

■ **Structure:** The way in which the components are interrelated. 

■**Function:** The operation of each individual component as part of the structure. 

In terms of description, we have two choices: starting at the bottom and build- ing up to a complete description, or beginning with a top view and decomposing the system into its subparts. Evidence from a number of fields suggests that the top- down approach is the clearest and most effective \[WEIN75\]. 

The approach taken in this book follows from this viewpoint. The computer system will be described from the top down. We begin with the major components of a computer, describing their structure and function, and proceed to successively 

4 CHAPTER 1 / BASIC CONCEPTS AND COMPUTER **EVOLUTION** 

lower layers of the hierarchy. The remainder of this section provides a very brief overview of this plan of attack. 

**Function** 

Both the structure and functioning of a computer are, in essence, simple. In general terms, there are only four basic functions that a computer can perform: 

■ **Data processing:** Data may take a wide variety of forms, and the range of pro- cessing requirements is broad. However, we shall see that there are only a few fundamental methods or types of data processing. 

■ **Data storage:** Even if the computer is processing data on the fly (i.e., data come in and get processed, and the results go out immediately), the computer must temporarily store at least those pieces of data that are being worked on at any given moment. Thus, there is at least a short\-term data storage function. Equally important, the computer performs a long\-term data storage function. Files of data are stored on the computer for subsequent retrieval and update. 

■ **Data movement:** The computer's operating environment consists of devices that serve as either sources or destinations of data. When data are received from or delivered to a device that is directly connected to the computer, the process is known as *input\-output (I/O*), and the device is referred to as a *peripheral.* When data are moved over longer distances, to or from a remote device, the process is known as *data communications*. 

**■Control:** Within the computer, a control unit manages the computer's resources and orchestrates the performance of its functional parts in response to instructions**.** 

The preceding discussion may seem absurdly generalized. It is certainly possible, even at a top level of computer structure, to differentiate a variety of func- tions, but to quote \[SIEW82\]: 

There is remarkably little shaping of computer structure to fit the function to be performed. At the root of this lies the general\-purpose nature of computers, in which all the functional specialization occurs at the time of programming and not at the time of design. 

**Structure** 

We now look in a general way at the internal structure of a computer. We begin with a traditional computer with a single processor that employs a microprogrammed control unit, then examine a typical multicore structure. 

***SIMPLE SINGLE\-PROCESSOR COMPUTER*** Figure 1.1 provides a hierarchical view of the internal structure of a traditional single\-processor computer. There are four main structural components: 

■ **Central processing unit (CPU)**: Controls the operation of the computer and performs its data processing functions; often simply referred to as **processor**. 

■ **Main memory:** Stores data. 

**I/O**   
**COMPUTER** 

**System bus**   
**Main** 

**memory** 

**CPU** 

**Sequencing**   
**CONTROL** 

**UNIT** 

**logic** 

**Control unit** 

**registers and** 

**decoders** 

**Control** 

**memory**   
1.2 / STRUCTURE AND FUNCTION **5** 

**Registers**   
**CPU** 

**Internal bus** 

**Control unit**   
**ALU** 

**Figure 1.1** The Computer: Top\-Level Structure 

■ **I/O:** Moves data between the computer and its external environment. 

■ **System interconnection:** Some mechanism that provides for communication among CPU, main memory, and I/O. A common example of system intercon- nection is by means of a **system** bus, consisting of a number of conducting wires to which all the other components attach. 

There may be one or more of each of the aforementioned components. Tra- ditionally, there has been just a single processor. In recent years, there has been increasing use of multiple processors in a single computer. Some design issues relat- ing to multiple processors crop up and are discussed as the text proceeds; Part Five focuses on such computers. 

6 CHAPTER 1 / **BASIC** CONCEPTS AND **COMPUTER** EVOLUTION 

Each of these components will be examined in some detail in Part Two. How- ever, for our purposes, the most interesting and in some ways the most complex component is the CPU. Its major structural components are as follows: 

**■ Control unit:** Controls the operation of the CPU and hence the computer. 

■ **Arithmetic and logic unit (ALU):** Performs the computer's data processing functions. 

■ **Registers:** Provides storage internal to the CPU. 

**■ CPU interconnection:** Some mechanism that provides for communication among the control unit, ALU, and registers. 

Part Three covers these components, where we will see that complexity is added by the use of parallel and pipelined organizational techniques. Finally, there are sev- eral approaches to the implementation of the control unit; one common approach is a *microprogrammed* implementation. In essence, a microprogrammed control unit operates by executing microinstructions that define the functionality of the control unit. With this approach, the structure of the control unit can be depicted, as in Figure 1.1. This structure is examined in Part Four. 

***MULTICORE COMPUTER STRUCTURE*** As was mentioned, contemporary computers generally have multiple processors. When these processors all reside on a single chip, the term *multicore computer* is used, and each processing unit (consisting of a control unit, ALU, registers, and perhaps cache) is called a *core*. To clarify the terminology, this text will use the following definitions. 

■ **Central processing unit (CPU):** That portion of a computer that fetches and executes instructions. It consists of an ALU, a control unit, and registers. In a system with a single processing unit, it is often simply referred to as a 

*processor.* 

**■ Core:** An individual processing unit on a processor chip. A core may be equiv- alent in functionality to a CPU on a single\-CPU system. Other specialized pro- cessing units**,** such as one optimized for vector and matrix operations, are also referred to as cores. 

■ **Processor:** A physical piece of silicon containing one or more cores. The processor is the computer component that interprets and executes instruc- tions. If a processor contains multiple cores, it is referred to as a **multicore processor**. 

After about a decade of discussion, there is broad industry consensus on this usage. Another prominent feature of contemporary computers is the use of multiple layers of memory, called *cache memory*, between the processor and main memory. Chapter 4 is devoted to the topic of cache memory. For our purposes in this section, we simply note that a cache memory is smaller and faster than main memory and is used to speed up memory access, by placing in the cache data from main memory, that is likely to be used in the near future. A greater performance improvement may be obtained by using multiple levels of cache, with level 1 (L1) closest to the core and additional levels (L2, L3, and so on) progressively farther from the core. In this scheme, level *n* **is** smaller and faster than level *n* \+ 1. 

1.2 / STRUCTURE AND FUNCTION **7** 

Figure 1.2 is a simplified view of the principal components of a typical mul- ticore computer. Most computers, including embedded computers in smartphones and tablets, plus personal computers, laptops, and workstations, are housed on a motherboard. Before describing this arrangement, we need to define some terms. A **printed circuit board (PCB)** is a rigid, flat board that holds and interconnects chips and other electronic components. The board is made of layers**,** typically two to ten, that interconnect components via copper pathways that are etched into the board. The main printed circuit board in a computer is called a system board or **motherboard**, while smaller ones that plug into the slots in the main board are called expansion boards. 

The most prominent elements on the motherboard are the chips. A **chip** is a single piece of semiconducting material, typically silicon, upon which electronic circuits and logic gates are fabricated. The resulting product is referred to as an **integrated circuit**.   
୬୦୦   
**MOTHERBOARD Main memory chips**   
000 

**I/O chips**   
**Processor chip** 

**CORE** 

**Arithmetic**   
**Instruction** 

**logic**   
**and logic unit (ALU)**   
**Load/ store logic** 

**L1 I\-cache**   
**L1 data cache** 

**L2 instruction**   
**L2 data** 

**cache**   
**cache**   
**PROCESSOR CHIP** 

**Core**   
**Core Core Core** 

**L3 cache**   
**L3 cache** 

**Core**   
**Core**   
**Core Core** 

**Figure 1.2** Simplified View of Major Elements of a Multicore Computer 

**8** CHAPTER 1 / BASIC CONCEPTS AND COMPUTER EVOLUTION 

The motherboard contains a slot or socket for the processor chip, which typ- ically contains multiple individual cores, in what is known as a *multicore processor*. There are also slots for memory chips, I/O controller chips, and other key computer components. For desktop computers, expansion slots enable the inclusion of more components on expansion boards. Thus, a modern motherboard connects only a few individual chip components, with each chip containing from a few thousand up to hundreds of millions of transistors. 

Figure 1.2 shows a processor chip that contains eight cores and an L3 cache. Not shown is the logic required to control operations between the cores and the cache and between the cores and the external circuitry on the motherboard. The figure indicates that the L3 cache occupies two distinct portions of the chip surface. However, typically, all cores have access to the entire L3 cache via the aforemen- tioned control circuits. The processor chip shown in Figure 1.2 does not represent any specific product, but provides a general idea of how such chips are laid out. 

Next, we zoom in on the structure of a single core, which occupies a portion of the processor chip. In general terms, the functional elements of a core are: 

■ **Instruction logic:** This includes the tasks involved in fetching instructions, and decoding each instruction to determine the instruction operation and the memory locations of any operands. 

■ **Arithmetic and logic unit** (**ALU):** Performs the operation specified by an instruction. 

■**Load/store logic:** Manages the transfer of data to and from main memory via cache. 

The core also contains an L1 cache, split between an instruction cache (I\-cache) that is used for the transfer of instructions to and from main memory, and an L1 data cache, for the transfer of operands and results. Typically, today's pro- cessor chips also include an L2 cache as part of the core. In many cases, this cache is also split between instruction and data caches, although a combined, single L2 cache is also used. 

Keep in mind that this representation of the layout of the core is only intended to give a general idea of internal core structure. In a given product, the functional elements may not be laid out as the three distinct elements shown in Figure 1.2, especially if some or all of these functions are implemented as part of a micropro- grammed control unit. 

***EXAMPLES*** It will be instructive to look at some real\-world examples that illustrate the hierarchical structure of computers. Figure 1.3 is a photograph of the motherboard for a computer built around two Intel Quad\-Core Xeon processor chips. Many of the elements labeled on the photograph are discussed subsequently in this book. Here, we mention the most important, in addition to the processor sockets: 

■ PCI\-Express slots for a high\-end display adapter and for additional peripher- als (Section 3.6 describes PCIe). 

■ Ethernet controller and Ethernet ports for network connections. 

■ USB sockets for peripheral devices. 

2x Quad\-Core Intel® Xeon® Processors with Integrated Memory Controllers   
Six Channel DDR3-1333 Memory Interfaces Up to 48GB 

CHASSIS PLANS   
1.2 / STRUCTURE AND FUNCTION 9 

Intel® 3420 Chipset 

Serial ATA/300 (SATA) Interfaces 

Power & Backplane I/O Connector C   
PCI Express® Connector B   
PCI Express Connector A   
Clock 

**Figure 1.3** Motherboard with Two Intel Quad\-Core Xeon Processors 

*Source:* Chassis Plans, www.chassis-plans.com   
2x USB 2.0 Internal 

2x USB 2.0 

External 

VGA Video Output 

BIOS 

2x Ethernet Ports 

10/100/1000Base-T 

Ethernet Controller 

■ Serial ATA (SATA) sockets for connection to disk memory (Section 7.7 discusses Ethernet, USB, and SATA). 

■ Interfaces for DDR (double data rate) main memory chips (Section 5.3 discusses DDR). 

Intel 3420 chipset is an I/O controller for direct memory access operations between peripheral devices and main memory (Section 7.5 discusses DDR). 

Following our top\-down strategy, as illustrated in Figures 1.1 and 1.2, we can now zoom in and look at the internal structure of a processor chip. For variety, we look at an IBM chip instead of the Intel processor chip. Figure 1.4 is a photograph of the processor chip for the IBM zEnterprise EC12 mainframe computer. This chip has 2.75 billion transistors. The superimposed labels indicate how the silicon real estate of the chip is allocated. We see that this chip has six cores, or processors. In addition, there are two large areas labeled L3 cache, which are shared by all six processors. The L3 control logic controls traffic between the L3 cache and the cores and between the L3 cache and the external environment. Additionally, there is stor- age control (SC) logic between the cores and the L3 cache. The memory controller (MC) function controls access to memory external to the chip. The GX I/O bus controls the interface to the channel adapters accessing the I/O. 

Going down one level deeper, we examine the internal structure of a single core, as shown in the photograph of Figure 1.5. Keep in mind that this is a portion of the silicon surface area making up a single\-processor chip. The main sub\-areas within this core area are the following: 

■ **ISU (instruction sequence unit):** Determines the sequence in which instructions are executed in what is referred to as a superscalar architecture (Chapter 16\). 

■ **IFU (instruction fetch unit):** Logic for fetching instructions. 

10 **CHAPTER** 1 / BASIC CONCEPTS AND COMPUTER EVOLUTION 

RU   
**IFU** 

**G**   
CORE CORE   
**CORE M**   
**ISU**   
BFU   
C   
**X**   
**1/a**   
**FXU** 

ilo 

**SC** VO   
**SC fo**   
**I\-cache** 

E3:   
G   
L3 

Cache Control   
**L3** 

Cache   
**LSU** 

XU 

**SC** lam   
**SO 16**   
**L2** 

**G** 

**X**   
CORE   
CORE   
CORE   
**Instr** 

L2   
**Control**   
**Data\-L2** 

1/0   
lo 

**COP** 

**Figure 1.4** zEnterprise EC12 Processor Unit (PU) chip diagram 

*Source:* IBM zEnterprise EC12 Technical Guide, December 2013, SG24-8049-01. IBM, Reprinted by Permission   
**Figure 1.5** zEnterprise EC12 Core layout *Source:* IBM zEnterprise EC12 Technical Guide, December 2013, SG24-8049-01. IBM, Reprinted by Permission 

■ **IDU (instruction decode unit):** The IDU is fed from the IFU buffers, and is responsible for the parsing and decoding of all z/Architecture operation codes. 

■ **LSU (load-store unit):** The LSU contains the 96-kB L1 data cache,1 and man- ages data traffic between the L2 data cache and the functional execution units. It is responsible for handling all types of operand accesses of all lengths, modes, and formats as defined in the z/Architecture. 

■ **XU (translation unit)**: This unit translates logical addresses from instructions into physical addresses in main memory. The XU also contains a translation lookaside buffer (TLB) used to speed up memory access. TLBs are discussed in Chapter 8. 

■ **FXU (fixed\-point** unit**):** The FXU executes fixed\-point arithmetic operations. 

■ **BFU (binary floating\-point unit):** The BFU handles all binary and hexadeci- mal floating\-point operations, as well as fixed\-point multiplication operations. 

■ **DFU (decimal floating\-point unit):** The DFU handles both fixed\-point and floating\-point operations on numbers that are stored as decimal digits. 

■**RU (recovery unit):** The RU keeps a copy of the complete state of the **sys-** tem that includes all registers, collects hardware fault signals, and manages the hardware recovery actions. 

1kB \= kilobyte \= 2048 bytes. Numerical prefixes are explained in a document under the "Other Useful" tab at ComputerScienceStudent.com. 

1.3 / A BRIEF **HISTORY** OF COMPUTERS **11** 

■ **COP (dedicated co\-processor):** The COP is responsible for data compression and encryption functions for each core. 

■ **I\-cache:** This is a 64\-kB L1 instruction cache, allowing the IFU to prefetch instructions before they are needed. 

**L2 control:** This is the control logic that manages the traffic through the two L2 caches. 

■ **Data\-L2:** A 1\-MB L2 data cache for all memory traffic other than instructions. 

**Instr-L2:** A 1\-MB L2 instruction cache. 

As we progress through the book, the concepts introduced in this section will become clearer. 

**1.3** A **BRIEF HISTORY OF COMPUTERS2** 

In this section, we provide a brief overview of the history of the development of computers. This history is interesting in itself, but more importantly, provides a basic introduction to many important concepts that we deal with throughout the book. 

**The First Generation: Vacuum Tubes** 

The first generation of computers used vacuum tubes for digital logic elements and memory. A number of research and then commercial computers were built using vacuum tubes. For our purposes, it will be instructive to examine perhaps the most famous first\-generation computer, known as the IAS computer. 

A fundamental design approach first implemented in the IAS computer is known as the *stored\-program concept.* This idea is usually attributed to the mathem- atician John von Neumann. Alan Turing developed the idea at about the same time. The first publication of the idea was in a 1945 proposal by von Neumann for a new computer, the EDVAC (Electronic Discrete Variable Computer).3 

In 1946, von Neumann and his colleagues began the design of a new stored- program computer, referred to as the IAS computer, at the Princeton Institute for Advanced Studies. The IAS computer, although not completed until 1952, is the prototype of all subsequent general\-purpose computers.4 

Figure 1.6 shows the structure of the IAS computer (compare with Figure 1.1). It consists of 

■ A **main memory**, which stores both data and instructions5 

■ An **arithmetic and logic unit** (**ALU)** capable of operating on binary data 

2This book's Companion Web site (WilliamStallings.com/ComputerOrganization) contains several links to sites that provide photographs of many of the devices and components discussed in this section. 3The 1945 report on EDVAC is available at box.com/COA10e. 

4A 1954 report \[GOLD54\] describes the implemented IAS machine and lists the final instruction set. It 

is available at box.com/COA10e. 

"In this book, unless otherwise noted, the term *instruction* refers to a machine instruction that is directly interpreted and executed by the processor, in contrast to a statement in a high\-level language, such as Ada or C\++, which must first be compiled into a series of machine instructions before being executed. 

**12** CHAPTER 1 / BASIC CONCEPTS AND COMPUTER EVOLUTION 

**Central processing unit (CPU)** 

**Arithmetic\-logic unit (CA)** 

**Instructions and data**   
**AC** 

**Arithmetic\-logic** 

**circuits** 

**MBR**   
**MQ** 

**M(0)** 

**M(1**) 

**M(2)** 

**M(3)**   
**PC**   
**IBR** 

**M(4)** 

**MAR**   
**IR** 

**Main** 

**memory** 

**(M)** 

**Control signals**   
**Control** 

**circuits** 

**M(4092)** 

**M(4093)** 

**M(4095)**   
**Program control unit (CC)** 

**Addresses** 

**Figure 1.6** IAS Structure   
**Input-** 

**output equipment** 

**(I, O)** 

**Instructions and data** 

AC: Accumulator register MQ: multiply\-quotient register MBR: memory buffer register IBR: instruction buffer register PC: program counter 

MAR: memory address register IR: insruction register 

■ A **control unit**, which interprets the instructions in memory and causes them to be executed 

■ **Input\-output (**I/**O**) equipment operated by the control unit 

This structure was outlined in von Neumann's earlier proposal, which is worth quoting in part at this point \[VONN45\]: 

2.2 **First:** Since the device is primarily a computer, it will have to perform the elementary operations of arithmetic most fre- quently. These are addition, subtraction, multiplication, and divi- sion. It is therefore reasonable that it should contain specialized organs for just these operations. 

1.3 / A BRIEF **HISTORY** OF COMPUTERS **13** 

It must be observed, however, that while this principle as such is probably sound, the specific way in which it is realized requires close scrutiny. At any rate a *central arithmetical* part of the device will probably have to exist, and this constitutes *the first specific part: CA.* 

2.3 **Second:** The logical control of the device, that is, the proper sequencing of its operations, can be most efficiently car- ried out by a central control organ. If the device is to be *elastic*, that is, as nearly as possible *all purpose,* then a distinction must be made between the specific instructions given for and defining a particular problem, and the general control organs that see to it that these instructions—no matter what they are — are carried out. The former must be stored in some way; the latter are represented by definite operating parts of the device. By the *central control* we mean this latter function only, and the organs that perform it form *the second specific part: CC*.   
\- 

2.4 **Third:** Any device that is to carry out long and compli- cated sequences of operations (specifically of calculations) must have a considerable memory 

The instructions which govern a complicated problem may constitute considerable material, particularly so if the code is cir- cumstantial (which it is in most arrangements). This material must be remembered. 

At any rate, the total *memory* constitutes *the third specific part of the device: M.* 

2.6 The three specific parts CA, CC (together C), and M cor- respond to the *associative* neurons in the human nervous system. It remains to discuss the equivalents of the *sensory* or *afferent* and the *motor* or *efferent* neurons. These are the *input* and *output* organs of the device. 

The device must be endowed with the ability to maintain input and output (sensory and motor) contact with some specific medium of this type. The medium will be called the *outside record- ing medium of the device: R.* 

2.7 **Fourth:** The device must have organs to transfer informa- tion from R into its specific parts C and M. These organs form its *input*, the *fourth specific part: I.* It will be seen that it is best to make all transfers from R (by I) into M and never directly from C. 

2.8 **Fifth:** The device must have organs to transfer from its specific parts C and M into R. These organs form its *output, the fifth specific part*: *O.* It will be seen that it is again best to make all transfers from M (by O) into R, and never directly from C. 

With rare exceptions, all of today's computers have this same general structure and function and are thus referred to as *von Neumann machines.* Thus, it is worth- while at this point to describe briefly the operation of the IAS computer \[BURK46, GOLD54\]. Following \[HAYE98\], the terminology and notation of von Neumann 

**14** CHAPTER 1 / **BASIC** CONCEPTS AND **COMPUTER EVOLUTION** 

are changed in the following to conform more closely to modern usage; the exam- ples accompanying this discussion are based on that latter text. 

The memory of the IAS consists of 4,096 storage locations, called *words,* of 40 binary digits (bits) each. Both data and instructions are stored there. Numbers are represented in binary form, and each instruction is a binary code. Figure 1.7 illustrates these formats. Each number is represented by a sign bit and a 39\-bit value. A word may alternatively contain two 20\-bit instructions, with each instruction consisting of an 8\-bit operation code (opcode) specifying the operation to be performed and a 12\-bit address designating one of the words in memory (numbered from 0 to 999\). 

The control unit operates the IAS by fetching instructions from memory and executing them one at a time. We explain these operations with reference to Figure 1.6. This figure reveals that both the control unit and the ALU contain stor- age locations, called *registers*, defined as follows: 

■ **Memory buffer register (MBR):** Contains a word to be stored in memory or sent to the I/O unit, or is used to receive a word from memory or from the I/O unit. 

■ **Memory address register** (**MAR):** Specifies the address in memory of the word to be written from or read into the MBR. 

■ **Instruction register (IR):** Contains the 8\-bit opcode instruction being executed. 

■ **Instruction buffer register (IBR):** Employed to hold temporarily the right- hand instruction from a word in memory. 

■ **Program counter (PC):** Contains the address of the next instruction pair to be fetched from memory. 

■ **Accumulator (AC) and multiplier quotient (MQ):** Employed to hold tem- porarily operands and results of ALU operations. For example, the result 

**0 1** 

**sign bit** 

**left instruction (20 bits)** 

**8**   
(a) Number word   
**39** 

**right instruction (20 bits**) 

**20**   
**28**   
**39** 

**opcode (8 bits)**   
**address (12 bits)**   
**opcode (8 bits)**   
**address (12 bits)** 

(b) Instruction word 

**Figure 1.7** IAS Memory Formats 

"There is no universal definition of the term *word.* In general, a word is an ordered set of bytes or bits that is the normal unit in which information may be stored, transmitted, or operated on within a given computer. Typically, if a processor has a fixed\-length instruction set, then the instruction length equals the word length. 

1.3 / A BRIEF HISTORY OF COMPUTERS **15** 

of multiplying two 40\-bit numbers is an 80\-bit number; the most significant 40 bits are stored in the AC and the least significant in the MQ. 

The IAS operates by repetitively performing an *instruction cycle,* as shown in Figure 1.8. Each instruction cycle consists of two subcycles. During the *fetch cycle,* the opcode of the next instruction is loaded into the IR and the address portion is loaded into the MAR. This instruction may be taken from the IBR, or it can be obtained from memory by loading a word into the MBR, and then down to the IBR, IR, and MAR. 

Why the indirection? These operations are controlled by electronic circuitry and result in the use of data paths. To simplify the electronics, there is only one reg- ister that is used to specify the address in memory for a read or write and only one register used for the source or destination. 

**Start** 

**Yes**   
**Is next instruction**   
**No** 

**MAR-PC** 

**No memory**   
**in IBR?**   
**Fetch cycle**   
**access** 

**required**   
**MBRM(MAR)**| 

**Left** 

**IR IBR (0:7)**   
**IR MBR (20:27)**   
**No**   
**Yes**   
**IBR**   
**MBR (20:39)** 

**| MAR←IBR (8:19)**| **|MAR←MBR (28:39)**   
**instruction required?**   
**IR**   
**MBR (0:7)** 

**MAR**   
**MBR (8:19)** 

**PC PC \+1** 

**Decode instruction in IR** 

**ACM(X) Go to M(X, 0:19)** 

**Execution cycle**   
**If AC \> 0 then go to M(X, 0:19)** 

**Yes**   
**AC AC+ M(X)** 

**Is AC \> 0?** 

**MBR\-M(MAR)**   
**PC**\-**MAR** 

**AC MBR** 

**M(X) \= contents of memory location whose address is X (i:j) \= bits i through j** 

**Figure 1.8** Partial Flowchart of IAS Operation   
**No**   
**MBR M(MAR)** 

**AC AC\+ MBR** 

**16** CHAPTER 1 / **BASIC** CONCEPTS AND COMPUTER **EVOLUTION** 

Once the opcode is in the IR, the *execute cycle* is performed. Control circuitry interprets the opcode and executes the instruction by sending out the appropri- ate control signals to cause data to be moved or an operation to be performed by the ALU. 

The IAS computer had a total of 21 instructions, which are listed in Table 1.1. These can be grouped as follows: 

■ **Data transfer:** Move data between memory and ALU registers or between two ALU registers. 

■ **Unconditional branch:** Normally, the control unit executes instructions in sequence from memory. This sequence can be changed by a branch instruc- tion, which facilitates repetitive operations. 

**Table 1.1** The IAS Instruction Set 

**Instruction Туре**   
**Symbolic Representation**   
**Opcode** 

00001010   
LOAD MQ 

00001001 LOAD MQ,M(X)   
Transfer contents of memory location X to MQ 

00100001   
STOR M(X) 

Data transfer 

Unconditional branch   
00000001 LOAD M(X) 00000010 LOAD \-M(X) 

00000011 LOAD M(X)| 00000100 LOAD \-M(X)| 00001101 JUMP M(X,0:19) 00001110 JUMP M(X,20:39) 00001111 JUMP \+ M(X,0:19)   
**Description** 

Transfer contents of register MQ to the accumulator AC 

Transfer contents of accumulator to memory location X 

Transfer M(X) to the accumulator 

Transfer \-M(X) to the accumulator 

Transfer absolute value of M(X) to the accumulator 

Conditional branch   
00010000 

00000101 ADD M(X) 00000111 ADD M(X) 

00000110 SUB M(X) 

00001000 SUB M(X) 

Arithmetic   
00001011   
MUL M(X) 

00001100   
DIV M(X) 

00010100 LSH   
Transfer \-|M(X)| to the accumulator 

Take next instruction from left half of M(X) 

Take next instruction from right half of M(X) 

If number in the accumulator is nonnegative, take next instruction from left half of M(X) 

JUMP \+ M(X,20:39) If number in the accumulator is nonnegative, take next 

instruction from right half of M(X) 

00010101 RSH 

00010010 STOR M(X,8:19) 

Address modify   
00010011   
STOR M(X,28:39)   
Add M(X) to AC; put the result in AC 

Add |M(X) to AC; put the result in AC 

Subtract M(X) from AC; put the result in AC 

Subtract |M(X) from AC; put the remainder in AC 

Multiply M(X) by MQ; put most significant bits of result in AC, put least significant bits in MQ 

Divide AC by M(X); put the quotient in MQ and the remainder in AC 

Multiply accumulator by 2; that is, shift left one bit position 

Divide accumulator by 2; that is, shift right one position 

Replace left address field at M(X) by 12 rightmost bits of AC 

Replace right address field at M(X) by 12 rightmost bits of AC 

1.3 / A BRIEF HISTORY OF COMPUTERS **17** 

■ **Conditional branch:** The branch can be made dependent on a condition, thus allowing decision points. 

■ **Arithmetic:** Operations performed by the ALU. 

**Address modify:** Permits addresses to be computed in the ALU and then inserted into instructions stored in memory. This allows a program consider- able addressing flexibility. 

Table 1.1 presents instructions (excluding I/O instructions) in a symbolic, easy\-to\-read form. In binary form, each instruction must conform to the format of Figure 1.7b. The opcode portion (first 8 bits) specifies which of the 21 instructions is to be executed. The address portion (remaining 12 bits) specifies which of the 4,096 memory locations is to be involved in the execution of the instruction. 

Figure 1.8 shows several examples of instruction execution by the control unit. Note that each operation requires several steps, some of which are quite elaborate. The multiplication operation requires 39 suboperations, one for each bit position except that of the sign bit. 

**The Second Generation: Transistors** 

The first major change in the electronic computer came with the replacement of the vacuum tube by the transistor. The transistor, which is smaller, cheaper, and gener- ates less heat than a vacuum tube, can be used in the same way as a vacuum tube to construct computers. Unlike the vacuum tube, which requires wires, metal plates, a glass capsule, and a vacuum, the transistor is a *solid\-state device*, made from silicon. 

The transistor was invented at Bell Labs in 1947 and by the 1950s had launched an electronic revolution. It was not until the late 1950s, however, that fully transis- torized computers were commercially available. The use of the transistor defines the *second generation* of computers. It has become widely accepted to classify com- puters into generations based on the fundamental hardware technology employed **(**Table 1.2). Each new generation is characterized by greater processing perfor- mance, larger memory capacity, and smaller size than the previous one. 

But there are other changes as well. The second generation saw the intro- duction of more complex arithmetic and logic units and control units, the use of high\-level programming languages, and the provision of *system software* with the 

**Table 1.2** Computer Generations 

**Approximate** 

**Generation** 

1   
**Dates** 

1946-1957   
**Technology**   
**Typical Speed (operations per second)** 

Vacuum tube   
40,000 

2   
1957-1964   
Transistor   
200,000 

3   
1965-1971   
Small- and medium\-scale integration   
1,000,000 

4 5   
1972-1977   
Large scale integration 

1978-1991   
Very large scale integration 

6   
1991-   
Ultra large scale integration   
10,000,000 

100,000,000 

\>1,000,000,000 

**18** CHAPTER 1 / **BASIC** CONCEPTS AND COMPUTER **EVOLUTION** 

computer. In broad terms, system software provided the ability to load programs, move data to peripherals, and libraries to perform common computations, similar to what modern operating systems, such as Windows and Linux, do. 

It will be useful to examine an important member of the second generation: the IBM 7094 \[BELL71\]. From the introduction of the 700 series in 1952 to the introduc- tion of the last member of the 7000 series in 1964, this IBM product line underwent an evolution that is typical of computer products. Successive members of the product line showed increased performance, increased capacity, and/or lower cost.   
The size of main memory, in multiples of 210 36\-bit words, grew from 2k (1k \= 210\) to 32k words, while the time to access one word of memory, the *mem- ory cycle time,* fell from 30 us to 1.4 *μs*. The number of opcodes grew from a modest 24 to 185. 

Also, over the lifetime of this series of computers, the relative speed of the CPU increased by a factor of 50\. Speed improvements are achieved by improved electronics (e.g., a transistor implementation is faster than a vacuum tube imple- mentation) and more complex circuitry. For example, the IBM 7094 includes an Instruction Backup Register, used to buffer the next instruction. The control unit fetches two adjacent words from memory for an instruction fetch. Except for the occurrence of a branching instruction, which is relatively infrequent (perhaps 10 to 15%), this means that the control unit has to access memory for an instruction on only half the instruction cycles. This prefetching significantly reduces the average instruction cycle time. 

Figure 1.9 shows a large (many peripherals) configuration for an IBM 7094, which is representative of second\-generation computers. Several differences from the IAS computer are worth noting. The most important of these is the use of *data channels*. A data channel is an independent I/O module with its own processor and instruction set. In a computer system with such devices, the CPU does not execute detailed I/O instructions. Such instructions are stored in a main memory to be executed by a special\-purpose processor in the data channel itself. The CPU initi- ates an I/O transfer by sending a control signal to the data channel, instructing it to execute a sequence of instructions in memory. The data channel performs its task independently of the CPU and signals the CPU when the operation is complete. This arrangement relieves the CPU of a considerable processing burden. 

Another new feature is the *multiplexor*, which is the central termination point for data channels, the CPU, and memory. The multiplexor schedules access to the memory from the CPU and data channels, allowing these devices to act independently. 

**The Third Generation: Integrated Circuits** 

A single, self\-contained transistor is called a *discrete component*. Throughout the 1950s and early 1960s, electronic equipment was composed largely of discrete components\-transistors, resistors, capacitors, and so on. Discrete components were manufactured separately, packaged in their own containers, and soldered or wired 

7A discussion of the uses of numerical prefixes, such as kilo and giga, is contained in a supporting docu- ment at the Computer Science Student Resource Site at ComputerScienceStudent.com. 

1.3 / A BRIEF HISTORY OF COMPUTERS 19 

**Peripheral devices** 

**Mag tape**   
**IBM 7094 computer** 

**CPU**   
**units** 

**Card** 

**Data** 

**channel**   
**punch** 

**Line printer** 

**Card reader** 

**Drum** 

**Multi- plexor**   
**Data** 

**channel** 

**Disk** 

**Memory**   
**Data channel**   
**Disk** 

**Hyper- tapes** 

**Data** 

**channel**   
**Teleprocessing equipment** 

**Figure 1.9** An IBM 7094 Configuration 

together onto Masonite\-like circuit boards, which were then installed in computers, oscilloscopes, and other electronic equipment. Whenever an electronic device called for a transistor, a little tube of metal containing a pinhead\-sized piece of silicon had to be soldered to a circuit board. The entire manufacturing process, from transistor to circuit board, was expensive and cumbersome. 

These facts of life were beginning to create problems in the computer indus- try. Early second\-generation computers contained about 10,000 transistors. This figure grew to the hundreds of thousands, making the manufacture of newer, more powerful machines increasingly difficult. 

In 1958 came the achievement that revolutionized electronics and started the era of microelectronics: the invention of the integrated circuit. It is the integrated circuit that defines the third generation of computers. In this section, we provide a brief introduction to the technology of integrated circuits. Then we look at perhaps the two most important members of the third generation, both of which were intro- duced at the beginning of that era: the IBM System/360 and the DEC PDP\-8. 

***MICROELECTRONICS*** Microelectronics means, literally, "small electronics." Since the beginnings of digital electronics and the computer industry, there has been a persistent and consistent trend toward the reduction in size of digital electronic circuits. Before examining the implications and benefits of this trend, we need to say something about the nature of digital electronics. A more detailed discussion is found in Chapter 11. 

**20** CHAPTER 1 / BASIC CONCEPTS AND **COMPUTER EVOLUTION** 

The basic elements of a digital computer, as we know, must perform data stor- age, movement, processing, and control functions. Only two fundamental types of components are required (Figure 1.10): gates and memory cells. A **gate** is a device that implements a simple Boolean or logical function. For example, an AND gate with inputs *A* and *B* and output *C* implements the expression IF *A* AND *B* ARE TRUE THEN *C* IS TRUE. Such devices are called gates because they control data flow in much the same way that canal gates control the flow of water. The **memory cell** is a device that can store 1 bit of data; that is**,** the device can be in one of two stable states at any time. By interconnecting large numbers of these fundamental devices, we can construct a computer. We can relate this to our four basic functions as follows: 

■ **Data storage:** Provided by memory cells. 

■ **Data processing:** Provided by gates. 

■ **Data movement:** The paths among components are used to move data from memory to memory and from memory through gates to memory. 

■**Control:** The paths among components can carry control signals. For example, a gate will have one or two data inputs plus a control signal input that activates the gate. When the control signal is ON, the gate performs its function on the data inputs and produces a data output. Conversely, when the control signal is OFF, the output line is null, such as the one produced by a high impedance state. Similarly, the memory cell will store the bit that is on its input lead when the WRITE control signal is ON and will place the bit that is in the cell on its output lead when the READ control signal is ON. 

Thus, a computer consists of gates, memory cells, and interconnections among these elements. The gates and memory cells are, in turn, constructed of simple elec- tronic components, such as transistors and capacitors. 

The integrated circuit exploits the fact that such components as transistors, resistors, and conductors can be fabricated from a semiconductor such as silicon. It is merely an extension of the solid\-state art to fabricate an entire circuit in a tiny piece of silicon rather than assemble discrete components made from separate pieces of silicon into the same circuit. Many transistors can be produced at the same time on a single wafer of silicon. Equally important, these transistors can be con- nected with a process of metallization to form circuits. 

**Input**   
**Boolean logic function**   
**Output**   
**Input**   
**Binary storage cell**   
**Output** 

**Activate signal**   
**Read** 

**Write** 

(a) Gate 

**Figure 1.10** Fundamental Computer Elements   
(b) Memory cell 

1.3 / A **BRIEF** HISTORY OF COMPUTERS **21** 

Figure 1.11 depicts the key concepts in an integrated circuit. A thin *wafer* of silicon is divided into a matrix of small areas, each a few millimeters square. The identical circuit pattern is fabricated in each area, and the wafer is broken up into *chips*. Each chip consists of many gates and/or memory cells plus a number of input and output attachment points. This chip is then packaged in housing that protects it and provides pins for attachment to devices beyond the chip. A number of these packages can then be interconnected on a printed circuit board to produce larger and more complex circuits. 

Initially, only a few gates or memory cells could be reliably manufactured and packaged together. These early integrated circuits are referred to as **small**\-**scale integration (SSI**). As time went on, it became possible to pack more and more com- ponents on the same chip. This growth in density is illustrated in Figure 1.12; it is one of the most remarkable technological trends ever recorded. This figure reflects the famous Moore's law, which was propounded by Gordon Moore, cofounder of Intel, in 1965 \[MOOR65\]. Moore observed that the number of transistors that could be put on a single chip was doubling every year, and correctly predicted that this pace would continue into the near future. To the surprise of many, including Moore, the pace continued year after year and decade after decade. The pace slowed to a doubling every 18 months in the 1970s but has sustained that rate ever since. 

The consequences of Moore's law are profound: 

**1\.** The cost of a chip has remained virtually unchanged during this period of rapid growth in density. This means that the cost of computer logic and memory cir- cuitry has fallen at a dramatic rate. 

**Packaged chip**   
**Wafer** 

**Chip** 

**Figure** 1.11 Relationship among   
Wafer, Chip, and Gate   
**Gate** 

Note that the vertical axis uses a log scale. A basic review of log scales is in the math refresher document at the Computer Science Student Resource Site at ComputerScienceStudent.com. 

**22 CHAPTER** 1 / BASIC **CONCEPTS** AND COMPUTER EVOLUTION 

**2\.** Because logic and memory elements are placed closer together on more densely packed chips, the electrical path length is shortened, increasing oper- ating speed. 

**3\.** The computer becomes smaller, making it more convenient to place in a vari- 

ety of environments. 

4\. There is a reduction in power requirements. 

**5\.** The interconnections on the integrated circuit are much more reliable than solder connections. With more circuitry on each chip, there are fewer inter- chip connections. 

***IBM*** **SYSTEM*/360*** By 1964, IBM had a firm grip on the computer market with its 7000 series of machines. In that year, IBM announced the System/360, a new family of computer products. Although the announcement itself was no surprise, it contained some unpleasant news for current IBM customers: the 360 product line was incompatible with older IBM machines. Thus, the transition to the 360 would be difficult for the current customer base, but IBM felt this was necessary to break out of some of the constraints of the 7000 architecture and to produce a system capable of evolving with the new integrated circuit technology \[PADE81, GIFF87\]. The strategy paid off both financially and technically. The 360 was the success of the decade and cemented IBM as the overwhelmingly dominant computer vendor, with a market share above 70%. And, with some modifications and extensions, the architecture of the 360 remains to this day the architecture of IBM's mainframe9 computers. Examples using this architecture can be found throughout this text. 

The System/360 was the industry's first planned family of computers. The family covered a wide range of performance and cost. The models were compatible in the 

**First working**   
**transistor**   
**Invention of integrated circuit**   
**Moore's law promulgated**   
**100 bn** 

**10 bn** 

1 **bn** 

**100 m** 

**10 m** 

**100,000** 

**10,000** 

**1,000** 

**100** 

**10** 

**1** 

**1947 50 55 60**   
**65**   
**70**   
**75**   
**80**   
**85**   
90   
**95 2000**   
**05**   
**11** 

**Figure 1.12** Growth in Transistor Count on Integrated Circuits 

'The term *mainframe* is used for the larger, most powerful computers other than supercomputers. Typical characteristics of a mainframe are that it supports a large database, has elaborate I/O hardware, and is used in a central data processing facility. 

1.3 / A BRIEF HISTORY OF COMPUTERS **23** 

sense that a program written for one model should be capable of being executed by another model in the series, with only a difference in the time it takes to execute. 

The concept of a family of compatible computers was both novel and extremely successful. A customer with modest requirements and a budget to match could start with the relatively inexpensive Model 30\. Later, if the customer's needs grew, it was possible to upgrade to a faster machine with more memory without sacrificing the investment in already\-developed software. The characteristics of a family are as follows: 

**Similar or identical instruction set:** In many cases, the exact same set of machine instructions is supported on all members of the family. Thus, a pro- gram that executes on one machine will also execute on any other. In some cases, the lower end of the family has an instruction set that is a subset of that of the top end of the family. This means that programs can move up but not down. 

■ **Similar or identical operating system:** The same basic operating system is available for all family members. In some cases, additional features are added to the higher\-end members. 

**Increasing speed:** The rate of instruction execution increases in going from lower to higher family members. 

■ **Increasing number of I**/**O ports**: The number of I/O ports increases in going from lower to higher family members. 

■ **Increasing memory size:** The size of main memory increases in going from lower to higher family members. 

■ **Increasing cost:** At a given point in time, the cost of a system increases in going from lower to higher family members. 

How could such a family concept be implemented? Differences were achieved based on three factors: basic speed, size, and degree of simultaneity \[STEV64\]. For example, greater speed in the execution of a given instruction could be gained by the use of more complex circuitry in the ALU, allowing suboperations to be car- ried out in parallel. Another way of increasing speed was to increase the width of the data path between main memory and the CPU. On the Model 30, only 1 byte (8 bits) could be fetched from main memory at a time, whereas 8 bytes could be fetched at a time on the Model 75. 

The System/360 not only dictated the future course of IBM but also had a pro- found impact on the entire industry. Many of its features have become standard on other large computers. 

**DEC *PDP\-8*** In the same year that IBM shipped its first System/360, another momentous first shipment occurred: PDP\-8 from Digital Equipment Corporation (DEC). At a time when the average computer required an air\-conditioned room, the PDP\-8 (dubbed a minicomputer by the industry, after the miniskirt of the day) was small enough that it could be placed on top of a lab bench or be built into other equipment. It could not do everything the mainframe could, but at $16,000, it was cheap enough for each lab technician to have one. In contrast, the System/360 series of mainframe computers introduced just a few months before cost hundreds of thousands of dollars. 

**24 CHAPTER** 1 / BASIC **CONCEPTS** AND COMPUTER EVOLUTION 

The low cost and small size of the PDP\-8 enabled another manufacturer to purchase a PDP\-8 and integrate it into a total system for resale. These other manu- facturers came to be known as **original equipment manufacturers (OEMs)**, and the OEM market became and remains a major segment of the computer marketplace. 

In contrast to the central\-switched architecture (Figure 1.9) used by IBM on its 700/7000 and 360 systems, later models of the PDP\-8 used a structure that became vir- tually universal for microcomputers: the bus structure. This is illustrated in Figure 1.13. The PDP\-8 bus, called the Omnibus, consists of 96 separate signal paths, used to carry control, address, and data signals. Because all system components share a common set of signal paths, their use can be controlled by the CPU. This architecture is highly flexible, allowing modules to be plugged into the bus to create various configurations. It is only in recent years that the bus structure has given way to a structure known as point\-to\-point interconnect, described in Chapter 3. 

**Later Generations** 

Beyond the third generation there is less general agreement on defining generations of computers. Table 1.2 suggests that there have been a number of later generations, based on advances in integrated circuit technology. With the introduction of **large- scale integration (LSI)**, more than 1,000 components can be placed on a single inte- grated circuit chip. Very\-large\-scale integration (VLSI) achieved more than 10,000 components per chip, while current ultra\-large\-scale integration (ULSI) chips can contain more than one billion components. 

With the rapid pace of technology, the high rate of introduction of new prod- ucts, and the importance of software and communications as well as hardware, the classification by generation becomes less clear and less meaningful. In this section, we mention two of the most important of developments in later generations. 

***SEMICONDUCTOR MEMORY*** The first application of integrated circuit technology to computers was the construction of the processor (the control unit and the arithmetic and logic unit) out of integrated circuit chips. But it was also found that this same technology could be used to construct memories. 

In the 1950s and 1960s, most computer memory was constructed from tiny rings of ferromagnetic material, each about a sixteenth of an inch in diameter. These rings were strung up on grids of fine wires suspended on small screens inside the computer. Magnetized one way, a ring (called a *core*) represented a one; mag- netized the other way, it stood for a zero. Magnetic\-core memory was rather fast; it took as little as a millionth of a second to read a bit stored in memory. But it was 

**Console controller**   
**CPU**   
**Main** 

**memory**   
**I/O** 

**module**   
**I/O**   
− \---   
**module** 

**Omnibus** 

**Figure 1.13** PDP\-8 Bus Structure 

1.3 / A BRIEF **HISTORY** OF COMPUTERS **25** 

expensive and bulky, and used destructive readout: The simple act of reading a core erased the data stored in it. It was therefore necessary to install circuits to restore the data as soon as it had been extracted. 

Then, in 1970, Fairchild produced the first relatively capacious semiconductor memory. This chip, about the size of a single core, could hold 256 bits of memory. It was nondestructive and much faster than core. It took only 70 billionths of a second to read a bit. However, the cost per bit was higher than for that of core. 

In 1974, a seminal event occurred: The price per bit of semiconductor memory dropped below the price per bit of core memory. Following this, there has been a con- tinuing and rapid decline in memory cost accompanied by a corresponding increase in physical memory density. This has led the way to smaller, faster machines with mem- ory sizes of larger and more expensive machines from just a few years earlier. Devel- opments in memory technology, together with developments in processor technology to be discussed next, changed the nature of computers in less than a decade. Although bulky, expensive computers remain a part of the landscape, the computer has also been brought out to the “end user," with office machines and personal computers. 

Since 1970, semiconductor memory has been through 13 generations: 1k, 4k, 16k, 64k, 256k, 1M, 4M, 16M, 64M, 256M, 1G, 4G, and, as of this writing, 8 Gb on a single chip (1k \= 210,1M \= 220,1G \= 230\). Each generation has provided increased storage density, accompanied by declining cost per bit and declining access time. Densities are projected to reach 16 Gb by 2018 and 32 Gb by 2023 \[ITRS14\]. 

***MICROPROCESSORS*** Just as the density of elements on memory chips has continued to rise, so has the density of elements on processor chips. As time went on, more and more elements were placed on each chip, so that fewer and fewer chips were needed to construct a single computer processor. 

A breakthrough was achieved in 1971, when Intel developed its 4004\. The 4004 was the first chip to contain *all* of the components of a CPU on a single chip: The microprocessor was born. 

The 4004 can add two 4\-bit numbers and can multiply only by repeated addi- tion. By today's standards, the 4004 is hopelessly primitive, but it marked the begin- ning of a continuing evolution of microprocessor capability and power. 

This evolution can be seen most easily in the number of bits that the processor deals with at a time. There is no clear\-cut measure of this, but perhaps the best meas- ure is the data bus width: the number of bits of data that can be brought into or sent out of the processor at a time. Another measure is the number of bits in the accumu- lator or in the set of general\-purpose registers. Often, these measures coincide, but not always. For example, a number of microprocessors were developed that operate on 16\-bit numbers in registers but can only read and write 8 bits at a time. 

The next major step in the evolution of the microprocessor was the introduc- tion in 1972 of the Intel 8008\. This was the first 8\-bit microprocessor and was almost twice as complex as the 4004. 

Neither of these steps was to have the impact of the next major event: the introduction in 1974 of the Intel 8080\. This was the first general\-purpose micropro- cessor. Whereas the 4004 and the 8008 had been designed for specific applications, the 8080 was designed to be the CPU of a general\-purpose microcomputer. Like the 

**26 CHAPTER** 1 / BASIC CONCEPTS AND COMPUTER EVOLUTION 

8008, the 8080 is an 8\-bit microprocessor. The 8080, however, is faster, has a richer instruction set, and has a large addressing capability. 

About the same time, 16\-bit microprocessors began to be developed. How- ever, it was not until the end of the 1970s that powerful, general\-purpose 16\-bit microprocessors appeared. One of these was the 8086\. The next step in this trend occurred in 1981, when both Bell Labs and Hewlett\-Packard developed 32\-bit, single\-chip microprocessors. Intel introduced its own 32\-bit microprocessor, the 80386, in 1985 (Table 1.3). 

**Table 1.3** Evolution of Intel Microprocessors (page 1 of 2\) 

**(a) 1970s Processors** 

Introduced   
**4004** 

1971   
**8008**   
**8080**   
**8086**   
**8088** 

1972   
1974   
1978   
1979 

Clock speeds   
108 kHz   
108 kHz   
2 MHz   
5 MHz, 8 MHz, 10 MHz   
5 MHz, 8 MHz 

Bus width   
4 bits   
8 bits   
8 bits   
16 bits   
8 bits 

Number of transistors 

Feature size (um) 

Addressable memory   
2,300 

10 

640 bytes   
3,500 

8   
6,000 

6   
29,000 

3   
29,000 

6 

16 KB   
64 KB   
1 MB   
1 MB 

**(b) 1980s Processors** 

**80286** 

Introduced   
1982   
**386TM DX** 

1985 

Clock speeds   
6–12.5 MHz   
16-33 MHz   
**386TM** SX 

1988 

16-33 MHz   
**486TM DX CPU** 

1989 

25-50 MHz 

Bus width 

Number of transistors 

Feature size (um)   
16 bits   
32 bits 

134,000 

1.5   
275,000 

1   
16 bits 

275,000 

1   
32 bits 

1.2 million 

0.8-1 

Addressable memory   
16 MB   
4 GB   
16 MB   
4 GB 

Virtual memory   
1 GB   
64 TB   
64 TB 

Cache   
64 TB 

8 kB 

**(c) 1990s Processors** 

**486TM** SX 

Introduced 

Clock speeds   
1991   
**Pentium** 

1993   
**Pentium Pro** 

1995 

Bus width   
16-33 MHz 

32 bits   
60-166 MHz, 

32 bits 

Number of transistors   
1.185 million   
3.1 million   
150-200 MHz 

64 bits 

5.5 million 

Feature size (um)   
1   
0.8 

Addressable memory   
4 GB   
4 GB   
0.6 

64 GB   
**Pentium II** 

1997 

200-300 MHz 

64 bits 

7.5 million 

0.35 

64 GB 

Virtual memory   
64 TB   
64 TB   
64 TB 

Cache   
8 kB   
8 kB   
512 kB L1 and   
64 TB 

512 kB L2 

1 MB L2 

1.4 / THE EVOLUTION OF THE **INTEL** x86 ARCHITECTURE **27** 

**(d) Recent Processors** 

**Pentium III** 

Introduced 

Clock speeds   
1999   
**Pentium 4** 

2000   
**Core 2 Duo**   
**Core i7 EE 4960X** 

450-660 MHz   
1.3-1.8 GHz   
2006 

1.06-1.2 GHz   
2013 

4 GHz 

Bus width   
64 bits 

Number of transistors   
9.5 million   
64 bits 

42 million 

Feature size (nm)   
250   
180 

Addressable memory   
64 GB   
64 GB   
64 bits 

167 million 

65 

64 GB   
64 bits 

1.86 billion 

22 

64 GB 

Virtual memory   
64 TB   
64 TB   
64 TB 

Cache   
512 kB L2   
256 kB L2   
2 MB L2 

Number of cores   
1   
1   
2   
64 TB 

1.5 MB L2/15 MB L3 

6 

**1.4 THE EVOLUTION OF THE INTEL x86 ARCHITECTURE** 

Throughout this book, we rely on many concrete examples of computer design and implementation to illustrate concepts and to illuminate trade\-offs. Numerous sys- tems, both contemporary and historical, provide examples of important computer architecture design features. But the book relies principally on examples from two processor families: the Intel x86 and the ARM architectures. The current x86 offer- ings represent the results of decades of design effort on **complex instruction set com- puters (CISCs)**. The x86 incorporates the sophisticated design principles once found only on mainframes and supercomputers and serves as an excellent example of CISC design. An alternative approach to processor design is the **reduced instruction set computer (RISC).** The ARM architecture is used in a wide variety of embedded sys- tems and is one of the most powerful and best\-designed RISC\-based systems on the market. In this section and the next, we provide a brief overview of these two systems. In terms of market share, Intel has ranked as the number one maker of micro- processors for non\-embedded systems for decades, a position it seems unlikely to yield. The evolution of its flagship microprocessor product serves as a good indica- tor of the evolution of computer technology in general. 

Table 1.3 shows that evolution. Interestingly, as microprocessors have grown faster and much more complex, Intel has actually picked up the pace. Intel used to develop microprocessors one after another, every four years. But Intel hopes to keep rivals at bay by trimming a year or two off this development time, and has done so with the most recent x86 generations.1 

10 Intel refers to this as the *tick\-tock model.* Using this model, Intel has successfully delivered next- generation silicon technology as well as new processor microarchitecture on alternating years for the past several years. See http://www.intel.com/content/www/us/en/silicon-innovations/intel-tick-tock- model\-general.html. 

**28** CHAPTER 1 / BASIC CONCEPTS AND **COMPUTER EVOLUTION** 

It is worthwhile to list some of the highlights of the evolution of the Intel prod- uct line: 

■ **8080:** The world's first general\-purpose microprocessor. This was an 8\-bit machine, with an 8\-bit data path to memory. The 8080 was used in the first personal computer, the Altair. 

■ **8086:** A far more powerful, 16\-bit machine. In addition to a wider data path and larger registers, the 8086 sported an instruction cache, or queue, that prefetches a few instructions before they are executed. A variant of this pro- cessor, the 8088, was used in IBM's first personal computer, securing the suc- cess of Intel. The 8086 is the first appearance of the x86 architecture. 

■ **80286:** This extension of the 8086 enabled addressing a 16\-MB memory instead of just 1 MB. 

■ **80386:** Intel's first 32\-bit machine, and a major overhaul of the product. With a 32\-bit architecture, the 80386 rivaled the complexity and power of minicom- puters and mainframes introduced just a few years earlier. This was the first Intel processor to support multitasking, meaning it could run multiple pro- grams at the same time. 

■ **80486:** The 80486 introduced the use of much more sophisticated and power- ful cache technology and sophisticated instruction pipelining. The 80486 also offered a built\-in math coprocessor, offloading complex math operations from the main CPU. 

■ **Pentium:** With the Pentium, Intel introduced the use of superscalar tech- niques, which allow multiple instructions to execute in parallel. 

■ **Pentium Pro:** The Pentium Pro continued the move into superscalar organiza- tion begun with the Pentium, with aggressive use of register renaming, branch prediction, data flow analysis, and speculative execution. 

■ **Pentium II:** The Pentium II incorporated Intel MMX technology, which is designed specifically to process video, audio, and graphics data efficiently. 

■ **Pentium III:** The Pentium III incorporates additional floating\-point instruc- tions: The Streaming SIMD Extensions (SSE) instruction set extension added 70 new instructions designed to increase performance when exactly the same operations are to be performed on multiple data objects. Typical applications are digital signal processing and graphics processing. 

■ **Pentium 4:** The Pentium 4 includes additional floating\-point and other enhancements for multimedia.1   
11 

**■ Core:** This is the first Intel x86 microprocessor with a dual core, referring to the implementation of two cores on a single chip. 

■ **Core 2:** The Core 2 extends the Core architecture to 64 bits. The Core 2 Quad provides four cores on a single chip. More recent Core offerings have up to 10 cores per chip. An important addition to the architecture was the Advanced Vector Extensions instruction set that provided a set of 256\-bit, and then 512- bit, instructions for efficient processing of vector data. 

11With the Pentium 4, Intel switched from Roman numerals to Arabic numerals for model numbers. 

1.5 / EMBEDDED SYSTEMS **29** 

Almost 40 years after its introduction in 1978, the x86 architecture continues to dominate the processor market outside of embedded systems. Although the organiza- tion and technology of the x86 machines have changed dramatically over the decades, the instruction set architecture has evolved to remain backward compatible with ear- lier versions. Thus, any program written on an older version of the x86 architecture can execute on newer versions. All changes to the instruction set architecture have involved additions to the instruction set, with no subtractions. The rate of change has been the addition of roughly one instruction per month added to the architecture \[ANTH08\], so that there are now thousands of instructions in the instruction set. 

The x86 provides an excellent illustration of the advances in computer hard- ware over the past 35 years. The 1978 8086 was introduced with a clock speed of 5 MHz and had 29,000 transistors. A six\-core Core i7 EE 4960X introduced in 2013 operates at 4 GHz, a speedup of a factor of 800, and has 1.86 billion transistors, about 64,000 times as many as the 8086\. Yet the Core i7 EE 4960X is in only a slightly larger package than the 8086 and has a comparable cost. 

**1.5 EMBEDDED SYSTEMS** 

The term *embedded system* refers to the use of electronics and software within a product, as opposed to a general\-purpose computer, such as a laptop or desktop sys- tem. Millions of computers are sold every year, including laptops, personal comput- ers, workstations, servers, mainframes, and supercomputers. In contrast, billions of computer systems are produced each year that are embedded within larger devices. Today, many, perhaps most, devices that use electric power have an embedded com- puting system. It is likely that in the near future virtually all such devices will have embedded computing systems. 

Types of devices with embedded systems are almost too numerous to list. Examples include cell phones, digital cameras, video cameras, calculators, micro- wave ovens, home security systems, washing machines, lighting systems, ther- mostats, printers, various automotive systems (e.g., transmission control, cruise control, fuel injection, anti\-lock brakes, and suspension systems), tennis rack- ets, toothbrushes, and numerous types of sensors and actuators in automated systems. 

Often, embedded systems are tightly coupled to their environment. This can give rise to real\-time constraints imposed by the need to interact with the environ- ment. Constraints, such as required speeds of motion, required precision of meas- urement, and required time durations, dictate the timing of software operations. If multiple activities must be managed simultaneously, this imposes more complex real\-time constraints. 

Figure 1.14 shows in general terms an embedded system organization. In addi- tion to the processor and memory, there are a number of elements that differ from the typical desktop or laptop computer: 

■ There may be a variety of interfaces that enable the system to measure, manip- ulate, and otherwise interact with the external environment. Embedded **sys-** tems often interact (sense, manipulate, and communicate) with external world through sensors and actuators and hence are typically reactive systems; a 

**30** CHAPTER 1 / BASIC CONCEPTS AND **COMPUTER EVOLUTION** 

**Human** 

**interface**   
**Custom logic** 

**Processor**   
**Memory** 

**A/D** 

**conversion**   
**D/A Conversion** 

**Sensors**   
**Actuators/** 

**indicators**   
**Diagnostic port** 

**Figure 1.14** Possible Organization of an Embedded System 

reactive system is in continual interaction with the environment and executes at a pace determined by that environment. 

■ The human interface may be as simple as a flashing light or as complicated as real\-time robotic vision. In many cases, there is no human interface. 

■ The diagnostic port may be used for diagnosing the system that is being controlled\-not just for diagnosing the computer. 

■ Special\-purpose field programmable (FPGA), application\-specific (ASIC), or even nondigital hardware may be used to increase performance or reliability. 

■ Software often has a fixed function and is specific to the application. 

Efficiency is of paramount importance for embedded systems. They are opti- mized for energy, code size, execution time, weight and dimensions, and cost. 

There are several noteworthy areas of similarity to general\-purpose computer systems as well: 

■ Even with nominally fixed function software, the ability to field upgrade to fix bugs, to improve security, and to add functionality, has become very important for embedded systems, and not just in consumer devices. 

■ One comparatively recent development has been of embedded system plat- forms that support a wide variety of apps. Good examples of this are smart- phones and audio/visual devices, such as smart TVs. 

**The Internet of Things** 

It is worthwhile to separately callout one of the major drivers in the proliferation of embedded systems. The **Internet of things (IoT)** is a term that refers to the expanding 

1.5 / EMBEDDED SYSTEMS **31** 

interconnection of smart devices, ranging from appliances to tiny sensors. A domi- nant theme is the embedding of short\-range mobile transceivers into a wide array of gadgets and everyday items, enabling new forms of communication between people and things, and between things themselves. The Internet now supports the intercon- nection of billions of industrial and personal objects, usually through cloud systems. The objects deliver sensor information, act on their environment, and, in some cases, modify themselves, to create overall management of a larger system, like a factory or city. 

The IoT is primarily driven by deeply embedded devices (defined below). These devices are low\-bandwidth, low\-repetition data\-capture, and low\-bandwidth data\-usage appliances that communicate with each other and provide data via user interfaces. Embedded appliances, such as high\-resolution video security cameras, video VoIP phones, and a handful of others, require high\-bandwidth streaming capabilities. Yet countless products simply require packets of data to be intermit- tently delivered. 

With reference to the end systems supported, the Internet has gone through roughly four generations of deployment culminating in the IoT: 

**1\. Information technology (IT):** PCs, servers, routers, firewalls, and so on, bought 

as IT devices by enterprise **IT** people and primarily using wired connectivity. **2\. Operational technology (OT):** Machines/appliances with embedded IT built by non\-IT companies, such as medical machinery, SCADA (supervisory con- trol and data acquisition), process control, and kiosks, bought as appliances by enterprise OT people and primarily using wired connectivity. 

**3\. Personal technology:** Smartphones, tablets, and eBook readers bought as IT devices by consumers (employees) exclusively using wireless connectivity and often multiple forms of wireless connectivity. 

4\. **Sensor/actuator technology:** Single\-purpose devices bought by consumers, IT, and OT people exclusively using wireless connectivity, generally of a single form, as part of larger systems. 

It is the fourth generation that is usually thought of as the IoT, and it is marked by the use of billions of embedded devices. 

**Embedded Operating Systems** 

There are two general approaches to developing an embedded operating system (OS). The first approach is to take an existing OS and adapt it for the embedded application. For example, there are embedded versions of Linux, Windows, and Mac, as well as other commercial and proprietary operating systems specialized for embedded systems. The other approach is to design and implement an OS intended solely for embedded use. An example of the latter is TinyOS, widely used in wireless sensor networks. This topic is explored in depth in \[STAL15\]. 

**Application Processors versus Dedicated Processors** 

In this subsection, and the next two, we briefly introduce some terms commonly found in the literature on embedded systems. **Application processors** are defined 

**32** CHAPTER 1 / **BASIC CONCEPTS** AND COMPUTER EVOLUTION 

by the processor's ability to execute complex operating systems, such as Linux, Android, and Chrome. Thus, the application processor is general\-purpose in nature. A good example of the use of an embedded application processor is the smartphone. The embedded system is designed to support numerous apps and perform a wide variety of functions. 

Most embedded systems employ a **dedicated processor**, which, as the name implies, is dedicated to one or a small number of specific tasks required by the host device. Because such an embedded system is dedicated to a specific task or tasks, the processor and associated components can be engineered to reduce size and cost. 

**Microprocessors** versus **Microcontrollers** 

As we have seen, early **microprocessor** chips included registers, an ALU, and some sort of control unit or instruction processing logic. As transistor density increased, it became possible to increase the complexity of the instruction set architecture, and ultimately to add memory and more than one processor. Contemporary micropro- cessor chips, as shown in Figure 1.2, include multiple cores and a substantial amount of cache memory. 

A **microcontroller** chip makes a substantially different use of the logic space available. Figure 1.15 shows in general terms the elements typically found on a microcontroller chip. As shown, a microcontroller is a single chip that contains the processor, non\-volatile memory for the program (ROM), volatile memory for input and output (RAM), a clock, and an I/O control unit. The processor portion of the microcontroller has a much lower silicon area than other microprocessors and much higher energy efficiency. We examine microcontroller organization in more detail in Section 1.6. 

Also called a "computer on a chip," billions of microcontroller units are embedded each year in myriad products from toys to appliances to automobiles. For example, a single vehicle can use 70 or more microcontrollers. Typically, especially for the smaller, less expensive microcontrollers, they are used as dedicated proces- sors for specific tasks. For example, microcontrollers are heavily utilized in automa- tion processes. By providing simple reactions to input, they can control machinery, turn fans on and off, open and close valves, and so forth. They are integral parts of modern industrial technology and are among the most inexpensive ways to produce machinery that can handle extremely complex functionalities. 

Microcontrollers come in a range of physical sizes and processing power. Pro- cessors range from 4\-bit to 32\-bit architectures. Microcontrollers tend to be much slower than microprocessors, typically operating in the MHz range rather than the GHz speeds of microprocessors. Another typical feature of a microcontroller is that it does not provide for human interaction. The microcontroller is programmed for a specific task, embedded in its device, and executes as and when required. 

**Embedded versus Deeply Embedded Systems** 

We have, in this section, defined the concept of an embedded system. A subset of embedded systems, and a quite numerous subset, is referred to as **deeply embed- ded systems.** Although this term is widely used in the technical and commercial 

**Analog data acquisition**   
**Processor**   
1.6 / ARM ARCHITECTURE **33** 

I 

**A/D** 

**converter**   
**RAM**   
**Temporary data** 

**Analog data transmission**   
**D/A** 

**converter**   
**ROM**   
**Program and data** 

**Send/receive** 

**data**   
**Serial I/O ports**   
**EEPROM**   
**Permanent data** 

**Peripheral interfaces**   
**Parallel I/O**   
**TIMER**   
**ports**   
**System bus**   
**Timing functions** 

**Figure 1.15** Typical Microcontroller Chip Elements 

literature, you will search the Internet in vain (or at least I did) for a straightfor- ward definition. Generally, we can say that a deeply embedded system has a proces- sor whose behavior is difficult to observe both by the programmer and the user. A deeply embedded system uses a microcontroller rather than a microprocessor, is not programmable once the program logic for the device has been burned into ROM (read\-only memory), and has no interaction with a user. 

Deeply embedded systems are dedicated, single\-purpose devices that detect something in the environment, perform a basic level of processing, and then do some- thing with the results. Deeply embedded systems often have wireless capability and appear in networked configurations, such as networks of sensors deployed over a large area (e.g., factory, agricultural field). The Internet of things depends heavily on deeply embedded systems. Typically, deeply embedded systems have extreme resource con- straints in terms of memory, processor size, time, and power consumption. 

**1.6 ARM ARCHITECTURE** 

The ARM architecture refers to a processor architecture that has evolved from RISC design principles and is used in embedded systems. Chapter 15 examines RISC design principles in detail. In this section, we give a brief overview of the ARM architecture. 

**34** CHAPTER 1 / **BASIC** CONCEPTS AND COMPUTER EVOLUTION 

**ARM Evolution** 

ARM is a family of RISC\-based microprocessors and microcontrollers designed by ARM Holdings, Cambridge, England. The company doesn't make processors but instead designs microprocessor and multicore architectures and licenses them to man- ufacturers. Specifically, ARM Holdings has two types of licensable products: proces- sors and processor architectures. For processors, the customer buys the rights to use ARM\-supplied design in their own chips. For a processor architecture, the customer buys the rights to design their own processor compliant with ARM's architecture. 

ARM chips are high\-speed processors that are known for their small die size and low power requirements. They are widely used in smartphones and other hand- held devices, including game systems, as well as a large variety of consumer prod- ucts. ARM chips are the processors in Apple's popular iPod and iPhone devices, and are used in virtually all Android smartphones as well. ARM is probably the most widely used embedded processor architecture and indeed the most widely used processor architecture of any kind in the world \[VANC14\]. 

The origins of ARM technology can be traced back to the British\-based Acorn Computers company. In the early 1980s, Acorn was awarded a contract by the Brit- ish Broadcasting Corporation (BBC) to develop a new microcomputer architecture for the BBC Computer Literacy Project. The success of this contract enabled Acorn to go on to develop the first commercial RISC processor, the Acorn RISC Machine (ARM). The first version, ARM1, became operational in 1985 and was used for internal research and development as well as being used as a coprocessor in the BBC machine. 

In this early stage, Acorn used the company VLSI Technology to do the actual fabrication of the processor chips. VLSI was licensed to market the chip on its own and had some success in getting other companies to use the ARM in their products, particularly as an embedded processor. 

The ARM design matched a growing commercial need for a high\-performance, low\-power\-consumption, small\-size, and low\-cost processor for embedded appli- cations. But further development was beyond the scope of Acorn's capabilities. Accordingly, a new company was organized, with Acorn, VLSI, and Apple Com- puter as founding partners, known as ARM Ltd. The Acorn RISC Machine became Advanced RISC Machines.12 

**Instruction Set Architecture** 

The ARM instruction set is highly regular, designed for efficient implementation of the processor and efficient execution. All instructions are 32 bits long and follow a regular format. This makes the ARM ISA suitable for implementation over a wide range of products. 

Augmenting the basic ARM ISA is the Thumb instruction set, which is a re- encoded subset of the ARM instruction set. Thumb is designed to increase the per- formance of ARM implementations that use a 16\-bit or narrower memory data bus, 

12The company dropped the designation *Advanced RISC Machines* in the late 1990s. It is now simply 

known as the ARM architecture. 

1.6 / ARM ARCHITECTURE **35** 

and to allow better code density than provided by the ARM instruction set. The Thumb instruction set contains a subset of the ARM 32\-bit instruction set recoded into 16\-bit instructions. The current defined version is Thumb\-2. 

The ARM and Thumb\-2 ISAs are discussed in Chapters 12 and 13. 

**ARM Products** 

ARM Holdings licenses a number of specialized microprocessors and related tech- nologies, but the bulk of their product line is the Cortex family of microprocessor architectures. There are three Cortex architectures, conveniently labeled with the initials A, R, and M. 

***CORTEX\-A**/CORTEX**\-A50*** The Cortex\-A and Cortex\-A50 are application processors, intended for mobile devices such as smartphones and eBook readers, as well as consumer devices such as digital TV and home gateways (e.g., DSL and cable Internet modems). These processors run at higher clock frequency (over 1 GHz), and support a memory management unit (MMU), which is required for full feature OSS such as Linux, Android, MS Windows, and mobile OSs. An MMU is a hardware module that supports virtual memory and paging by translating virtual addresses into physical addresses; this topic is explored in Chapter 8\. 

The two architectures use both the ARM and Thumb\-2 instruction sets; the principal difference is that the Cortex\-A is a 32\-bit machine, and the Cortex\-A50 is a 64\-bit machine. 

***CORTEX\-R*** The Cortex\-R is designed to support real\-time applications, in which the timing of events needs to be controlled with rapid response to events. They can run at a fairly high clock frequency (e.g., 200MHz to 800MHz) and have very low response latency. The Cortex\-R includes enhancements both to the instruction set and to the processor organization to support deeply embedded real\-time devices. Most of these processors do not have MMU; the limited data requirements and the limited number of simultaneous processes eliminates the need for elaborate hardware and software support for virtual memory. The Cortex\-R does have a Memory Protection Unit (MPU), cache, and other memory features designed for industrial applications. An MPU is a hardware module that prohibits one program in memory from accidentally accessing memory assigned to another active program. Using various methods, a protective boundary is created around the program, and instructions within the program are prohibited from referencing data outside of that boundary. 

Examples of embedded systems that would use the Cortex\-R are automotive braking systems, mass storage controllers, and networking and printing devices. 

***CORTEX\-M*** Cortex\-M series processors have been developed primarily for the microcontroller domain where the need for fast, highly deterministic interrupt management is coupled with the desire for extremely low gate count and lowest possible power consumption. As with the Cortex\-R series, the Cortex\-M architecture has an MPU but no MMU. The Cortex\-M uses only the Thumb\-2 instruction set. The market for the Cortex\-M includes IoT devices, wireless sensor/actuator networks used in factories and other enterprises, automotive body electronics, and so on. 

**36 CHAPTER** 1 / **BASIC** CONCEPTS AND **COMPUTER EVOLUTION** 

There are currently four versions of the Cortex\-M series: 

■ **Cortex\-M0:** Designed for 8- and 16\-bit applications, this model emphasizes low cost, ultra low power, and simplicity. It is optimized for small silicon die size (starting from 12k gates) and use in the lowest cost chips. 

■ **Cortex\-**M0**\+**: An enhanced version of the MO that is more energy efficient. 

■ **Cortex\-M3:** Designed for 16- and 32\-bit applications, this model emphasizes performance and energy efficiency. It also has comprehensive debug and trace features to enable software developers to develop their applications quickly. 

**■ Cortex\-M4:** This model provides all the features of the Cortex\-M3, with addi- tional instructions to support digital signal processing tasks. 

In this text, we will primarily use the ARM Cortex\-M3 as our example embed- ded system processor. It is the best suited of all ARM models for general\-purpose microcontroller use. The Cortex\-M3 is used by a variety of manufacturers of micro- controller products. Initial microcontroller devices from lead partners already combine the Cortex\-M3 processor with flash, SRAM, and multiple peripherals to provide a competitive offering at the price of just $1. 

Figure 1.16 provides a block diagram of the EFM32 microcontroller from Sil- icon Labs. The figure also shows detail of the Cortex\-M3 processor and core com- ponents. We examine each level in turn. 

The **Cortex\-M3 core** makes use of separate buses for instructions and data. This arrangement is sometimes referred to as a Harvard architecture, in contrast with the von Neumann architecture, which uses the same signal buses and mem- ory for both instructions and data. By being able to read both an instruction and data from memory at the same time, the Cortex\-M3 processor can perform many operations in parallel, speeding application execution. The core contains a decoder for Thumb instructions, an advanced ALU with support for hardware multiply and divide, control logic, and interfaces to the other components of the processor. In particular, there is an interface to the nested vector interrupt controller (NVIC) and the embedded trace macrocell (ETM) module. 

The core is part of a module called the **Cortex\-M3 processor**. This term is somewhat misleading, because typically in the literature, the terms core and pro- cessor are viewed as equivalent. In addition to the core, the processor includes the following elements: 

■ **NVIC:** Provides configurable interrupt handling abilities to the processor. It facilitates low\-latency exception and interrupt handling, and controls power management. 

■ **ETM:** An optional debug component that enables reconstruction of program execution. The ETM is designed to be a high\-speed, low\-power debug tool that only supports instruction trace. 

■ **Debug access port (DAP):** This provides an interface for external debug access to the processor. 

■ **Debug logic:** Basic debug functionality includes processor halt, single\-step, processor core register access, unlimited software breakpoints, and full system memory access**.** 

Security Analog Interfaces   
Timers & Triggers   
Parallel I/O Ports   
Serial Interfaces 

Hard- 

ware 

AES   
A/D 

con-   
D/A 

con- 

verter verter   
PeriphTimer/ bus int counter) 

Low Real energy time ctr   
(General) External Pulse Watch-   
purpose Inter- counter dog tmr) I/O rupts   
Pin 

reset   
USART   
USB 

Low- 

UART energy 

UART 

Peripheral bus 

**32-bit bus** 

Voltage Voltage 

regula- compar-   
High fre- quency RC 

tor   
ator   
oscillator   
High freq crystal oscillator   
Flash 

memory 64 kB   
SRAM 

memory 64 kB   
Debug inter-   
DMA 

control- 

face   
ler 

Power-   
Brown- 

out de-   
Low fre- 

on reset   
quency RC   
Low freq crystal 

tector   
oscillator   
oscillator 

Energy management   
Clock management 

**Microcontroller Chip**   
Memory protec- tion unit   
Cortex\-M3 processor 

Core and memory 

ICode 

interface   
SRAM & 

peripheral I/F 

Bus matrix 

Debug logic 

DAP   
Memory protection unit 

NVIC   
ARM 

core   
ETM 

**Cortex-M3 Core** 

NVIC 

interface   
ETM interface   
**Cortex-M3 Processor** 

Hardware 

divider   
32-bit ALU 

32-bit multiplier 

Control logic   
Thumb 

decode 

Instruction interface   
Data interface 

**Figure 1.16** Typical Microcontroller Chip Based on Cortex\-M3 

**37** 

**38** CHAPTER 1 / BASIC **CONCEPTS** AND COMPUTER EVOLUTION 

■ **ICode interface:** Fetches instructions from the code memory space. 

■ **SRAM & peripheral interface:** Read/write interface to data memory and peripheral devices. 

**Bus matrix:** Connects the core and debug interfaces to external buses on the microcontroller. 

**Memory protection unit:** Protects critical data used by the operating system from user applications, separating processing tasks by disallowing access to each other's data, disabling access to memory regions, allowing memory regions to be defined as read\-only, and detecting unexpected memory accesses that could potentially break the system. 

The upper part of Figure 1.16 shows the block diagram of a typical micro- controller built with the Cortex\-M3, in this case the EFM32 microcontroller. This microcontroller is marketed for use in a wide variety of devices, including energy, gas, and water metering; alarm and security systems; industrial automation devices; home automation devices; smart accessories; and health and fitness devices. The sil- icon chip consists of 10 main areas:13 

14   
15   
**■ Core and memory:** This region includes the Cortex\-M3 processor, static RAM (SRAM) data memory,1 and flash memory" for storing program instructions and nonvarying application data. Flash memory is nonvolatile (data is not lost when power is shut off) and so is ideal for this purpose. The SRAM stores variable data. This area also includes a debug interface, which makes it easy to reprogram and update the system in the field. 

■ **Parallel** I/**O ports:** Configurable for a variety of parallel I/O schemes. 

■ **Serial interfaces**: Supports various serial I/O schemes. 

■ **Analog interfaces:** Analog\-to\-digital and digital\-to\-analog logic to support sensors and actuators. 

■ **Timers and triggers:** Keeps track of timing and counts events, generates out- put waveforms, and triggers timed actions in other peripherals. 

■ **Clock management:** Controls the clocks and oscillators on the chip. Multiple clocks and oscillators are used to minimize power consumption and provide short startup times. 

**Energy management**: Manages the various low\-energy modes of operation of the processor and peripherals to provide real\-time management of the energy needs so as to minimize energy consumption. 

■ **Security:** The chip includes a hardware implementation of the Advanced Encryption Standard (AES). 

13 This discussion does not go into details about all of the individual modules; for the interested reader, an in\-depth discussion is provided in the document EFM32G200.pdf, available at box.com/COA10e. 14Static RAM (SRAM) is a form of random\-access memory used for cache memory; see Chapter 5. 15 Flash memory is a versatile form of memory used both in microcontrollers and as external memory; it is discussed in Chapter 6. 

1.7 / CLOUD COMPUTING **39** 

■ **32-bit bus:** Connects all of the components on the chip. 

■ **Peripheral bus:** A network which lets the different peripheral module commu- nicate directly with each other without involving the processor. This supports timing\-critical operation and reduces software overhead. 

Comparing Figure 1.16 with Figure 1.2, you will see many similarities and the same general hierarchical structure. Note, however, that the top level of a microcontroller computer system is a single chip, whereas for a multicore com- puter, the top level is a motherboard containing a number of chips. Another note- worthy difference is that there is no cache, neither in the Cortex\-M3 processor nor in the microcontroller as a whole, which plays an important role if the code or data resides in external memory. Though the number of cycles to read the instruc- tion or data varies depending on cache hit or miss, the cache greatly improves the performance when external memory is used. Such overhead is not needed for a microcontroller. 

**1.7 CLOUD COMPUTING** 

Although the general concepts for cloud computing go back to the 1950s, cloud computing services first became available in the early 2000s, particularly targeted at large enterprises. Since then, cloud computing has spread to small and medium size businesses, and most recently to consumers. Apple's iCloud was launched in 2012 and had 20 million users within a week of launch. Evernote, the cloud\-based notetaking and archiving service, launched in 2008, approached 100 million users in less than 6 years. In this section, we provide a brief overview. Cloud computing is examined in more detail in Chapter 17\. 

**Basic Concepts** 

There is an increasingly prominent trend in many organizations to move a substantial portion or even all information technology (IT) operations to an Internet\-connected infrastructure known as enterprise cloud computing. At the same time, individual users of PCs and mobile devices are relying more and more on cloud computing services to backup data, synch devices, and share, using personal cloud computing. NIST defines cloud computing, in NIST SP\-800-145 *(The NIST Definition of Cloud Computing*), as follows: 

**Cloud computing:** A model for enabling ubiquitous, convenient, on\-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction. 

Basically, with cloud computing, you get economies of scale, professional network management, and professional security management. These features can be attractive to companies large and small, government agencies, and individual PC and mobile users. The individual or company only needs to pay for the storage 

**40 CHAPTER** 1 / BASIC **CONCEPTS** AND COMPUTER **EVOLUTION** 

capacity and services they need. The user, be it company or individual, doesn't have the hassle of setting up a database system, acquiring the hardware they need, doing maintenance, and backing up the data\-all these are part of the cloud service. 

In theory, another big advantage of using cloud computing to store your data and share it with others is that the cloud provider takes care of security. Alas, the customer is not always protected. There have been a number of security failures among cloud providers. Evernote made headlines in early 2013 when it told all of its users to reset their passwords after an intrusion was discovered. 

**Cloud networking** refers to the networks and network management function- ality that must be in place to enable cloud computing. Most cloud computing solu- tions rely on the Internet, but that is only a piece of the networking infrastructure. One example of cloud networking is the provisioning of high\-performance and/or high\-reliability networking between the provider and subscriber. In this case, some or all of the traffic between an enterprise and the cloud bypasses the Internet and uses dedicated private network facilities owned or leased by the cloud service pro- vider. More generally, cloud networking refers to the collection of network capa- bilities required to access a cloud, including making use of specialized services over the Internet, linking enterprise data centers to a cloud, and using firewalls and other network security devices at critical points to enforce access security policies. 

We can think of **cloud storage** as a subset of cloud computing. In essence, cloud storage consists of database storage and database applications hosted remotely on cloud servers. Cloud storage enables small businesses and individual users to take advantage of data storage that scales with their needs and to take advantage of a variety of database applications without having to buy, maintain, and manage the storage assets. 

**Cloud Services** 

The essential purpose of cloud computing is to provide for the convenient rental of computing resources. A cloud service provider (CSP) maintains computing and data storage resources that are available over the Internet or private networks. Customers can rent a portion of these resources as needed. Virtually all cloud ser- vice is provided using one of three models (Figure 1.17): SaaS, PaaS, and IaaS, which we examine in this section. 

***SOFTWARE AS A*** **SERVICE *(SAAS*)** As the name implies, a SaaS cloud provides service to customers in the form of software, specifically application software, running on and accessible in the cloud. SaaS follows the familiar model of Web services, in this case applied to cloud resources. SaaS enables the customer to use the cloud provider's applications running on the provider's cloud infrastructure. The applications are accessible from various client devices through a simple interface such as a Web browser. Instead of obtaining desktop and server licenses for software products it uses, an enterprise obtains the same functions from the cloud service. SaaS saves the complexity of software installation, maintenance, upgrades, and patches. Examples of services at this level are Gmail, Google's e\-mail service, and Salesforce.com, which help firms keep track of their customers. 

Common subscribers to SaaS are organizations that want to provide their employees with access to typical office productivity software, such as document 

1.7/CLOUD COMPUTING **41** 

**Applications** 

**Application** 

**Framework** 

**Compilers** 

**Run-time** 

**environment**   
**Traditional IT** 

**architecture**   
**Managed by CSP**   
**Managed by client**   
**Infrastructure as** 

**a service (IaaS)** 

**Applications** 

**Application** 

**Framework** 

**Compilers** 

**Run-time** 

**environment** 

**Databases** 

**Operating** 

**system** 

**Virtual** 

**machine** 

**Server hardware**   
**Databases** 

**Operating** 

**system** 

**Virtual** 

**machine** 

**Server** 

**hardware** 

**Storage** 

**Networking** 

**More complex** 

**More upfront cost** 

**Less scalable** 

**More customizable** 

IT \= information technology   
**Managed by CSP**   
**Managed**   
**by client**   
**Platform as a**   
**Software as a** 

**service (PaaS)**   
**service (SaaS)** 

**Applications**   
**Applications** 

**Application Framework**   
**Application Framework** 

**Compilers** 

**Run-time** 

**environment** 

**Databases**   
**Managed by CSP**   
**Compilers** 

**Run-time** 

**environment** 

**Databases** 

**Operating system** 

**Virtual** 

**machine**   
**Operating** 

**system** 

**Virtual** 

**machine** 

**Server** 

**hardware**   
**Server** 

**hardware** 

**Storage**   
**Storage**   
**Storage** 

**Networking**   
**Networking**   
**Networking** 

CSP \= cloud service provider 

**Figure 1.17** Alternative Information Technology Architectures   
**Less complex** 

**Lower upfront cost** 

**More scalable** 

**Less customizable** 

management and email. Individuals also commonly use the SaaS model to acquire cloud resources. Typically, subscribers use specific applications on demand. The cloud provider also usually offers data\-related features such as automatic backup and data sharing between subscribers. 

***PLATFORM AS A SERVICE (PAAS*****)** A PaaS cloud provides service to customers in the form of a platform on which the customer's applications can run. PaaS enables the customer to deploy onto the cloud infrastructure containing customer\-created or acquired applications. A PaaS cloud provides useful software building blocks, plus a number of development tools, such as programming languages, run\-time environments, and other tools that assist in deploying new applications. In effect, PaaS is an operating system in the cloud. PaaS is useful for an organization that wants to develop new or tailored applications while paying for the needed computing resources only as needed and only for as long as needed. Google App Engine and the Salesforce1 Platform from Salesforce.com are examples of PaaS. 

**42** CHAPTER 1 / BASIC CONCEPTS AND **COMPUTER EVOLUTION** 

***INFRASTRUCTURE AS A SERVICE (IAAS*****)** With IaaS, the customer has access to the underlying cloud infrastructure. IaaS provides virtual machines and other abstracted hardware and operating systems, which may be controlled through a service application programming interface (API). IaaS offers the customer processing, storage, networks, and other fundamental computing resources so that the customer is able to deploy and run arbitrary software, which can include operating systems and applications. IaaS enables customers to combine basic computing services, such as number crunching and data storage, to build highly adaptable computer systems. Examples of IaaS are Amazon Elastic Compute Cloud (Amazon EC2) and Windows Azure. 

**1.8 KEY TERMS, REVIEW QUESTIONS, AND PROBLEMS** 

**Key Terms** 

application processor   
gate 

arithmetic and logic unit 

(ALU) 

ARM 

central processing unit 

(CPU) 

chip 

cloud computing 

cloud networking 

cloud storage 

computer architecture 

computer organization control unit 

core 

dedicated processor 

deeply embedded system 

embedded system   
infrastructure as a service 

(IaaS) 

input\-output (I/O) 

instruction set architecture 

(ISA) 

integrated circuit 

Intel x86 

Internet of things (IoT) 

main memory 

memory   
cell 

memory management unit 

(MMU) 

memory protection unit 

(MPU) microcontroller 

microelectronics   
microprocessor motherboard multicore 

multicore processor original equipment 

manufacturer (OEM) platform as a service 

(PaaS) 

printed circuit board 

processor 

registers 

semiconductor 

semiconductor memory 

software as a service (SaaS) system bus 

system interconnection vacuum tubes 

**Review Questions** 

**1.1** What, in general terms, is the distinction between computer organization and com- 

puter architecture? 

**1.2** What, in general terms, is the distinction between computer structure and computer 

function? 

**1.3**   
What are the four main functions of a computer? 

**1.4**   
List and briefly define the main structural components of a computer. 

**1.5**   
List and briefly define the main structural components of a processor. 

**1.6** What is a stored program computer? 

**1.7** Explain Moore's law. 

**1.8** List and explain the key characteristics of a computer family. 

**1.9**   
What is the key distinguishing feature of a microprocessor? 

1.8 / KEY TERMS, REVIEW QUESTIONS**,** AND PROBLEMS **43** 

**Problems** 

**1.1** You are to write an IAS program to compute the results of the following equation. 

*N* 

*Y* \= ΣX 

*X*\=1 

Assume that the computation does not result in an arithmetic overflow and that *X, Y*, and *N* are positive integers with N≥ 1\. *Note:* The IAS did not have assembly language, only machine language. 

**a.** Use the equation Sum(*Y*) \=   
*N(N* \+ 1\) 

2   
when writing the IAS program. 

**b.** Do it the "hard way," without using the equation from part (a). 

**1.2**   
**a.** 

**1.3** 

**1.4**   
On the IAS, what would the machine code instruction look like to load the con- tents of memory address 2 to the accumulator? 

**b.** How many trips to memory does the CPU need to make to complete this instruc- 

tion during the instruction cycle? 

On the IAS, describe in English the process that the CPU must undertake to read a value from memory and to write a value to memory in terms of what is put into the MAR, MBR, address bus, data bus, and control bus. 

Given the memory contents of the IAS computer shown below, 

**Address** 

08A 

08B   
**Contents** 

010FA210FB 

010FA0F08D 

020FA210FB   
08C 

show the assembly language code for the program, starting at address 08A. Explain what this program does. 

**1.5** In Figure 1.6, indicate the width**,** in bits, of each data path (e.g., between AC and ALU). **1.6** In the IBM 360 Models 65 and 75, addresses are staggered in two separate main mem- ory units (e.g., all even\-numbered words in one unit and all odd\-numbered words in another). What might be the purpose of this technique? 

**1.7** The relative performance of the IBM 360 Model 75 is 50 times that of the 360 Model 30, yet the instruction cycle time is only 5 times as fast. How do you account for this discrepancy? 

**1.8**   
While browsing at Billy Bob's computer store, you overhear a customer asking Billy Bob what is the fastest computer in the store that he can buy. Billy Bob replies, "You're looking at our Macintoshes. The fastest Mac we have runs at a clock speed of 1.2 GHz. If you really want the fastest machine, you should buy our 2.4\-GHz Intel Pentium IV instead." Is Billy Bob correct? What would you say to help this customer? 

**1.9** The ENIAC, a precursor to the ISA machine, was a decimal machine, in which each register was represented by a ring of 10 vacuum tubes. At any time, only one vacuum tube was in the ON state, representing one of the 10 decimal digits. Assuming that ENIAC had the capability to have multiple vacuum tubes in the ON and OFF state simultaneously, why is this representation "wasteful" and what range of integer values could we represent using the 10 vacuum tubes? 

**1.10** For each of the following examples, determine whether this is an embedded system, 

explaining why or why not. 

**a**. Are programs that understand physics and/or hardware embedded? For example, 

one that uses finite\-element methods to predict fluid flow over airplane wings? **b**. Is the internal microprocessor controlling a disk drive an example of an embedded 

system? 

**44** CHAPTER 1 / BASIC CONCEPTS AND **COMPUTER EVOLUTION** 

c. I/O drivers control hardware, so does the presence of an I/O driver imply that the 

computer executing the driver is embedded? 

**d**. Is a PDA (Personal Digital Assistant) an embedded system? 

**e.**   
Is the microprocessor controlling a cell phone an embedded system? 

f. Are the computers in a big phased\-array radar considered embedded? These radars are 10\-story buildings with one to three 100\-foot diameter radiating patches on the sloped sides of the building. 

g. Is a traditional flight management system (FMS) built into an airplane cockpit 

considered embedded? 

**h.** Are the computers in a hardware\-in\-the\-loop (HIL) simulator embedded? 

i. Is the computer controlling a pacemaker in a person's chest an embedded 

computer? 

**j.**   
Is the computer controlling fuel injection in an automobile engine embedded? 