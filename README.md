# yamlfmt-action

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/yk-lab/yamlfmt-action?style=for-the-badge)](https://github.com/yk-lab/yamlfmt-action/releases)
[![GitHub license](https://img.shields.io/github/license/yk-lab/yamlfmt-action?style=for-the-badge)](https://github.com/yk-lab/yamlfmt-action?tab=MIT-1-ov-file#readme)
[![GitHub stars](https://img.shields.io/github/stars/yk-lab/yamlfmt-action?style=for-the-badge)](https://github.com/yk-lab/yamlfmt-action/stargazers)
[![GitHub watchers](https://img.shields.io/github/watchers/yk-lab/yamlfmt-action?style=for-the-badge)](https://github.com/yk-lab/yamlfmt-action/watchers)

English | [日本語](README.ja.md)

Automatically format YAML files using `yamlfmt` in your GitHub Actions workflows. This action helps maintain consistent code style, making reviews and debugging easier.

## TL;DR

```yaml
name: YAML Formatting

on:
  push:
    branches:
      - main
  pull_request:
    types: [opened, synchronize, reopened]
  workflow_dispatch:

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: yamllint
        uses: reviewdog/action-yamllint@v1
        with:
          github_token: ${{ secrets.github_token }}
          fail_on_error: true
      - name: yamlfmt
        uses: yk-lab/yamlfmt-action@v1
```

## Features

- **Automatic Formatting**: Uses `yamlfmt` to standardize the formatting of YAML files.
- **Easy Integration**: Add a few lines to your existing workflows to get started.
- **Customizable Options**: Configure `yamlfmt` options to suit your project's needs.
- **Fast and Lightweight**: Designed for speed and efficiency.

## Table of Contents

- [Usage](#usage)
- [Options](#options)
- [FAQ](#faq)
- [Contributing](#contributing)
- [License](#license)
- [Related Links](#related-links)

## Usage

Add `yk-lab/yamlfmt-action` as a step in your workflow:

```yaml
name: YAML Formatting

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  format:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run yamlfmt
        uses: yk-lab/yamlfmt-action@v1
```

## Options

The action supports the following input parameters:

- `version`: Version of `yamlfmt` to use (default: `latest`, e.g., `v0.13.0`)
- `path`: Path to the YAML file or directory to format
- `dstar`: Enable double-star expansion
- `exclude`: Exclude files matching the specified pattern
- `gitignore_excludes`: Exclude files matching patterns specified in `.gitignore`
- `gitignore_path`: Path to the `.gitignore` file
- `extensions`: List of file extensions to format
- `formatter`: Set the formatter to use

### Example of Using Parameters

```yaml
- name: Run yamlfmt with options
  uses: yk-lab/yamlfmt-action@v1
  with:
    path: '.github/workflows'
```

## FAQ

### Q1. Can I use a configuration file for `yamlfmt`?

A1. Yes, you can include a configuration file like `.yamlfmt` in your repository to customize `yamlfmt` behavior.

### Q2. Can I exclude specific files or directories?

A2. You can specify exclude patterns using `yamlfmt` options. Refer to the [yamlfmt documentation](https://github.com/google/yamlfmt) for details.

## Contributing

Contributions are welcome! Feel free to open an issue or submit a pull request.

**Steps to Contribute:**

1. Fork the repository.
2. Create a new branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a pull request.

## License

This project is licensed under the [MIT License](LICENSE).

## Related Links

- [yamlfmt Repository](https://github.com/google/yamlfmt)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Other GitHub Actions](https://github.com/marketplace?type=actions)
