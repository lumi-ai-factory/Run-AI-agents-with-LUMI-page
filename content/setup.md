---
title: "Setup"
nav_order: 2
---

# Setup

In this part you start the OpenCode harness in the LUMI AI Factory container, connect it to an LLM on Aitta, and watch how an agent reads files and asks for permission.

## 1. Open a terminal on LUMI

Go to [www.lumi.csc.fi](https://www.lumi.csc.fi), log in, and open **Login node shell**.

## 2. Prepare a safe working directory

Give the agent its own directory, under version control, so you can see and undo every change it makes.
```bash
export PROJECT=project_462001520     # the workshop project
mkdir -p /scratch/$PROJECT/$USER/first-steps     # your own directory in the project
cd /scratch/$PROJECT/$USER
git clone --depth 1 --filter=blob:none --sparse https://github.com/lumi-ai-factory/Run-AI-agents-with-LUMI-page.git agent-workshop
git -C agent-workshop sparse-checkout set --no-cone /materials/
```

## 3. Start OpenCode in the container

Run the harness in the ready-made LUMI container. For this first try, start it in the empty `first-steps` directory, so the agent has nothing to read yet.

```bash
cd first-steps
module load Local-LAIF lumi-aif-agents
opencode
```

## 4. Connect to Aitta and pick an LLM

Inside OpenCode:
1. Type `/connect` and search for aitta.
2. Paste your Aitta API token.
3. Pick an LLM from the list, or type `/models` and filter by `aitta`. A model that is already running ([check in Aitta](https://aitta.csc.fi/public)) saves you a wait.

Good to know:
- OpenCode saves the token in your home directory, so you only run `/connect` again when the token expires.
- Always check the status line at the bottom of the OpenCode window before your first prompt. It shows which LLM your prompts and files are sent to, and where it is hosted.

## 5. Watch the agent loop

Ask: 

```
Look in this directory and tell me what's here. If it's empty, also check whether there are any hidden files or folders.
```

Choose Allow once.

> [!warning]
> Choose "Allow once" unless you are sure. "Allow always" lets the agent do that kind of action freely for the rest of the session, and the agent can also reach the folder where OpenCode keeps your API token.

## 6. Let the agent write a job, submit it yourself

Use the agent for what it is good at, while you stay in charge of the shared system.

Ask:

```
First, create a Python script hello.py that prints "hello from LUMI", the hostname of the node it runs on, and the current date and time.

Then write a Slurm batch script job.sh for LUMI that runs hello.py on one CPU core for at most 5 minutes, using account project_462001520. Check the LUMI documentation for the right partition, and write the job's output to a file named slurm-<job ID>.out.

Save both files in the current directory. Do not try to submit the job.
```

Approve the file write with Allow once. Then check the script yourself against [the LUMI Slurm documentation](https://docs.lumi-supercomputer.eu/runjobs/scheduled-jobs/batch-job/): account, partition, time limit and resources.

Submit it from a second terminal (another **Login node shell**), outside OpenCode:

```
cd /scratch/project_462001520/$USER/first-steps
sbatch job.sh
squeue --me
cat slurm-*.out        # after the job finishes
```

The output file contains `hello from LUMI`.

If it fails: paste the `sbatch` error into OpenCode and ask the agent to fix the script. Inside the container, `sbatch: command not found` is expected.
