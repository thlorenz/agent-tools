We want to remove the following feature: _feature_

We will do this in multiple steps:

## 1. Plan

Device a plan how to remove this feature step by step. I should be able to build the project
after each step and the unit tests should pass.

Therefore these steps need to be planned well, a few examples:

- remove tests depending on a feature first
- remove code depending on a feature next
- remove the feature, i.e. the module/struct and implementation only when nothing more depends on it

Each step should be numbered header thus that we can implement it one by one.

Here is an example plan:

```markdown
## Step 1: Remove Tests

- <which tests to remove and how>

## Step 2: Remove Usage in <module_name> module

- <how to remove/adjust usage in the module>

## Step 3: Remove Usage <somewhere else>

- <explanation>

## Step4: Remove the Feature

- <explanation of which part of the code/files to remove, etc.>
```

Write that plan to this file `_planfile_`.

I will review it and adapt if needed. When I'm done I will confirm with `ok`.
Then go on to the next step.

## 2. Implementation

After I finalized the plan read the plan file again. Then ask me which step to implement.
I will then type a number like `1` to implement step 1.

When you are done run the build and unit tests and format the code.
DO NOT COMMIT OR STAGE ANYTHING, i.e. do not run `git add` or `git commit`.

I will then review and stage the changes and type `ok` once done.

## 3. Commit

Now supply me with a one line commit message, i.e. `chore: remove usage of x in y`
I will type `ok` to accept or suggest another one.

At that point run `git commit -m "<the message we agreed on>".

DO NOT RUN EITTHER OF THE BELOW, but leave it as is:
- `git add`
- `git push`

Update the `/tmp/01_plan.md` by adding a check mark in front of the step's header and adding
the following right below the header:

Addressed by <commit_hash>.
> <commit message we agreed on>

Example:
```markdown
## Step 1: Remove Tests

Addressed by 3ae34ab
> chore: remove usage of x in y

- <which tests to remove and how>
```

Now go back to `## 2. Implementation` to continue with the next step.
