# GitHub Repository Setup for Iron House Gym

## Option 1: Create New Repository (Recommended)

### Step 1: Create New GitHub Repository
1. Go to [github.com](https://github.com)
2. Click **"New repository"**
3. **Repository name:** `iron-house-gym`
4. **Description:** `Complete fitness platform with 9 pages`
5. **Public** (so AI can access it)
6. **DON'T** check "Add a README file"
7. **DON'T** check "Add .gitignore" 
8. **DON'T** check "Choose a license"
9. Click **"Create repository"**

### Step 2: Push to New Repository
```bash
cd "d:\gym-portfolio"
git remote add origin https://github.com/itsnaman30/iron-house-gym.git
git push -u origin main
```

## Option 2: Force Push to Existing Repository (If you want to use CrowdCover)

### WARNING: This will overwrite the existing repository!
```bash
cd "d:\gym-portfolio"
git push -u origin main --force
```

## Option 3: Create Empty Repository and Push

### Step 1: Delete existing remote
```bash
git remote remove origin
```

### Step 2: Create new empty repository on GitHub
- Name: `iron-house-gym`
- Make it completely empty (no README, no .gitignore)

### Step 3: Push to new repository
```bash
git remote add origin https://github.com/itsnaman30/iron-house-gym.git
git push -u origin main
```

## Recommended: Option 1
Create a new repository called `iron-house-gym` for your fitness platform!
