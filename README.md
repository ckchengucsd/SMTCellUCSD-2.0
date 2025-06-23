# SMTCell 2.0
<p align="center">
    <img src="/doc/figure/SMTCellLogo.png" width="650">
</p>
<p align="center">
    <a href="https://github.com/ckchengucsd/SMTCellUCSD-2.0/network/dependencies" alt="Contributors">
        <img src="https://img.shields.io/github/contributors/ckchengucsd/SMTCellUCSD-2.0" /></a>
    <a href="https://github.com/ckchengucsd/SMTCellUCSD-2.0/network/pulse" alt="Activity">
        <img src="https://img.shields.io/github/commit-activity/m/ckchengucsd/SMTCellUCSD-2.0" /></a>
    
</p>


**SMTCell** is a cell layout generation toolkit developed by the VLSI Lab at the University of California, San Diego, designed for DTCO/STCO exploration.  
Our goal is to facilitate technology exploration for **FinFET** and **CFET** devices through intuitive design rule encoding using **Satisfiability Modulo Theories (SMT)**.

## Why SMTCell 2.0?

**SMTCell 2.0** offers significant improvements over the original version — it's on average **10× faster**.  
It supports both **FinFET**, **GAAFET** and **CFET** technologies (with certain assumptions) and introduces a range of new features that allow users to **customize and optimize** their designs more effectively.


## Main Flow
<!-- <p align="center">
    <img src="/doc/figure/flow.png" width="650">
</p> -->

## Setup Guide
### Quick Setup Guide
With [CMake(>3.18.0)](https://cmake.org/download/), you can easily compile our codebase. Please follow the steps below:
```bash
mkdir build && cd build
cmake ..
make # you should genSMTInputAGR and convSMTResult executables
cd ..
```
Our underlying SMT solver is [Z3 Prover Version 4.8.5](https://github.com/Z3Prover/z3/releases/tag/Z3-4.8.5). Please follow the link, download and install the software. Alternatively, if you have Python installed, we recommend you to use `pip` for easy install. 
*(Version 4.8.5 is highly recommended. Installing any other version of Z3 Prover may cause unexpected behavior.)*
```bash
# [optinal] create a Python virtual environment using venv
python3 -m venv smtcell
# [optinal] activate the virtual environment
source smtcell/bin/activate
# install z3-solver using pip
pip install z3-solver
# sanity check
z3 --version # this should return Z3 version 4.8.5 - 64 bit
```
Now you are ready to go! Optionally, please consider installing the following tools and libraries for better experience.

### Optional Tools and Libraries (Recommended)
_SMTCell_ depends on open source tools and libraries. Please download and install the following software if you want to enjoy the complete functionality of _SMTCell_.
- [GDT2GDS](https://sourceforge.net/projects/gds2/) for converting .gdt to .gds.
- [KLayout](https://www.klayout.de/) for viewing .gds/.lef files.
- [PROBE3.0](https://github.com/ABKGroup/PROBE3.0/) for custom PDK generation.

## Quick Start
_SMTCell_ contains three different flows. For generating
```bash
# inside the main directory
make SMTCell
# or Prepartition + main flow
make SMTCell_prepartition
# generate .gds/.lef and preview cells using Klayout
make viewSMTCell
```
## Design Your Own Cell
For setting up the cell configuration and customize cell based on your own designs, please visit this documentation [here](https://github.com/ckchengucsd/SMTCellUCSD/blob/main/doc/Design.md).

## Pre-Partitioning
<p align="center">
    <img src="/doc/figure/prepartition.png" width="650">
</p>

While smaller cell designs (e.g. AND, INV, ...) can be quickly generated within minutes of runtime, larger cells like DFF can be siginificantly slower. This is due to the fact that with larger design space, the literal, clauses and formulas grow exponentially. To combat this problem, we provide options to reduce the solution space by using prepartition engine. More documentation can be found [here](https://github.com/ckchengucsd/SMTCellUCSD/blob/agr/doc/PrePartition.md).

## Report an Issue
If you encounter any issue, please report it to us by creating an issue [here](###).

## Past Works and References (not in any particular order)
- Park, Dong Won Dissertation: [Logical Reasoning Techniques for Physical Layout in Deep Nanometer Technologies](https://escholarship.org/content/qt9mv5653s/qt9mv5653s.pdf)
- Lee, Daeyeal Dissertation: [Logical Reasoning Techniques for VLSI Applications](https://escholarship.org/content/qt7xp6p3h1/qt7xp6p3h1.pdf)
- Ho, Chia-Tung Dissertation: [Novel Computer Aided Design (CAD) Methodology for Emerging Technologies to Fight the Stagnation of Moore’s Law](https://escholarship.org/content/qt2ts172zd/qt2ts172zd.pdf)
- D. Park, I. Kang, Y. Kim, S. Gao, B. Lin, and C.K. Cheng, "ROAD: Routability Analysis and Diagnosis Framework Based on SAT Techniques," ACM/IEEE Int. Symp. on Physical Design, pp. 65-72, 2019. \[[Paper](https://dl.acm.org/doi/pdf/10.1145/3299902.3309752)\] \[[Slides](https://cseweb.ucsd.edu//~kuan/talk/placeroute18/routability.pdf)\]
- D. Park, D. Lee, I. Kang, S. Gao, B. Lin, C.K. Cheng, "SP&R: Simultaneous Placement and Routing Framework for Standard Cell Synthesis in Sub-7nm," IEEE Asia and South Pacific Design Automation, pp. 345-350, 2020. \[[Paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9045729)\] \[[Slides](https://www.aspdac.com/aspdac2020/archive/pdf/5C-3.pdf)\]
- C.K. Cheng, C. Ho, D. Lee, and D. Park, "A Routability-Driven Complimentary-FET (CFET) Standard Cell Synthesis Framework using SMT," ACM/IEEE Int. Conf. on Computer-Aided Design, pp. 1-8, 2020. \[[Paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9256570)\]
- D. Lee, C.T. Ho, I. Kang, S. Gao, B. Lin, and C.K. Cheng, "Many-Tier Vertical Gate-All-Around Nanowire FET Standard Cell Synthesis for Advanced Technology Nodes," IEEE Journal of Exploratory Solid-State Computational Devices and Circuits, 2021, Open Access. \[[Paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9454552)\]
- C.K. Cheng, C.T. Ho, D. Lee, and B. Lin, "Multi-row Complementary-FET (CFET) Standard Cell Synthesis Framework using Satisfiability Modulo Theories (SMT)," IEEE Journal of Exploratory Solid-State Computational Devices and Circuits, 2021, Open Access. \[[Paper](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9390403)\]
- S. Choi, J. Jung, A. B. Kahng, M. Kim, C.-H. Park, B. Pramanik, and D. Yoon, "PROBE3.0: A Systematic Framework for Design-Technology Pathfinding with Improved Design Enablement," IEEE Transactions on Computer-Aided Design of Integrated Circuits and Systems, 2023, Open Access. \[[Paper](https://ieeexplore.ieee.org/document/10322780)\]
- The PROBE3.0 Framework. \[[GitHub](https://github.com/ABKGroup/PROBE3.0)\]


## Acknowledgement
Our work here is built upon previous works done by authors/researchers: Daeyeal Lee, Dong Won Park, Chia Tung Ho, and Minsoo Kim Et al. Also we would like to thank our collaborators and contributors: Prof. Andrew B. Kahng, Prof. Bill Lin, [Dooseok Yoon](https://github.com/doo3yoon), Zichen Zhou, and Nihal Nazeem. 
