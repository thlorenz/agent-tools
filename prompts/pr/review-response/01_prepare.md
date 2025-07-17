## Pull Request Review Comments Collection

### Details

I provided a pull request to my team and it was reviewed.
I want to collect the comments of one of the reviewers. Here are the details:

- pull request link: link_to_pr
- reviewer github name: reviewer_github_name
- base: <base branch of commit>

### Task

In the title provide the number of the PR on top

Below the title provide the reviewer and the link of the PR below that.

Then start a Comments section.

Do the following for each comment by this reviewer:

1. Create a short title that summarizes the comment, no more than 6 words
2. Provide the link to the comment inside the pull request below that
3. Add the full comment text below the title in comment style
4. Provide the diff to which the comment refers, if available

NOTE: the title of each comment is prefixed with the number of the comment (increase by 1 for each comment).

Here is an example of a PR with one comment:

    ## PR 457 List of Comments by single Reviewer

    - reviewer: taco-paco
    - [pr](<link to pull request>)

    ## 01: Title of the comment

    [Link](<link to comment>)

    > First line of comment text.
    > Second line of comment text.

    ```diff
    <some code diff here>
    ```


Write the results to the following file:

- path_to_comments_file

#### Comment Links

The link should be to the comment in the Conversation tab of the pull request. Don't try to
link to the Files tab.

The below is an example of a correct link to a comment:

- https://github.com/magicblock-labs/magicblock-validator/pull/457#discussion_r2209647862

This is linking to the same but in the files tab and thus is incorrect:

- https://github.com/magicblock-labs/magicblock-validator/pull/457/files/f007d4fbcb3b65a81fc8c52c743b9e474b7fe180#discussion_r2209647862

#### Diff

Whenever there is a diff related to a comment you must provide it. Only leave it out for
comments that are not referring to any code.

In order to obtain the diff that the comment refers do the following:

1. You already fetched the base branch on which this commit is based on, below we assume it is
`dev`
2. Use `git diff` to obtain the diff for the file which the comment refers to (example below)

```sh
git diff origin/dev..origin/thlorenz/committor-improve-table-speed magicblock-committor-service/src/commit/commit_using_buffer.rs`
```

Then extract the diff that matters, i.e. 3 lines above and below the change, and format it as
follows.

Format the diffs such that they appear properly inside a `diff` code block, including
the relative file name above the diff and line numbers on first line of the diff itself.

For instance this diff is correctly formatted:

magicblock-committor-service/src/commit/commit_using_buffer.rs
```diff
@ -378,19 +410,12 @@ impl CommittorProcessor {
                                CommitStage::FailedUndelegate((
                                    x.clone(),
                                    CommitStrategy::args(use_lookup),
-                                   CommitSignatures {
```

### Notes

You do not need to read any local files to accomplish this task.
All needed information is provided in the PR and the comments and by obtaining diffs of the
remote branches.
