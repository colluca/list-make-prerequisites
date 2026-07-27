# list-make-prerequisites

A GitHub Action that lists all prerequisites of a Makefile target (optionally
recursively), and computes a combined hash of their contents. Uses the
[pymakeutils](https://github.com/colluca/pymakeutils) `list-make-prerequisites`
CLI under the hood.

## Usage

```yaml
- uses: colluca/list-make-prerequisites@v1.1.0
  id: prereqs
  with:
    target: my-target
    flags: --recursive
- run: |
    echo "${{ steps.prereqs.outputs.prerequisites }}"
    echo "${{ steps.prereqs.outputs.hash }}"
```

## Inputs

| Name                | Description                                          | Required | Default |
| ------------------- | ----------------------------------------------------- | -------- | ------- |
| `target`            | Target to list prerequisites for                      | yes      |         |
| `working-directory`  | Working directory to run Make in                       | no       | `.`     |
| `flags`              | Additional flags to pass to `list-make-prerequisites`  | no       | `''`    |
| `pymakeutils-version` | Version of the `pymakeutils` PyPI package to install  | no       | latest  |

## Outputs

| Name            | Description                              |
| --------------- | ----------------------------------------- |
| `hash`          | Hash of all prerequisite file contents    |
| `prerequisites` | Space-separated list of prerequisite files |
