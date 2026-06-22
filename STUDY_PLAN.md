# 105-Hour DFIR Career Sprint

**Dates:** June 22-August 7, 2026  
**Schedule:** Monday-Friday, 3 hours per day  
**Total:** 35 study days / 105 hours

## The outcome

By August 7, the target is not “DFIR expert.” The realistic and valuable
target is:

- Strong junior-level investigation fundamentals
- Four coherent investigations you can explain without bluffing
- One useful script with tests and documentation
- A clean GitHub portfolio and evidence-based resume
- Rehearsed answers for common DFIR technical and behavioral interviews

The portfolio should prove that you can answer:

1. What happened?
2. When did it happen?
3. How confident are you, and what evidence supports the conclusion?
4. What systems, users, and data were affected?
5. What should the organization do next?

## Priority order

The sprint deliberately prioritizes:

1. Windows endpoint artifacts and event logs
2. Timeline construction and evidence-based reporting
3. Incident response decisions and communication
4. Memory analysis
5. Network, SIEM, and identity-log analysis
6. DFIR tool engineering and validation
7. Linux and cloud breadth

Do not attempt to master every DFIR tool. Learn the evidence first, then use
tools to answer investigative questions.

## Daily operating rhythm

Use this structure on ordinary study days:

- **15 minutes — retrieval:** Explain yesterday's concepts from memory.
- **45 minutes — focused learning:** Read documentation or watch one targeted
  lesson while taking short notes.
- **90 minutes — hands-on work:** Analyze evidence and record commands,
  queries, timestamps, and findings.
- **30 minutes — communicate:** Update the case notebook, README, timeline, or
  report and commit the work.

On Fridays, replace the learning block with review and use at least 45 minutes
for verbal interview practice.

## Core technical stack

Keep the stack intentionally small:

- **Lab:** Windows 11 evaluation VM plus a Linux analysis VM if hardware allows
- **Collection/triage:** KAPE or Velociraptor
- **Windows artifacts:** Eric Zimmerman's tools plus Chainsaw or Hayabusa
- **Disk/file-system review:** Autopsy/The Sleuth Kit
- **Memory:** Volatility 3
- **Network:** Wireshark and Zeek
- **Search/SIEM:** Splunk Free, Elastic, or a lab-provided interface—choose one
- **Automation:** Python, `argparse`, `csv`/`json`, regular expressions, and
  `pytest`
- **Knowledge mapping:** MITRE ATT&CK and NIST incident response guidance

Use only legally provided training images, logs, memory captures, and PCAPs.
Do not upload copyrighted evidence files or malware samples to GitHub.

## Portfolio layout

Create this structure as work is completed:

```text
cases/
  01-windows-endpoint/
  02-memory-triage/
  03-network-identity/
  04-enterprise-capstone/
projects/
  headerhunter-case-study.md
notes/
  windows-artifacts.md
  memory-forensics.md
  network-and-identity.md
  incident-response.md
templates/
  case-report-template.md
```

Each case directory should contain only safe, shareable material:

```text
README.md
report.md
timeline.csv
iocs.csv
queries/
screenshots/
```

Never commit secrets, personal information, proprietary internship data,
malware, or evidence that you do not have redistribution rights for.

## Week 1 — Foundations and lab discipline

**Objective:** Understand the investigation lifecycle, establish a repeatable
workflow, and become conversationally competent with core Windows artifacts.

| Date | Three-hour assignment | Required output |
|---|---|---|
| Mon Jun 22 | Baseline assessment: explain the IR lifecycle, chain of custody, hashing, order of volatility, MFT, Registry, event logs, prefetch, memory, PCAP, SIEM, EDR, and ATT&CK without references. Read the executive portions of NIST SP 800-61 Rev. 3. | `notes/baseline.md` with green/yellow/red ratings and 10 questions you cannot yet answer |
| Tue Jun 23 | Build/verify the lab. Configure UTC, snapshots, shared folders, Git, Python, and a Windows VM. Record evidence-handling rules. | Reproducible `lab-setup.md`; no secrets or license keys |
| Wed Jun 24 | Learn NTFS essentials: MFT, MACB timestamps, USN Journal, `$LogFile`, ADS, deleted files, and timestamp limitations. Perform a small controlled file-activity experiment. | Artifact table: what each source can and cannot prove |
| Thu Jun 25 | Learn Windows execution and persistence artifacts: Prefetch, Amcache, Shimcache, SRUM, services, scheduled tasks, Run keys, LNK, Jump Lists, PowerShell, and common event IDs. | `notes/windows-artifacts.md` organized by investigative question |
| Fri Jun 26 | Mini-triage: examine a small Windows artifact set. Build a 10-20-event UTC timeline and give a five-minute verbal briefing. | First mini-report and recorded self-critique |

