# GitHub Deployment Tracking Test

Test repository for exploring [`bobheadxi/deployments`](https://github.com/bobheadxi/deployments) GitHub Action behavior across different deployment events.

## Workflows

| Workflow | Trigger | What it tests |
|---|---|---|
| `deploy-production.yml` | Push to `main` | Full lifecycle: `start` → deploy → `finish` (success/failure) |
| `deploy-staging.yml` | Push to `staging` | Staging deployment with `override: true` |
| `deploy-preview.yml` | Pull request opened/synced | PR preview environment (`pr-<number>`) |
| `cleanup-preview.yml` | Pull request closed | `deactivate-env` to shut down PR preview |
| `deploy-manual.yml` | `workflow_dispatch` | Manual deployment with selectable environment and simulated outcome |

## How to test

1. **Production deploy** -- push a commit to `main`
2. **Staging deploy** -- create and push to a `staging` branch
3. **Preview deploy** -- open a pull request
4. **Preview cleanup** -- close/merge the pull request
5. **Manual deploy** -- go to Actions > "Manual Deployment" > Run workflow, pick an environment and outcome
6. **Failure scenario** -- use the manual workflow with `outcome: failure`

Check the **Environments** section in the repo sidebar and individual commit/PR deployment statuses to see the results.
