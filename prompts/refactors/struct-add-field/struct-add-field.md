## Task

I want you to add the following field to the `_struct_name_` struct.

- _field_name_: _field_type_

Make sure to update the following where it applies:

- constructors, i.e. `new` methods
- Debug implementation
- Display implementation
- serialization and deserialization implementations

Code initializing this struct will now miss this field. If possible provide a default value
along with a `TODO: @@@ review this argument` comment so I can review it later.

## 1. Plan

I want you to first outline a plan and write it to `_planfile_`.
Each step in the plan should be a numbered header, i.e. `## Step 1: <label>` followed by a
short description of what it will do.

I will then review and possibly adapt it and confirm with `ok` when done. Ask me to do that.

## 2. Implementation

After I confirmed the plan, read it again and ask me which step to implement. I will select a
step simply by providing a number. If I provide multiple comma separated numbers then implement
all those steps before moving to `3. Commit`.

## 3. Commit

Now supply me with a one line commit message, i.e. `chore: <description>`

Tell me to review the commit message and type `ok` to accept it or suggest another one.
I will type `ok` to accept or suggest another one.

Now I added all changes I want to commit to staging and typed `ok`. This means you should not
add any more changes to the commit, i.e. DO NOT RUN `git add`.

At that point run `git commit -m "<the message we agreed on>".

DO NOT PUSH TO THE REMOTE REPOSITORY, i.e. DO NOT RUN `git push`.

Update the `_planfile_` by adding a checkmark (✅) in front of the step's header and adding
the following right below the header:

Addressed by <commit_hash>.
> <commit message we agreed on>

Example:
```markdown
## Step 1: Update Debug

Addressed by 3ae34ab
> chore: update debug implementation

- <how to update the Debug implementation>
```

Now go back to `## 2. Implementation` to continue with the next step.
