# DFIR Education Portfolio

This repository documents a focused 105-hour digital forensics and incident
response training sprint from June 22 through August 7, 2026. It begins from a
documented beginner baseline and emphasizes measurable improvement rather than
implied prior expertise.

## Goals

- Investigate Windows endpoint, memory, network, and identity evidence.
- Build defensible timelines and explain conclusions with cited artifacts.
- Connect forensic findings to containment, eradication, and recovery.
- Demonstrate forensic-tool engineering through a validated project.
- Publish professional case reports that can be discussed in interviews.

## Planned portfolio

1. Windows endpoint intrusion investigation
2. Memory and malware-triage investigation
3. Network and identity investigation
4. End-to-end enterprise incident response capstone
5. HeaderHunter forensic-tool engineering case study

## Existing flagship project

**HeaderHunter** is a cross-platform forensic CLI and GUI developed during an
internship to identify encrypted containers and expose defensible metadata for
triage and recovery workflows. The project includes format-aware detectors,
entropy and statistical analysis, tests, documentation, and packaging for
Windows, macOS, and Linux.

Because the source project was developed in an internship environment, this
repository contains only a sanitized case-study template. Source code,
screenshots, employer details, datasets, and internal design information must
not be published without written authorization from the rights holder.

See [projects/headerhunter-case-study.md](projects/headerhunter-case-study.md).

## Repository standard

Every published case will include:

- An executive summary
- Scope and investigative questions
- Evidence inventory and integrity information
- Methodology and tools
- UTC-normalized timeline
- Findings with artifact-level support
- MITRE ATT&CK mapping
- Indicators and detection opportunities
- Containment, eradication, and recovery recommendations
- Limitations and unanswered questions

The detailed schedule is in [STUDY_PLAN.md](STUDY_PLAN.md). The working
checklist is in [TRACKER.md](TRACKER.md).

The starting assessment is in [notes/baseline.md](notes/baseline.md).
