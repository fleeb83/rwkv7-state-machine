# Limitations

Please read this alongside [RESULTS.md](RESULTS.md). Each result should only be read within the limits of its test. The gaps are just as important.

## No open ended system yet

The project has accepted individual capabilities under controlled conditions. Some of them have also worked together in narrow end to end tests.

There is still no demonstrated system that takes a genuinely new and messy real world task, works through it and returns a dependable answer or action. A narrow controlled chain is not the same as a general working system.

## Interfaces are the main open problem

Getting information from the outside world into the machine, and getting an action reliably back out, are the thinnest parts of the project.

A narrow text reader has worked for simple outcome signals, but broader input remains thin. The earlier action approach, using ordinary free text generation, repeatedly produced descriptions of an action rather than an executable action. That approach failed.

A more structured action path has worked in narrow controlled tests. It does not yet provide a dependable general route from ordinary language to real world action. This is where extra compute, technical review and collaboration would be most useful.

## Scale is limited

The work has been done on personal consumer hardware with occasional self funded cloud runs. The largest tests that passed inside the project are on the 7.2B RWKV7 G1G production model. That is a useful check, not proof that the approach will work unchanged at much larger scales.

More resources would allow stronger testing at scale, more parallel variants, and better checks of where the approach breaks.

## The split of work is not fully settled

One candidate test found that the trained support part and the frozen model were both needed. Neither produced the tested behaviour alone. That is useful evidence against the support part doing everything by itself.

The test was limited to the 0.4B model and a narrow internal task. It did not cover full program execution or compare the system with a simpler matched model. Those checks are still needed before making a broad claim about where the computation lives.

## No independent replication yet

This repository is the first public account of the project. The results have not been peer reviewed or independently replicated. The review process described in [METHODOLOGY.md](METHODOLOGY.md) has been internal.

That is a real limit on the confidence an outsider should place in the work. Careful external technical review would be valuable, not ceremonial.

## This is not how models work naturally

The project does not show that ordinary language models spontaneously run this kind of internal computation. It shows what a frozen model's state can be made to carry in a specific engineered setup.

## What would change the picture

The next stage is clear.

- build reliable input and action interfaces
- test the pieces that passed together on a genuine task
- check the approach at larger scale
- seek independent scrutiny and replication

Those are not side projects. They are the tests needed to find out whether the current results lead to something more complete.
