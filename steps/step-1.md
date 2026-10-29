# Step 1: Rerun every check on `main`

## `image_digest` mismatches on a clean tree

<details><summary>Hint 1</summary>

Did `poe start` rebuild the image? Compare the image ID the candidate tag points at now with the recorded one.

</details>

<details><summary>Hint 2</summary>

Two things change the build's input without changing a commit: a cleared build cache, and files rewritten on disk by a checkout or a merge. On Windows, check the line endings of your working tree against the commit.

</details>

## You're not sure the candidate still describes `main`

<details><summary>Hint 1</summary>

Which commit does the record name? Is it in `main`'s history?

</details>

<details><summary>Hint 2</summary>

Which files has `main` changed since that commit? Are any of them inside the build context? List them with Git.

</details>

## A check runs against the wrong build

<details><summary>Hint 1</summary>

Which tag is set in the shell where you ran it? Is it set in every shell you use, or in an environment file Compose reads?

</details>

<details><summary>Hint 2</summary>

Did you run `poe start` after setting the tag, or only restart containers?

</details>

## `poe verify` moves the candidate's tag

<details><summary>Hint 1</summary>

Does `poe verify` start the stack, and does starting the stack build an image? Which tag does it build under?

</details>

<details><summary>Hint 2</summary>

Once you've changed a file the image is built from, which tag should every later `poe verify` run use?

</details>

## A result differs from your Task 8 or Task 9 note

<details><summary>Hint 1</summary>

What changed between then and now: a case, a script, the configuration, or the build? Find out before you go on.

</details>
