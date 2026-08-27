---
title: "SplicePrep"
description: "Automation of experiment runfile creation for behavioural experiments."

weight: 50

project_type: Research software platform
users: researchers
timeline: 2017-present

technologies:
  - Python
  - PyGUI
  - pandas
  - pytest
  - Pydantic
  - openpyxl

github:
website:
paper:

---
## The Problem

Experimental psycholinguistics often requires researchers to transform trial lists stored in spreadsheets into specialised input files for experimental software. This involves more than simply converting file formats: researchers need to select and reorder columns, add experiment-specific commands and timing information, modify stimulus filenames, generate coding information, and insert breaks or countdowns at appropriate points in an experiment.

I first wrote the script that became SplicePrep in 2017 to automate this process for experiments using the Splice presentation system. It evolved incrementally as it was used for different experiments, accumulating additional functionality as new requirements arose.

Although the script continued to work, its architecture reflected that history. It relied heavily on pandas DataFrames, mixed input handling, transformations and Splice-specific formatting, and used multi-stage operations such as inserting empty rows before making a second pass to convert them into experimental breaks. The implementation had become harder to reason about, test and extend than the underlying problem required.

I am therefore re-engineering the original research script as SplicePrep: a small, maintainable Python library and CLI for generating validated Splice experiment files.

## The Solution: SplicePrep

SplicePrep converts configurable CSV and Excel experiment lists into Splice-compatible experimental scripts. Researchers map columns in their own spreadsheets onto semantic roles, allowing the same software to support experiments with different input schemas without requiring researchers to rename or restructure their source data.

The redesigned system uses a layered architecture centred around a streaming transformation pipeline. Input rows are converted into an internal **Working Row** representation and progressively enriched as they pass through a fixed sequence of transformations. Rows are mutated in place and yielded onwards, avoiding the repeated creation of intermediate DataFrames. A final projection stage selects and orders the information required for the Splice output.

Configuration is represented by immutable, validated Pydantic models. This provides a common API that can be used by the current CLI and by a planned FastAPI backend without coupling the experiment-generation logic to either interface.

The engineering work is therefore not simply a migration away from pandas. It is the modernisation of a long-lived research script into a reusable, typed and testable software component while preserving the experimental workflow it has supported since 2017.

## Engineering Highlights

| Feature | Notes |
|---|---|
| Legacy software modernisation | re-engineering a research script developed incrementally since 2017 rather than replacing a newly designed prototype |
| Layered architecture | separation of interface, application, domain and infrastructure concerns, allowing the core library to remain independent of CLI or web frameworks |
| Streaming transformation pipeline | generator-based row processing replaces repeated whole-DataFrame transformations and unnecessary intermediate objects |
| Explicit internal data model | mutable Working Rows act as the internal representation, with enrichment stages preserving information until final output projection |
| Configuration-driven schema mapping | user spreadsheet columns map onto semantic roles rather than requiring a fixed input schema |
| Validated configuration | immutable Pydantic configuration provides fail-fast validation and a shared contract for CLI and future FastAPI callers |
| Reliability and error handling | invalid configuration and input data fail early with specific, explanatory errors rather than propagating ambiguous processing failures |
| Observability | library code emits standard Python log records while logging configuration remains the responsibility of the calling CLI or application |
| Testability | small, single-responsibility transformations support focused unit testing, complemented by golden-file integration tests against known-correct Splice output |
| Architecture governance | architectural invariants, development conventions and significant design decisions are documented separately through architecture documentation and ADRs |

## Planned Improvements

The immediate work is to complete the migration from the original pandas-based implementation to the new architecture. CSV and Excel readers will normalise source data into the same Working Row representation, after which enrichment, break insertion, projection and Splice serialisation can operate independently of the original file format.

I will build regression coverage around existing experiment files using golden-file tests. This is particularly important for a mature scientific script: the objective is not merely to produce output that looks plausible, but to demonstrate that the re-engineered implementation preserves known experimental behaviour while making future changes safer.

The initial interface will remain a CLI. I subsequently plan to incorporate SplicePrep into a FastAPI application with a Jinja/HTMX frontend. The core generation library is deliberately independent of these interfaces, so the web application will reuse the same validated configuration models and processing pipeline rather than introducing a second implementation of the experiment-generation logic.

The redesign also establishes clearer boundaries for future maintenance. Configuration changes parameters rather than determining which transformations execute; transformations receive only the information they require; library code does not configure logging or interact directly with users; and architectural decisions are recorded explicitly rather than remaining implicit in a legacy script.

## Evolution of the Project

SplicePrep is an example of a common research software lifecycle. It began in 2017 as a script written to solve an immediate experimental problem. Continued research use demonstrated its value, but also led it to accumulate features and assumptions over time.

The current work applies modern research software engineering practices to that established functionality: explicit architecture, typed interfaces, dependency boundaries, configuration validation, deterministic transformations, automated regression testing and separation between the reusable scientific logic and its user interfaces.

The objective is not to turn a relatively small data-transformation problem into an unnecessarily complex system. It is to retain the simplicity that made the original script useful while introducing enough engineering structure that the software can be understood, tested, reused and safely maintained as it continues to evolve.

## Related Projects
This helps create the input files for XMOD.