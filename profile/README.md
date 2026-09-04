# Agent Enrollment Protocol

The Agent Enrollment Protocol (AEP) enables Agents to establish an identity and credential
relationship with Services. It defines Service discovery, enrollment, lifecycle status,
session-credential grants, revocation, and authentication of protected resources.

AEP is an open protocol with public specifications, schemas, examples, test vectors, conformance
artifacts, and software development kits. It lets Services enroll Agents without coupling either
party to one identity host, session-credential format, or application framework.

## How AEP works

1. An Agent retrieves a Service's public Inspect document from `/.well-known/aep` to discover its
   commands, identity methods, requested claims, and credential options.
2. The Agent proves control of a supported identity and invokes Enroll with the claims it can
   provide.
3. The Agent uses Status to query the enrollment relationship and any outstanding requirements.
4. When supported, the Agent invokes Grant to obtain a scoped session credential for later Service
   requests.
5. The Agent invokes Revoke to invalidate an issued session credential.

Authenticated AEP commands use signed client assertions rooted in the Agent's enrolled identity.
Session credentials are optional and let a Service reuse authentication mechanisms such as API
keys, OAuth Bearer tokens, or HTTP Basic credentials.

## Protocol composition

AEP provides agentic enrollment: how an Agent establishes an identity and credential relationship
with a Service. It composes with the Offering Discovery Protocol (ODP) for agentic discovery and
with MPP or x402 for agentic payments.

These layers can be used independently, but together they provide a complete agentic commerce flow:
an Agent discovers an Offering, enrolls when the Service requires an identity or credential, and
pays through the payment protocol accepted by the Action endpoint.

## Start here

| Goal                                 | Resource                                                                                                         |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| Learn the protocol                   | [AEP documentation](https://www.aep.foundation/)                                                                 |
| Read the Internet-Draft              | [AEP Internet-Draft](https://datatracker.ietf.org/doc/draft-kavian-agent-enrollment-protocol/)                   |
| Build an Agent, Service, or Platform | [AEP software development kits](#repositories)                                                                   |
| Compare SDK support                  | [Compatibility, releases, and conformance](https://github.com/aep-foundation/aep-specs/blob/main/SDK_SUPPORT.md) |
| Run end-to-end examples              | [Runnable examples](https://github.com/aep-foundation/aep-node/tree/main/examples)                               |
| Use AEP from an Agent or terminal    | [InFlow CLI](https://www.inflowcli.ai/)                                                                          |
| Discuss protocol design              | [`aep-specs` Discussions](https://github.com/aep-foundation/aep-specs/discussions)                               |

## Repositories

| Repository                                                   | Purpose                                                          |
| ------------------------------------------------------------ | ---------------------------------------------------------------- |
| [`aep-specs`](https://github.com/aep-foundation/aep-specs)   | Specifications, schemas, examples, test vectors, and conformance |
| [`aep-node`](https://github.com/aep-foundation/aep-node)     | Node.js software development kit and reference implementation    |
| [`aep-go`](https://github.com/aep-foundation/aep-go)         | Go software development kit                                      |
| [`aep-java`](https://github.com/aep-foundation/aep-java)     | Java software development kit                                    |
| [`aep-python`](https://github.com/aep-foundation/aep-python) | Python software development kit                                  |
| [`aep-rust`](https://github.com/aep-foundation/aep-rust)     | Rust software development kit                                    |

Protocol proposals and wire-format discussions belong in `aep-specs`. Implementation bugs and
language-specific integration questions belong in the corresponding software development kit
repository.
