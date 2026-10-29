# Step 4: Prove it with tests and write the evidence note

## The six-field tests break on the next candidate

<details><summary>Hint 1</summary>

Where do the tests get the expected values? If a digest is typed into the test, which copy goes stale?

</details>

## A test passes when the check rejects every manifest

<details><summary>Hint 1</summary>

Does each rejection test assert the field the check names? Is there also a test that a good manifest passes?

</details>

## After your last edit, the verifier no longer passes

<details><summary>Hint 1</summary>

Which tag was the stack started with for your final `poe verify`? What does the release verifier compare when that tag isn't the candidate's?

</details>

<details><summary>Hint 2</summary>

Which run is the passing verifier output your note cites, and when did you capture it?

</details>
