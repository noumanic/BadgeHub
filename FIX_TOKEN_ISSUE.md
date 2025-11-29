# 🔧 Fix Invalid Token Error

## Current Issue
The Vercel token in GitHub secrets is invalid or not updated.

## ✅ Step-by-Step Fix

### Step 1: Verify Token in GitHub Secrets

1. **Go to Secrets Page:**
   - https://github.com/noumanic/BadgeHub/settings/secrets/actions

2. **Check VERCEL_TOKEN:**
   - Find `VERCEL_TOKEN` in the list
   - Click on it to view (you won't see the value, but you can update it)

### Step 2: Create a New Vercel Token

1. **Go to Vercel Tokens Page:**
   - https://vercel.com/account/tokens

2. **Delete Old Token (Optional):**
   - If you see the old token listed, you can delete it
   - Click on it → Delete

3. **Create New Token:**
   - Click **"Create Token"** button
   - **Name**: `GitHub Actions Deployment` (or any name)
   - **Expiration**: Choose **"No expiration"** (recommended for CI/CD)
   - Click **"Create Token"**
   - ⚠️ **COPY THE TOKEN IMMEDIATELY** - You won't see it again!

### Step 3: Update Token in GitHub

1. **Go back to GitHub Secrets:**
   - https://github.com/noumanic/BadgeHub/settings/secrets/actions

2. **Update VERCEL_TOKEN:**
   - Click on `VERCEL_TOKEN`
   - Click **"Update"** button
   - Paste your **new token** (the one you just created)
   - Click **"Update secret"**

### Step 4: Verify All Secrets

Make sure all 3 secrets exist:
- ✅ `VERCEL_TOKEN` = (your new token)
- ✅ `VERCEL_ORG_ID` = `team_nTChTnFEANqGEKAYBUwrS00A`
- ✅ `VERCEL_PROJECT_ID` = `prj_O2x3dZ12QiroXFf4lkDF2EpLLCuZ`

### Step 5: Re-run Workflow

1. **Go to Actions:**
   - https://github.com/noumanic/BadgeHub/actions

2. **Re-run Workflow:**
   - Click on the most recent failed workflow
   - Click **"Re-run all jobs"** (top right)

---

## 🔍 Troubleshooting

### If token still doesn't work:

1. **Check Token Permissions:**
   - Make sure the token has access to your team/organization
   - The token should have full access to deploy projects

2. **Verify Token Format:**
   - Vercel tokens usually start with letters/numbers
   - No spaces before or after
   - Should be around 20-30 characters

3. **Check Team/Org Access:**
   - Make sure your Vercel account has access to:
     - Team: `team_nTChTnFEANqGEKAYBUwrS00A`
     - Project: `prj_O2x3dZ12QiroXFf4lkDF2EpLLCuZ`

4. **Try Creating Token from Different Location:**
   - Sometimes tokens created from different accounts/teams don't work
   - Make sure you're logged into the correct Vercel account

---

## 📝 Quick Checklist

- [ ] Go to https://vercel.com/account/tokens
- [ ] Create new token with "No expiration"
- [ ] Copy token immediately
- [ ] Go to https://github.com/noumanic/BadgeHub/settings/secrets/actions
- [ ] Update `VERCEL_TOKEN` with new token
- [ ] Verify all 3 secrets exist
- [ ] Re-run workflow at https://github.com/noumanic/BadgeHub/actions

---

## 🎯 Expected Result

After updating the token and re-running:
- ✅ Workflow should show "Retrieving project…" (not error)
- ✅ Should proceed to deployment
- ✅ Should show "Deployment successful!" message

---

**Important:** Make sure you copy the token immediately after creating it. If you lose it, you'll need to create a new one.

