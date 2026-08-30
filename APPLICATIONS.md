# Possible applications

The strongest possible use for this work right now is as a potential ground truth testbed for interpretability. It gives researchers intended internal behaviour and a separate reference checker. If outside reviewers confirm that the internal state matches its intended meaning, and the interfaces work reliably on broader end to end tasks, it could also lead to AI systems with decision steps that are easier to check and control.

Those are two different claims. This page keeps them separate.

The accepted findings are summarised in [RESULTS.md](RESULTS.md). The current gaps are set out in [LIMITATIONS.md](LIMITATIONS.md).

## What the existing results could support

### A potential ground truth testbed for interpretability

This is the strongest current research direction.

Interpretability tools are often tested on models where nobody knows the full internal process. A tool may find a feature or circuit that looks convincing, but there is often no known answer to compare it with.

This project offers a different kind of test. The internal machine has defined states and operations, its execution can be checked against a separate reference checker, and deliberately broken versions are used to test whether the claimed state is actually doing the work.

That could provide a useful benchmark for questions like these.

- Did an interpretability method recover the state that really controlled the result?
- Can it identify the internal step where a decision changed?
- Did it find something that caused the result, or something that only lined up with it?
- Does it still work when the program, state or control path changes?

Toy models can be built with known ground truth. Real language models rarely provide it. A controlled machine inside a real frozen model may offer a useful middle ground.

The project has enough internal evidence to justify testing this use. Turning it into something other researchers can trust would still require outside review and a public release plan that protects unpublished work.

### Testing whether reasoning is causally faithful

A model can produce a plausible explanation without that explanation being the process that caused its answer. This is the chain of thought faithfulness problem in plain terms.

The project has limited tests where removing a relevant internal value causes the output to fail as expected. That is evidence the internal value is doing the work, not just lining up with the answer.

This does not solve chain of thought faithfulness in general. It creates a controlled setting where a claim about the model's reasoning can be checked against known internal state and direct intervention.

### Research into computation inside recurrent state

The existing system could also support controlled work on how a frozen recurrent model carries memory, exact operations, branching, halting and repeated execution.

The value is not a claim that the model has general reasoning. It is the ability to study a limited internal process with known intended behaviour, held out tests, checks on what caused the result and a record of failures and corrections.

## What could become possible after broader end to end validation

The applications below depend on a reliable path from a real situation into the machine, through its internal process and back out as a valid action or answer. Narrow controlled chains have worked. The full chain has not been shown on open ended real world tasks.

### A different route to checking neural systems

Formally verifying the behaviour of a whole language model is far beyond what this project claims. A smaller and more realistic target may be to split the problem into two checks.

1. Check that a small, defined decision process follows the required rules.
2. Test whether the neural system follows that process faithfully under the conditions where it will be used.

This would combine formal checking of the small process with practical testing of the neural system carrying it. It would not be a proof of the entire model. If it holds up, it could be useful for limited tasks where one part of a decision must follow a strict rule.

### A controlled test case for hidden computation

A system with known internal programs and known triggers could become a useful test case for research into backdoors, sleeper behaviour and deceptive computation.

Researchers could test whether a detection method finds the hidden process, whether an intervention disables it, and whether the method produces false confidence when the process is absent. The value would come from having ground truth about what was installed and when it runs.

This would be later work. It requires stronger integration and careful safeguards. It is not evidence that the project has solved deceptive alignment or built a general sleeper agent detector.

### Mechanical replay as an oversight tool

Many AI oversight approaches rely on outputs, explanations or another model judging whether an answer looks sound. A completed version of this work could offer another option for narrow decisions. Replay a defined internal trace and check it against known rules.

That would not replace human judgement or solve scalable oversight. It could make certain steps easier to inspect because the reviewer would be checking a trace rather than judging an argument about what supposedly happened.

### Auditable decision components

In higher stakes settings, evaluation scores and written explanations do not show exactly how an individual decision was reached. A decision component that can be replayed could provide a different kind of evidence. It could show what state was read, what rule was applied, which path was taken and whether the required checks passed.

That could eventually be useful in assurance, audit, insurance or certification work. It would only become credible after reliable input grounding, dependable action interfaces, operational testing and outside review. This project is not currently a compliance product and does not provide a legal guarantee.

### Exact steps inside flexible AI systems

Some tasks combine open ended language work with narrow steps that must be exact. Examples include a calculation, a permission check, a limited procedure or a rule that must be applied before an action is allowed.

If the full chain works, a language model could handle context and communication while a smaller, checkable internal process handles the exact step. The aim would not be to turn all reasoning into a program. It would be to make the parts that need precision easier to test and audit.

## What this project should not be presented as

The current evidence does not support calling this a general autonomous agent, an unrestricted natural language compiler, a complete verification method, a solution to deceptive alignment or a production ready safety and compliance system.

It also does not show that limited internal execution automatically becomes general reasoning, long horizon planning or reliable real world action.

## Why support matters now

The near term goal is clear. Test whether the existing work can become a properly reviewed ground truth interpretability testbed. The larger applications depend on proving the interfaces and the complete chain.

Modest funding, compute sponsorship, collaboration or technical review would directly support this work.

- preparing a public interpretability benchmark that protects unpublished work
- building and testing the remaining input and action interfaces
- running a genuine end to end task with preset success and failure conditions
- checking whether the results hold at larger scale
- bringing in independent reviewers before stronger claims are made

That work would answer the question that matters next. Do the tested pieces remain trustworthy when they have to work together?
