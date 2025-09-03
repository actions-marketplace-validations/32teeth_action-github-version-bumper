# GitHub Version Bumper Action

The **GitHub Version Bumper** is a GitHub Action that automatically increments your project's version number based on commit messages or workflow triggers. It streamlines version management, making it easier to automate releases and maintain semantic versioning.

## Features

- **Automatic Version Bumping:** Increments major, minor, or patch versions according to commit messages or configuration.
- **Semantic Versioning:** Follows [SemVer](https://semver.org/) standards.
- **Customizable:** Supports configuration for version file location and bumping rules.
- **Easy Integration:** Designed to fit seamlessly into your existing GitHub Actions workflows.

## Usage

Add the following to your workflow file (e.g., `.github/workflows/release.yml`):

```yaml
on:
  push:
    branches:
      - main

jobs:
  version-bump:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Bump version
        id: bumper
        uses: your-username/action-github-version-bumper@v1
        with:
          version_file: 'package.json' # or your version file
          bump: 'auto' # options: auto, major, minor, patch
      - name: Output new version
        run: echo "New version: ${{ steps.bumper.outputs.version }}"
```

## Inputs

| Name         | Description                                | Default      |
| ------------ | ------------------------------------------ | ------------ |
| version_file | Path to the version file                   | package.json |
| bump         | Version bump type (auto/major/minor/patch) | auto         |

## Outputs

| Name    | Description           |
| ------- | --------------------- |
| version | The new version value |

## Example

After a commit with `feat: add new feature`, the action will bump the minor version and output the new version number.

## License

MIT

---

Automate your versioning and streamline your release process with **GitHub Version Bumper**!
