Please analyze the following code base for attack vectors and security issues following the
steps I outline below. Do not build the project, perform the audit on the source code only.

## Code of Dependencies

The source code of all crates used in this codebase are locally inside either subdirectory of:

$HOME/.cargo/registry/src/

The `Cargo.lock` contains the exact versions of the dependencies used in this codebase.

### Example quote dependency

Cargo.lock entry:

```
[[package]]
name = "quote"
version = "1.0.40"
```

The code is inside `$HOME/.cargo/registry/src/index.crates.io-<cargo index>/quote-1.0.40/`.

## Analyzing Dependencies

You don't have to analyze all dependencies, namely we trust the following since they are in
wide use in the community.

- borsh,
- bytemuck,
- num_enum,
- solana-program,
- solana-curve25519,
- solana-program-test,
- solana-client,
- solana-account-decoder,
- curve25519-dalek,
- sha2,
- hkdf,
- solana-sdk,
- tokio,
- clap,
- anyhow,
- log,
- env_logger,
- anchor-lang,
- helius-laserstream,
- futures-util,
- futures,
- futures-core,
- async-trait,
- crossbeam-channel,
- bincode,
- base64,

You don't have to analyze the above.

However the following library: `steel` is fairly new and we need to ensure that our program
code interfades with it correctly and that `steel` performs the correct security checks etc.

## Analyzing Program Code

Analyze the code looking for one of the below aspects at a time. Do this in multiple steps,
i.e. first security, then efficiency.

Whenever you find an issue or have a suggestion include the relevant filename and linenumber
along with a code snippet along with your analysis.

### Security

Make sure that we verify signers, owners, etc.

### Efficiency

Ensure that only accounts that need to be writable are actually passed as writable to the
instruction.
Also look for

### Tests

Evaluate the tests and ensure that they cover the code sufficiently especially regarding
security.

## Report

Write a report to `security-rust-solana-report.md` with the following sections:

- Dependencies
- Program Code
  - Instructions sub section explaining each instructions and security checks performed
- Tests
- Security Issues
  - any potential or real issues that you found in the codebase
- Conclusion
- Recommendations
- References


