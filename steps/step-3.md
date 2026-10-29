# Step 3: Prepare for the first Instructor Review

## The idea

Your instructor reads ten pull requests and ten evidence notes and asks four questions:

- Did you meet each Task's requirements?
- Did you explain your design choices?
- Can your tests fail when the code is wrong?
- Did you state the limits of what your checks show?

Then they accept the work or return it. Your job in this Step is to make the answers easy to find, not to produce new evidence.

Three pieces do that:

- **An overview:** one row per Task, with what it built in plain words, its pull request and its evidence note. It's an index to everything else.
- **Four answers, once, for all of Part 1:** each points at the notes that hold the evidence. A claim that names no note isn't evidence. It's a memory.
- **An honest list of gaps:** where an earlier note doesn't answer one of the questions, you say so here, with the Task, the question and the answer you'd give now. You don't rewrite the earlier note. It's the record of what you knew then.

If your instructor shared a solution guide for any Task, the overview says so too, with the Task and the part. And if they accept, you'll open one more pull request that changes only the decision in the manifest.

> Covered in **How the project is submitted and reviewed**.

## What's expected

- You read each Task's note with the four questions beside it, and know which paragraph answers each.
- The overview has ten rows: what each Task built, its pull request number and its note's path.
- Each of the four answers is two to four sentences and names the notes and Tasks it rests on.
- The limits answer gathers every stand-in and limit from Tasks 1 to 10 into one list.
- Every gap in an earlier note appears with its Task, its question and your answer now.
- Any solution guide you used is named, with the Task and the part.
- You can say what the decision pull request will change, and what it won't.

## When you're stuck

### An earlier note doesn't answer one of the questions

<details><summary>Hint 1</summary>

Does the lesson ask you to fix that note, or to say where it's thin?

</details>

<details><summary>Hint 2</summary>

For that gap, what's the answer you'd give now? Where's the evidence for it?

</details>

<details><summary>Hint 3</summary>

Add it to this Task's note as one line: the Task, the question, your answer, and where the evidence is.

</details>

### You can't find a pull request number

<details><summary>Hint 1</summary>

Open your repository's pull requests, including closed and merged ones.

</details>

<details><summary>Hint 2</summary>

Which pull request merged each Task's branch into `main`?

</details>

<details><summary>Hint 3</summary>

Search the merged pull requests by branch name or by the evidence note's path.

</details>

### Your answers read like memories

<details><summary>Hint 1</summary>

For each sentence in your four answers, which note and which Task shows it?

</details>

<details><summary>Hint 2</summary>

If no note shows it, what's the claim resting on?

</details>

<details><summary>Hint 3</summary>

Rewrite each answer so every claim names a note and a Task, or move the unsupported claim to your gap list.

</details>

### The limits list is short

<details><summary>Hint 1</summary>

Go through every note's **What I'd defend**. Which stand-ins did you use?

</details>

<details><summary>Hint 2</summary>

For each stand-in, what did it stop you from seeing? Think of the emulator, LocalStack, the local token issuer and one sample of a hosted model.

</details>

<details><summary>Hint 3</summary>

Collect every limit, one line each, with the Task it comes from.

</details>

### You're not sure how to report a solution guide you used

<details><summary>Hint 1</summary>

Did your note for that Task already say so?

</details>

<details><summary>Hint 2</summary>

Which part of that Task did the guide cover?

</details>

<details><summary>Hint 3</summary>

Repeat it in the overview with the Task and the part. At Final Demo Day you'll explain those parts like any other.

</details>

### You're not sure what the decision pull request may change

<details><summary>Hint 1</summary>

Which single field records your instructor's decision?

</details>

<details><summary>Hint 2</summary>

What should a reviewer see in the diff of that pull request, and nothing more?

</details>

<details><summary>Hint 3</summary>

Say out loud what your tests will check on it: the seven fields, the six against the candidate, and `accepted` with a date as an allowed decision.

</details>
