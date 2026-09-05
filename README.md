# Latent Stored-Program Computer

Independent experimental research into stored-program execution within the recurrent state of a frozen RWKV7 G1G language model.

Russell Thomas, Australia · [russthomas.dev](https://russthomas.dev)

Updated 5 September 2026.

The project investigates whether a frozen language model, coupled with small trained support components, can carry a defined machine state and execute programs over it. Controlled experiments at 0.4B and 7.2B cover exact computation, memory, branching, halting and repeated execution. Recent 7.2B tests connect language descriptions to program execution and a bounded readout of the computed result.

These are internally evaluated research results. They have not been independently replicated or peer reviewed. This repository provides public summaries of the evidence, methodology and limitations; the underlying implementation and research materials remain unpublished.

## Research overview

| Document | Contents |
|---|---|
| [Results](RESULTS.md) | Evaluation outcomes, controls and failure record |
| [Methodology](METHODOLOGY.md) | Pass conditions, held out evaluations and internal review |
| [Limitations](LIMITATIONS.md) | Scope of the evidence and unresolved questions |
| [Capability map](CAPABILITY-MAP.md) | Current status across the tested capabilities |
| [Potential applications](APPLICATIONS.md) | Research uses and their validation requirements |
| [Upstream credits](UPSTREAM.md) | RWKV attribution, GitHub and Hugging Face links |

## Selected results

The following results passed their project evaluations unless marked as candidate evidence. Test conditions and controls are described in [Results](RESULTS.md).

| Area | Reported outcome | Scope |
|---|---|---|
| Stored-program execution | Exact execution in the reported tests, including memory, branching and halting | Tested at 0.4B and 7.2B; maximum boundaries were not all combined in one run |
| Language-to-program execution | 502 of 520 held out descriptions produced the required result; all 513 runnable programs matched reference execution | One problem family at 7.2B; seven outputs were not runnable and eleven runnable programs computed the wrong result |
| Computed-result readout | 513 of 513 final values read back correctly | The same runnable programs; includes faithfully reading wrong computed answers |
| Repeated environment interaction | Passed the registered loop and negative-control checks | A separate 7.2B experiment with 24 fixed cases and three iterations per case in one simulated environment |
| Contribution of the frozen model | Disabling trained support or disrupting the frozen model's learned structure reduced performance to chance | Candidate evidence on a narrow 0.4B task; the division of computation remains unresolved |

Additional experiments cover memory-based subgoal selection, rule learning and translation of straight line programs, decisions and loops. These are distinct evaluations; their results do not establish a single system with all capabilities combined.

## Research direction

A potential use is a controlled testbed for interpretability: the machine has defined states and operations, execution can be compared with a separate reference, and interventions can test whether particular internal values affect the result. Establishing this as a dependable benchmark requires independent validation of the relationship between the intended machine state and the neural computation.

Current priorities are stronger input and output interfaces, transfer beyond the tested problem families, comparisons with simpler systems and independent reproduction. Broader applications are discussed in [Potential applications](APPLICATIONS.md).

## Current limitations

- No demonstrated general system for open ended real world tasks.
- Correct execution and readout do not guarantee that the generated program solves the requested task. Tested attempts at correction from execution feedback have not passed.
- Structured actions and bounded result readout have passed narrow tests; the earlier free text action route was unreliable.
- The environment loop and language-to-result chain are separate experiments.
- Results at two model sizes do not establish a scaling law. Candidate evidence about the frozen model's contribution has not been repeated at 7.2B or compared with a simpler matched system.
- The setup is engineered around a frozen model. It does not show that models perform this computation spontaneously in ordinary use.

See [Limitations](LIMITATIONS.md) for the full scope and [Methodology](METHODOLOGY.md) for how evaluations, negative controls and failed attempts are recorded.

## Access and review

Detailed evidence and the materials needed to assess specific claims may be made available for confidential technical review or an independent reproduction attempt under an agreed NDA or equivalent terms. Review scope, access and publication terms would be agreed in advance, including provision for a factual non-confidential summary of what reproduced, failed or could not be checked.

Private access does not grant public release, reuse or redistribution rights. The repository licence covers the public writing only; any future release of code, data or other research materials would carry separate terms.

## Upstream

Credit for the RWKV architecture, base models and associated software belongs to BlinkDL and the respective RWKV contributors. This project is independent and does not imply upstream endorsement. See [Upstream credits](UPSTREAM.md) for the original projects and accounts.

## Contact

For technical review, collaboration or research sponsorship: [russthomas.dev](https://russthomas.dev) · [russellt83@gmail.com](mailto:russellt83@gmail.com).

---

Public writing is licensed under [Creative Commons Attribution NonCommercial NoDerivatives 4.0 International](LICENSE). This repository does not release code, training material, model weights or other software artefacts.
