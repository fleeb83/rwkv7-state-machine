# Limitations

Each result in [Results](RESULTS.md) applies to its stated evaluation conditions. The following limits remain unresolved.

## No open ended system demonstrated

Individual capabilities and some narrow combinations have passed controlled evaluations. No system has been demonstrated that takes a new, open ended real world task and returns a dependable answer or action.

## Input and output interfaces

A narrow reader has worked in a repeated simulated-environment loop. A separate prediction test transferred to unseen states, with a substantial drop from performance on training states. Broader input grounding and transfer remain unestablished.

The earlier action approach used free text generation and repeatedly produced descriptions of actions rather than executable actions. A structured action path has since passed narrow controlled tests. A separate language-to-execution chain also includes correct readout of a bounded computed value. These results do not establish a dependable general route from ordinary language to real world action.

## Correct execution does not guarantee a correct program

The latest language-to-execution test produced the required result on 502 of 520 held out descriptions. Seven outputs were not runnable and eleven runnable programs computed the wrong result, even though execution matched the reference. The readout faithfully reported the computed values, including wrong answers.

Attempts to correct programs using execution feedback have not passed the tested evaluations. Reliable self-correction, live search and transfer beyond the tested problem family remain unshown. The successful environment loop and language-to-result chain are separate experiments; their capabilities should not be combined into a broader claim.

## Limited scale evidence

Experiments have been conducted at 0.4B and 7.2B parameters. The largest tests that passed the project evaluations use RWKV7 G1G at 7.2B. Results at these sizes do not establish a scaling law or show that the approach will work unchanged at larger scales.

Some capacity boundaries passed separate tests and have not all been combined in one maximum configuration.

## Unresolved division of computation

One candidate test found that trained support and the frozen model were both needed for the tested behaviour. Disabling support or disrupting the frozen model's learned structure reduced performance to chance. This supports dependence on both components within that test, but does not establish the exact division of computation.

The test was limited to the 0.4B model and a narrow internal task. It did not cover full program execution or compare the system with a simpler matched model. Those checks are needed before making broader claims about where the computation occurs.

## No independent replication

The results have not been peer reviewed or independently replicated. The review process described in [Methodology](METHODOLOGY.md) has been internal. Public summaries do not provide the underlying materials needed for independent verification; confidential review arrangements are described in the [README](README.md#access-and-review).

## Engineered behaviour

The project studies what a frozen model's state can be made to carry in a specific engineered setup. It does not show that ordinary language models spontaneously perform this kind of internal computation.

## Further validation

The main outstanding tests are broader input and action interfaces, integration on a new task, comparisons with simpler systems, scale checks and independent reproduction. These are necessary to assess whether the controlled results extend beyond the current evaluations.
