---
title: Architecture / Performance Modeling
subtitle: Working with Memory, Processors, IO and everything that defines how
  computers “compute”
date: 2022-08-31T17:49:16.336Z
summary: ""
draft: false
featured: false
authors: []
lastmod: 2020-12-13T00:00:00.000Z
tags: []
categories: []
projects: []
image:
  caption: "Image credit:
    [**Unsplash**](https://medium.com/geekculture/computer-architecture-ii-pipe\
    line-8e65944a1b27)"
  focal_point: ""
  placement: 2
  preview_only: false
  filename: comparch.png
---
## Topics covered

* There will almost always be questions on Caches
* * Basics - why do we need caches in the first place (memory hierarchy pyramid)
  * 3C’s of Cache - Compulsory, Capacity and Conflict misses + Coherence misses for multicore 
  * Sizing and properties of caches at various levels 
  * Cache coherence and the different coherence protocols
  * * Should be able to walk through an example for each protocol
    * Why ‘O’ state in MOESI, why ‘E’ state in MESI?
  * Banking schemes in Caches - not many undergrad courses cover this, so needs extra preparation
  * Inclusiveness and exclusiveness of caches
  * Basic cache replacement policies (LRU, FIFO, SRRIP and other protocols if mentioned in resume projects).
  * * Know for which workloads which works best (cache friendly workloads, scan based workloads, thrashing workloads and mixed workloads)
    * Coherence vs Consistency (Basic understanding of memory consistency is necessary) 
* Pipeline basics
* * Hazards, Superscalar, etc 
  * Different types of hazards and what exists in an in order pipeline
  * Hazards that arise  in a pipeline with multiple functional units with different latencies (The issue is still in order to the Func. units, but they complete out of order)
  * Hazards in a full out of order pipeline and how to mitigate them 
* Out of order execution
* * Should be able to walk through Tomasulo’s algorithm
  * Graduate students could be asked advanced concepts
  * * Handling exceptions in Out of Order processors (precise exceptions)
    * Need of Reorder buffer, reservation station
    * RAT (register alias table)
    * Register renaming and different ways to achieve that (separate rename register file, physical register file concept, renaming using ROB, using the reservation station entries etc)
    * Think about when rename registers can be recycled/resued exactly?
    * Load Store Dependence (Memory disambiguation , load store forwarding,load store queue)
* Branch Prediction 
* * Different schemes (Gshare, Gselect, Bimodal, global vs local schemes)
  * BTB (branch target buffer), Return address stack 
* Value prediction and Prefetching (Usually not asked unless you might have specific projects) 
* Virtual memory 
* * Address translation mechanism in x86 using multi level page table, TLB
  * Page table walk on a TLB miss
  * VIPT (virtually indexed physically tagged) /PIPT caches 
  * Homonyms and Synonyms problems in the above caches and how to solve them.
* Interrupts 
* * Basics on what they are, interrupts vs exceptions and how they are handled
* Basics OS theory-
* * Threads, processes
  * * What happens on a process context switch vs thread context switch 
  * Mutex, Semaphore
  * * Internal implementation of mutex using (TestandSet, Compare and Swap, load linked, store conditional. These are basically instructions in an ISA) 
  * Atomics
  * Memory barriers and Memory fence
* Programming
* * Typical C++ knowledge based questions - Classes, OOP concepts, etc
  * Linked list manipulation - very important (Ex- Reversing linked lists, intersection of 2 linked lists etc)
  * Stacks and Queues (implementation from scratch)
  * Bit manipulation questions - frequently asked
  * Arrays (Two pointer techniques) 
  * Hash maps/ unordered maps  (Mainly used in other problems due ot O(1) search complexity)

## Some “gotchas”

* Since computer architecture comes under “computer science” in many places, there is an assumption that you are a good programmer
* * So if you are from an Electrical Engineering background, this could be the harder part of the interview. Spend a lot of time programming, and be familiar with language specific constructs (especially C++). 
* In architecture interviews there is sometime more importance given to syntax than algorithms (Pseudo codes expected mainly atleast for many interviews)
*
* In general the “architecture” part of comp arch interviews are more of a discussion to know how much you are aware of. The questions will depend on how you answer. They might for example ask you to explain what all you know regarding the fetch stage. Say you start talking about icache. They might ask you for ideal sizing, associativity etc for the icache. If you bring up I-TLB, then VM concepts come into picture. You might talk about branch prediction in the first stage. Then they go deep about how BP is exactly done.. Using BTB, BP-predictor (counter based), return address stack etc

