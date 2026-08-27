---
title: "XMOD"
description: "Cross-platform Java Swing behavioural experimentation platform replacing legacy Visual Basic software"

weight: 20

project_type: Research software platform
users: researchers
timeline: 2025-present

technologies:
  - Java
  - Swing/AWT
  - Java Sound
  - jSerialComm
  - JUnit

github:
website:
paper:

---

## The Problem

When investigating mental representations of language, psycholinguistic experiments often require millisecond-level precision in reaction time measurements. The technology you use to run these experiments matters.

Oxford University's Language and Brain Lab had used software written in Visual Basic coupled with custom hardware for over 15 years. This set up worked well both at the lab in Oxford, and also could be taken abroad to Europe and India for fieldwork. Researchers could run up to 16 participants at once.

However, the software was run on two very old computers. Attempts to port it to new computers failed. Therefore, new software that could integrate with the existing hardware while maintaining the same functionality was required. I identified the key specification and possible improvements. I architected, implemented, tested and deployed Xmod 2.0.

## The Solution: Xmod 2.0

XMOD is a Java desktop application for running laboratory linguistics experiments involving synchronised audio stimuli, visual stimuli, and participant reaction-time collection through dedicated hardware.

It uses *Swing/AWT* for researcher and participant interfaces, Java Sound for WAV playback, and jSerialComm to communicate with an external controller over USB serial.
The application loads experiment definitions from TMS files, coordinates each experimental trial, sends timing/control information to the hardware, receives binary response packets from up to 16 participant response boxes, decodes reaction times and button presses, and exports experimental results.
The design separates experiment orchestration, serial communication, audio playback, experiment loading, result processing and presentation, with event-driven communication between components.
Long-running operations are moved away from the Swing UI thread, making concurrency and resource lifecycle management important engineering concerns.



## Engineering Highlights

| Purpose | Notes|
|---|---|
|Hardware/software integration | implementing a binary serial protocol around dedicated experimental hardware |
|Concurrent programming | coordinating UI, serial I/O, experiment execution and audio playback without blocking the application |
|Binary data processing | decoding hardware response packets into participant responses and reaction-time measurements |
|Experiment orchestration | coordinating visual presentation, audio, hardware timing commands and response collection across repeated trials |
|Fault handling | dealing with controller disconnection, experiment aborts, invalid experiment definitions and unavailable audio|
|Research data processing | turning raw hardware responses and experiment metadata into structured result files|
|Multi-display UI | providing a researcher interface alongside a full-screen participant display|
|Legacy compatibility | reproducing behaviour and data conventions from an earlier experimental system while moving the implementation to Java.|
|Testing | X% test coverage with JUnit|

### Architecture



## Planned Improvements:

A subsequent iteration will focus on making the concurrency and I/O boundaries more explicit: using a single-owner model for serial communication, an explicit experiment lifecycle/state machine, atomic cancellation and deterministic resource cleanup. I will also strengthen research-data integrity through transactional experiment loading, incremental result persistence, unique run identifiers and provenance metadata such as hashes of the experiment and audio inputs.