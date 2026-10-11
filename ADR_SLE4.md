# SLE-4: Architecture Decision Record (ADR)

**Course:** 02AML204 – Introduction to Artificial Intelligence  
**PRN:** 25UAM068  
**Name:** Manasi Ghorpade  
**Division:** A  
**Date:** 11 October 2026  
**Repository:** https://github.com/ghorpademanasi2007/IAI_SLE4

## PART A — Architecture Decision Record

**Title:** Separate Input Handling, Search Logic, and Output/Reporting  
**Status:** Accepted (confirm against the submitted SLE-1–SLE-3 implementation)  
**Date:** 11 October 2026

### 1. Context
The search/agent work needs to accept a problem or graph, execute a search procedure, and present the result. Keeping these responsibilities mixed together can make code harder to test, profile, and maintain. SLE-2 involved profiling and comparing search implementations, while SLE-3 involved C4 architecture diagrams. A clear separation makes the relationship between implementation, performance measurements, and architecture easier to explain.

### 2. Decision
Organize the solution into distinct responsibilities: input/problem setup, search algorithm execution, and output/results reporting. Keep the search procedure independently callable so it can be tested and profiled without changing input or presentation code.

### 3. Alternatives Considered
- **Single combined program:** simple for a very small demonstration, but input, algorithm, and output become tightly coupled.
- **Separate files without clear interfaces:** offers some organization but can still leave responsibilities dependent on implementation details.
- **Separate components with defined responsibilities (chosen):** supports focused testing, profiling, and clearer C4 explanation.

### 4. Rationale / Justification
- This decision follows the SLE-3 C4 approach of explaining the system at different levels and identifying component responsibilities.
- The search logic can be tested independently with known graph/problem inputs.
- Profiling can focus on the search operation rather than mixing it with user input and printing.
- The design makes it easier to compare BFS and DFS (or the actual algorithms used in the submitted work) under consistent test conditions.
- A change to output formatting should not require changes to the search algorithm.
- Separate responsibilities make debugging and maintenance more manageable.
- **SLE-2 evidence to insert before submission:** measured runtime for each algorithm and test size: [insert values from your actual report].
- **SLE-2 evidence to insert before submission:** memory/other profiling observations and the test conditions: [insert actual values and conditions].
- Do not claim a performance improvement unless the SLE-2 measurements support it.

### 5. Consequences
**Positive**
- Easier testing, profiling, debugging, and explanation.
- Clearer mapping between implementation components and the SLE-3 architecture diagrams.
- Algorithm and output changes can often be made independently.

**Negative / Trade-offs**
- Requires clear interfaces and slightly more initial organization.
- Small demonstrations may need more files or functions than a single-script approach.
- Actual performance benefits must be established through measurement, not assumed.

### 6. References
- SLE-4 Student Guideline, 02AML204 – Introduction to Artificial Intelligence.
- SLE-2 profiling report and SLE-3 C4 diagrams: add the exact repository paths/links used in your submitted work.

## PART B — Short Summary of My SLE Journey
- **SLE-1:** Developed the agent/search implementation and documented it with a README and AI contribution log.
- **SLE-2:** Profiled the code and compared performance using measured results.
- **SLE-3:** Prepared C4 architecture diagrams to explain the system at context, container, component, and code levels.
- **SLE-4:** Recorded a design decision and connected the reason for it to implementation structure and profiling evidence.
- This sequence helped connect working code, measured behaviour, architecture, and technical explanation.
- Before final submission, insert the exact SLE-2 measurements and ensure this decision accurately describes the submitted SLE-3 design.

## PART C — AI Contribution Note
- **AI tools used:** ChatGPT, for drafting and organizing the ADR, README, and viva notes.
- **What AI helped with:** structuring the ADR, listing alternatives, and improving clarity.
- **What I did myself:** I must verify the decision against my own code, C4 diagrams, and profiling report; insert the actual measurements; and ensure I can explain and defend every statement during viva.

## PART D — Viva Preparation Notes
1. Explain the chosen decision in one sentence: input, search, and output have separate responsibilities.
2. Explain why this makes profiling fairer and testing easier.
3. Give the actual SLE-2 measurements and state the test conditions.
4. Explain how the decision appears in the SLE-3 C4 diagrams.
5. State one trade-off and what could become harder as the problem grows.
