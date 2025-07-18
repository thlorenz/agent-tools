I want to submit a PR for the current branch onto the _branch_ branch.

I pulled the latest changes for both branches and based the current branch on the _branch_
branch. Thus you can use `git diff` and `git log` in order to see which changes were applied.

## Closed Issues

Ask me for issues that this PR closes, I will provide them via comma separated numbers, or
empty if there is none.

You will add these issues as part of the PR summary section via the _CLOSES_ keyword.
Example:

```markdown
## Summary

<summary of the PR>
CLOSES: #123, #456
```

## PR Message

Please recommend a content for the pull request body based on the changes made in this branch.
The pull request body should have two sections:

- Summary: which summarizes what this PR does in a short paragraph or list of items
- Details: which provides more details on the changes, why they were made and how they work, it
  can have list items, sub sections and so on

Here is an example of a pull request message:

```markdown
## Summary

Adding a full fledged committor service to support the following kind of commits:

- commits up to 10Kb as long as the size increase per commit is <=1Kb
- max accounts per bundle is 3 without lookup tables and  12 with lookup tables
- commit results are persisted into a SQlite database in the ledger directory which makes it
easy to manually retry them or do this automatically (next committor version will support this)

## Details

The following crates were developed
[here](https://github.com/magicblock-labs/committor/pulls?q=is%3Apr+is%3Aclosed) and integrated
into the validator:

### magicblock-rpc-client

- thin wrapper around the solana rpc client with added features like improved transaction
signature status checking (including sane retries)
- lookup table convenience methods
- multi account fetch with known max limit
- waiting for slots

### magicblock-table-mania

- a lookup table manager that allows to create, extend and deactivate + close lookup tables
- the API supports _reserving_ pubkeys which will be added to a table and when they need to be
  used in a transaction the needed table addresses are provided
- once a pubkey is _released_ this is noted and a table is deactivated and closed on chain once
  all its pubkeys are released

### magicblock-committor-program

- allows the committor service to upload account data to be committed in chunks
- supports creation/resizing of buffers and filling them with transactions running in parallel
  (out of order is ok)

### magicblock-committor-service

- commits a changeset as fast and efficiently as possible
- first prefers transactions that don't require lookup tables since those take time to become
available
- then prefers args only commits to the use of buffers (which require preparation)

## Sample Flow

1. Validator starts up and reserves common pubkeys (used in all commits) with the committor
service
2. Account are cloned and for each account the pubkeys for commits are reserved to prepare the
lookup tables which we might need as fast as possible
3. Account(s) commit is scheduled and registered as we did before
4. The commits are processed via the committor service and the on chain transaction signature
is provided to the user via logs in a transaction (as we did before, just now we have to wait
for the commit to complete)

For those commits the committor service ensures that accounts with the same commit (bundle) id
are always processed atomically.

The committor service also picks the best possible strategy to commit each changeset,
preferring speed and then cost.

It also inserts configurable (via code) compute budget instructions to each transaction.

The outcome of each commit is persisted to a database which allows manual (and in the next
version) automated retries of failed commits.
Succeessful commits are also persisted to the database and can be used for diagnostics. In the
future they should be removed since no retry is necessary.

On chain signatures for process-commit/finaliz/undelegate transactions are also persisted to
the database in a separate table.

This table is queried by the validator to log those signatures as part of a transaction that
the user waits for.
```

When going into details do not explain all code changes to the letter, i.e. something was added
to a constructor or things like that. Devs can see that from the diff. Instead explain _what_ I
did, not _how_ I did it.

When you are done, write the results to a tmp file. I will review it and update it and type
`ok` when I am done.

## PR Title

Please recommend a title for the pull request based on the changes made in this branch.

The pull request title should be short and descriptive, ideally no more than 50 characters.

It should have this format:
`<type>: <description>`

Where type is one of the following:

- `feat`: for new features
- `fix`: for bug fixes
- `docs`: for documentation changes
- `chore`: for maintenance tasks, refactors and other changes that don't change the
functionality
- `perf`: for performance improvements
- `test`: for changes to tests

Then ask me to approve the title. If I type `ok` use it, otherwise I will provide a title you
should use.

## Submit PR

Once you have the PR message and title, submit the pull request using the following command:

```bash
gh pr create --title='<title>' --body-file <path to tmp file> --base _branch_
```

Where `<title>` is the title we decided on and `<path to tmp file>` is the path to the file
containing the PR body.
