# TruffleHog

## What It Is & What It's Used For

TruffleHog is a specialized scanning engine designed to find leaked secrets, passwords, high-privilege keys, API tokens, and database connection strings hidden inside code repositories and commit histories.

## Why It's Needed

Accidentally pushing an unencrypted AWS root key or OpenAI API string to a public or private git branch can expose production infrastructure within seconds to automated scrapers. TruffleHog deep-scans individual git commit layers to catch secrets before they leak.

## How To Set It Up

Run an on-demand local scanning pass:

```bash
trufflehog git file://. --only-verified
```

Set up an automated check inside a continuous integration workflow:

```yaml
- name: TruffleHog OSS Secret Scan
  uses: trufflesecurity/trufflehog@main
  with:
    path: ./
    base: ${{ github.event.repository.default_branch }}
    head: HEAD
    extra_args: --only-verified
```

## Best Use Case

Pre-commit hooks and repository validation loops. The `--only-verified` option actively tests found tokens against target vendor APIs, such as AWS or Stripe, to verify whether a key is live and reduce false positives.

## Alternatives

- GitGuardian
- Gitleaks
- SecretScanner
