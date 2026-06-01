# AFAuth

> **The next user signing up to your service _isn't a human._**
> AFAuth — Agent-First Auth — is the open protocol that makes AI agents first-class users of every service. They sign themselves up with their own cryptographic identity. A human can take ownership later — or never.

→ Landing: **[afauth.org](https://afauth.org)** · Docs: **[docs.afauth.org](https://docs.afauth.org)**

Every request is signed per RFC 9421. Agents identify with `did:key`. No passwords, no bearer tokens, no `client_id`-style developer registration. The protocol is intentionally small and language-agnostic — the [`spec`](https://github.com/AFAuthHQ/spec) repo is the normative source.

Services stay spam-resistant by accepting only **attested** signups by default: an agent links once to a human at the canonical attestor (**[trust.afauth.org](https://trust.afauth.org)**, AFAP-0006), then presents a short-lived, PII-free attestation JWT per request — a per-human pseudonym the service can rate-limit on, with no human OAuth and no shared identity.

## Pick your side

### If you run an agent — install the CLI

```bash
brew install afauthhq/tap/afauth                     # macOS / Linuxbrew
curl -fsSL https://afauth.org/install.sh | sh        # direct download
go install github.com/afauthhq/cli/cmd/afauth@latest # from source
```

```bash
$ afauth init                          # keypair → did:key:…
$ afauth trust link                    # one-time: link this agent to a human at trust.afauth.org
$ afauth signup https://api.example.com  # signs up; auto-attaches an attestation when the service requires one
```

→ [`AFAuthHQ/cli`](https://github.com/AFAuthHQ/cli) · pre-built binaries on the [releases page](https://github.com/AFAuthHQ/cli/releases/latest)

### If you ship a service — install the SDK

```bash
npm i @afauthhq/server   # any HTTP framework
npm i @afauthhq/worker   # Cloudflare Workers
npm i @afauthhq/agent    # build an agent client
```

```ts
import { Server } from '@afauthhq/server';

const server = new Server({
  nonceStore, revocationList,
  serviceDid, accounts, recipients,
});
```

→ [`AFAuthHQ/typescript-sdk`](https://github.com/AFAuthHQ/typescript-sdk) · packages under [`@afauthhq`](https://www.npmjs.com/org/afauthhq)

## Repositories

| Repo | What it is |
|---|---|
| [**`spec`**](https://github.com/AFAuthHQ/spec) | Normative protocol specification, JSON schemas, and Appendix C test vectors. Start here. |
| [**`cli`**](https://github.com/AFAuthHQ/cli) | Reference command-line interface in Go. Generates identities, signs calls, runs the conformance probe. |
| [**`typescript-sdk`**](https://github.com/AFAuthHQ/typescript-sdk) | Reference TypeScript SDKs — composable agent / server / Cloudflare Worker packages. |
| [**`trust`**](https://github.com/AFAuthHQ/trust) | The canonical **trust attestor** at `trust.afauth.org` (AFAP-0006) — links an agent DID to a human and mints short-lived, PII-free attestation JWTs, the signal that lets an agent reach a spam-resistant `attested_only` service. |
| [**`registry`**](https://github.com/AFAuthHQ/registry) | The opt-in service directory at `registry.afauth.org` (AFAP-0003) for cold-start discovery. |

## Status

**v0.1.** Signature verification, owner-invitation + claim ceremony, pre-claim key rotation, owner-initiated revocation, attestation, rate-limit envelope. Reference implementations published at 0.1.x. An executable conformance harness lives in [`spec/harness/`](https://github.com/AFAuthHQ/spec/tree/main/harness).

## Contributing, security & license

- **Issues** — protocol: [`spec/issues`](https://github.com/AFAuthHQ/spec/issues); implementations: file in the relevant repo. New ideas live as [AFAuth Protocol Proposals](https://github.com/AFAuthHQ/spec/tree/main/proposals).
- **Security** — report privately, see [`SECURITY.md`](./SECURITY.md). No public issues for security-sensitive findings.
- **License** — spec text [CC-BY-4.0](https://github.com/AFAuthHQ/spec/blob/main/LICENSE); code-shaped artefacts [Apache-2.0](https://github.com/AFAuthHQ/spec/blob/main/LICENSE-CODE); CLI & SDKs [MIT](https://github.com/AFAuthHQ/cli/blob/main/LICENSE). Dual-licensing follows standard protocol-repo practice.
