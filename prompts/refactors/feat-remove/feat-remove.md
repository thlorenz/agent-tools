We want to remove the following feature: _feature_

_moredetails_

We will remove the feature in multiple steps:

## 1. Plan

First look if the plan file already exists at `_planfile_`.

In that case let me know that you found an existing plan file and skip to `## 2. Implementation`.

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

Tell me that I should review the plan and adapt it if needed, and confirm with `ok` when done.

I will review the plan file and adapt if needed. When I'm done I will confirm with `ok`.
Then go on to the next step.

## 2. Implementation

After I finalized the plan read the plan file again.
Steps with a checkmark (✅)  were already implemented previously so you can ignore those.

Ask me which step to implement. I will then type a number like `1` to implement step 1.

When you are done run the build and unit tests and format the code.
DO NOT COMMIT OR STAGE ANYTHING, i.e. DO NOT RUN `git add` or `git commit`.

Tell me to stage the changes and type `ok` when done.

I will then review and stage the changes and type `ok` once done.

## 3. Commit

Now supply me with a one line commit message, i.e. `chore: remove usage of x in y`

Tell me to review the commit message and type `ok` to accept it or suggest another one.
I will type `ok` to accept or suggest another one.

Now I added all changes I want to commit to staging and typed `ok`. This means you should not
add any more changes to the commit, i.e. DO NOT RUN `git add`.

At that point run `git commit -m "<the message we agreed on>".

DO NOT PUSH TO THE REMOTE REPOSITORY, i.e. DO NOT RUN `git push`.

Update the `/tmp/01_plan.md` by adding a checkmark (✅) in front of the step's header and adding
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
