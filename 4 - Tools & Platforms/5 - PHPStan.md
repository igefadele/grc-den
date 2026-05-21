# PHPStan

## What It Is & What It's Used For

PHPStan is an advanced static analysis framework focused on the PHP ecosystem. It scans an application workspace to discover bugs, data structure mismatches, invalid method parameters, and hidden edge flaws.

## Why It's Needed

PHP's dynamic nature makes it easy for hidden runtime `TypeError` issues to pass unnoticed until they reach production. PHPStan enforces stronger typing expectations and scans execution paths to confirm functions receive the expected data profiles.

## How To Set It Up

Install PHPStan via Composer into development dependencies:

```bash
composer require --dev phpstan/phpstan
```

Create a base execution rules manifest named `phpstan.neon`:

```yaml
parameters:
    level: 8 # Scale rules from 0 (loose) to 9 (strict)
    paths:
        - app
        - core
```

Execute PHPStan through the standard CLI:

```bash
vendor/bin/phpstan analyze
```

## Best Use Case

Open-source framework stability and custom architecture refactoring. PHPStan verifies that type safety rules, object schemas, and internal core methods pass strict architectural constraints before code ships.

## Alternatives

- Psalm
- Phan
