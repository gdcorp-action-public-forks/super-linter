# GitHub Super-Linter Slim Image Action

The **GitHub Super-Linter** maintains `two` major images:

- `gdcorp-action-public-forks/super-linter:7cf9265a98d5b34a7cef84ef48402e71edb5bde5`
- `gdcorp-action-public-forks/super-linter/slim:7cf9265a98d5b34a7cef84ef48402e71edb5bde5`

In order to help users pull this image more naturally, the `action.yml` in this directory can help users pull the `slim image`.

## Slim Image

The slim `gdcorp-action-public-forks/super-linter:slim-gdcorp-4.41` comes with all supported linters but removes the following:

- `rust` linters
- `dotenv` linters
- `armttk` linters
- `pwsh` linters
- `c#` linters

By removing these linters, we were able to bring the image size down by `2gb` and drastically speed up the build and download time.
The behavior will be the same for non-supported languages, and will skip languages at run time.
Example usage:

```yml
################################
# Run Linter against code base #
################################
- name: Lint Code Base
  uses: gdcorp-action-public-forks/super-linter/slim@7cf9265a98d5b34a7cef84ef48402e71edb5bde5
  env:
    VALIDATE_ALL_CODEBASE: false
    DEFAULT_BRANCH: main
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
