# UR2NLP Lab Website

University of Rochester Under-Resourced Natural Language Processing Lab
**Live at:** `https://ur2nlp.github.io/`

## What This Is: Minimal Jekyll

This site uses **Minimal Jekyll** - a hand-coded approach that uses Jekyll only for its core feature: turning structured data files into HTML. No fancy plugins, no complex build process, no abstraction you don't understand.

### The Core Idea

Instead of editing HTML every time a lab member joins, you edit a simple YAML data file:

```yaml
# _data/people.yml
members:
  - name: "Jane Doe"
    role: "PhD Student"
    interests: "Multilingual morphology"
    website: "https://janedoe.com"
```

Jekyll reads this file and generates the HTML cards automatically. That's it.

## File Structure

```
ur2nlp.github.io/
├── _config.yml          # Site settings (10 lines)
├── _data/               # Structured data (YAML files)
│   ├── people.yml       # Lab members
│   ├── projects.yml     # Research projects
│   └── publications.yml # Publications
├── index.html           # Main page (uses Liquid templates)
├── lab.css              # Custom styles
└── README.md            # This file
```

That's the entire site. No `_layouts/`, no `_includes/`, no Sass compilation, no Gemfile. Just data files and one HTML template.

## How to Add Content

### Adding a Lab Member

1. Edit `_data/people.yml`
2. Add a new entry under `members:`:

```yaml
members:
  - name: "Your Name"
    role: "PhD Student"
    interests: "Your research interests"
    website: "https://yoursite.com"  # optional
```

3. Commit and push. GitHub Pages rebuilds automatically.

### Adding a Project

Edit `_data/projects.yml`:

```yaml
- title: "Project Name"
  description: "What the project is about"
  tags:
    - "multilingual NLP"
    - "low-resource"
```

### Adding a Publication

Edit `_data/publications.yml`:

```yaml
- title: "Paper Title"
  authors: "Author 1, Author 2"
  venue: "Conference Name"
  year: 2024
  paper_url: "https://arxiv.org/..."  # optional
  code_url: "https://github.com/..."  # optional
```

## What Jekyll Actually Does

Jekyll uses **Liquid templating** to turn data into HTML. Here's what that looks like:

**In `_data/people.yml`:**
```yaml
pi:
  - name: "C.M. Downey"
    role: "Assistant Professor"
```

**In `index.html`:**
```liquid
{% for person in site.data.people.pi %}
  <h5>{{ person.name }}</h5>
  <p>{{ person.role }}</p>
{% endfor %}
```

**Jekyll generates:**
```html
<h5>C.M. Downey</h5>
<p>Assistant Professor</p>
```

It's just find-and-replace with loops. No magic.

### The Liquid Syntax You Need to Know

That's it. You've learned Liquid templating.

- `{{ variable }}` - Print a variable
- `{% for item in list %}` - Loop through a list
- `{% if condition %}` - Conditional logic
- `{% endif %}`, `{% endfor %}` - Close blocks

## Testing Locally

### One-time Setup

Install Jekyll (requires Ruby, which macOS has by default):

```bash
# Install Jekyll
gem install jekyll bundler

# That's it - no Gemfile needed for minimal Jekyll
```

### Running the Site

```bash
# From the repository directory
jekyll serve

# Opens at http://localhost:4000
```

Jekyll watches for changes and rebuilds automatically.

### Troubleshooting

If you get a "command not found" error:
```bash
# Add gem executables to your PATH
echo 'export PATH="$HOME/.gem/ruby/X.X.0/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

Replace `X.X.0` with your Ruby version (run `ruby -v` to check).

## How GitHub Pages Works

When you push to GitHub:

1. GitHub Pages sees `_config.yml` and knows it's a Jekyll site
2. It runs `jekyll build` automatically
3. The built site (in `_site/`) is deployed to `ur2nlp.github.io`
4. Takes about 30-60 seconds

**No GitHub Actions needed.** It's built into GitHub Pages.

## Customizing the Design

All visual styling is in `lab.css` - standard CSS, nothing fancy. The UR brand colors are documented at the top of the file.

Bootstrap 4.4.1 is loaded from CDN (same as the personal homepage).

## Why This Approach?

### What You Get
- **Structured data workflow**: Lab members edit YAML, not HTML
- **No manual HTML duplication**: Add one YAML entry, get a formatted card
- **Automatic deployment**: Push to GitHub, site updates
- **Understandable**: You can read every line and know what it does

### What You Don't Get (Intentionally)
- Complex layouts system
- Sass/SCSS compilation
- Blog post functionality
- Fancy plugins
- Collection-based content management
- Build dependencies (Gemfile, etc.)

This is **Minimal Jekyll**: just enough abstraction to make content management sustainable, not so much that you can't understand what's happening.

## Lab Member Workflow

1. Fork the repository
2. Edit your entry in `_data/people.yml`
3. Test locally with `jekyll serve` (optional)
4. Submit a pull request
5. PI reviews and merges

Simple, transparent, version-controlled.

## Philosophy

From the project context:

> **Minimalist approach**: No unnecessary dependencies or build tools
> **Understandable code**: All code should be readable and maintainable
> **No magic**: Avoid frameworks or libraries that obscure what's happening

This Jekyll setup honors that philosophy. It adds exactly one abstraction (data → template → HTML) and nothing more.
