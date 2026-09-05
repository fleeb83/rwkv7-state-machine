# Methodology

This independent experimental work uses predefined evaluations, negative controls and a retained record of failures and corrections. Review has been internal; independent replication remains outstanding.

This document describes the checking process at a high level. It does not publish code, prompts, training material, configuration or other implementation detail.

## Set the test before the result

Before a result can be accepted, the claim, pass and failure conditions, and held out evaluation are recorded. This limits selective reporting of successful runs.

## Try to break it

Each claim is tested against deliberately broken versions of the setup. Depending on the result, this can include disabling the component being tested, corrupting the relevant internal state, or breaking the relationship between the training inputs and outputs.

If a negative control passes, the result does not establish the intended claim, even if the main evaluation score meets its threshold.

## Check held out cases make sense

A held out test must be representable by the system being evaluated. Planned tests have been deferred when direct checks showed they did not fit the current setup. These remain open questions rather than evidence of generalisation.

## Review the result, not just the average

Accepted results are checked beyond the top line score. This has already caught a case where the average appeared to pass but a required held out group did not. The result was not accepted until the issue was addressed and the test rerun.

This review has been internal. It is useful, but it is not independent external review. Outside scrutiny is a priority for the next stage.

## Keep the failure record

Failed, null and corrected attempts are recorded in a permanent project log. Some are failed approaches. Some are evaluation problems caught before they produced a misleading claim. Some are regressions that showed a good looking direction was not reliable. Recent unsuccessful program-repair tests are retained alongside successful execution and readout results.

The record supports traceability and helps prevent repeated failed approaches. It does not replace validation of individual claims.

## Keep scope tight

A result at one scale is not treated as a result at another until it is checked there. A result in one evaluation setting is not treated as proof in a different setting. Every public claim should say what it does not show as clearly as what it does.

## Record integrity

The project log has required repairs after record integrity problems. Corrections and retractions are retained, and current summaries must account for them rather than treating every historical entry as an active claim.

## What this methodology does not prove

These procedures support inspection and challenge of the reported results. They do not establish correctness or replace independent replication, peer review or external technical scrutiny.
