# 🚀 Vercel Deployment Guide for BadgeHub

This guide will help you set up automatic deployment to Vercel whenever you push code to the main branch.

## 📋 Prerequisites

- A GitHub account with the BadgeHub repository
- A Vercel account (sign up at [vercel.com](https://vercel.com) if you don't have one)
- Your repository pushed to GitHub: `https://github.com/noumanic/BadgeHub`

## 🎯 Method 1: Vercel Native Integration (Recommended - Easiest)

This is the simplest method and requires no additional setup:

### Step 1: Connect Repository to Vercel

1. Go to [vercel.com](https://vercel.com) and sign in
2. Click **"Add New Project"** or **"Import Project"**
3. Select **"Import Git Repository"**
4. Choose **GitHub** as your Git provider
5. Authorize Vercel to access your GitHub account (if not already done)
6. Find and select **`noumanic/BadgeHub`** repository
7. Click **"Import"**

### Step 2: Configure Project Settings

1. **Project Name**: `badgehub` (or keep default)
2. **Framework Preset**: Select **"Other"** or **"Static Site"**
3. **Root Directory**: Leave as `./` (root)
4. **Build Command**: Leave empty (static site, no build needed)
5. **Output Directory**: Leave empty (serves from root)
6. **Install Command**: Leave empty

### Step 3: Environment Variables (Optional)

If you need any environment variables, add them in the Vercel dashboard.

### Step 4: Deploy

1. Click **"Deploy"**
2. Vercel will automatically:
   - Deploy your site
   - Set up automatic deployments on every push to `main`
   - Provide you with a deployment URL

### Step 5: Automatic Deployments

✅ **Done!** Now whenever you push to the `main` branch:
```bash
git push origin main
```

Vercel will automatically:
- Detect the push
- Deploy the new version
- Update your live site

---

## 🔧 Method 2: GitHub Actions + Vercel CLI (Advanced)

If you want more control or need to use GitHub Actions:

### Step 1: Get Vercel Tokens

1. Go to [vercel.com/account/tokens](https://vercel.com/account/tokens)
2. Create a new token
3. Copy the token (you'll need it)

### Step 2: Get Vercel Project IDs

1. Install Vercel CLI:
   ```bash
   npm install -g vercel
   ```

2. Login to Vercel:
   ```bash
   vercel login
   ```

3. Link your project:
   ```bash
   vercel link
   ```
   This will create a `.vercel` folder with your project IDs.

4. Get your Organization ID and Project ID from `.vercel/project.json`

### Step 3: Add GitHub Secrets

1. Go to your GitHub repository: `https://github.com/noumanic/BadgeHub`
2. Click **Settings** → **Secrets and variables** → **Actions**
3. Click **"New repository secret"**
4. Add these secrets:
   - `VERCEL_TOKEN` - Your Vercel token from Step 1
   - `VERCEL_ORG_ID` - Your organization ID
   - `VERCEL_PROJECT_ID` - Your project ID

### Step 4: Push to Main

The GitHub Actions workflow will automatically run on push to main:

```bash
git add .
git commit -m "Setup Vercel deployment"
git push origin main
```

---

## 📝 Configuration Files

### `vercel.json`
This file configures Vercel deployment settings:
- Build configuration
- Routing rules
- Security headers
- Cache control

### `.github/workflows/vercel-deploy.yml`
GitHub Actions workflow for automated deployment (Method 2 only)

### `.github/workflows/ci.yml`
CI workflow for linting and validation

---

## 🔍 Verify Deployment

After deployment, you can:

1. **Check Vercel Dashboard**: Go to [vercel.com/dashboard](https://vercel.com/dashboard)
2. **View Deployments**: See all your deployments and their status
3. **Check Logs**: View build and deployment logs
4. **Preview URLs**: Each deployment gets a unique URL

---

## 🌐 Custom Domain (Optional)

To add a custom domain:

1. Go to your project in Vercel dashboard
2. Click **Settings** → **Domains**
3. Add your custom domain
4. Follow DNS configuration instructions

---

## 🐛 Troubleshooting

### Deployment Fails

1. Check Vercel dashboard logs
2. Verify `vercel.json` is correct
3. Ensure all files are committed
4. Check GitHub Actions logs (if using Method 2)

### Changes Not Reflecting

1. Clear browser cache
2. Check deployment status in Vercel dashboard
3. Verify you pushed to `main` branch
4. Wait a few seconds for deployment to complete

### Build Errors

1. Check `vercel.json` configuration
2. Verify all file paths are correct
3. Check Vercel build logs for specific errors

---

## 📚 Useful Commands

### Manual Deployment (if needed)
```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel --prod
```

### Check Deployment Status
```bash
vercel ls
```

### View Logs
```bash
vercel logs
```

---

## ✅ Quick Start Checklist

- [ ] Create Vercel account
- [ ] Connect GitHub repository to Vercel
- [ ] Configure project settings
- [ ] Deploy initial version
- [ ] Test automatic deployment by pushing to main
- [ ] Verify site is live
- [ ] (Optional) Add custom domain

---

## 🎉 You're All Set!

Your BadgeHub site will now automatically deploy to Vercel whenever you push to the main branch!

**Repository**: `https://github.com/noumanic/BadgeHub`  
**Vercel Dashboard**: [vercel.com/dashboard](https://vercel.com/dashboard)

---

**Need Help?**
- [Vercel Documentation](https://vercel.com/docs)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Vercel Support](https://vercel.com/support)