## Some challenging interview questions

Programming

* Difference between shallow and deep copy - this is subtle, but important
* How do you find if 2 nodes in a graph are connected

Micro architecture

* In a typical MIPS ISA, you have only 2 working registers. But you have a large number of ALU units. Design an instruction to emulate swap

## Resources

For architecture good resources include -

* [Gatech HPCA](https://www.youtube.com/watch?v=tawb_aeYQ2g&list=PLAwxTw4SYaPmqpjgrmf4-DGlaeV0om4iP&ab_channel=Udacity) (Covers most concepts asked in interviews. Very short videos and easy to follow. If you are still not exposed to comp arch and have interviews coming up, this is the best place to get started in my opinion. It will take a few days to finish)
* [madhu mutyam iit-m nptel](https://www.youtube.com/watch?v=NjsEz_tBVxw&list=PLdS3u59E0DKjUKPcnCYxVxssEkX2zo-kV&ab_channel=ComputerArchitecture)  (especially for out of order execution, superscalar microarchitecture, coherence, synchronization concepts, memory consistency concepts)
* [Onur Mutlu](https://www.youtube.com/watch?v=LbC0EZY8yw4&list=PL5Q2soXY2Zi_uej3aY39YB5pfW4SJ7LlN&ab_channel=OnurMutluLectures) (Slightly long lectures, but gives a detailed understanding of the concepts) 
* [Modern processor design (Superscalar)](https://www.amazon.com/Modern-Processor-Design-Fundamentals-Superscalar/dp/1478607831) (Chapters 4 and 5 are very detailed for superscalar microarch and arch for apple interviews (full time). This level might not be expected during internships )
* [Eric rotenberg slides](https://people.engr.ncsu.edu/ericro/teaching.htm) 

Say you say I don’t know any DSA, and need to have a good understanding of the basics. This is possibly one of the best introduction to abstract data structures, array,linked lists, stack, queue, trees, graphs.  (9 hr video. Solid content. ([dsa](https://www.youtube.com/watch?v=B31LgI4Y4DQ&ab_channel=freeCodeCamp.org) ) <RIP Harsha/ HumbleFool >

Say you don’t know even basics of pointers. Another gem of a video from humblefool ([pointers](https://www.youtube.com/watch?v=zuegQmMdy8M&t=852s&ab_channel=freeCodeCamp.org) )

The best book on OS. Not super important, but good to know ([OSTEP](https://pages.cs.wisc.edu/~remzi/OSTEP/) )

Some good set of programming questions (topic wise)- It is good to solve the first few questions in all topics, though this comprehensive list is meant for software interviews  ([450 questions luv bubbar](https://drive.google.com/file/d/1FMdN_OCfOI0iAeDlqswCiC2DZzD4nPsb/view) )

Some basic C questions - <https://www.interviewbit.com/c-interview-questions/>

C/C++ knowledge based questions - <https://www.codingninjas.com/blog/2021/09/13/top-c-c-interview-questions-in-2021-part-1/>

<https://www.codingninjas.com/blog/2021/09/14/top-c-c-interview-questions-in-2021-part-2/>

Basic C++ programs to understand syntax - <https://www.codezclub.com/cpp-solved-programs-problems-solutions/>

This is a good (good=small here) set of programs for DSA questions (May not need this level for Hardware interviews, but good to do anyway) - <https://www.byte-by-byte.com/50-questions/>

Low power design concepts for Power Architecture roles (Can clear many power arch roles if these basics from NPTEL are known). 

<https://www.youtube.com/watch?v=TFOO1JAll2Y&ab_channel=VLSIPhysicalDesign> 

<https://www.youtube.com/watch?v=ORtlxpW_LMU&ab_channel=VLSIPhysicalDesign>

**Quick recap for Cache Coherence protocols - <https://www.youtube.com/watch?v=r_ZE1XVT8Ao&ab_channel=NesoAcademy>**