# Agent Instructions

Include these inside the `AGENT.md` file in the root of your project to make extra features
work.
Replace `~/dev/ai/agent-tools/` with the path to your agent tools directory.

## Instruction Snippets

I defined additional instruction snippets inside  ~/dev/ai/agent-tools/ixs.
I will refer to them via `ix:<instruction_name>`. When you encounter this you should read the
relevant file and inline its contents as part of the full task instruction that you will
process later.

For instance when I say:

```markdown
ix:rust-check
```

you should read the file `~/dev/ai/agent-tools/ixs/rust-check.md` and inline its contents and
continue.
