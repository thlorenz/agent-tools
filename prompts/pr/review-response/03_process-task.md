## Pull Request Review Comments Collection

### Details

I provided a pull request to my team and it was reviewed.

- pull request link: link_to_pr
- reviewer github name: reviewer_github_name
- base: <base branch of commit>

In a previous steps we extracted all comments from the pull request to a file and then
separated them so that now we know which coding tasks to address.

- path_to_comments_separated

As a result all coding tasks are under the `Tasks` section.

## Task

Lets start with task numbered: task_number

What I want you to do is the following:

1. Understand what changes are required and provide a quick plan on how to implement them, then
prompt me for confirmation.

2. If I confirm, implement the changes, and if I don't ask me if you should try again

DO NOT ADD ANYTHING TO git YET, i.e. DON'T RUN any of the following commands:

- `git add`
- `git commit`

Instead I will review the changes myself and if I approve I will stage them.

DON'T RUN BUILD or TESTS either, I will do that myself or in the next step.

_Format_ the code after your changes are complete

3. Ask me if you should run any checks to ensure the code is correct and do the following based
on my reply:

- `no` goto step 4
- `check` run the _check_ as specified in the `AGENT.md` and fix issues until it passes
- `build` run the _build_ as specified in the `AGENT.md` and fix issues until it passes
- `test` run _unit tests_ as specified in the `AGENT.md` and fix issues until it passes

Ask me again after each check until I type `no`. Then go to step 4.

4. Wait for me to review and stage the changes to git, as part of this I may ask you to make
additional changes. However if I just type `ok` then go to step 4.

5. Provide me with a short commit message which is derived form the title and the reviewer's name.

Example: `chore: address - add new feature - taco-paco`

Then ask me if you should proceed with the commit using that message.
If I say `ok` then proceed, otherwise wait for further instructions and don't go to step 5 for now.

DON'T ADD ANY FILES TO STAGING when committing, i.e. don't run `git add`.
All you need to do is runt `git -m "<commit message>"`

6. Update the path_to_comments_separated file by moving the completed task to the `Done`
section as is and add the following text below it:

```markdown
#### Reply

Addressed in <commit hash>
```

Read the commit hash from the commit we just completed.

NOTE: don't use the full commit hash, but a short version instead, example:
- don't use `dd6bf69a999f0b78aa55c7855069584b4f55e6f6`
- do use `dd6bf69a` instead
