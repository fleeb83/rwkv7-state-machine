# Results

This page separates results that passed the project tests from active work and open gaps. It is a public summary, not a recipe for reproducing the project.

Updated 5 September 2026 from the current project record. New entries report outcomes and limits only; implementation and research materials remain private.

## What accepted means here

An accepted result has passed the project's preset evaluation and relevant negative controls. Acceptance is internal and applies only within the stated test scope; it does not imply independent reproduction. See [METHODOLOGY.md](METHODOLOGY.md).

The experiments use RWKV7 G1G at 0.4B and 7.2B parameters. Scale-specific results are identified where reported; evidence at one scale does not establish a result at the other.

## Public evidence snapshot

The table summarises selected evaluations without disclosing unpublished methods. Status refers to internal project review.

| Claim | Public test size | Public result | Status | Main limit |
|---|---|---|---|---|
| The trained support part and frozen model were both needed | Six checks with 192 held out cases each | Full setup 1.00, support off 0.47, frozen structure disrupted 0.54, chance 0.50 | Candidate | 0.4B model and narrow internal task only |
| Hidden rule learning | 24 held out cases | 24 of 24 correct, with first guess chance below 1 per cent | Accepted inside the project | One defined task family and no outside reproduction |
| Expanded stored program machine | 24 held out cases on each 0.4B development rung. The 7.2B case count is not public | 24 of 24 on each 0.4B development rung, then exact in the reported 7.2B test | Accepted inside the project | Maximum boundaries were not all combined in one run |
| Plain English to machine instructions | Full case count not public | About 0.90 to 0.96 across four planned measures, with negative controls breaking the result as required | Accepted inside the project | One branch case passed at its threshold with no margin |
| Narrow live action chain | Five consecutive live transitions | Correct typed actions and independently checked next states | Accepted inside the project | Fixed protocol, not an open ended agent |
| Language-to-program execution at 7.2B | 520 held out descriptions | 502 of 520 correct; all 513 runnable programs matched the reference execution | Accepted inside the project | Seven outputs were not runnable; eleven runnable programs were wrong |
| Computed-result readout at 7.2B | The same 513 runnable programs | 513 of 513 final values read back correctly | Accepted inside the project | Reads a bounded internal result, including wrong computed answers; not general prose output |
| Repeated environment loop at 7.2B | 24 fixed cases, three iterations each | Passed the registered loop and negative-control checks | Accepted inside the project | One simulated environment and a fixed short horizon |

## Candidate evidence

### Did the trained support part do all the work

One candidate test asked whether the trained support part was doing the computation while the frozen model only carried information.

Turning off the trained support part dropped the tested behaviour to chance. Leaving it on while breaking the learned structure of the frozen model also dropped the behaviour to chance.

Across six checks with 192 held out cases each, the full setup scored 1.00. With the trained support part turned off, the mean score was 0.47. With the frozen model's learned structure disrupted, it was 0.54. Chance was 0.50.

There is also a simple structural check. The support path in this test could only make linear changes. One of the operations being tested was not linear. The support part could not have performed that whole operation by itself.

The careful conclusion is that both parts were needed in this test. It does not show the exact split of work between them. It was run on the 0.4B model, on a narrow internal task, and did not cover full program execution. It is candidate evidence, not an independently reproduced result. A comparison with a simpler matched system is still needed.

## Results accepted inside the project

### Exact internal computation

The frozen model's internal state can carry out exact small integer calculation and comparison in the tested setting. More complex arithmetic was also tested. The final answers were exact in the tested cases. Some internal values carried a small error that levelled off rather than growing with each repeated step.

### Stored program execution

A small stored program machine has run inside the frozen model's state. It can use instruction and data memory, make choices based on its own data and stop under its own conditions. The same general mechanism, developed on the 0.4B model, passed the corresponding project test on the 7.2B production model without a change in the core implementation.

The instruction set was later expanded and remained exact in the tested configurations. Some boundaries passed separate tests and have not yet all been combined in one maximum configuration. They should be read as separate tested capabilities, not one larger combined claim.

### Closed loop operation

The machine has run over repeated cycles with a correct trace in the tests performed. It can use state it computed itself on one cycle as input to the next. This is a real closed loop within the tested range, not evidence of long horizon reliability in an open environment.

