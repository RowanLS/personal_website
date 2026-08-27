---
title: "Harken"
description: "Full-stack configurable React-based speech data collection platform for independent linguistics fieldwork"

weight: 30

project_type: Research software platform
users: researchers
timeline: 2023-present

technologies:
  - Python 3.12
  - FastAPI
  - Vue3
  - SQLite
  - Briefcase

github:
website:
paper:

---

## The Problem

Linguistic data is key to linguistics research. However, collecting and labelling large amounts of linguistics data is time-consuming and risks errors.

## The Solution : Harken

Harken is a local-first desktop application for collecting and managing audio recordings for linguistic fieldwork and experimental research. It is designed for researchers who may be working without reliable internet access, so recording, administration, storage and data management all operate locally on the researcher’s computer.
The application combines a dedicated participant recording interface with a separate researcher administration interface, coordinated by a local Python backend. Research metadata is stored in SQLite while audio and other large artefacts are maintained on the filesystem.



## Engineering Highlights

|Purpose | Notes|
|---|---|
|Software architecture	| Multi-component desktop application with clearly defined frontend, backend and persistence boundaries|
|Research software engineering	| Software designed around reproducibility, provenance, archival requirements and research workflows|
|Backend engineering	|FastAPI service coordinating validation, business logic, persistence, audio processing and exports|
|Frontend engineering	|Vue/TypeScript participant SPA alongside a server-rendered Jinja/htmx researcher interface|
|Data modelling	|Relational representation of experiments, versions, participants, sessions, consent and recordings|
|Data integrity	|Immutable experiment versioning and idempotent recording uploads|
|Audio processing	|Centralised capture, validation, processing and archival storage pipeline|
|Persistence	|Deliberate separation of structured SQLite data from binary filesystem assets|
|Offline operation	|Local-first architecture requiring no network connection during normal research use|
|Data portability	|Self-contained projects and exports designed for movement, analysis and long-term archiving|
|Resilience	|Explicit backup, recovery, archival and deletion workflows|
|Maintainability	|Separation of concerns supported by documented Architecture Decision Records|

## Architecture

Diagrams Coming

## Related Projects
An earlier version of this software was deployed for a colleague to use on fieldwork in India. Harken facilitated the collection of 4800 files that were preprocessed using Talverk and then analysed as part of my Bengali Aspiration research project.