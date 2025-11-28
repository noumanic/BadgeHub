# 🔐 Quick Setup: Add Vercel Token to GitHub

## Your Vercel Token
```
txs2C5iCAz3jF4WLKUrtlt0C
```

## ⚠️ IMPORTANT: Never commit this token to your repository!

## Steps to Add Token to GitHub Secrets

1. **Go to GitHub Secrets Page:**
   ```
   https://github.com/noumanic/BadgeHub/settings/secrets/actions
   ```

2. **Click "New repository secret"**

3. **Add the token:**
   - **Name**: `VERCEL_TOKEN`
   - **Value**: `txs2C5iCAz3jF4WLKUrtlt0C`
   - Click **"Add secret"**

## Still Need: Org ID & Project ID

You still need to get:
- **VERCEL_ORG_ID** - Your organization/team ID
- **VERCEL_PROJECT_ID** - Your project ID

### Quick Way to Get Them:

**Option 1: After First Deployment**
1. Deploy your project to Vercel (via dashboard)
2. Go to Project Settings → General
3. Find both IDs there

**Option 2: Using Vercel CLI**
```bash
npm install -g vercel
vercel login
vercel link
# Check .vercel/project.json
```

**Option 3: From Vercel Dashboard**
- Go to your project settings
- Both IDs are visible in the settings page

## Add Remaining Secrets

Once you have them, add to GitHub Secrets:
- `VERCEL_ORG_ID` = (your org ID)
- `VERCEL_PROJECT_ID` = (your project ID)

## ✅ Verify Setup

After adding all secrets, test by pushing:
```bash
git push origin main
```

Check GitHub Actions to see if deployment works!

