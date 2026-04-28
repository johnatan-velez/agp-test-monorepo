# AGP Test Monorepo

Test repository for verifying AGP (Agent P) fix for GUIDE-2036 - duplicate package names in PR titles.

## Structure

This repo simulates a multi-project setup where the same packages appear in multiple projects:

| Project | lodash | axios | eslint |
|---------|--------|-------|--------|
| `@test/ui` | ✓ (4.17.20) | ✓ (0.27.0) | ✓ (8.40.0) |
| `@test/admin` | ✓ (4.17.20) | ✓ (0.27.0) | ✓ (8.40.0) |
| `@test/shared` | ✓ (4.17.20) | - | ✓ (8.40.0) |

## Expected AGP behavior (GUIDE-2036 fix)

When AGP detects the same outdated package across multiple projects, it should:

1. **Deduplicate package names** in the PR title
2. **Show workspace count** for duplicate packages

### Expected PR title format:
```
Update lodash (3 workspaces) + axios (2 workspaces) + eslint (3 workspaces)
```

### NOT (old buggy behavior):
```
Update lodash + lodash + lodash + axios + axios + eslint + eslint + eslint
```
