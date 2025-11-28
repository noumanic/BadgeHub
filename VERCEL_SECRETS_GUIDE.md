# 🔐 How to Get Vercel Token, Org ID, and Project ID

This guide will walk you through getting all the secrets needed for GitHub Actions deployment.

## 📋 Step-by-Step Guide

### Step 1: Get Your Vercel Token

1. Go to [vercel.com/account/tokens](https://vercel.com/account/tokens)
2. Sign in to your Vercel account
3. Click **"Create Token"** button
4. Give it a name (e.g., "BadgeHub GitHub Actions")
5. Set expiration (or leave as "No expiration" for permanent token)
6. Click **"Create"**
7. **IMPORTANT**: Copy the token immediately - you won't be able to see it again!
   - It will look like: `xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

### Step 2: Get Your Organization ID

**Method 1: From Vercel Dashboard**
1. Go to [vercel.com/dashboard](https://vercel.com/dashboard)
2. Click on your profile/team name in the top right
3. The Organization ID is in the URL or you can find it in the API section

**Method 2: Using Vercel CLI**
```bash
# Install Vercel CLI (if not already installed)
npm install -g vercel

# Login to Vercel
vercel login

# Link your project
vercel link

# This will create a .vercel folder with project.json
# Open .vercel/project.json and find "orgId"
```

**Method 3: From API**
1. Go to [vercel.com/account/tokens](https://vercel.com/account/tokens)
2. Use your token with the API:
```bash
curl -H "Authorization: Bearer YOUR_TOKEN" https://api.vercel.com/v2/teams
```

### Step 3: Get Your Project ID

**Method 1: After First Deployment**
1. Deploy your project to Vercel (using the dashboard)
2. Go to your project settings
3. The Project ID is shown in the project settings page

**Method 2: Using Vercel CLI**
```bash
# After running 'vercel link', check:
cat .vercel/project.json

# You'll see something like:
# {
#   "orgId": "team_xxxxxxxxxxxxx",
#   "projectId": "prj_xxxxxxxxxxxxx"
# }
```

**Method 3: From Project Settings**
1. Go to your project in Vercel dashboard
2. Click **Settings** → **General**
3. Scroll down to find **Project ID**

### Step 4: Add Secrets to GitHub

1. Go to your GitHub repository: `https://github.com/noumanic/BadgeHub`
2. Click **Settings** (top menu)
3. Click **Secrets and variables** → **Actions** (left sidebar)
4. Click **"New repository secret"** button
5. Add each secret one by one:

   **Secret 1: VERCEL_TOKEN**
   - Name: `VERCEL_TOKEN`
   - Value: Your Vercel token from Step 1
   - Click **"Add secret"**

   **Secret 2: VERCEL_ORG_ID**
   - Name: `VERCEL_ORG_ID`
   - Value: Your organization ID from Step 2
   - Click **"Add secret"**

   **Secret 3: VERCEL_PROJECT_ID**
   - Name: `VERCEL_PROJECT_ID`
   - Value: Your project ID from Step 3
   - Click **"Add secret"**

## 🎯 Quick Method (Easiest)

If you want the easiest way, just use Vercel's native integration instead:

1. Go to [vercel.com](https://vercel.com)
2. Click **"Add New Project"**
3. Import your GitHub repository
4. Vercel will automatically:
   - Set up webhooks
   - Deploy on every push
   - Handle everything automatically

**No secrets needed!** This is the recommended method for most users.

## 🔍 Verify Your Secrets

After adding secrets, you can verify they're set:

1. Go to: `https://github.com/noumanic/BadgeHub/settings/secrets/actions`
2. You should see all three secrets listed:
   - ✅ VERCEL_TOKEN
   - ✅ VERCEL_ORG_ID
   - ✅ VERCEL_PROJECT_ID

## 🧪 Test the Setup

1. Make a small change to your project
2. Commit and push:
   ```bash
   git add .
   git commit -m "test: verify Vercel deployment"
   git push origin main
   ```
3. Go to GitHub Actions tab: `https://github.com/noumanic/BadgeHub/actions`
4. You should see the workflow running
5. Check Vercel dashboard to see the deployment

## 📝 Example Values Format

Your values will look like this:

- **VERCEL_TOKEN**: `xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx` (long string)
- **VERCEL_ORG_ID**: `team_xxxxxxxxxxxxx` or `user_xxxxxxxxxxxxx`
- **VERCEL_PROJECT_ID**: `prj_xxxxxxxxxxxxx`

## ⚠️ Important Notes

1. **Never commit tokens to your repository** - always use GitHub Secrets
2. **Keep your token secure** - don't share it publicly
3. **If token expires**, create a new one and update the secret
4. **Organization ID** - If you're using a personal account, it starts with `user_`. For teams, it starts with `team_`

## 🆘 Troubleshooting

### "Invalid token" error
- Make sure you copied the entire token
- Check if token has expired
- Create a new token and update the secret

### "Organization not found" error
- Verify the Org ID is correct
- Make sure you have access to that organization
- Check if you're using `team_` vs `user_` prefix correctly

### "Project not found" error
- Make sure the project exists in Vercel
- Verify the Project ID is correct
- Ensure you have access to the project

## 🎉 You're Done!

Once all secrets are added, your GitHub Actions workflow will automatically deploy to Vercel on every push to main!

---

**Need Help?**
- [Vercel Documentation](https://vercel.com/docs)
- [GitHub Secrets Documentation](https://docs.github.com/en/actions/security-guides/encrypted-secrets)

