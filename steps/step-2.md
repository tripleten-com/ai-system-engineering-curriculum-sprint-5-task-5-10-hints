# Step 2: Write the accepted release manifest and make your verifier read it

## Your verifier fails before any manifest exists

<details><summary>Hint 1</summary>

Is a missing manifest a mismatch, or a state the verifier should report and move past? What does the lesson say?

</details>

## Rerunning the command would reset the decision

<details><summary>Hint 1</summary>

What should the command do if a manifest is already there, especially one that says `accepted`?

</details>

## The decision field breaks the seven-field rule

<details><summary>Hint 1</summary>

How can one top-level field hold a value and a date? Count your top-level fields after you choose a shape.

</details>

## You can't make the verifier fail without editing the manifest

<details><summary>Hint 1</summary>

Can the verifier read a manifest from a path you give it? Where could you put a changed copy so the repository stays untouched?

</details>

## The command writes a manifest for a candidate that doesn't hold

<details><summary>Hint 1</summary>

What does your command check before it writes? Which code already knows whether the candidate matches the running containers?

</details>
