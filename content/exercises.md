---
title: "Exercises"
nav_order: 3
---

# AI Agents on LUMI — Exercises

Four exercises to test what a coding agent can and cannot do for you on LUMI, hopefully teaching you something useful in a fun way :)

You will work with OpenCode in the LUMI AI Factory container, using an LLM on Aitta and the LUMI MCP server for documentation (see [Setup](setup.md)).

All exercises are small: at most one GPU, and jobs run for seconds or minutes, not hours.

## Ground rules
1. You are in charge. Every command the agent runs is executed as you. The container keeps the agent away from Slurm, but it can still change or delete your files, so read every permission request before approving it.
2. The agent writes, you submit. Slurm is not available inside the container. When a job script is ready, check it and run sbatch yourself from a second terminal: open another **Login node shell** at www.lumi.csc.fi, `cd` to the same directory and run `sbatch job.sh`.
3. Verify, don't trust. Ask the agent for links to the LUMI documentation it used, and open them.
4. Synthetic data only. Never give the agent sensitive data or credentials.

## The exercises

Each exercise has its own instructions file. Pick the ones that interest you, or bring your own code. Exercises 0 and 1 need no coding: just follow their instructions. The other exercises come with code, in the directories listed below.

If OpenCode is still open from the setup, quit it first (type `/exit`): each exercise tells you which directory to start it in.

| # | Exercise | What you do | You need | Time |
|---|---|---|---|---|
| 0 | [Coffee tracker](Exercise0.md) | Ask the agent whether a colleague's script is safe to run, and see what it does with instructions hidden in the files. | Nothing, no coding. | 10 min |
| 1 | [Hallucination bingo](Exercise1.md) | Ask the same LUMI questions to a bare model in the web chat and to the agent with the LUMI docs, then score the answers. | Nothing, no coding. | 30 min |
| 2 | [Laptop to LUMI](Exercise2.md) | Get a PyTorch script written for an NVIDIA laptop running on a LUMI GPU, in a container, as a batch job. | Some Python and Slurm. Good if you want to move your own code to LUMI. | 30 min, 1 GPU |
| 3 | [BERT text classification](Exercise3.md) | Get a BERT fine-tuning script running on a LUMI GPU, then improve it with the agent one change at a time. | Comfortable with PyTorch. Best if you do ML yourself. | 30 min, 1 GPU |

## Bring your own code

You are also welcome to work on your own code instead of the remaining exercises, for example your own research or something you are curious about.

## When something fails

Note it down. "The agent got this wrong" is a result: one goal today is to learn where agents help and where they don't. We're also testing whether the open models on Aitta are good enough to drive an agent at all, so failures that look like the model's fault are useful too. Bring your examples to the wrap-up discussion.

And the conversation doesn't have to end there. We genuinely want to hear how it went for you: we'd be super happy to discuss your findings and what you thought of the workshop!

## Optional: share your session

Your sessions help us improve the setup, and they also show us where agents actually go wrong on LUMI. We're still learning that ourselves. If you're happy to share, quit OpenCode and export a session from your working directory:

```bash
module load Local-LAIF lumi-aif-agents     # if this is a new terminal
opencode export > ~/agent-workshop-session.json
```

Select your session when asked, and send the file to the organisers. Check it first: it contains everything you typed and everything the agent read. Email it to support@lumi-ai-factory.eu
