# Can a Frozen Language Model Carry a Small Computer?

Independent experimental work by Russell Thomas, Australia.

[russthomas.dev](https://russthomas.dev)

Public summary updated 5 September 2026.

I started with a simple question. Can the internal state of a frozen language model (RWKV7 G1G) carry and run a real program?

After months of controlled tests, the answer inside the project is yes. The base model is RWKV7 G1G, an open recurrent architecture, tested at two scales: 0.4B and 7.2B parameters. The base model stays frozen at both scales. Small trained support parts help move information, but one candidate check found they could not perform the whole operation alone.

This has not been independently reproduced. It is not a finished system.

The upstream RWKV architecture and base models are credited to BlinkDL and the respective RWKV contributors. See [Upstream credits](UPSTREAM.md) for their GitHub and Hugging Face links and the distinction from this independent work.

## Why it matters

The most useful result may not be the computer itself.

Interpretability tools are often tested on models where nobody knows the correct internal process. This project may provide a testbed with a defined internal process, intended state and separate reference answer.

If that holds up, researchers could test whether an interpretability method found something real or only produced a convincing explanation.

## What I am asking for

I am not asking anyone to fund a finished product.

I am asking for enough managed compute and confidential outside review to test this properly.

If it does not reproduce, or a simpler system explains it just as well, stop.

If it holds up, we have outside evidence and a reason to keep going.

## What has passed the project tests

These are results accepted inside the project, not claims of outside proof. Each accepted result had set pass conditions and checks intended to catch shortcuts. None has been independently reproduced unless clearly stated. See [RESULTS.md](RESULTS.md) and [METHODOLOGY.md](METHODOLOGY.md).

- Exact small scale calculation and state handling inside a frozen model.
- A stored program machine that can follow instructions, use memory, branch based on its own state and stop itself.
- Closed loop operation where the machine uses its own state to decide what happens next.
- Choosing a subgoal and first action from internal memory, with tests showing that the relevant memory is genuinely being used.
- Rule learning from examples, including a held out evaluation and checks against simple shortcuts.
- Translation from plain English program descriptions into executable machine instructions, including straight line programs, decisions and loops.
- A connected language-to-program-to-execution test at 7.2B, with the model reading back the computed result on the same held out problem set.
- A controlled environment loop that reads the changed situation again after each action.

The core result has also been checked on both the 0.4B and 7.2B model versions. That is encouraging, but it is not evidence of a general scaling law.

## An important candidate check

One smaller scale test asked whether the trained support part was doing all the work while the frozen model only carried the state.

The answer in that test was no. Turning off the trained support part dropped the result to chance. Keeping it on while breaking the learned structure of the frozen model also dropped the result to chance. The support path could only make linear changes, while one of the tested operations was not linear. It could not have performed the whole operation by itself.

The careful conclusion is that both parts were needed. This is candidate evidence from one narrow test on the 0.4B model. It has not been repeated at 7.2B or independently reproduced.

## What has not been shown

This is the important part.

- Some capabilities have worked together in narrow controlled tests. That is not the same as a complete system working on a new real world problem.
- Reading a broad external situation into the machine, and returning a dependable answer or action, are still the weakest areas.
- The previous free text route for actions did not work reliably. Structured actions and a narrow computed-result readout have now passed controlled tests; dependable open ended output remains unshown.
- Reading back a computed result has not yet led to reliable correction of a wrong program from execution feedback.
- There has been no outside replication or peer reviewed publication.
- This work does not show that language models do any of this by themselves in normal use. It shows what their frozen internal state can be made to carry in a specific engineered setup.

The full limits and failure record are in [LIMITATIONS.md](LIMITATIONS.md).

## What support would pay for

The next bottleneck is strengthening the interfaces, then running a genuine end to end test on a new problem.

Compute sponsorship on its own would help. That could be managed compute credits, access to suitable hardware for agreed runs, or support for short cloud runs. A small grant tied to the same work would also help.

Any first support can be kept small and tied to clear stopping points.

- private technical review of the evidence
- an independent reproduction attempt and comparison with simpler systems
- controlled input and action interfaces
- a registered end to end test on a new problem
- a larger model check only if the earlier work passes
- public reporting of the result, including failures and limits

This lets a funder stop if the evidence does not hold up. If it does, the next decision can be based on outside evidence.

## How the work is checked

Before a result is accepted, the test, pass conditions and held out evaluation are set in advance. Each claim must also fail in deliberately broken versions of the setup. Failed, null and corrected attempts are kept in the project record rather than discarded, including recent unsuccessful attempts to correct programs using execution feedback.

This does not make the work beyond question. It is intended to make the claims easier to question properly.

## Public access and technical review

The public repository is a results and methodology summary, not a release of the underlying research materials. Detailed evidence can be discussed for genuine funding, collaboration or technical review enquiries, subject to protecting work that is still unpublished.

The current licence covers this public writing only. Any later release of code, benchmark material or replication tools would use a separate licence suited to that material and its intended use.

## Private confidential external review

Private and confidential external review is welcome and wanted.

If you are looking at funding, compute sponsorship, collaboration or technical diligence, please get in touch.

I am willing to share detailed results and the private research material needed to check them under an agreed NDA or similar confidentiality agreement.

For a serious review, this can include full result tables, raw evaluation outputs, control results, failure records, source code, prompts, training material, checkpoints and unpublished methods. Access would be limited to the agreed review or reproduction work.

Private access does not place any of those materials under the public repository licence. It does not allow public release, reuse or redistribution unless that is separately agreed in writing.

For funded technical diligence, the reviewer should have complete access to the material needed to check the agreed claims, including relevant negative results. The review rules should be agreed before the work starts. The reviewer should then be free to publish a factual non confidential summary covering what reproduced, what failed and what could not be checked.

I am also open to a properly scoped independent reproduction attempt. The tests, access rules and what can be published would need to be agreed before the review starts.

The aim is simple. Let serious reviewers test the claims properly without putting unpublished methods into the public repository.

## Contact

Russell Thomas, Australia.

Open to modest funding, compute sponsorship, collaboration and careful technical review.  
[russthomas.dev](https://russthomas.dev)

`russellt83@gmail.com`

---

Content is licensed under [Creative Commons Attribution NonCommercial NoDerivatives 4.0 International](LICENSE). This repository does not release code, training material, model weights or other software artefacts.
