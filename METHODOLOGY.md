# Methodology

I am not presenting this as academic research or as a substitute for outside replication. It is independent experimental work. The standard I have tried to follow is simple. Make the test clear before running it, try to break the result and keep the failures.

This document describes the checking process at a high level. It does not publish code, prompts, training material, configuration or other implementation detail.

## Set the test before the result

Before a result can be accepted, I record what is being tested, what would count as a pass or failure and what held out cases will be used. This is meant to reduce the temptation to run many versions and only describe the one that happened to work.

## Try to break it

Each claim is tested against deliberately broken versions of the setup. Depending on the result, this can include disabling the component being tested, corrupting the relevant internal state, or breaking the relationship between the training inputs and outputs.

If a broken version still passes, the claim stops there. A good headline number is not enough if the control suggests the system found a shortcut.

## Check held out cases make sense

A held out test only helps if the task can actually be represented by the system being tested. In this project, planned tests have been deferred after direct checks showed they did not fit the current setup. I would rather record that limit than make the result look broader than it is.

## Review the result, not just the average

Accepted results are checked beyond the top line score. This has already caught a case where the average appeared to pass but a required held out group did not. The result was not accepted until the issue was addressed and the test rerun.

This review has been internal. It is useful, but it is not independent external review. Outside scrutiny is a priority for the next stage.

## Keep the failure record

Failed, null and corrected attempts are recorded in a permanent project log. Some are failed approaches. Some are evaluation problems caught before they produced a misleading claim. Some are regressions that showed a good looking direction was not reliable. Recent unsuccessful program-repair tests are retained alongside successful execution and readout results.

The record is there to avoid repeating work blindly and to make the public account more honest. It does not mean the project is free of mistakes.

## Keep scope tight

A result at one scale is not treated as a result at another until it is checked there. A result in one evaluation setting is not treated as proof in a different setting. Every public claim should say what it does not show as clearly as what it does.

## Improve the process when it fails

The project record keeping process has been changed when it was not doing its job. A heavier tracking layer was removed after it added work without improving trust. The underlying log later needed repair after a problem damaged some records. That work cost time, but it was necessary before later results could be trusted and checked properly.

The point is not that process is automatically good. The point is that it should be tested as well. If it is not helping, it should be fixed or removed.

## What this methodology does not prove

It does not prove the results are correct. It does not replace independent replication, peer review or outside technical criticism. It is a practical attempt to make the work easier to test, inspect and challenge while those things are still missing.