**Week 1 gate:** You can explain why one artifact rarely proves execution by
itself and can distinguish evidence preservation from analysis.

## Week 2 — Windows endpoint investigation

**Objective:** Complete a defensible endpoint case rather than a collection of
tool screenshots.

| Date | Three-hour assignment | Required output |
|---|---|---|
| Mon Jun 29 | Select a public Windows forensic image/artifact challenge. Write scope, scenario, evidence inventory, hashes if provided, and five investigative questions before touching the evidence. | Case 01 skeleton and evidence log |
| Tue Jun 30 | Triage file-system and Registry evidence. Identify users, host details, suspicious files, persistence, USB activity, and relevant time zones. | Findings log with artifact paths and confidence |
| Wed Jul 1 | Parse event logs and execution artifacts. Correlate process creation, PowerShell, logons, services/tasks, Prefetch, Amcache, and timeline sources. | UTC super-timeline draft |
| Thu Jul 2 | Determine initial access, execution, persistence, privilege/lateral movement evidence, and impact. Map only supported ATT&CK techniques. | Findings and ATT&CK table with evidence citations |
| Fri Jul 3 | Write and publish Case 01. Deliver a seven-minute briefing: incident, evidence, scope, confidence, and actions. | Polished endpoint report, timeline, IOC list, and lessons learned |

**Week 2 gate:** Every major conclusion points to at least one specific
artifact, and important conclusions are corroborated where possible.

## Week 3 — Memory and malware triage

**Objective:** Explain what volatile evidence contributes that disk evidence
may miss.

| Date | Three-hour assignment | Required output |
|---|---|---|
| Mon Jul 6 | Learn Windows process, handle, DLL, token, registry, command-line, and network concepts relevant to memory. Practice Volatility 3 image identification and core plugins. | Memory command/reference sheet with interpretation notes |
| Tue Jul 7 | Select a legal memory challenge. Establish system profile, process tree, suspicious parents/children, command lines, users, and network connections. | Process tree and prioritized leads |
| Wed Jul 8 | Investigate injection, suspicious DLLs, handles, persistence clues, console history, and network indicators. Extract only safe metadata/hashes. | Evidence matrix with benign and malicious hypotheses |
| Thu Jul 9 | Perform static triage of one suspicious executable or script: hashes, strings, imports, metadata, packing clues, and behavior hypothesis. Do not execute live malware outside a purpose-built isolated lab. | Malware triage note and basic YARA rule if justified |
| Fri Jul 10 | Publish Case 02 and give a seven-minute briefing contrasting disk and memory evidence. | Memory report, process diagram, IOCs, YARA/detection idea, limitations |

**Week 3 gate:** You can defend why a process is suspicious beyond “the tool
colored it red.”

## Week 4 — Network, SIEM, and identity

**Objective:** Correlate activity across hosts and accounts instead of treating
an endpoint as the whole incident.

| Date | Three-hour assignment | Required output |
|---|---|---|
| Mon Jul 13 | Learn TCP/IP and DNS/HTTP/TLS evidence needed for investigations. Practice Wireshark display filters and Zeek logs. | Network investigation cheat sheet |
| Tue Jul 14 | Analyze a public PCAP or Zeek dataset. Identify conversations, DNS behavior, downloads, beaconing clues, and possible exfiltration. | Network timeline and communication map |
| Wed Jul 15 | Load or use a provided SIEM dataset. Write searches for suspicious logons, PowerShell, process execution, new services/tasks, and rare outbound destinations. | At least five documented queries with purpose and caveats |
| Thu Jul 16 | Study identity attacks: password spraying, impossible travel limitations, MFA abuse, token/session theft, Kerberoasting, Pass-the-Hash/Ticket, and privileged account changes. Correlate identity and network evidence in the case. | Identity investigation checklist and supported findings |
| Fri Jul 17 | Publish Case 03 and give a seven-minute analyst briefing plus a two-minute executive summary. | Network/identity report, queries, timeline, and detection recommendations |

