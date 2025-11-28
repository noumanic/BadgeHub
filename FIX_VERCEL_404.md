# 🔧 Fix Vercel 404: DEPLOYMENT_NOT_FOUND Error

This error means the project doesn't exist on Vercel yet. Here's how to fix it:

## ✅ Solution: Deploy Project First via Vercel Dashboard

### Step 1: Create Project on Vercel

1. **Go to Vercel Dashboard:**
   - Visit [vercel.com](https://vercel.com)
   - Sign in to your account

2. **Import Your Repository:**
   - Click **"Add New Project"** or **"Import Project"**
   - Select **"Import Git Repository"**
   - Choose **GitHub**
   - Find and select **`noumanic/BadgeHub`**
   - Click **"Import"**

3. **Configure Project:**
   - **Project Name**: `badge-hub` (or keep default)
   - **Framework Preset**: Select **"Other"** or **"Static Site"**
   - **Root Directory**: `./` (leave as default)
   - **Build Command**: (leave empty - no build needed)
   - **Output Directory**: (leave empty - serves from root)
   - **Install Command**: (leave empty)

4. **Deploy:**
   - Click **"Deploy"**
   - Wait for deployment to complete
   - Your site will be live!

### Step 2: Get Your Project IDs

After the first deployment:

1. **Go to Project Settings:**
   - Click on your project in Vercel dashboard
   - Click **"Settings"** tab
   - Go to **"General"** section

2. **Copy the IDs:**
   - **Organization ID**: Found in the settings (starts with `team_` or `user_`)
   - **Project ID**: Found in the settings (starts with `prj_`)

### Step 3: Add Secrets to GitHub

1. **Go to GitHub Secrets:**
   ```
   https://github.com/noumanic/BadgeHub/settings/secrets/actions
   ```

2. **Add All Three Secrets:**
   - `VERCEL_TOKEN` = `txs2C5iCAz3jF4WLKUrtlt0C`
   - `VERCEL_ORG_ID` = (from Step 2)
   - `VERCEL_PROJECT_ID` = (from Step 2)

### Step 4: Test Automatic Deployment

1. **Make a small change:**
   ```bash
   # Edit any file
   git add .
   git commit -m "test: verify auto-deployment"
   git push origin main
   ```

2. **Check GitHub Actions:**
   - Go to: `https://github.com/noumanic/BadgeHub/actions`
   - You should see the workflow running

3. **Check Vercel:**
   - Go to your Vercel dashboard
   - You should see a new deployment

## 🎯 Alternative: Use Vercel Native Integration (Easier)

If you use Vercel's native integration (Step 1 above), you **don't need GitHub Actions at all**:

- ✅ Automatic deployments on every push
- ✅ No secrets needed
- ✅ No GitHub Actions workflow needed
- ✅ Everything handled automatically

You can delete the `.github/workflows/vercel-deploy.yml` file if you use native integration.

## 🐛 Troubleshooting

### Still Getting 404?

1. **Check if project exists:**
   - Go to Vercel dashboard
   - Verify `badge-hub` project is listed

2. **Verify project name:**
   - Make sure it matches in `vercel.json` (should be `badge-hub`)

3. **Check deployment status:**
   - Go to project → Deployments tab
   - See if any deployments exist

4. **Re-deploy manually:**
   - In Vercel dashboard, click "Redeploy" on latest deployment

### Project Not Showing Up?

1. **Check repository connection:**
   - Go to Project Settings → Git
   - Verify GitHub repo is connected

2. **Check permissions:**
   - Make sure Vercel has access to your GitHub account
   - Re-authorize if needed

## ✅ Success Checklist

- [ ] Project deployed on Vercel dashboard
- [ ] Site is accessible via Vercel URL
- [ ] Got Organization ID from settings
- [ ] Got Project ID from settings
- [ ] Added all 3 secrets to GitHub
- [ ] Tested push to main branch
- [ ] GitHub Actions workflow runs successfully
- [ ] New deployment appears in Vercel

---

**Once the project exists on Vercel, the GitHub Actions workflow will work!**

