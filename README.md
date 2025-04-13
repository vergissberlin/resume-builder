# resume-builder

Builds a resume from Markdown File in your repository.

## Usage

1. Create a Markdown file in your repository with the following format:

```markdown
# Resume

## Name

[…]
````

2. Add the following to your GitHub Actions workflow:

```yaml
name: Deploy Resume CINO

on:
  push:
    tags:
      - '*'
  workflow_dispatch:

jobs:
  call-builder:
    uses: vergissberlin/resume-builder/.github/workflows/build-resume.yml@main
    with:
      filename: YOURNAME
      formats: '["pdf", "epub"]'
      tag_name: ${{ github.ref_name }}
    secrets:
      GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

3. Push a tag to your repository to trigger the workflow.
4. The resume will be built and uploaded as an artifact to the workflow run.
5. Download the artifact and use it as needed.
