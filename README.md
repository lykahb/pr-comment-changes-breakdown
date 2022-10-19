# PR Comment with Changes Breakdown

A breakdown tells reviewer at a glance what the changes are. Does the bulk of them come from the tests or documentation? Is a particular subsystem affected? This heads-up can make a reviewer more motivated, particularly for the larger PRs.

## Example usage

``` yaml
- uses: actions/checkout@v3
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
With that workflow, a comment for a PR may look like this:

![diff](https://user-images.githubusercontent.com/852150/164955141-4567981d-201b-4c3a-ac20-76060823de2f.png)

The breakdown only lists the groups that have changed files. And if some files do not fall into any group, they are categorized as "other".

Also see [lykahb/paths-filter](https://github.com/lykahb/paths-filter) for the syntax of grouping files.
