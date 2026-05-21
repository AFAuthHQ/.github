# AFAuth

> **Human attention is finite. Agent attention is exploding.**
> AFAuth is the open protocol that makes AI agents first-class citizens of every service.

AI agents sign themselves up to AFAuth-supporting services automatically — with their own cryptographic identity, no human in the loop. Your agent reaches every service that exists. Your service reaches every agent that exists. Both sides multiply each other.

Every request is signed per [RFC 9421](https://www.rfc-editor.org/rfc/rfc9421) (HTTP Message Signatures) — no passwords to share, no bearer tokens, no `client_id`-style developer registration. Time to make agents first-class users of your service.

## Repositories

| Repo | What it is |
|---|---|
| **[`spec`](https://github.com/AFAuthHQ/spec)** | The normative protocol specification, JSON schemas, and Appendix C test vectors. Start here. |
| **[`cli`](https://github.com/AFAuthHQ/cli)** | Reference command-line interface in Go. Generate a keypair, signed-call any AFAuth service, and run the conformance probe against a deployment. |
| **[`typescript-sdk`](https://github.com/AFAuthHQ/typescript-sdk)** | Reference TypeScript SDK published as [`@afauthhq/*`](https://www.npmjs.com/org/afauthhq). Composable agent / server / Cloudflare Worker packages. |

## Try it

```bash
# Service side — install the alpha SDK
npm i @afauthhq/server@alpha

# Agent side — pre-built CLI binaries on the releases page:
# https://github.com/AFAuthHQ/cli/releases/latest
```

The CLI's `afauth probe` command runs the full §-level conformance harness against any AFAuth service, including yours under development.

## Status

**v0.1 — alpha.** The protocol is feature-complete for the v0.1 milestone (signature verification, owner-invitation + claim ceremony, pre-claim key rotation, owner-initiated revocation, attestation, rate-limit envelope). The spec is still a working draft and packages are tagged `alpha` — breaking changes are possible until v0.1 is finalised.

## Contributing

- Protocol questions, ambiguities, and proposals: [`spec/issues`](https://github.com/AFAuthHQ/spec/issues).
- Implementation bugs: file in the relevant implementation repo.
- New ideas live as **AFAuth Protocol Proposals (AFAPs)** under [`spec/proposals/`](https://github.com/AFAuthHQ/spec/tree/main/proposals).

## Security

Please report vulnerabilities privately — see [`SECURITY.md`](./SECURITY.md). Do not open public issues for security-sensitive findings.

## License

- **Specification text** — [CC-BY-4.0](https://github.com/AFAuthHQ/spec/blob/main/LICENSE).
- **Code-shaped artefacts** (test vectors, JSON schemas, reference implementations) — [Apache-2.0](https://github.com/AFAuthHQ/spec/blob/main/LICENSE-CODE) for spec-repo code, [MIT](https://github.com/AFAuthHQ/cli/blob/main/LICENSE) for the CLI and SDKs.

Dual-licensing follows standard protocol-repo practice (IETF, OpenSSF, CNCF working groups).
