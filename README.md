# carabiner-dev/verify action

Easily verify 🔴🟡🟢 AMPEL supply chain policies in CI.

## What this is

> [!NOTE]  
> This repository is a **thin forwarding wrapper** around the `ampel/verify`
> composite action that lives in
> [carabiner-dev/actions](https://github.com/carabiner-dev/actions/tree/main/ampel/verify).
>
> The implementation, tests, and changelog are maintained there. This repo
> exists so the action can be published as a single, root-level entry on the
> GitHub Actions Marketplace as the multi-action `carabiner-dev/actions`
> monorepo is not eligible for Marketplace listing because GitHub Marketplace
> only actions when their repository only hosts a single action.

Each release of `carabiner-dev/verify` mirrors the upstream tags on
`carabiner-dev/actions`. Dependabot watches that pin and opens an update PR
whenever a new version of the upstream action is tagged.

## Usage

```yaml
- uses: carabiner-dev/verify@v1.0.0
  with:
    policy: '.ampel/policy.yaml'
    subject: 'path/to/binary'
    collector: 'github'
```

The input contract is identical to the upstream
[`carabiner-dev/actions/ampel/verify`](https://github.com/carabiner-dev/actions/tree/main/ampel/verify)
action. See the upstream README for the full input table and additional
examples.

### Quick reference

| Input | Required | Default | Description |
| --- | --- | --- | --- |
| `policy` | Yes | — | Path or URI to the security policy to evaluate against |
| `subject` | Yes | — | Path to a file or hash (`algo:value`) to use as verification subject |
| `collector` | Yes | — | Collector to load to read attestations (e.g. `jsonl`, `github`, `oci`) |
| `attest` | No | `true` | Attest the policy evaluation results |
| `attest-format` | No | `ampel` | Format of the results attestation |
| `results-path` | No | `ampel.intoto.json` | Path to store the results attestation |
| `push-attestation` | No | `false` | Push the attestation to the GitHub attestations store |
| `attestation` | No | `""` | Comma-separated list of attestations to ingest |
| `signer` | No | `""` | Comma-separated list of expected signer identity slugs |
| `key` | No | `""` | Path to a key file to use for verification |
| `keydata` | No | `""` | Raw key material to use for verification |
| `context` | No | `""` | Contextual values to pass to the policy |
| `fail` | No | `true` | Fail the workflow if the policy fails |

## Issues and Suggestions

To open an issue, please
[file it in the Carabiner Actions monorepo](https://github.com/carabiner-dev/actions/issues).

## License

This thin wrapper is released by Carabiner Systems, Inc under the Apache 2.0 
license. See [LICENSE](./LICENSE) for details.
