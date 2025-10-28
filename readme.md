# ur2nlp Lab Website - Contributor Guide

This guide is for lab members who want to add or update their information on the lab website.

## Quick Links

- **Live site:** https://ur2nlp.github.io
- **Technical documentation:** See `jekyll_readme.md` for how the site works

## What You Can Update

- Your bio and photo in the People section
- Lab projects you're working on
- Publications

All content is stored in simple YAML files in the `_data/` folder.

---

## How to Add/Update Your Information

### One-Time Setup

1. **Get added as a collaborator**
   - Ask the PI to add you to the repository with write access

2. **Clone the repository**
   ```bash
   git clone https://github.com/ur2nlp/ur2nlp.github.io.git
   cd ur2nlp.github.io
   ```

### Every Time You Make Changes

#### Step 1: Create a Branch

Always work on a new branch, not directly on `main`:

```bash
# Make sure you're on main and it's up to date
git checkout main
git pull

# Create a new branch with a descriptive name
git checkout -b update-my-info
```

Good branch names:
- `add-jane-bio`
- `update-project-description`
- `fix-typo-in-publication`

#### Step 2: Edit the Appropriate YAML File

All website content lives in the `_data/` folder. Edit the file that matches what you want to change:

**Adding yourself to the People section:**

Edit `_data/people.yml` and add your information under the `members:` section:

```yaml
members:
  - name: "Your Name"
    role: "PhD Student"  # or "Postdoc", "MS Student", "Undergrad", etc.
    interests: "Brief description of your research interests"
    website: "https://yourwebsite.com"  # optional
```

**Adding a project:**

Edit `_data/projects.yml`:

```yaml
- title: "Project Name"
  description: "Brief description of what the project is about"
  tags:
    - "multilingual NLP"
    - "low-resource"
```

**Adding a publication:**

Edit `_data/publications.yml`:

```yaml
- title: "Paper Title"
  authors: "Author 1, Author 2, Author 3"
  venue: "Conference or Journal Name"
  year: 2024
  paper_url: "https://arxiv.org/..."  # optional
  code_url: "https://github.com/..."  # optional
```

#### Step 3: Test Your Changes (Optional but Recommended)

If you have Jekyll installed locally, you can preview your changes:

```bash
jekyll serve
# Visit http://localhost:4000 in your browser
```

If you don't have Jekyll, that's fine—just skip this step and let the PR review catch any issues.

#### Step 4: Commit Your Changes

```bash
# See what files you changed
git status

# Add the files you changed
git add _data/people.yml  # or whichever file you edited

# Commit with a clear message
git commit -m "Add Jane Doe to lab members"
```

Good commit messages:
- "Add my bio to People section"
- "Update publication list with ACL 2024 paper"
- "Fix typo in project description"

#### Step 5: Push Your Branch

```bash
git push origin update-my-info
```

(Replace `update-my-info` with whatever you named your branch)

#### Step 6: Create a Pull Request

1. Go to https://github.com/ur2nlp/ur2nlp.github.io
2. You'll see a yellow banner saying "Your recently pushed branch" with a button **"Compare & pull request"** → Click it
3. Fill in the PR description:
   - Title: Short description (e.g., "Add Jane Doe to lab members")
   - Comment: Any additional context (optional)
4. Click **"Create pull request"**

The PI will review your changes and merge them. Once merged, the website updates automatically within a minute or two.

---

## Tips and Troubleshooting

### YAML Formatting

- **Indentation matters!** Use spaces, not tabs
- Each list item starts with a dash `-`
- Strings with special characters should be in quotes: `"Title: A Study"`
- Be consistent with spacing (look at existing entries as examples)

### Testing YAML Syntax

If you're not sure if your YAML is valid, you can test it at https://www.yamllint.com/

### Common Mistakes

**Missing quotes around URLs:**
```yaml
website: https://example.com  # Might cause issues
website: "https://example.com"  # Better
```

**Wrong indentation:**
```yaml
members:
- name: "Jane"  # Too far left - needs to be indented
  role: "PhD Student"
```

Should be:
```yaml
members:
  - name: "Jane"
    role: "PhD Student"
```

### I Made a Mistake in My Branch

No problem! You can keep making commits:

```bash
# Make your fixes
git add _data/people.yml
git commit -m "Fix typo in my bio"
git push origin update-my-info
```

The PR automatically updates with your new commits.

### My Branch is Behind Main

If someone else merged changes while you were working:

```bash
git checkout main
git pull
git checkout your-branch-name
git merge main
```

Resolve any conflicts, then push again.

---

## Getting Help

- **Technical issues with Jekyll:** See `jekyll_readme.md`
- **Git questions:** Plenty of Git tutorials online, or ask a labmate
- **Website content questions:** Contact the PI

## For Maintainers

If you're the PI or maintaining the site, see `jekyll_readme.md` for:
- How Jekyll works
- Local development setup
- Deploying to GitHub Pages
- Design decisions and CSS documentation
