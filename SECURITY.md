# Security policy

If you believe you have found a security vulnerability — in the AFAuth protocol, the reference CLI, or the TypeScript SDKs — please report it privately. **Do not file a public GitHub issue.**

## Where to report

Email **guowen89@gmail.com** with:

- A description of the issue and its potential impact.
- Steps to reproduce or a proof-of-concept, if available.
- Your name and how you'd like to be credited (or `anonymous`).

We aim to acknowledge reports promptly and to work with you on a coordinated fix and disclosure timeline.

## Scope

**In scope:**

- The AFAuth protocol specification in [`AFAuthHQ/spec`](https://github.com/AFAuthHQ/spec) — design-level flaws, ambiguities that lead to interoperability gaps with security impact, missing requirements.
- Reference implementation code in [`AFAuthHQ/cli`](https://github.com/AFAuthHQ/cli) and [`AFAuthHQ/typescript-sdk`](https://github.com/AFAuthHQ/typescript-sdk).
- The published npm packages under [`@afauthhq`](https://www.npmjs.com/org/afauthhq).

**Out of scope:**

- Vulnerabilities in third-party services that implement AFAuth — please contact those services directly. We're happy to be cc'd if the issue stems from spec-level ambiguity.
- Findings that require an already-compromised operator key, root access to the user's device, or other pre-conditions that fall outside the threat model in [`spec/core.md` §2](https://github.com/AFAuthHQ/spec/blob/main/spec/core.md).

## Coordinated disclosure

We follow standard coordinated disclosure. Once a fix is available, we'll work with you on a publication window that gives downstream implementers time to upgrade — typically up to **90 days** from the initial report — before public disclosure.

Credit for the finding goes in the release notes unless you ask otherwise.
