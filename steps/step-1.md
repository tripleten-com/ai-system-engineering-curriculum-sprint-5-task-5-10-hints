# Step 1: Rerun every check on `main`

## The idea

A check that passed on another commit is history, not evidence about this build. Since your evaluation passed in Task 8 and your verifier passed in Task 9, you've merged more work. Before anyone decides about the build, a freeze runs every check again, at one moment, on the commit `main` holds now, against the build your candidate record names.

Two questions come before any command.

- **Is the candidate's commit in `main`'s history?**
- **Has any later commit changed a file the image is built from?** That means the source, the dependencies, the Dockerfile, the configuration, the migrations or the evaluation set.

If both answers are right, the candidate still describes `main`. If not, the freeze would measure a build nobody recorded, and you need a new candidate first.

Then the freeze itself: start the stack from the candidate's tag, and run the public check, the demo, your evaluation and your release verifier, in that order, keeping each command, time and result. Compare the results with your Task 8 and Task 9 notes. Same cases, same verdicts, same digest. A difference is something to understand before you go on, not something to explain away.

From here on, your Task 10 code is part of the build, so any later stack start uses a scratch tag.

> Covered in **CI Gates and Release Verification**.

## What's expected

- Your Task branch starts at `main`'s tip and doesn't change the agent or its configuration.
- Git confirms the candidate's commit is an ancestor of `main`, and no later commit touches a file inside the build context.
- With the candidate's tag set, `poe start`, `poe ready` and `poe ingest` finish, and these four run to the end, in order:
  - `poe verify`
  - `poe demo`
  - your evaluation command
  - your release verifier
- The verifier passes, and you kept its whole output with the command and the time.
- Each result matches what your Task 8 and Task 9 notes recorded, or you found out why not.

## When you're stuck

### You're not sure the candidate still describes `main`

<details><summary>Move 1</summary>

Which commit does the record name? Is it in `main`'s history? Ask Git directly.

</details>

<details><summary>Move 2</summary>

Which files has `main` changed since that commit? List them with Git.

</details>

<details><summary>Move 3</summary>

For each file, is it inside the build context, or excluded by `.dockerignore`?

</details>

<details><summary>Move 4</summary>

If any listed file is inside the build context, the candidate no longer describes `main`. Record a new candidate from `main`, then freeze against that one.

</details>

### `image_digest` mismatches on a clean tree

<details><summary>Move 1</summary>

Did `poe start` rebuild the image? Compare the image ID the candidate's tag points at now with the recorded one.

</details>

<details><summary>Move 2</summary>

Two things change the build's input without changing a commit: a cleared build cache, and files rewritten on disk by a checkout or a merge.

</details>

<details><summary>Move 3</summary>

On Windows, compare the working tree's line endings with the commit's. Which command lists both?

</details>

<details><summary>Move 4</summary>

Fix what changed on disk, confirm the rebuild under a scratch tag gives the recorded ID, and only then run the freeze under the candidate's tag.

</details>

### A check runs against the wrong build

<details><summary>Move 1</summary>

Which tag is set in the shell where you ran it?

</details>

<details><summary>Move 2</summary>

Is it set in every shell you use, or in an environment file Compose reads?

</details>

<details><summary>Move 3</summary>

Did you run `poe start` after setting the tag, or only restart containers? A restart keeps each container on the image it already runs.

</details>

### A check was skipped or stopped early

<details><summary>Move 1</summary>

Did each of the four print its own result, or did one stop before its end?

</details>

<details><summary>Move 2</summary>

A check that didn't run to the end isn't a pass. Which one stopped, and what did it print last?

</details>

<details><summary>Move 3</summary>

Fix the cause and run all four again, in order, so the freeze is one moment, not a mix of moments.

</details>

### `poe verify` moves the candidate's tag

<details><summary>Move 1</summary>

Does `poe verify` start the stack, and does starting it build an image?

</details>

<details><summary>Move 2</summary>

Your Task 10 code lives inside the build context. Once it exists, what does a build under the candidate's tag produce?

</details>

<details><summary>Move 3</summary>

After the freeze, run `poe start` and `poe verify` only under a scratch tag. Never use the candidate's.

</details>

### A result differs from your Task 8 or Task 9 note

<details><summary>Move 1</summary>

What changed between then and now: a case, a script, the configuration, or the build?

</details>

<details><summary>Move 2</summary>

Compare the commit in each note with the commit you're on. What did the commits in between change?

</details>

<details><summary>Move 3</summary>

Find the reason before you go on, and write it down. The freeze records what is, not what was.

</details>
