# Dependency Maintenance

## Scope And Invariants

Use the patched Symfony 8.1 line because the reported YAML vulnerability has no patched 8.0 release. Preserve application code, authorization, external clients, database schema, migrations, deployment workflows and user data. Keep Composer advisory blocking enabled. The resolved framework requires PHP 8.4.1 or newer.

## Validation

PHP 8.4.27 and Composer 2.10.3 completed dependency installation and a zero-advisory audit. Composer application validation, PHP syntax checks, Twig lint and the full PHPUnit suite passed: 777 tests and 2,094 assertions, with no skips or incomplete tests. Test setup installed the existing import-map assets, used the documented runtime version and a private test database, and allowed 512 MB for the test process.

The first portable test attempt lacked import-map assets and exhausted the default 128 MB process limit. Its failed log is retained outside the repository. No test assertions changed.

The local Docker engine is unavailable. The portable checks cover the commands in `make check`. The hosted container build, health check and exact `make check` job remain required before merge. No image release or running deployment is claimed.

## Delivery Gates

Freeze the clean candidate, target tip and merge base outside the tree. Require fresh independent source review, exact-candidate GitHub review and the hosted container checks before normal merge. Preserve all original migrations and provider configuration.
