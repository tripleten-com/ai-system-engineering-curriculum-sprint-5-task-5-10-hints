# Step 2: Write the accepted release manifest and make your verifier read it

## The idea

The candidate record says what the build is. The accepted release manifest adds who stood behind it. It's the same six fields, plus one for your instructor's decision. Kept next to the six fields that identify the build, the decision can't drift away from it the way a chat message or a ticket can.

Three ideas keep the manifest trustworthy:

- **Copied, never typed:** a command reads the six fields from the candidate record and writes them. One mistyped character would name a build nobody has.
- **Written only for a candidate that holds:** before it writes, the command checks the candidate against the running containers, reusing your verifier. If the candidate doesn't hold, it writes nothing and says why. If a manifest already records a decision for this build, it doesn't overwrite it.
- **Checked by the verifier:** the verifier compares each of the six manifest fields with the candidate record, flags a missing or extra field, and checks that the decision is one of the allowed values. A manifest that doesn't exist yet is a state to report, not a mismatch.

The decision field says `pending` until the review. After it, it says `accepted`, with the review's date. One top-level field has to carry both shapes, and the manifest still holds exactly seven fields.

> Covered in **CI Gates and Release Verification**.

## What's expected

- The manifest sits beside the candidate record, in the same file format, with exactly seven top-level fields. The decision is `pending`.
- A comment at the top describes the decision field's shape before and after acceptance.
- Your manifest command copies the six fields from the record. It writes nothing when the candidate doesn't verify, and it refuses to overwrite an accepted decision for the same build.
- Your verifier prints one row per manifest field, a row for the decision, and a row for any extra field. When the manifest is missing, it reports that.
- Pointed at a changed copy outside the repository, the verifier fails and names the field. Without the argument, it passes.

## When you're stuck

### The six values don't match the candidate

<details><summary>Move 1</summary>

Did your command read them from the record, or were any typed?

</details>

<details><summary>Move 2</summary>

Does the command read the record from the path the verifier uses?

</details>

<details><summary>Move 3</summary>

Regenerate the manifest with the command, compare it line by line with the record, and commit both together.

</details>

### The command writes a manifest for a candidate that doesn't hold

<details><summary>Move 1</summary>

What does your command check before it writes?

</details>

<details><summary>Move 2</summary>

Which code already knows whether the candidate matches the running containers?

</details>

<details><summary>Move 3</summary>

Call that code first. If it finds any mismatch, print what didn't match and exit without writing.

</details>

### Rerunning the command would reset the decision

<details><summary>Move 1</summary>

What should the command do if a manifest is already there?

</details>

<details><summary>Move 2</summary>

What if that manifest says `accepted` for the same tag?

</details>

<details><summary>Move 3</summary>

Refuse in that case, and say that a fix needs a new candidate and then a new manifest.

</details>

### The decision field breaks the seven-field rule

<details><summary>Move 1</summary>

How can one top-level field hold a value, and later a value and a date?

</details>

<details><summary>Move 2</summary>

Would a small nested block, or one value with the date beside it, keep the count at seven?

</details>

<details><summary>Move 3</summary>

Choose one shape, write it in the comment at the top, and make the verifier accept exactly that shape and nothing else.

</details>

### Your verifier fails before any manifest exists

<details><summary>Move 1</summary>

Is a missing manifest a mismatch, or a state the verifier should report?

</details>

<details><summary>Move 2</summary>

What does the lesson say about this case?

</details>

<details><summary>Move 3</summary>

When the file doesn't exist, print that it's missing, skip the manifest rows, and keep the exit code driven by the candidate's rows.

</details>

### You can't make the verifier fail without editing the manifest

<details><summary>Move 1</summary>

Can the verifier read a manifest from a path you give it?

</details>

<details><summary>Move 2</summary>

Where could you put a changed copy so the repository stays untouched?

</details>

<details><summary>Move 3</summary>

Copy the manifest somewhere outside the repository, change one value, run the verifier against the copy, and keep that output.

</details>