**Week 4 gate:** You can explain the difference between an indicator, an
analytic, a hypothesis, and a confirmed finding.

## Week 5 — Enterprise IR and HeaderHunter engineering

**Objective:** Turn technical findings into response decisions and demonstrate
engineering ability through a careful, sanitized analysis of HeaderHunter.

| Date | Three-hour assignment | Required output |
|---|---|---|
| Mon Jul 20 | Study scoping, severity, incident command, evidence preservation, legal/HR/privacy involvement, and communication cadence. Draft a ransomware or compromised-account playbook. | One concise IR playbook |
| Tue Jul 21 | Practice containment tradeoffs: isolate host vs preserve access, disable account vs monitor, block IOC vs hunt behavior, rebuild vs remediate. Run a tabletop with a written decision log. | Tabletop decision log with assumptions and risks |
| Wed Jul 22 | HeaderHunter architecture review: document the investigative problem, input-to-output flow, detector strategy, false-positive controls, supported formats, and boundaries. Use only information approved for public disclosure. | Sanitized architecture and design narrative |
| Thu Jul 23 | HeaderHunter validation review: select safe synthetic samples, document test categories, expected results, ambiguous cases, failure modes, and how cautious language prevents overclaiming. Run the existing test suite privately if permitted. | Validation matrix and quantified test summary |
| Fri Jul 24 | Complete a portfolio-safe HeaderHunter case study and rehearse a five-minute engineering deep dive. If publication permission is absent, publish no source or internal artifacts—describe only your own skills and approved high-level outcomes. | Sanitized case study, resume bullets, interview talking points |

**Week 5 gate:** You can explain HeaderHunter's engineering decisions,
validation, limitations, and investigative value without exposing internship
intellectual property or exaggerating attribution.

## Week 6 — End-to-end capstone

**Objective:** Perform one investigation using a professional workflow from
intake through lessons learned.

Choose a public dataset with at least two evidence types, ideally endpoint
artifacts plus memory, network, or authentication logs.

| Date | Three-hour assignment | Required output |
|---|---|---|
| Mon Jul 27 | Intake and plan: write scenario, scope, stakeholders, assumptions, evidence inventory, time-zone handling, and prioritized questions. Start a contemporaneous activity log. | Case 04 plan and chain-of-custody/evidence table |
| Tue Jul 28 | Rapid triage and scoping. Identify likely patient zero, affected users/hosts, initial time window, and collection gaps. | Triage briefing and collection requests |
| Wed Jul 29 | Deep analysis. Build a corroborated timeline and test competing hypotheses for initial access, persistence, movement, and impact. | Super-timeline and evidence matrix |
| Thu Jul 30 | Response design. Write containment, eradication, recovery, detection, and longer-term hardening actions in priority order. | Technical findings complete; recommendations tied to findings |
| Fri Jul 31 | Draft the full report and present a 10-minute mock client briefing. Revise after reviewing clarity, unsupported claims, and jargon. | Complete capstone draft and presentation notes |

**Week 6 gate:** A reader can distinguish facts, interpretations,
assumptions, and unknowns.

## Week 7 — Career packaging and interview readiness

**Objective:** Convert learning into credible hiring evidence.

| Date | Three-hour assignment | Required output |
|---|---|---|
| Mon Aug 3 | Audit every repository as a hiring manager. Remove clutter, unsafe evidence, dead links, unexplained screenshots, and unsupported claims. Standardize structure. | Clean portfolio with pinned-project shortlist |
| Tue Aug 4 | Rewrite resume. Use internship accomplishments plus 2-3 strongest DFIR projects. Quantify evidence volume, artifacts analyzed, queries/rules built, tests, and investigation outcomes without exaggeration. | One-page master resume and DFIR-targeted version |
| Wed Aug 5 | Technical interview circuit: Windows artifacts, event logs, memory, networking, SIEM/EDR, IR lifecycle, evidence integrity, ATT&CK, ransomware, and compromised identity. Answer aloud, then repair weak areas. | 40-question answer bank; red/yellow/green reassessment |
| Thu Aug 6 | Behavioral/client circuit: ambiguity, pressure, mistakes, communication, teamwork, ethics, prioritization, and explaining a technical finding to an executive. Create STAR stories from the internship and projects. | Eight concise STAR stories and 30/90-second introductions |
| Fri Aug 7 | Final capstone publication, portfolio review, mock 45-minute interview, and application plan. Compare against the June 22 baseline. | Final report, resume, GitHub profile text, gap analysis, and target-company tracker |

