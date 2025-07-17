## agent-tools

This repository contains a collection of tools that are used to interact with coding agents.

Mainly, it includes prompts for specific use cases.

### Responding to Pull Request Reviews

In order to respond to pull request reviews we perform the following steps:

1. Download comments and filter by particular reviewer
2. Separate comments into tasks, won't fix and plain comments
3. Process each task and add a commit that fixes the issue outlined in it

For each of those steps a prompt is provided inside `prompts/pr/review-response/`.

For the `amp` tool a script to execute them is provided as well.
Here would be an example on how to use them.

#### 1. Set env vars in Shell

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

#### 2. Run the prompt scripts

Ideally you add the `prompts/pr/review-response/` directory to your `PATH` so you can run
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

## LICENSE

MIT
