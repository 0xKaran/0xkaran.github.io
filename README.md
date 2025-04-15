# 🚀 Personal Portfolio with Chirpy Starter

This guide walks you through setting up a personal portfolio using the [Chirpy Starter](https://github.com/cotes2020/chirpy-starter) Jekyll theme. Follow these instructions to modify the repository, customize your site, and deploy it to GitHub Pages.

### Notes
> Don't run ```JEKYLL_ENV=production bundle exec jekyll b``` because it will create static HTML website in ```_sites``` folder instead just keep publishing ```.md``` files and let github build the changes.
{: .prompt-tip }

## 🎥 Video Tutorial

Watch the full tutorial on YouTube:

[![Watch the tutorial](https://img.youtube.com/vi/F8iOU1ci19Q/0.jpg)](https://youtu.be/F8iOU1ci19Q?si=3viR8oxF4gQo6cA_)

---

## 🛠️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/cotes2020/chirpy-starter
mv chirpy-starter portfolio
cd portfolio
sudo bundle           # Installs all required dependencies
bundle exec jekyll s  # Starts the local Jekyll server
```

Once the server is up and running, access your site locally at:
http://127.0.0.1:4000/

### Modify Your Site
Edit _config.yml to update your site’s global settings such as:

    Site title
    Tagline
    Author info
    Social links

### Set Up GitHub Pages

Remove Existing Git History (If Present)
```bash
rm -rf .git
```

### Create a New GitHub Repository

Create a new GitHub repository with no files (not even a README.md).
Repo name: <username>.github.io (replace <username> with your GitHub username)

Initialize Git and Connect to Your Repository
```bash
git init
git remote add origin https://github.com/0xKaran/0xkaran.github.io
git add .
git commit -m "Initial commit"
git push -u origin main
```

### Publish Changes
Check git status:

```bash
git status
```

Stage changes:

```bash
git add .
```

Commit changes:

```bash
git commit -m "any message"
```

Push changes to GitHub:

```bash
git push
```

Oneliner
```bash
git status; git add .; git commit -m "."; git push 
```

### Notes
- Wait for github build to see changes
- Don't run ```JEKYLL_ENV=production bundle exec jekyll b``` because it will create static HTML website in ```_sites``` folder instead just keep publishing ```.md``` files and let github build the changes.