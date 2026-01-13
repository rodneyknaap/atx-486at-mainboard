# atx-486at-mainboard
An ATX form factor 486 AT PC system based on technology from my previous 286 project

My aim is to preserve PC computing history, beyond the level of the physical existence of museum items, in a complete and open design, by recreating the original 286 and 486 AT PC system concepts in a known system design down to the full hardware component level details. This will enable the technology, even if no historic examples would exist anymore, to still be able to be kept alive in digital form here on GitHub. This project is different from what emulation offers, because inside this project, the actual original circuits and designs are kept alive and functionally intact, faithful to the original systems as these were created. 
So the system design is targeted to achieve the identical and original experience, same as if you would power up an original real PC from the 80s and 90s years. Of course, most of the 486 generation designs are hidden inside large scale integration ICs of completely unknown designs, so I will need to redesign much of the unknown elements with my own ideas and concepts to at least be able to approximate the functionality needed for this project. I already have done a lot of this type of work in the previous 286 project where for example I was successful to reproduce the functionality of the 82284 and 82288 controller chips. So in the final design version of that project, these chips are now successfully recreated in a known component level form, and thus no longer essential for the system to be functional. 

My aim is to reproduce the 286/486 system using as little unknown technology hidden inside ICs as possible, so that every aspect of the system can be completely and openly known and able to be studied by others. If anyone has some VHDL code or other idea which could contribute to replacing various typical integrated ICs in PC technology, such as DMA controllers, interrupt controllers, keyboard controller, timer, RTC/CMOS chip etc, please get in touch with me because I would prefer to replace these as well so that in future designs, these ICs would become unnecessary for the system to be able to function. The ultimate design goal is completely achieving an open concept, independent of any unknown custom logic, and only needing standard FPGA design components and VHDL level recreations needed.

## Purpose and permitted use, cautions for a potential builder of this design
This project was created for historical purposes out of love for historical computing designs and for the purpose of enabling computing enthousiasts with a sufficient level of building and troubleshooting expertise to be able to experience the technology by building and troubleshooting the hardware described in this project. 

Due to the level of this project, it may be suitable as a project for students to get into. If there are any questions from teachers who like to teach about this technology I would be happy to answer them. It may be really interesting to analyse the elaborate and complex CPU timing and 8 bit to 16 bit data byte translation and DMA mechanisms in an educational setting.

Besides the GPL3 license there are a few warnings and usage restrictions applicable: No guarantees of function or fitness for any particular or useful purpose is given, building and using this design is at the sole responsibility of the builder.

Do not attempt this project unless you have the necessary electronics assembly expertise and experience, and know how to observe all electronics safety guidelines which are applicable.

It is not permitted to use the computer built from this design without the assumption of the possibility of loss of data or malfunction of the connected device. To be used strictly for personal hobby and experimental purposes only. No applications are permitted where failure of the device could result in damage or injury of any kind.

If you plan to use this design or any part of it in new designs, the acknowledgement of the designer and the design sources and inspirations, historical and modern, of all subparts contained within this design should be included and respected in your publication, to accredit the hard work, time and effort dedicated by the people before you who contributed to make your project possible.

No guarantee for any proper operation or suitability for any possible use or purpose is given, using the resulting hardware from this design is purely educational and experimental and not intended for serious applications. Loss of data is likely and to be expected when connecting any storage device or storage media to the resulting system from this design, or when configuring or operating any storage device or media with the system of this design.

When connecting this system to a computer network which contains stored information on it, it is at the sole responsibility and risk of the person making the connection, no guarantee is given against data loss or data corruption, malfunctions or failure of the whole computer network and/or any information contained inside it on other devices and media which are connected to the same network.

When building this project, the builder assumes personal responsibility for troubleshooting it and using the necessary care and expertise to make it function properly as defined by the design. You can email me with questions, but I will reply only if I have time and if I find the question to be valid. Which will probably also lead to an update here. I want to primarily dedicate my time to new project development, I am not able to do any user support, so that's why I provide the elaborate info here which will be expanded if needed.


# Acknowledgements
I want to refer to the elaborate text on the 286 project repository to read all about the work, help and encouragements I got on my work recreating the 5170 based AT design.
Additional thanks specific to this project I will continue here, and in relevant sections of the project readme document as the themes arrive.

