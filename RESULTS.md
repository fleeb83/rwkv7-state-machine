# Results

This page separates results that passed the project tests from active work and open gaps. It is a public summary, not a recipe for reproducing the project.

## What accepted means here

An accepted result has passed the project's preset evaluation and the relevant negative controls. It has been accepted inside the project. It has not been independently reproduced unless clearly stated. It is not accepted just because it looks good, and it is not treated as proof of anything broader than the test supports. See [METHODOLOGY.md](METHODOLOGY.md).

All results below are on RWKV7 G1G, at either the 0.4B development scale or the 7.2B production scale; each
result states which.

## Public evidence snapshot

This table gives a small amount of checkable context without publishing the private method. Accepted means accepted inside the project, not confirmed by someone outside it.

| Claim | Public test size | Public result | Status | Main limit |
|---|---|---|---|---|
| The trained support part and frozen model were both needed | Six checks with 192 held out cases each | Full setup 1.00, support off 0.47, frozen structure disrupted 0.54, chance 0.50 | Candidate | 0.4B model and narrow internal task only |
| Hidden rule learning | 24 held out cases | 24 of 24 correct, with first guess chance below 1 per cent | Accepted inside the project | One defined task family and no outside reproduction |
| Expanded stored program machine | 24 held out cases on each 0.4B development rung. The 7.2B case count is not public | 24 of 24 on each 0.4B development rung, then exact in the reported 7.2B test | Accepted inside the project | Maximum boundaries were not all combined in one run |
| Plain English to machine instructions | Full case count not public | About 0.90 to 0.96 across four planned measures, with negative controls breaking the result as required | Accepted inside the project | One branch case passed at its threshold with no margin |
| Narrow live action chain | Five consecutive live transitions | Correct typed actions and independently checked next states | Accepted inside the project | Fixed protocol, not an open ended agent |

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

## Deferred tests

Two planned generalisation tests were examined before being run and found not to fit the current memory setup. They were deferred rather than forced through with a workaround that would overstate what had been tested. They remain open questions.

## Interfaces and end to end work

Parts of the input, machine execution and action path have now worked together in narrow controlled tests. A structured action path has also produced correct actions with independently checked outcomes in that setting.

That is an accepted narrow result inside the project. It is not proof that the full system can handle a new and messy real world task.

- A narrow reader can identify simple outcome signals from text, but broader input remains thin.
- Using ordinary free text generation as the action path repeatedly produced descriptions of intended actions rather than executable actions. That approach is considered a real failure.
- A different structured action route has passed narrow controlled tests. It does not show general action from ordinary language output.

## Failure record

The project keeps failures, null outcomes and corrections in its permanent record. There are 129 such entries across the wider project history. This includes failed design choices, invalid evaluation ideas and approaches that regressed previously working behaviour. The count is context, not proof that the claims are right.

The point is practical. Record what did not work so it does not get rediscovered by accident. It is not a claim that the process prevents mistakes.

For the wider project picture, see [CAPABILITY-MAP.md](CAPABILITY-MAP.md). For what these results may eventually enable, without presenting it as confirmed, see [APPLICATIONS.md](APPLICATIONS.md).

Detailed results can be shared privately for confidential external review. See [README.md](README.md) for the scope.
