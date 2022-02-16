---
layout: page
title: "Google Summer of Code 2022 - Ideas for Projects"
---

*Note that this page is under construction for the new year of GSoC. Projects listed here will change and estimated project lengths are still to be defined.*

FOSSi Foundation is applying as an umbrella organization in Google
Summer of Code 2022. That means that we give small projects the
chance to participate in the program. Below you can find a list of
ideas that the projects had, but students are encouraged to propose
their own ideas. These projects are mostly open-ended and can be
tailored to your level of experience, assuming that you have the 
appropriate set of required skills for the particular project idea.

Whether you’re an aspiring student or mentor, feel free to contact us,
either through the private GSoC-specific mailing list [gsoc@fossi-foundation.org](mailto:gsoc@fossi-foundation.org),
through the public [discussion mailing list](https://lists.librecores.org/listinfo/discussion),
or through the mentors listed for each project below.
We are also available on [Gitter in librecores/Lobby](https://gitter.im/librecores/Lobby).

Looking forward to meet you all!

* TOC
{:toc}


### Porting BaseJump STL to FuseSoc

*Details:* FuseSoC is a package manager and set of build tools for reusable hardware building blocks, which makes it easy to share designs between projects and reuse open IP. BaseJump STL is a comprehensive hardware library for SystemVerilog that seeks to contain all of the commonly used hardware primitives, much as the C++ Standard Template Library does with software primitives. This project is to port BaseJumpSTL to FuseSoC so that new hardware projects can hit the ground running and reuse hand-optimized IP cores rather than re-designing and re-debugging.

*Skill level:* Beginner

*Language/Tool:* SystemVerilog, Python

*Mentor:* [Michael Taylor](mailto:prof.taylor@gmail.com)


### Logical Equivalence Checks with LLHD

The Low Level Hardware Description language, or [LLHD](https://llhd.io/) in short, is simple intermediate representation that is able to capture the semantics of today's hardware description languages *including* their behavioral, verification, and testing features. The IR has been developed alongside the [Moore](https://github.com/fabianschuiki/moore) compiler and published as a [paper](https://arxiv.org/pdf/2004.03494) at PLDI 2020. Since then, we have been busy merging LLHD into the [CIRCT](https://github.com/llvm/circt) project, a larger joint effort to develop Circuit IR Compilers and Tools.

When working with LLHD, you can assume that all the nasty parts of languages like SystemVerilog or VHDL have already been taken care of by a language frontend, and you are dealing with a much simpler but still complete representation of a circuit. As of today there are already a basic reference simulator as well as a faster LLVM-JIT-compilation-based simulator available for LLHD.

As a proof of concept for LLHD's verification prowess we would like you to implement a basic Logical Equivalence Check (LEC) for LLHD designs. This is essentially the process of taking two circuits and formally proving (or disproving) that they logically do the same thing, even if they use a different combination of logic gates to do so. This is a crucial step in chip design flows, to ensure that a synthesizer has properly translated RTL into a gate-level implementation, and that further place-and-route work did not violate the operation of a design.

In this project you will take two LLHD designs, translate them into the fundamental boolean equations, and formulate a satisfiability problem for an existing optimized SAT/SMT solver with them. You can scale this project's complexity to your liking, for example simplifying by looking only at combinational circuits, or complicating by finding ways to use registers as invariant anchor points in a circuit.

SAT/SMT solvers are tools that are extremely fun and satisfying to work with, but generally don't get the love they deserve in the circuit design community. With this project you'll be able to contribute to a key process in the ASIC design flow and generally show that, with good existing abstractions such as LLHD and the standardized solver file formats, it is very easy to create seemingly daunting formal tools for an open ASIC world.

*Skill Level:* Intermediate to Advanced

*Language/Tools:* C++, SAT/SMT Solver (e.g. Z3, Boolector, Bitwuzla, or others)

*Mentor:* [Fabian Schuiki](mailto:fschuiki@iis.ee.ethz.ch)


### Circuit Visualization

*Details:* The Makerchip platform for open-source circuit design has introduced support for custom visualization of circuit simulations. This has been used to great success in RISC-V training and has other applicability as well. In fact, any circuit can be visualized in useful ways. A few examples can be opened from [this repo](https://github.com/stevehoover/makerchip_examples). Some circuits we would like to provide visibility into include:

  - SweRV
  - SERV
  - TL-Verilog flow library
  - BaseJump STL
  - basic circuits for instructional purposes
  - virtualized FPGA boards

Visualization is written in (very straight-forward) JavaScript that has access to trace data from simulation and a canvas to draw on. A bit more detail on these ideas can be found [here](https://github.com/stevehoover/TL-V_Projects)

*Skill level:* Beginner

*Language/Tools:* JavaScript, Verilog/SystemVerilog/TL-Verilog

*Mentor:* [Steve Hoover](https://www.linkedin.com/in/steve-hoover-a44b607/) ([email](mailto:steve.hoover@redwoodeda.com)), Secondary: [Akos Hadnagy](https://www.linkedin.com/in/akos-hadnagy/)


### Create your own LibreCores, or contribute to an existing one

*Details:* Our main goal is to grow the community around open source silicon
designs. LibreCores are IP cores, but they are free and open. While
there are many projects you can contribute too, you may have your own
great idea for a LibreCore. All projects start small, and we see this
is a great chance to bring forward new ideas and start building new
tiny bits and pieces that enable free and open source chips.

We are happy to mentor you with your own idea, but it is important
that it is re-usable and contains everything needed for simple and
flexible integration, like testbenches, the required software drivers
etc. So, it is important that you discuss a proposal intensively.

*Skill level:* All

*Language/Tool:* Verilog, VHDL, Chisel, TL-Verilog, ...

*Mentor:* We will find the mentor with you,
 [LibreCores GSoC team](mailto:gsoc@fossi-foundation.org)


### Continuous Integration for Hardware Projects on LibreCores CI

*Goal:* Setup verification and continuous integration flow for one of open-source digital hardware projects.

*Details:*
[LibreCores CI](https://www.librecores.org/static/librecores-ci) is a
under-development Continuous Integration service within
[LibreCores](http://librecores.org). In this project we offer students
to work with modern hardware verification tools, RTL codebase and
[Jenkins Pipeline](https://jenkins.io/solutions/pipeline/) in order to
setup efficient verification flows for one of the open-source hardware
project being hosted on LibreCores. The project includes improvements
of the HW project testability in RTL, development/improvement of
testing frameworks and a development of a new Pipeline Library for
automation in Jenkins.

Prerequisites:
* Basic knowledge of the hardware verification techniques
* Knowledge of one of RTL languages
* Knowledge of one of the scripting languages (preferably Python or Groovy)

*Skill Level:* Intermediate

*Language/Tools:* Verilog/VHDL/.../Python, Jenkins, Groovy

*Mentors:* [Stefan Wallentowitz](mailto:stefan@wallentowitz.de)


### Building Manycore SoCs with OpenPiton + LiteX
[LiteX](https://github.com/enjoy-digital/litex) makes building FPGA-based SoCs easy. Using the Python hardware design library Migen, LiteX provides a variety of peripherals to enable users to build a complex SoC around a core of their choice. For this project, we would like to connect a manycore [OpenPiton](http://www.openpiton.org/) processor design in order to build a new manycore LiteX SoC.

*Skill level:* Intermediate

*Language/Tools:* Python (Migen), Verilog

*Mentor:* [Jonathan Balkind](mailto:jbalkind@ucsb.edu)


### Embench IoT OpenRISC port

The [Embench](https://www.embench.org/news.html) benchmark suite is a modern tool used to measure embedded processor and compiler toolchain performance.  The [Embench IoT project](https://github.com/embench/embench-iot) has ports for ARM, RISC-V and other embedded processors.  The goal of this project will be to port Embench to run the OpenRISC toolchain and collect benchmarks.  The benchmarks should be recorded at [Embench IoT results](https://github.com/embench/embench-iot-results) to be able to compare OpenRISC vs other popular CPUs.

*Skill level:* Easy

*Language/Tools:* Shell scripting, C, Makefile, Python

*Mentor:* [Stafford Horne](mailto:shorne@gmail.com)


### Integration of WARP-V with OpenPiton

*Details:* In GSoC 2020, one of Shivam Potdar's accomplishments was to prepare the [WARP-V](https://github.com/stevehoover/warp-v) CPU core for integration with the [OpenPiton](https://parallel.princeton.edu/openpiton/) heterogeneous many-core framework. This project would aim to complete that integration.

This will enable academic exploration of the combined flexibility benefits of OpenPiton and WARP-V. OpenPiton provides flexibility through the integration of different CPU cores. WARP-V provides flexibility of the CPU core itself. WARP-V can be optimized for the cycle-time of OpenPiton, and differently-configured WARP-V cores could be run within the same system along with other CPU cores.

*Skill level:* Advanced

*Languages/Tools:* Verilog, TL-Verilog

*Co-mentors:* [Steve Hoover](https://www.linkedin.com/in/steve-hoover-a44b607/) ([email](mailto:steve.hoover@redwoodeda.com)), [Jonathan Balkind](https://www.linkedin.com/in/jbalkind/) ([email](mailtojbalkind@ucsb.edu)), [Akos Hadnagy](https://www.linkedin.com/in/akos-hadnagy/) ([email](mailto:akos.hadnagy@gmail.com))

*Discussion:* [WARP-V LibreCores Gitter Room](https://gitter.im/librecores/warp-v), [OpenPiton LibreCores Gitter Room](https://gitter.im/librecores/openpiton)


### Improve Test Coverage of the Moore HDL Compiler

[Moore](https://github.com/fabianschuiki/moore) is a compiler for SystemVerilog and VHDL hardware designs. Its goal is world domination by finally moving the burden of implementing SV and VHDL out of tools like synthesizers and simulators and into a separate frontend, very much like what Clang and LLVM did for the software world. In contrast to other projects that focus on specific use cases such as synthesis or netlists processing, Moore strives to support the entirety of the SV and VHDL languages. As output the compiler produces [LLHD IR](https://llhd.io/), a simple intermediate representation that is able to capture the semantics of today's hardware description languages *including* their behavioral, verification, and testing features. (See also the [LLHD paper](https://arxiv.org/pdf/2004.03494) from PLDI 2020 for details.)

We would love to have you help make Moore even better! Since the input languages are very complex, a key aspect of Moore is to perform well on existing test suites and benchmarks. The [SymbiFlow](https://github.com/SymbiFlow) project maintains a [large suite of SystemVerilog tests](https://symbiflow.github.io/sv-tests-results/) where Moore is also represented. The goal of this project is to go into these tests and extend and improve the Moore compiler to support more of the use cases that are currently failing. You'll be able to look for juicy optimization targets and common reasons of failure, fix them, and reap the benefits of seeing a lot more green on this dashboard!

The Moore compiler is written in Rust. Don't be scared if you haven't touched Rust before -- if you know C or C++ you'll feel right at home. The main language we're currently tackling with Moore right now is SystemVerilog, so either knowing the language a bit or not being scared of looking into language reference manual will be useful.

*Skill Level:* Advanced

*Language/Tools:* Rust, SystemVerilog

*Mentor:* [Fabian Schuiki](mailto:fschuiki@iis.ee.ethz.ch)


### Giving AnyCore an Open-Source FPU
[AnyCore](https://people.engr.ncsu.edu/ericro/research/anycore.htm) is an advanced superscalar processor developed at NC State University, designed to be highly configurable across parameters like issue width and pipeline depth. This project would entail connecting an open-source Floating Point Unit (FPU) to the high performance AnyCore processor, which runs the RISC-V ISA.

*Skill level:* Beginner/Intermediate

*Language/Tools:* Verilog/SystemVerilog, RISC-V

*Mentor:* [Jonathan Balkind](mailto:jbalkind@ucsb.edu)


### Other TL-Verilog-Related Projects

If you are interested in the TL-Verilog ecosystem, you might also consider any of these [TL-Verilog project ideas](https://github.com/stevehoover/TL-V_Projects). All would make excellent GSoC projects and mentors can be identified.


### Architectural Improvements to OpenPiton+Ariane
[OpenPiton+Ariane](https://openpiton-blog.princeton.edu/2018/11/announcing-openpiton-with-ariane/) is a permissively-licensed RISC-V manycore processor, built as a collaboration between the [PULP Platform](https://www.pulp-platform.org/) from ETH Zürich and the [OpenPiton Platform](http://www.openpiton.org/) from Princeton University. We would like to co-optimise OpenPiton and Ariane in their combined platform, to improve performance of the processor both in FPGA emulation systems and for eventual silicon chips. Possible improvements could be along the lines of: adding a global branch predictor, introducing a multi-level TLB, etc. We are also open to other projects aimed at improving the performance of aspects of either Ariane or OpenPiton.

*Skill level:* Intermediate

*Language/Tools:* Verilog, SystemVerilog, RISC-V

*Mentor:* [Jonathan Balkind](mailto:jbalkind@ucsb.edu)


### Extend LibreCores.org

[LibreCores](https://www.librecores.org) is a community web site with the goal of providing an overview of IP cores and the corresponding ecosystem. We strive for LibreCores to be *the* resource for free and open source IP: it should be easy to find, integrate, and contribute to the projects found there -- to make digital design projects as easy as writing software. For further information on our goals, see the [FOSDEM Presentation slides](https://fosdem.org/2016/schedule/event/digital_hardware_design/attachments/slides/1037/export/events/attachments/digital_hardware_design/slides/1037/fossi_fosdem.pdf) announcing LibreCores. The full site source code is available on [GitHub](https://github.com/librecores/librecores-web).

You can find a non-exhaustive [list of available tasks in our documentation](http://librecores-web.readthedocs.io/en/latest/contributing.html). Please talk to Philipp if you have other ideas, or didn't find an interesting project. We welcome your own ideas!

*Skill Level:* Intermediate

*Language/Tools:* PHP7 with the [Symfony Framework](http://symfony.com/), MySQL, HTML/JS

*Mentor:* [Philipp Wagner](mailto:mail@philipp-wagner.com)


### Push a Design through the Moore HDL Compiler

[Moore](https://github.com/fabianschuiki/moore) is a compiler for SystemVerilog and VHDL hardware designs. Its goal is world domination by finally moving the burden of implementing SV and VHDL out of tools like synthesizers and simulators and into a separate frontend, very much like what Clang and LLVM did for the software world. In contrast to other projects that focus on specific use cases such as synthesis or netlists processing, Moore strives to support the entirety of the SV and VHDL languages. As output the compiler produces [LLHD IR](https://llhd.io/), a simple intermediate representation that is able to capture the semantics of today's hardware description languages *including* their behavioral, verification, and testing features. (See also the [LLHD paper](https://arxiv.org/pdf/2004.03494) from PLDI 2020 for details.)

We would love to have you help make Moore even better! As a proof of concept that goes beyond the single RISC-V core that Moore tackles successfully, we would like to push a larger, more complex compute cluster through the compiler. This could be for example a [Snitch](https://github.com/pulp-platform/snitch) compute cluster of ETH Zurich which contains complex caches, interconnects, memory systems, multiple processor cores and large floating-point data paths. The goal of this project is to take this cluster's SV source code and implement the pieces Moore currently lacks in order to be able to compile the cluster. You'll be able to look for frequent sources of errors and juicy implementation targets, implement them in the compiler, and see the errors disappear one by one. If it turns out that not a lot of pieces are missing, you'll be able to fully simulate the cluster with an LLHD-based simulator and push the project forward significantly.

The Moore compiler is written in Rust. Don't be scared if you haven't touched Rust before -- if you know C or C++ you'll feel right at home. The main language we're currently tackling with Moore right now is SystemVerilog, so either knowing the language a bit or not being scared of looking into language reference manual will be useful.

*Skill Level:* Advanced

*Language/Tools:* Rust, SystemVerilog

*Mentor:* [Fabian Schuiki](mailto:fschuiki@iis.ee.ethz.ch)

### Minimal RISC-V core with AI Acceleration synthesizable with open source tools

A series of  projects between Embecosm and Southampton University over the past and a FOSSi GSoC project from 2021 have developed a simple (8 instruction) open source ISA extension for the CV32E40P and CV32E40X RISC-V cores to accelerate neural network inference acceleration.  The project [GitHub](https://github.com/AI-Vector-Accelerator) has demonstrated a 5 fold increase in inference performance.   [YouTube](https://youtu.be/DY8WXLF7CEg) has the most recent presentation of the project, given at the London Open Source RISC-V meetup in January 2022.

This demonstrated the potential benefit of this approach, but could only be synthesized using proprietary FPGA synthesis tools.  This project proposes trying to create a stripped down version which can be synthesized using the Yosys open source tool suite.

The core is delivered within the CORE-V MCU, a SoC wrapper which provides a debug interface, memory and a range of peripherals.  In order to make this project tractable, this will be stripped down to a minimal MCU providing just the debug interface and memory alongside the core. CORE-V MCU uses FuseSoc for ease of development, but the AVA work has not picked this up, so cleaning up the code to use FuseSoc will be an important starting point.

There are a series of steps in this project, so it can be provided as either a medium or long project. It is also quite open ended, so applicants should consider how they would wish to craft the project to directions that most interest them.

The deliverables of this project would be for the medium project:

 - the stripped down, synthesizable with Verilator as a model;
 - the stripped down CORE-V MCU with the CV32E40P core, synthasizable for FPGA with Yosys; and
 - Embench benchmarking of the stripped down CORE-V MCU on FPGA.

The long project would then extend these deliverables with the AI interface using the CV32E40X core:

 - a modified stripped down CORE-V MCU using the CV32E40X core with AI instruction set extensions cleaned up to build completely under FuseSoc.
 - a modified stripped down CORE-V MCU using the CV32E40X core with AI instruction set extensions as a Verilator model;
 - a modified stripped down CORE-V MCU using the CV32E40X core with AI instruction set extensions, synthasizable for FPGA with Yosys; and
 - measurement of the impact on AI inference using TinyMLPerf.

*Skill level:* Advanced (particularly FPGA synthesis using Yosys)

*Project length:* medium or long

*Mentors:* [Jeremy Bennett](https://github.com/jeremybennett) ([email](mailto:jeremy.bennett@embecosm.com)) and [William Jones](https://github.com/william-r-jones) ([email](mailto:william.jones@embecosm.com))

*Language/Tools:* Verilog, SystemVerilog, RISC-V, Yosys open source tool suite, TinyML benchmark suite

### The World's smallest AI processor

The prize winning bit-serial [SERV core](https://github.com/olofk/serv), created by Olof Kindgren, is the world's smallest RISC-V processor. In this project, we propose combining SERV with the miinimal AI instruction set extension developed under the AVA project (https://github.com/AI-Vector-Accelerator). This could for example use the CFU-LI interface.

The goal would be to demonstrate the world's smallest processor optimized for AI inference.

*Skill level:* Intermediate (particularly FPGA synthesis using Yosys)

*Project length:* medium

*Mentors:* [Jeremy Bennett](https://github.com/jeremybennett) ([email](mailto:jeremy.bennett@embecosm.com)) and [Olof Kindgren](https://github.com/olofk) ([email](mailto:olof@fossi-foundation.org))

*Language/Tools:* Verilog/SystemVerilog, RISC-V, Yosys open source tool suite

### Embench DSP Extensions

We will be developing a set of new digital signal processing benchmarks to add to the current suite of Embench DSP benchmarks.  The starting point will be the current suite of DSP benchmarks (FIR, IIR, and FFT).  New benchmarks will be run on a microprocessor and its performance evaluated.

These new benchmarks will be added to the Embench DSP suite and be made available to the world.

There will the opportunity to engage with students at Rice University who are also working on the project.

*Skill level:* Beginner (accessible to students who have some programming experience and are willing to learn)

*Project length:* medium

*Mentors:* Ray Simar ([email](mailto:ray.simar@rice.edu)).

*Language/Tools:* C, embedded platforms on which to evaluate the benchmarks.

### Embench Interrupt Latency benchmark

Embench has always envisaged measuring the dynamic behavior of systems as well as computation throughput.  This is the Embench-RT benchmark suite.

One of the benchmarks on [Embench-RT](https://github.com/embench/embench-rt) is [IRQ latency](https://github.com/embench/embench-rt/blob/main/irq_latency/design/rv-int-latency.md).  The benchmark goal is to measure an MCU interrupt latency. This factor is crucial for RT FW/SW that is driven by interrupts.

Currently, this benchmark can run on RISCV cores; the project will be to integrate the benchmark for the reference Arm Cortex M4 board used for the main [Embench IoT](https://github.com/embench/embench-iot) benchmark. This will act as the reference against which all others will be compared.

*Skill level:* Intermediate (some experience with embedded devices and board support packages).

*Project length:* long

*Mentors:* Ofer Shinaar ([email](mailto:Ofer.Shinaar@wdc.com)) assisted by one of his colleagues (name TBC).

*Language/Tools:* C, embedded platforms on which to evaluate the benchmarks.

# Porting Compiler test-suite (micro-benchmarks) to Embench

Embench contains several benchmarks for IoT, benchmarks targeting performance, and code-size comparison. One missing piece is a compiler test-suite.

The project goal is to port the [riscv32-Code-density-test-bench](https://github.com/westerndigitalcorporation/riscv32-Code-density-test-bench) to Embench IoT new repo. The effort will include porting the Embench build system, bringing up the repo for users (instructions, build, and full run), adding "correctness testing" to the test suite.

*Skill level:* Beginner (some experience with C Python and Git).

*Project length:* medium

*Mentors:* Ofer Shinaar ([email](mailto:Ofer.Shinaar@wdc.com)) assisted by one of his colleagues (name TBC).

*Language/Tools:* C, embedded platforms on which to evaluate the benchmarks.

### VPI based fst digital simulation waveform dumping

Most digital simulators use a proprietary binary data format for storing the simulation waveforms. This makes it impossible to access these waveforms for post processing. The only waveform format which is supported by all simulators is vcd. But the vcd waveform format is very limited as it does not support complex data structures and stores the waveform data in ASCII format resulting in very large waveform data files. The fst file format provided by GTKWave is an alternative. It is open available and represents an efficient binary file format overcoming the vcd file limitations.

The goal of the project is to develop VPI based functions to dump digital simulation waveforms in fst format. 

*Primary Mentor:* Klaus Strohmayer / semify e.U. [email](mailto:office@semify.com)

*Skill level:* intermediate

*Language/Tools:* Verilog / SystemVerilog, C/C++

### More precise instruction scheduling in LLVM for RISC-V based HammerBlade Manycore
The RISC-V ISA will transform the world. Recently, UW taped out an open source RISC-V manycore processor with 496 cores that hits 500 Billion RISC-V instructions per second in one chip. The latest version is called HammerBlade Manycore, the design is hosted on Amazon F1, which allows us to simulate having the real chip even as we develop new features. We maintain a downstream RISC-V LLVM backend for custom compiler support. We want to improve the code generation with better instruction scheduling. We already have some basic scheduling support in our LLVM backend, this project aims to improve it by more precisely describing the pipeline model with adjusted weights.

*Skill level:* intermediate

*Project length:* long

*Mentors:* [Reshabh K Sharma](mailto:reshabh@cs.washington.com), [Michael Taylor](mailto:prof.taylor@gmail.com)

*Language/Tools:* C++, some knowledge of computer architecture, instruction pipelining and LLVM

### TinyParrot: A minimal BlackParrot RISC-V Multicore variant
*Details:* BlackParrot aims to be the default open-source, Linux-capable, cache-coherent, RV64GC multicore used by the world. It has been FPGA and Silicon-validated as an industry-strength design with leading efficiency. We wish to support open-source toolchains for FPGA and ASIC flows, but current open-source SRAM generators have not quite matured to make this seamless. This project will shrink BlackParrot to have extremely tiny caches, provide minimal ISA support and have other logic-saving optimizations with the goal of being able to easily synthesize to gates.

*Skill level:* beginner-intermediate

*Project length:* medium

*Mentors:* [Dan Petrisko](mailto:petrisko@cs.washington.com), [Michael Taylor](mailto:prof.taylor@gmail.com)

*Language/Tools:* SystemVerilog, some knowledge of computer architecture, RISC-V knowledge preferred but not required