### Choosing a subgoal and first action

The system has derived a subgoal and first action from internal memory it addresses itself. Tests that removed, misaligned or disabled the relevant memory path broke the result as expected. The work also showed that an indexed approach kept decision cost stable as the amount of live memory grew in the tested range.

### Rule learning

A propose, test, revise and settle loop inferred hidden rules from examples over a defined set of possibilities. It passed its held out tests and the controls designed to rule out straightforward shortcuts. A different type of task was also checked at 0.4B development scale.

### Plain English to executable instructions

A trained support component translated free form English descriptions into executable instructions for the project machine. The base language model remained frozen. The output was run and checked against a separate reference. Straight line programs, conditional decisions and loops each passed their planned evaluations, with controls behaving as required.

There is one known held out case at the threshold rather than above it. It remains a pass, but it is tracked as a specific weakness rather than being hidden inside an average score.

### Language, execution and result readout on the same problems

The language-to-program component has now been connected to the 7.2B internal machine on 520 held out descriptions. Of these, 513 produced runnable programs and 502 produced the required result. All 513 runnable programs agreed with a separate reference execution. The eleven wrong runnable programs were compiler errors that the machine executed faithfully. Disabling the writer gave zero correct results; scrambling its output gave one.

A subsequent readout test used those same 513 runnable cases. The model's output recovered the final internal value correctly in every case, with removal and shuffle controls supporting dependence on the computed state. This includes faithfully reporting wrong computed answers; reading a value correctly does not make the program correct.

Together these tests establish a narrow connected chain from a held out description to a program, its execution and a readout of its result. The readout is a bounded value, not a natural language explanation. The result does not establish unrestricted compilation, transfer to other tasks or reliable self-correction.

### Repeated interaction with a controlled environment

At 7.2B, a registered test connected fresh observations, stored program execution, structured actions and new observations after the environment changed. It passed on 24 fixed cases over three iterations, including the registered checks that disrupted observations, program choice and stopping behaviour.

This is a tested composition in a simulated environment. It does not demonstrate general task competence, new program construction, live search or long horizon autonomy.

### Narrow prediction beyond the frozen base

In a separate 7.2B test, a trained reader predicted one defined outcome on states excluded from training. Held out balanced accuracy was about 0.69, compared with about 0.51 for the frozen base and 0.49 after shuffling. Accuracy on training states was about 0.88, so the generalisation gap remains substantial.

This is a narrow prediction result, not general perception or planning. It does not establish that a trained reader is necessary for every input task, or settle how prediction should be divided between the reader and the internal machine.

## Deferred tests

Two planned generalisation tests were examined before being run and found not to fit the current memory setup. They were deferred rather than forced through with a workaround that would overstate what had been tested. They remain open questions.

## Interfaces and end to end work

Parts of the input, machine execution and action path have now worked together in narrow controlled tests. A structured action path has also produced correct actions with independently checked outcomes in that setting.

That is an accepted narrow result inside the project. It is not proof that the full system can handle a new and messy real world task.

- Narrow observation and prediction tests have passed, but broader input and transfer to other environments remain thin.
- Using ordinary free text generation as the action path repeatedly produced descriptions of intended actions rather than executable actions. That approach is considered a real failure.
- A different structured action route and a bounded computed-result readout have passed controlled tests. Neither shows general action from ordinary language output.

## Execution feedback has not enabled reliable repair

Recent controlled attempts to use execution feedback to correct wrong programs did not pass. This remained true across the tested revision interfaces, including richer feedback and examples. These are limits of the tested setups, not proof that program repair is impossible. The earlier rule-learning result is a different experiment and should not be read as evidence that this compiler can correct itself.

## Failure record

The project keeps failures, null outcomes and corrections in its permanent record. This includes failed design choices, invalid evaluation ideas and approaches that regressed previously working behaviour. Recent program-repair failures remain part of that record alongside the successful execution and readout tests.

The record supports traceability of unsuccessful approaches and subsequent corrections.

For the wider project picture, see [CAPABILITY-MAP.md](CAPABILITY-MAP.md). For what these results may eventually enable, without presenting it as confirmed, see [APPLICATIONS.md](APPLICATIONS.md).

Detailed results can be shared privately for confidential external review. See [README.md](README.md) for the scope.
