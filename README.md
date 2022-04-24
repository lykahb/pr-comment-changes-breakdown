# PR Comment with Changes Breakdown

A breakdown tells reviewer at a glance what the changes are. Does the bulk of them come from the tests or documentation? Is a particular subsystem affected? This heads-up can make a reviewer more motivated, particularly for the larger PRs.

## Example usage

``` yaml
- uses: actions/checkout@v2
- uses: lykahb/paths-filter@v2
  id: filter
  with:
    stat: json
    filters: |
      src:
      - 'src/**/*.ts'
      - 'src/**/*.tsx'
      tests:
      - 'test/**'
      documentation:
      - '*.md'
    # or extract filters into a file:
    # filters: .github/group-files.yml
- uses: lykahb/pr-comment-changes-breakdown@v1
  with:
    diff-stat: ${{ steps.filter.outputs.stat }}
```

Also see [lykahb/paths-filter](https://github.com/lykahb/paths-filter) for the syntax of grouping files.
