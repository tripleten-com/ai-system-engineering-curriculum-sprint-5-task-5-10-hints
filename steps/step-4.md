# Step 4: Prove it with tests and write the evidence note

## The idea

The manifest check reads two files and compares them, so its tests need no stack and no server. Hand the check the manifest and the candidate record, or an in-memory copy with one change, and read the result. Three groups cover the rules:

- **The shape:** the committed manifest has exactly the seven fields, and a copy with one missing or one extra is rejected.
- **The six fields:** each equals the candidate record, and a copy with one changed value is rejected, naming that field.
- **The decision:** the allowed values pass, and anything else is rejected.

Read the expected values from the candidate record in the test. Typing a digest into a test makes a second copy that goes stale on the next candidate. Make every rejection test check the field the check names. A check that fails for the wrong reason, or that rejects every manifest, would otherwise pass.

The break loop uses only the command that runs your tests. It starts no build, so the candidate's image is safe. Your final `poe verify` runs under a scratch tag, never the candidate's. The verifier's passing output that your note cites comes from the run started under the candidate's tag. Your instructor reads this note first, so it opens with the overview.

> Covered in **CI Gates and Release Verification**.

## What's expected

- Your test file sits where `poe student-tests` collects it, beside your earlier tests, and runs with no stack.
- The shape tests reject a missing field and an eighth field.
- The six-field tests read the record in the test and reject a changed value, naming the field.
- The decision tests pass both allowed values and reject any other.
- You broke each group once with `poe student-tests` and saw a test fail.
- `docs/capstone/task-10.md` holds these:
  - the freeze
  - the manifest checks
  - the overview of Tasks 1 to 10
  - your four answers
  - the gaps list
  - the decisions you made
- `poe verify` passes under a scratch tag after your last edit.

## When you're stuck

### The six-field tests break on the next candidate

<details><summary>Hint 1</summary>

Where do the tests get their expected values?

</details>

<details><summary>Hint 2</summary>

If a digest is typed into the test, which copy goes stale when you record again?

</details>

<details><summary>Hint 3</summary>

Load the candidate record in the test and compare each manifest field with the record's value of the same name.

</details>

### A test passes when the check rejects every manifest

<details><summary>Hint 1</summary>

Is there a test that a good manifest passes?

</details>

<details><summary>Hint 2</summary>

Does each rejection test check which field the check named?

</details>

<details><summary>Hint 3</summary>

Add the passing test, assert the field name in every rejection, then make the check reject everything and watch the passing test fail.

</details>

### After your last edit, the verifier no longer passes

<details><summary>Hint 1</summary>

Which tag was the stack started with for your final `poe verify`?

</details>

<details><summary>Hint 2</summary>

What does the release verifier compare when the running tag isn't the candidate's?

</details>

<details><summary>Hint 3</summary>

Cite the passing verifier output from the run started under the candidate's tag, and say in your note that the final `poe verify` ran under a scratch tag, and why.

</details>
