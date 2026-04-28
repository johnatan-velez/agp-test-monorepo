# AGP Test Monorepo

Test repository for verifying AGP (Agent P) fix for duplicate package names in PR titles.

## Structure

This monorepo has 3 packages with overlapping dependencies:

| Package | lodash | axios | eslint |
|---------|--------|-------|--------|
| @test/ui | ✓ | ✓ | ✓ |
| @test/admin | ✓ | ✓ | ✓ |
| @test/shared | ✓ | - | ✓ |

Expected AGP behavior:
- `lodash` should appear with "(3 workspaces)" annotation
- `axios` should appear with "(2 workspaces)" annotation
- `eslint` should appear with "(3 workspaces)" annotation

## Testing GUIDE-2036

This repo tests the fix for duplicate package names in PR title/body when the same dependency is updated across multiple workspaces.

Expected PR title format: `Update lodash (3 workspaces) + axios (2 workspaces) + eslint (3 workspaces)`

NOT: `Update lodash + lodash + lodash + axios + axios + eslint + eslint + eslint`
