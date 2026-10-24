# Atlas Plan

Runs `atlas preflight` and `atlas config plan` (read-only) and writes both to the job summary. Fails the step on preflight errors and, by default, on drift between the committed config directory and the live instance.

```yaml
- uses: actions/checkout@v4
- uses: Atlas-Authorization/atlas-plan-action@v1
  with:
    api-url: https://api.atlasauth.net
    management-key: ${{ secrets.ATLAS_SECRET_KEY }}
    dir: ./atlas-config
```

Inputs: `api-url`, `management-key`, `dir`, `format`, `prune`, `fail-on-drift`, `preflight-fail-on` (`error`, `warning`, `none`), `cli-version`, `node-version`. Outputs: `drift`, `preflight-ok`. Pair it with `atlas-deploy` to apply on merge.
