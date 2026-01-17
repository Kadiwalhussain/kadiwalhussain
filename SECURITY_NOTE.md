# ⚠️ Security Notice

## Important: Token Security

If you've shared a GitHub Personal Access Token publicly:

1. **IMMEDIATELY REVOKE IT** at: https://github.com/settings/tokens
2. Create a new token if needed
3. **NEVER** commit tokens to your repository
4. **NEVER** share tokens in public messages

## For GitHub Actions

Your workflow should work with the default `GITHUB_TOKEN` that GitHub provides automatically. You typically don't need a personal access token.

## If You Need a Personal Token

1. Create it at: https://github.com/settings/tokens
2. Add it as a **Secret** in your repository:
   - Go to: Settings → Secrets and variables → Actions
   - Click "New repository secret"
   - Name it (e.g., `GH_TOKEN`)
   - Paste the token value
   - Click "Add secret"

3. Use it in workflow like this (if needed):
```yaml
- name: Push to GitHub
  env:
    GITHUB_TOKEN: ${{ secrets.GH_TOKEN }}
  run: |
    git push https://${{ secrets.GH_TOKEN }}@github.com/${{ github.repository }}.git
```

## Current Workflow Status

Your current workflow uses the default `GITHUB_TOKEN` which should work fine. Just make sure:
- Repository Settings → Actions → General
- Workflow permissions: "Read and write permissions" is enabled

---

**Remember: Keep your tokens secret! 🔒**
