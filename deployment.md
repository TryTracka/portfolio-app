# Deployment Notes

This app is deployed to Azure App Service with GitHub Actions.

## Azure App Service

- Web App name: `portfolio-personal`
- Runtime: `Node 22 LTS`
- OS: `Linux`
- Branch: `main`

## GitHub Actions

Create a GitHub Actions workflow in `.github/workflows/azure-webapp.yml`.
The workflow:

1. Installs dependencies with `npm ci`.
2. Builds the app with `npm run build`.
3. Removes dev dependencies with `npm prune --omit=dev`.
4. Deploys the repo to Azure App Service.

## Required Secret

Add this GitHub secret before the workflow can deploy:

- `AZURE_WEBAPP_PUBLISH_PROFILE`

You can download the publish profile from the Azure Web App overview page.

## Azure App Settings

Set these app settings in Azure:

- `OPENROUTER_API_KEY`
- `OPENROUTER_MODEL = openai/gpt-oss-20b:free`

## Startup

If Azure asks for a startup command, use:

```bash
npm start
```
