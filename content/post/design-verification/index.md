---
title: Design Verification
subtitle: Involves the design/integration of digital logic modules that go into
  a chip or IP.
date: 2022-08-31T17:38:06.483Z
summary: ""
draft: false
featured: false
authors: []
lastmod: 2020-12-13T00:00:00.000Z
tags:
  - Digital
categories:
  - Digital
projects: []
image:
  caption: "Image credit: [**Unsplash**](http://www.vegasemi.com/dv.php)"
  focal_point: ""
  placement: 2
  preview_only: false
  filename: design_verification.jpeg
---
## Topics covered

* Verilog syntax and programming
* * Try to be familiar with all the synthesizable constructs used in Verilog
  * * Ex. Blocking vs Non-blocking statements - trivial, but it is surprising how often it comes up (and how often interviewees stumble)
    * Casex, Casez and the variations
  * A very common question pattern: 
  * * Write Verilog code to do “something” (Ex. BCD counter)
    * What do the different sections of your code synthesize to - very important to know this, this is where Verilog interviews are different from other coding interviews. For example, always @ (posedge clock) would typically result in a logic involving Flip-Flops
    * Make some kind of changes to the input/output (Ex. Output should be triggered by another signal, Output should be seen with a delay of one cycle, Synchronous vs Asynchronous reset, etc)
* Digital Design concepts
* * Basic logic design (the kind of questions that show up in an undergraduate digital electronics course) - Ex. Universal gates, design different gates using a MUX
  * Designing a counter is also the most commonly asked design question
  * State Machine design
  * * Design state machines (Draw the state diagram) for the given scenario
    * Mealy vs Moore model - very very important - learn how to come up with both models any scenario
    * Typically, state machine questions are converted to Verilog questions (i.e. write verilog code for the state machine you designed). It is good to practice a template for state machines (both models) so that you can convert any state diagram to code easily.
    * Another variation here could be binary encoding vs one-hot encoding for the states - each has pros and cons
* Static Timing Analysis
* * What the different terms (setup time, hold time, etc) mean
  * Given a Flop - Logic - Flop configuration
  * * Is there setup or hold violations
    * If there are any, how to fix them
    * There are multiple variations of this question, and they are well documented in any STA book or tutorial - spend time to master this
  * Time borrowing (Especially if you are a grad student)
  * Metastability and how to deal with it
  * * Know the basics for all interviews, but also learn about specifics like MTBF in case of clocking-related roles
* C Programming
* * Basic C programming could be asked in both RTL design and verification roles. One should be able to code at least till Linked Lists. 
  * * Sorting is also commonly asked

## Some “gotchas”

* Although you might be interviewing for an RTL design role, it is better to prepare a little above and below the VLSI stack
* * Up the stack: Computer Architecture - A theoretical understanding is recommended (The typical 5-stage pipeline, Memory hierarchy, Branch prediction, etc)
  * Down the stack: MOSFETs and CMOS design (These are not asked as often, but as a digital designer you are expected to know about CMOS inverters and basic logic gates at the transistor level)
* If you have previous experience in RTL design
* * Identify some key blocks from your previous design (Ex. Content Addressable Memories, FIFOs, etc) - this is a typical question to know how deep you have been
  * You should also be able to come up with a quick implementation of these structures (You could always skip the edge cases that would have been covered in the actual design, but be able to write basic working HDL)
  * Understand basic Valid-Ready handshaking and learn how to design for it. This is used in almost every digital block in the industry.
  * * Read about the AXI protocols (the different channels and how transactions work) if you have any experience involving AXI blocks (which would be the case for most RTL in the industry)
    * * “Backpressure” is something that is asked often - in simple words, how do you tell the block before you that it needs to stop sending data. The simple way to do this is using the valid-ready protocol, but there are others (valid-afull, valid-credit, etc)
* If you are applying for an FPGA company or team, make sure you understand FPGAs well, and how they are different from ASICs
* * And also how to write better RTL for FPGAs (they are register rich, have hard DSP blocks, etc - how does this impact your design decisions?)

