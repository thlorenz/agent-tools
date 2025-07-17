## Pull Request Review Comments Collection

### Details

I provided a pull request to my team and it was reviewed.
I want to collect the comments of one of the reviewers. Here are the details:

- pull request link: link_to_pr
- reviewer github name: reviewer_github_name

### Task

In the title provide the number of the PR on top

Below the title provide the reviewer and the link of the PR below that.

Then start a Comments section.

Do the following for each comment by this reviewer:

1. Create a short title that summarizes the comment, no more than 6 words
2. Provide the link to the comment below that
3. Add the full comment text below the title in comment style
4. Provide the diff to which the comment refers, if available

NOTE: the title of each comment is prefixed with the number of the comment (increase by 1 for each comment).

Here is an example of a PR with one comment:

    ## PR 457 List of Comments by single Reviewer

    - reviewer: taco-paco
    - [Link to PR](<link to pr>)

    ## 01: Title of the comment

    [Link to comment]
    (<link to comment>)

    > First line of comment text.
    > Second line of comment text.

    ```diff
    <some code diff here>
    ```


Write the results to the following file:

- path_to_comments_file

#### Link Formatting

It is important to put the link itself on a new line so it is easy to see it fully in an
editor.

#### Diff Formatting

Please format the diffs such that they appear properly inside a `diff` code block, including
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

This diff is not correctly formatted since it is missing line numbers and is not how the code
is rendered on github:

```diff
- CommitStage::FailedUndelegate((
- x.clone(),
- CommitStrategy::args(use_lookup),
- CommitSignatures {
+ CommitStage::FailedUndelegate((x.clone(), CommitStrategy::args(use_lookup), CommitSignatures {
```

### Notes

You do not need to read any local files to accomplish this task.
All needed information is provided in the PR and the comments.
