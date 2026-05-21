# Snyk

## What It Is & What It's Used For

Snyk is a developer-first security platform that scans application code, open-source dependencies, container images, and Infrastructure-as-Code (IaC) configurations for known security vulnerabilities and licensing issues.

## Why It's Needed

Modern software stacks rely heavily on open-source packages such as npm, Composer, and Go modules. Snyk flags vulnerabilities nested deep inside indirect dependency trees before hazardous code reaches the build.

## How To Set It Up

Authenticate the CLI tool locally:

```bash
npm install -g snyk
snyk auth
```

Run an on-demand test in your code repository directory:

```bash
snyk test
```

Integrate Snyk into a GitHub Actions workflow such as `.github/workflows/security.yml`:

```yaml
- name: Run Snyk to check for vulnerabilities
  uses: snyk/actions/node@master
  env:
    SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
```

## Best Use Case

Gating production deployment branches. If a developer attempts to merge an open-source package with a high severity CVSS score of `>= 8.0`, Snyk automatically fails the build.

## Alternatives

- GitHub Native Dependency Review
- SonarQube
- Mend, formerly WhiteSource
