## Pull Request Review Comments Collection

### Details

I provided a pull request to my team and it was reviewed.

- pull request link: link_to_pr
- reviewer github name: reviewer_github_name
- base: <base branch of commit>

In a previous step we extracted all comments from the pull request to a file.

- path_to_comments_file

## Task

I want to separate the comments into 3 sections.

1. comments not referring to code under `Plain Comments`
2. comments referring to code that we consider invalid and will address with an explanation
3. comments referring to code that we should address with a code change

### Comments Not Referring to Code

When you see a comment that does not refer to code, copy it in the `Plain Comments` section as
is.

### Comments Referring to Code

When you see a comment referring to code think very hard if it is a valid request and do the
following depending on the answer.

#### Invalid Request

Put this comment in the `Won't Fix` section and add a detailed markdown formatted
explanation on why the current implementation is fine and does not need to be changed.

NOTE: we want to keep the existing section of the comment as well, so copy it as is and add the
explanation below it.

NOTE: the explanation should be below a `#### Explanation` header.

#### Valid Request

Move this comment as is into the `Tasks` section. We will address those later.

Save the result of this task to the following file:

- path_to_comments_separated