## Some challenging interview questions

* Minimum FIFO Depth Calculation given sender and receiver transfer rates (This can get complex with multiple inputs/outputs)
* FSMs
* * Serial 2’s complementer
  * Detect more than two 1’s in the last 3 samples
  * Pattern (Ex. 1011) detector - overlapping and non-overlapping case
* Verilog
* * Detecting positive edge/negative edge/both
  * FIFO (Usually for experienced candidates)
  * Clock dividers (Divide by 2, 3, etc) with different duty cycle
* CMOS
* * Which is faster - PMOS or NMOS? Why do we size them differently?
* Puzzles
* * Sometimes the interviewers end the round with some puzzle questions. One such example question is - There are 25 horses with 5 race tracks. Each track can be used to race 5 horses. You don't have a watch. Find the minimum number of races needed to identify the top 3 fastest horses?

## Resources

Verilog basics practice (“leetcode for Verilog”) - <https://hdlbits.01xz.net/wiki/Main_Page>

Free verilog/system verilog simulation tool - <https://www.edaplayground.com/> - You can write your own designs and testbenches for practice here

Some good coding guidelines - [RTL_coding_guidelines](http://www.sunburst-design.com/papers/CummingsSNUG1999SJ_SynthMismatch.pdf) 

Good resource for FIFO depth calculation questions - <https://hardwaregeeksblog.files.wordpress.com/2016/12/fifodepthcalculationmadeeasy2.pdf>

Low power RTL methods (Good to know for follow-up questions about improving your code) - <https://www.design-reuse.com/articles/20775/hdl-design-low-power.html>

Common digital blocks in Verilog - <https://verificationguide.com/verilog-examples/>

Common digital blocks in System Verilog (Synthesizable) - <https://www.asic-world.com/examples/systemverilog/index.html>

Cracking the Digital VLSI Verification Interview (Book by Ramdas Mozhikunnath and Robin Garg) - This is a great book for basic digital design questions. Can skip the verification part for RTL design roles.

FPGA specific concepts - this is a good playlist - <https://www.youtube.com/playlist?list=PLPmSCnkkX4qtfS4quvY2UDsNSBY5cuIB9>

Verilog Syntax Questions - <http://asic.co.in/Index_files/verilog_interview_questions.htm>

Designing an Arbiter - <https://github.com/bmartini/verilog-arbiter>

Designing FIFOs the right way - <http://www.sunburst-design.com/papers/CummingsSNUG2002SJ_FIFO1.pdf>

In general all Sunburst papers are very good if you want to become a better RTL designer (but might be overkill just for an interview) - <http://sunburst-design.com/papers/>

Digital Logic RTL and Verilog Interview Questions (Book by Trey Johnson) - Excellent for RTL interviews, has some challenging design questions

Some challenging FSM Questions - <https://www.vlsiuniverse.com/fsm-finite-state-machine-qustions/#:~:text=Design%20a%20finite%20state%20machine%20%28FSM%29%20that%20will,and%20111.%20Let%20us%20assume%20four%20different%20states>

A painstakingly long question list (worth skimming through, there are few interesting questions ) - <https://cdcnitw.files.wordpress.com/2013/04/vlsi_questions.pdf>

The typical STA interview question - <https://www.youtube.com/watch?v=iqvZLAgoA-g&list=PLD5C0Wv5Dnmdv-B6NGOu4MA3yDlqFfdre&index=4&t=2s&ab_channel=ElectroTuts>

<https://www.youtube.com/watch?v=R50lGuibylE&list=PLD5C0Wv5Dnmdv-B6NGOu4MA3yDlqFfdre&index=5&ab_channel=ElectroTuts>

AXI protocol basics - <https://www.youtube.com/watch?v=1zw1HBsjDH8&list=PLaSdxhHqai2_7WZIhCszu5PLSbZURmibN&ab_channel=DillonHuff>