First of all, a special thank you to Luca (Retro*Tech) from Italy, who supported me with encouraging words and expressed the kind wish to contribute some helpful hardware items for my research, testing and development work. Thanks Luca for your interest and support! I am always inspired by comments from other retro enthousiasts!

# Project development
In this project I will continue my work based on FPGA technology which will provide more speed and larger scaling of pin numbers which will be needed to accomplish the next development steps envisioned. The project will feature several modules, one of which is the CPU module which allows to swap and test with multiple CPUs. Support will be developed for the 286 and 486DX CPU initially to get the project started. After achieving proper base operation, project development will progress further.

# Modular approach
I have decided to divide this project into several modules. This provides many advantages because of being able to swap out different functional areas of the system in the form of PCB modules. During development I can have more options for testing. The connectivity is extremely important in any system where the design is still fluid and being developed so that the connections available will be able to support as many future design changes and upgrades as possible. By having a system element on a module, it will be possible to redesign or reprogram only that element while the rest of the system is able to remain the same, resulting in much less work for realizing future upgrades. 

# Research and test phase
The first step I am doing in this new project is to test some typical example mainboards which I will be using as a reference and also as a system for testing out modifications to the orginal concept which will help this project progress further. The Hyundai corporate mainboard which I bought turned out not to be suitable because of having too many jumper and dipswitch options and no manual available. I did get it to POST and boot however the cache on the system was non functional which didn't work well. I was however able to verify that a 286 MR BIOS is fully able to initialize and boot the system using a 486 CPU. Using the 486 MR BIOS this only made it possible to enable or disable the CPU cache. It looks like possibly examining existing 486 mainboards will not help me that much. So I am currently continuing my research by studying the Intel 486 book first and will proceed from there. As I am accumulating more insights about all the 486 CPU operations and system structure, I am getting a much better idea and concept of the much more advanced 486 system control I will be designing using a FPGA.

# The new mainboard design
The new mainboard design I will also start early on in the project because I want to be able to crosscheck the connectivity in practical form with the actual PCBs.
Initially it will be mostly placement changes and looking at the 3D representations but later I will also start to do the PCB routing.

![First rough draft of the mainboard, remaining components will be added after these are defined.](486AT_PC_ATX_mainboard_draft_001.jpg)

I will be updating the rough draft PCB layout for this project. This mainboard will be modified to not contain any more separate core AT controller ICs. The IDE port will also be fully integrated into the FPGA as well.
As things are looking now (jan 2026) we will probably feature an external FDC controller in PLCC form which contains the full FDC logic contrary to the DIP IC. 
The project will include options for USB mouse and USB keyboard, and PS/2 keyboard/mouse as an option. I will attempt to add all possible types of keyboard and mouse connections so all of these can be used according to preference.

## Memory subsystem and FPGA integration
A FPGA will be used to create all the system control for the 286 and 486 CPUs. Part of the tasks of the FPGA will be, as I have mentioned a few times in the VCF thread, to transparently provide a modern and fast type of DRAM to the system. Basically the FPGA will be in charge of doing all the memory control, and will aim to provide the RAM memory to the system at the highest possible speeds. I talked with newold86 on the VCF thread and he mentioned how he soldered a FPGA directly onto his own PCB. It's looking like I will need to do some BGA soldering as well because the available FPGA modules on the market are simply too severely limited in terms of available pins for the very advanced level of integration needed for this project. I will need a few hundred pins probably, so I will need a really modern type of FPGA and make use of level shifting transceivers to interface the low voltage FPGA to the system and CPU. Since the FPGA will go between the CPU and RAM, it will also open up all sorts of EMS type paging memory solutions which will also be available to a 286 CPU. This opens up the possibility of running [RealDoom](https://github.com/sqpat/RealDOOM) on this design, which is one of my goals that I am looking forward to working on. Basically I intend to feature EMS as done by VLSI in their TOPCAT chipset as an option in this project when using the 286. Of course, this is a more advanced goal which I will work on when I am further along in the testing and debugging phase of the project.

