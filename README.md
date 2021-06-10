# Action: Pull Request Labeler
The GitHub action which sets the labels on Pull Requests by their content

# Usage
In order to use it:
1) Add the Github action script to your repository and call the PR Labeler there. Example of the .yml file here:
```yml
name: Update PRs with labels
on:
  pull_request:
    types: [opened, edited, synchronize]
jobs:
  set-pr-labels:
    runs-on: ubuntu-latest
    steps:
      - name: Set the labels
        uses: 3ShapeInternal/PR-Labeler2-Action@v0.3
        with:
          configuration-path: .github/pr-labeler.json # optional, .github/pr-labeler.json is the default value
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
 ```
 2) Add the configuration file in JSON format somewhere next to your script (e.g. `.github/pr-labeler.json` which is a default location). Example of the .json file here:
 ```json
 [
  [
    {
    "label": "MyProject",
    "color": "27408b",
    "path":  ["Cool/Features", "Applications/MyProject"]
    },
    {
    "label": "AnotherProject",
    "color": "BFD4F2",
    "path":  ["secretfilenames"]
    }
  ],
  [
    {
    "label": "Size: S :white_medium_small_square:",
    "color": "000000",
    "size": 100
    },
    {
    "label": "Size: M :white_medium_square:",
    "color": "000000",
    "size": 500
    },
    {
    "label": "Size: L :white_large_square:",
    "color": "000000",
    "size": 1000
    }
  ]
]
```

That's all! Commit these changes to your repository, and perform the commits.
