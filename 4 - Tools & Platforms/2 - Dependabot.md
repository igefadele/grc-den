# Dependabot

## What It Is & What It's Used For

Dependabot is an automated dependency management tool natively integrated into GitHub. It continuously checks package manifests for outdated or vulnerable dependencies.

## Why It's Needed

Staying on top of security patches across multiple codebases manually is time-consuming. Dependabot monitors upstream security advisories daily and actively fixes code by generating automated update pull requests.

## How To Set It Up

Create a configuration file at `.github/dependabot.yml`:

```yaml
version: 2
updates:
  - package-ecosystem: "npm" # Can change to composer, gomod, pip, etc.
    directory: "/"
    schedule:
      interval: "daily"
    open-pull-requests-limit: 5
```

## Best Use Case

Automated software ecosystem maintenance. Dependabot keeps platforms relying on high-velocity updates stable by isolating minor and patch security releases into organized pull requests.

## Alternatives

- Renovate Bot
- Greenkeeper
