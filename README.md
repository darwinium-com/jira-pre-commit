# jira-pre-commit

A [`pre-commit`](https://pre-commit.com) hook to check commit messages for
[Conventional Commits](https://conventionalcommits.org) formatting.

## Usage

Make sure `pre-commit` is [installed](https://pre-commit.com#install).

Create a blank configuration file at the root of your repo, if needed:

```console
touch .pre-commit-config.yaml
```

Add a new repo entry to your configuration file:

```yaml
repos:

# - repo: ...

  - repo: https://github.com/erskaggs/jira-pre-commit
    rev: <git sha or tag>
    hooks:
      - id: jira-pre-commit
```

Install the `pre-commit` script:

```console
pre-commit install --hook-type commit-msg
```

Make a (normal) commit :x::

```console
$ git commit -m "add a new feature"

[INFO] Initializing environment for ....
Conventional Commit......................................................Failed
- hook id: conventional-pre-commit
- duration: 0.07s
- exit code: 1

[Commit message] add a new feature

Your commit message does not follow Conventional Commits formatting
https://www.conventionalcommits.org/

Conventional Commits start with one of the below types, followed by a colon,
followed by the commit message:

    build chore ci docs feat fix perf refactor revert style test

Example commit message adding a feature:

    feat: implement new API

Example commit message fixing an issue:

    fix: remove infinite loop

Optionally, include a scope in parentheses after the type for more context:

    fix(account): remove infinite loop
```

Make a (conventional) commit :heavy_check_mark::

```console
$ git commit -m "feat: add a new feature"

[INFO] Initializing environment for ....
Conventional Commit......................................................Passed
- hook id: conventional-pre-commit
- duration: 0.05s
```

## Versioning

Versioning generally follows [Semantic Versioning](https://semver.org/).

In addition to the strict version tag, we also maintain a "latest" tag for each
major version, e.g. `v1` always points to the latest `v1.x.x` tag.

## License

[Apache 2.0](LICENSE)

Inspired by matthorgan's [`pre-commit-conventional-commits`](https://github.com/matthorgan/pre-commit-conventional-commits).
