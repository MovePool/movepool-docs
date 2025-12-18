# GitBook Sync Setup (Best Practice)

MovePool uses a **docs-as-code** workflow so documentation can be reviewed like code.

## Recommended setup

1. Create a GitBook **Site** and **Space**.
2. In the Space, go to **Configure → GitHub Sync**.
3. Install the GitBook GitHub App (https://github.com/apps/gitbook-com) with access to your docs repository.
4. Select repository + branch.
5. Choose initial sync direction:
   - **GitHub → GitBook** (recommended if docs already exist in the repo)
   - **GitBook → GitHub** (if starting in GitBook from scratch)

## Repository configuration

This repo includes `.gitbook.yaml` at the repository root:

```yaml
root: ./docs/

structure:
  readme: README.md
  summary: SUMMARY.md
```

This tells GitBook to use:

- `docs/README.md` as the landing page
- `docs/SUMMARY.md` as the table of contents

## References

- GitBook Quickstart: https://gitbook.com/docs/getting-started/quickstart
- Enable GitHub Sync: https://gitbook.com/docs/getting-started/git-sync/enabling-github-sync
- Content configuration (`.gitbook.yaml`): https://gitbook.com/docs/getting-started/git-sync/content-configuration