## Choice of CPU for this project
Initially I had the idea to feature two CPUs however I have reconsidered this aspect. Even though it's technically possible and sound, I will develop a separate project featuring a 286 first. I found that there are too many design developments to feature in a single board design step. So I will create another FPGA based mainboard specifically for the 486 CPU. After finishing the 286 FPGA stage we will have a lot of verified concepts which can enable the 486 system to be created in a more established format where more areas of this project design are already verified and known.

## PCI
I have seen PCI solutions using a 486 CPU so I will at some time in the future look into featuring functional PCI slot connectors as well. For me, the most important consideration regarding any part of the development remains that no chipset will be used anywhere, only a completely open, fully known concept solution will be developed. For this purpose I will continue to study all the various design specifications involved to gain the complete insight into the 486 CPU and PCI technology. I will also route any remaining available FPGA pins from the CPU System Control module into the mainboard connectors, allowing new designs, system upgrades and other new expansions to be interfaced on another card in the system. 
I have also started to study the PCI standard and technology to attempt to use this with the 286 CPU, where I also plan to work on PCI for the 486 CPU in this project as well. We can use the ISA bus for initial debugging providing VGA display through an ISA slot card, and then move on to create the PCI bus in the FPGA. I will feature one or two PCI slots in the 286 mainboard, and the same will be done for this 486 project.

## Continued development inside this project and into the next stage
As with the 286 project, this project is also aimed at the largest possible range of continued development of the system using this second design stage. This time, even more so than before. I will want to do a lot of experimentation with PC technology which would normally not be possible with traditional mainboards from the 90s. I will want to go a few steps beyond and enable more functionality to the system. Basically I will keep going until I reach the outer limitations of this hardware, after which I will continue to the third hardware design stage. The experiences I have gained from my work on this stage, as with the 286 project, I will re-invest into the next stage, which will probably have a completely different structure depending on my findings. At some point I hope that I could develop everything into a single mainboard PCB, that is, if the ATX PCB space could allow for this.

## Update for followers of this project  
The REV3D CPLD project has been completed where we now have a fully integrated PC/AT design using a 286 CPU and 5 CPLDs which has been completely debugged.
Work on the REV3D will receive further updates if and when enhancements are being discovered during the work on the next stage FPGA based systems.
The REV3D 286 project is important for the future work on this 486 system which is going to be based on FPGA.
After completing the REV3D 286 system we now have a basis to proceed into FPGA technology where we will take the integration level further by integrating the core AT controller ICs into the FPGA.  

I have started work on the next stage FPGA system which I am going to base solely on the 286 CPU.  
The 286 is going to help us get started with FPGA technology and HDL designs.
It will be based on hybrid design to attempt to preserve the PC/AT structure in the quartus block design structure.
This will need to be slightly modified to achieve a compatible state for quartus compilation and programming an FPGA.
The major change being that we will remove the X-BUS from the PC/AT system since the DMA is getting completely integrated into all the other areas of the system.
Another reason for not creating an X-bus anymore is that we will do complete integration where most of the system is no longer employing tri stating to share a common bus.
So bus members will be joined by multiplexing logic instead.  

After the FPGA stage is developed and debugged, it will then be suitable to serve for the first design steps using the 486 CPU.
In the 486 stage it is the plan that all the core AT controllers will be integrated inside the FPGA to allow the system to be more compact and run at higher clock speeds matching the 486.  

In the 286 project we will use the Altera Cyclone II FPGA in 672 pin BGA package. For this 486 project we may choose a newer FPGA if one can be found from the Chinese IC dealers that supports enough single ended IO pins and at the same time is reasonably affordable to keep the costs for building this system under control.

So after debugging the 286 FPGA stage (REV4) we will not be needing an X-device card after all.
The 286 FPGA project will also serve to prepare that important development step and have the integrated core AT controllers available for this 486 project next.  

If you are interested in the 486 project please star this repo to show your interest and support, and I suggest you also can follow the work being done on creating and debugging the REV4 286 system because that will in part define this 486 project as well. I will devote the effort into that first and then follow up here to redefine the outline of this project as a result from that work.  

Thank you to everyone who expressed an interest by starring this project, it is much appreciated!

Kind regards,

Rodney

Last updated january 13th, 2026.
