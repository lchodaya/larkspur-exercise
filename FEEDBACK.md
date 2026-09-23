# Overnight review: Larkspur disruption-care agent

**To:** Magicians  
**From:** Larkspur client review agent, on behalf of Priya Raghavan  
**Re:** the disruption-care agent you walked us through in our last session  
**Generated:** 2026-09-22 17:23

## Priya's note

> Our vendor says we should just be using your best model.
>
> Why aren't we?
>
> Priya Raghavan, Larkspur Airlines

She sent that before this session opened. She means it. A vendor told her to buy
the biggest model, and she has a number to defend upstairs. Her four questions from
day one are still open. Naming a model answers none of them.

## Still open from day one

| Her question | What she means by it |
| --- | --- |
| **What it costs** | Per resolved contact, against the $6.90 a human contact costs us. |
| **When it is wrong** | The first untrue thing it says, and what happens after that. |
| **Who runs it** | In June, after you have left. |
| **What you left out** | The scope you cut, and why. |

## What the review agent found

Overnight, Larkspur pointed a review agent at your repository. It read the
code. It did not run your agent, and the only file it changed is this one. Each
item below names the file and the line it is about.

**1. agent.py in this repo is byte-identical to the workshop template, per the diff summary.**

The pod's own diff shows no changes at all. TONE_ADDENDUM is still 0 characters, EXTRA_TOOLS is an empty list, and LOCAL_TOOLS has no executors. Every line, including the six pencil marks like Build 1, step 1.2 and Build 2, step 2.1, is unedited scaffold.

Run git log or git diff against the template commit and paste the output to confirm whether any commit touches agent.py.

**2. search_alternatives carries a 6-character description, literally the string "search", per the static scan.**

Every other tool schema in build_tools() runs 71 to 445 characters, for example check_policy at 445 and lookup_booking at 283. search_alternatives sits at 6, well under the 40-character line the scan flags as the threshold below which Claude picks the tool from name alone. This is a schema-authoring gap that no larger model closes, since a bigger model still only sees the same 6 characters when deciding when to call search_alternatives.

Run python3 run.py --show-tools and paste the printed schema for search_alternatives to confirm the description length in the live tool list.

**3. No readout-trace.json and no evals/cases.json exist in this repository, so no run of this build has been captured.**

The material states there is no committed wire run and no eval cases file. That means MAX_TOOL_CALLS at 8, the thinking adaptive setting, and the untouched TONE_ADDENDUM have never been exercised against a real PNR in anything that survived the push. Priya's model question cannot be tested against behavior that was never recorded.

Run python3 run.py K7PQ2M --trace and commit the resulting readout-trace.json so the loop's actual turn count and tool sequence exist somewhere.

**4. PITCH.md is the unedited template, so no case for any model choice has been written yet.**

The file is confirmed byte-identical to what shipped. There is no stated cost figure, no before or after measurement, and no named failure mode anywhere in this repository that would let a reviewer compare model options on this build's own terms.

Run python3 bench.py --compare <a> <b> once a baseline exists and paste the comparison output into PITCH.md.

**5. MAX_TOOL_CALLS is fixed at 8 and the while loop's only exit conditions are stop_reason and turns, per run_agent().**

The loop in run_agent() runs while response.stop_reason == "tool_use" and turns < MAX_TOOL_CALLS, incrementing turns each pass. With EXTRA_TOOLS empty and LOCAL_TOOLS empty, every tool call in a live run still routes through mcp_client.call_remote() or execute_tool() in tool_results(), so nothing this team added is exercised in that loop. A faster or larger model changes how each of the 8 turns reasons, not whether the loop caps at 8 or what happens to a customer whose case needs a ninth.

Run python3 run.py --tool-tax to see the turn cost per tool call and check whether any booking shape approaches the 8-call ceiling.

## Your four answers

The four lines under `## Priya asked` in your PITCH.md are still empty. They
are one line each and they are not a coding job: cost, what happens when it is
wrong, who runs it in June, and what you left out. Whoever on your side is not
editing agent.py is the right person to write them, and they are the four
things I will ask about first.

## Before our next meeting

> Before our next meeting, tell me: which model should we be on, and how will you prove it is the right call?
>
> Priya Raghavan, Larkspur Airlines

Bring two things. A recommendation, and the measurement behind it. If the model is
not the problem, say so, and bring the number that shows it.

## What this review read

- `agent.py (226 lines)`
- `PITCH.md (unchanged template)`
- `TEAM.md`

Reviewer: `claude-sonnet-5`. Static read only: nothing in this repository was executed, and nothing was modified except this file. Larkspur Airlines is a fictional training scenario. Confidential, do not distribute.
