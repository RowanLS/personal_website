---
title: "Talverk"
description: "A Python CLI pipeline for preparing, validating, aligning, reviewing, and exporting speech/audio datasets. It manages the full lifecycle from source audio/transcripts through forced alignment to research-ready aligned outputs."

weight: 40

project_type: Research software platform
users: researchers
timeline: 2026-present

technologies:
  - Python
  - MFA
  - FFmpeg
  - SQLite
  - pytest

github:
website:
paper:

---

## The Problem

Linguists are interested in how people actually use language, not just how textbooks claim people do.
Therefore, many linguistics research projects require the collection and preprocessing of audio data for analysis.
Preprocessing audio data is a very time consuming activity for researchers - whether it is done manually or by a succession of individual scripts. Automating this process saves time, allowing researcher time to be spent on the activities that truly need manual handling.

In addition to traditional linguistics research, training and benchmarking machine learning models requires accurately transcribed and processed data.

Faced with these difficulties, I designed, implemented, tested and deployed Talverk.

## The Solution: Talverk
Talverk is a Python CLI pipeline for transforming speech recordings and transcripts into reviewed, research-ready aligned datasets. The system uses FFmpeg and Montreal Forced Aligner (MFA), manages out-of-vocabulary words and G2P pronunciation generation, processes Praat TextGrids, and supports word-level audio export.

The engineering focus is on building a reproducible, stateful processing workflow around tools that operate on the filesystem and through long-running subprocesses. A SQLite manifest tracks samples and processing state, while structured logging provides traceability across ingestion, validation, preparation, alignment, review and export.

## Engineering Highlights

| Feature | Notes |
|---|---|
|Stateful pipeline design | persistent SQLite manifest rather than an ephemeral sequence of scripts |
|Scientific tool orchestration | controlled integration of FFmpeg, MFA and G2P through Python subprocesses |
|Research reproducibility | checksums, structured metadata and a clear path toward artifact/configuration provenance |
|Human-in-the-loop workflow | alignment output passes through explicit review before final export |
|Data transformation | canonical audio preparation, OOV remediation, TextGrid manipulation and word-level segmentation |
|Observability | structured JSON logging and planned event-driven progress reporting |
|Reliability engineering | identified concurrency, atomicity, cancellation and recovery requirements rather than treating filesystem processing as inherently transactional|
|Comprehensive Testing| 67% coverage with pytest|

## Planned Improvements
The initial implementation exposed an important systems problem: database state, filesystem artifacts and external subprocesses cannot participate in a single transaction. A second version will therefore model processing explicitly as recoverable runs, with guarded SQLite state transitions, isolated workspaces and atomic publication of validated artifacts.


I will add artifact provenance—linking outputs to input checksums, configuration, models and tool versions—and formalise idempotency so interrupted operations can be safely retried. Subprocess management would gain bounded output, timeouts and signal-aware cancellation.


Finally, I will extract orchestration from the CLI into a service layer that emits typed progress events. This would support a Rich terminal interface while preserving clean non-interactive/CI operation and keeping presentation independent of processing correctness.

## Related Projects
I built Harken, desktop software to collect audio data on fieldwork that was then processed by Talverk. I used Talverk to preprocess 4800 files for my Bengali Aspiration project. This avoided manual preprocessing by research assistants, who could then focus on checking automated measurements.

I also used Talverk to process the training and testing data for different FlexSR applications. As of August 2026, I have processed over 100,000 files for this purpose.