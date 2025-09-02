# Set Wrangler Name Action

A GitHub Action that automatically sets the `name` field in your `wrangler.json` file to match your repository name. This action modifies the file in-place without committing changes, allowing you to handle the commit yourself or use the modified file in subsequent workflow steps.

## Usage

Add this action to your workflow:

```yaml
name: Update Wrangler Config

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
  workflow_dispatch:

jobs:
  update-wrangler:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set Wrangler Name
        uses: nemolize/set-wrangler-name@v1

      # The wrangler.json file is now updated with your repository name
      # You can commit it yourself or use it in subsequent steps
```

## Inputs

| Input           | Description                    | Required | Default         |
| --------------- | ------------------------------ | -------- | --------------- |
| `wrangler-file` | Path to the wrangler.json file | No       | `wrangler.json` |

## Examples

### Custom wrangler.json location

```yaml
- name: Set Wrangler Name
  uses: nemolize/set-wrangler-name@v1
  with:
    wrangler-file: "config/wrangler.json"
```

## Requirements

- Your repository must have a `wrangler.json` file
- The runner must have `jq` installed (available by default on GitHub-hosted runners)

## License

MIT
