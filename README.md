# glab-groups-openai

Thin GitHub Actions wrapper for the OpenAI GitHub organization mirror.

## Scope

- Loads `gh-actions-cfg/glab-groups-openai`
- Calls the reusable workflow in `glab-groups-shared@mcr/main`
- Uses the BWS target PAT secret `GL_PAT_GROUP_OPENAI_SVC`
- Uses the shared GitHub App secrets `GH_ORG_READ_APP_ID`,
  `GH_ORG_READ_APP_INSTALL_ID`, and `GH_ORG_READ_APP_PEM` for GitHub
  organization discovery and clone auth
- Mirrors the current public `github.com/openai` repositories into `openai/*`
  beneath `glab-forks`
- Runs deterministic mirror batch shards with five jobs max in parallel
- Schedules at minute 5 of hours 1 and 13 UTC
- Publishes discovery, plan, report, CSV, JSON, and Parquet artifacts for each run

## Validation

```sh
python3 -m unittest discover -s tests
```
