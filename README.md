## agent-tools

This repository contains a collection of tools that are used to interact with coding agents.

Mainly, it includes prompts for specific use cases.

### Pull Requests

#### Creating Pull Requests

The `amp-pr-create` script helps create comprehensive pull requests by generating appropriate titles and descriptions based on your changes.

```bash
./prompts/pr/create/amp-pr-create "main"
```

This script analyzes your current branch's changes, helps you craft a proper PR title following
conventional commit format, generates a detailed PR body with Summary and Details sections, and
submits the PR using the GitHub CLI.

#### Responding to Pull Request Reviews

In order to respond to pull request reviews we perform the following steps:

1. Download comments and filter by particular reviewer
2. Separate comments into tasks, won't fix and plain comments
3. Process each task and add a commit that fixes the issue outlined in it

For each of those steps a prompt is provided inside `prompts/pr/review-response/`.

For the `amp` tool a script to execute them is provided as well.
Here would be an example on how to use them.

##### 1. Set env vars in Shell

Those should be the same for each prompt script and should be exported in the terminal that we
will use to address the pull request review.

NOTE: it is required to also be in the root of the repository for this to work, however don't
have to check out the branch as all information is obtained from remote branches.

Example:

```bash
export LINK=https://github.com/me/my-project/pull/457
export REVIEWER=my-friend
export COMMENTS=pr-457/comments.md
```

##### 2. Run the prompt scripts

Ideally you add the `bin` directory to your `PATH` so you can run
the scripts directly.

```bash
amp-pr-01
```

_Downloads all comments_

After this is done you can remove those that you don't care about

```bash
amp-pr-02
```

This will separate the comments into three sections: `Plain Comments`, `Won't Fix` and `Tasks`
and save them next to your COMMENTS file, i.e. `pr-457/comments_separated.md`.

Open that file to see each task you should address then run the below for each task:

```bash
amp-pr-03 <task-number>
```

Finally reply to the won't fix issues and you're done responding to the PR.

### Refactors

#### Feature Removal

The `amp-feat-remove` script helps systematically remove features from a codebase by guiding
you through a planned, step-by-step process.

```bash
./prompts/refactors/feat-remove/amp-feat-remove "feature name"
```

This script creates a structured plan for feature removal that ensures the project builds and
tests pass after each step. It handles dependencies correctly by removing tests first, then
dependent code, and finally the feature implementation itself.

## LICENSE

MIT