## Case-report quality rubric

Score each category 0-2. Do not call a case finished below 16/20.

| Category | 0 | 1 | 2 |
|---|---|---|---|
| Scope | Missing | Implicit | Explicit questions, boundaries, assumptions |
| Evidence | Unclear | Listed | Sources, integrity, provenance, time zone |
| Reproducibility | Screenshots only | Partial commands | Queries/commands and versions documented |
| Timeline | Missing | Tool dump | Curated UTC timeline with interpretation |
| Findings | Unsupported | Some support | Artifact-level support and confidence |
| Corroboration | None | Occasional | Major claims use multiple sources where possible |
| IR relevance | Forensics only | Generic actions | Prioritized containment/recovery tied to findings |
| Communication | Jargon-heavy | Understandable | Executive and technical layers |
| Limitations | Missing | Generic | Specific gaps and alternative explanations |
| Safety/polish | Unsafe/cluttered | Minor issues | Sanitized, navigable, professional |

## Resume conversion

Do not write “completed a DFIR lab.” Use evidence and outcomes:

- Investigated a simulated Windows intrusion by correlating Event Logs,
  Registry, Prefetch, Amcache, file-system metadata, and network evidence into
  a UTC-normalized timeline; identified the supported attack sequence and
  produced prioritized containment and detection recommendations.
- Developed and tested HeaderHunter, a cross-platform forensic triage
  application that identifies encrypted-container signatures and reports
  visible metadata while explicitly distinguishing confirmed structure from
  heuristic high-entropy findings. Use this bullet only if it accurately
  reflects your contribution and the employer permits public disclosure.
- Analyzed a Windows memory image with Volatility 3, reconstructing process and
  network activity, evaluating injection and persistence hypotheses, and
  documenting findings, confidence, and evidentiary limitations.

Replace broad claims with accurate numbers from the finished work.

## Interview standard

For any concept or tool on the resume, be ready to explain:

1. What question it answers
2. What evidence it uses
3. What a result does and does not prove
4. One source of false positives or ambiguity
5. How you would corroborate it
6. What response action may follow

If you cannot answer those six prompts, remove the item from the resume or
study it again.

## What to skip during this sprint

- Starting multiple certifications
- Spending days perfecting a home lab
- Collecting dozens of tools without understanding artifacts
- Writing walkthroughs that merely repeat challenge flags
- Publishing raw evidence or proprietary internship information
- Claiming malware reverse-engineering expertise after static triage
- Building a flashy dashboard before producing sound investigations
- Publishing internship source code or internal details without written
  authorization

If you already have a nearly completed certification, reserve no more than
three hours per week for it. Otherwise, revisit certification strategy after
August 7.

## Weekly accountability

Every Friday record:

- Hours completed
- Deliverable shipped
- Three things now explainable without notes
- One technical weakness
- One communication weakness
- Next week's adjustment

The invariant is **publish one useful artifact every week**.

## Authoritative anchors

- NIST SP 800-61 Rev. 3, published April 2025:
  https://csrc.nist.gov/pubs/sp/800/61/r3/final
- NIST NICE Framework Resource Center:
  https://www.nist.gov/itl/applied-cybersecurity/nice/nice-framework-resource-center
- MITRE ATT&CK:
  https://attack.mitre.org/
- Volatility 3 documentation:
  https://volatility3.readthedocs.io/
- Microsoft Windows security auditing documentation:
  https://learn.microsoft.com/windows/security/threat-protection/auditing/
- Wireshark documentation:
  https://www.wireshark.org/docs/
- Zeek documentation:
  https://docs.zeek.org/
- The Sleuth Kit and Autopsy:
  https://www.sleuthkit.org/
- Velociraptor documentation:
  https://docs.velociraptor.app/
- NIST CFReDS forensic datasets:
  https://cfreds.nist.gov/
