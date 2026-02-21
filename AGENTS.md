# Agent Guidelines - Eric Glasser Website

AI assistant guidelines for this Hugo static site project.

## Project Overview

- **Type**: Hugo static site generator (resume/portfolio)
- **Theme**: hugo-resume by eddiewebb
- **Domain**: ericglasser.com
- **Output**: `public/` (GitHub Pages)

## Build Commands

```bash
# Development server with hot reload
hugo server -D

# Production build (minified)
hugo --minify

# Build with verbose output for debugging
hugo --verbose

# Clean build (remove public/ first)
rm -rf public/ && hugo --minify

# Update theme submodules
git submodule update --remote

# Initialize submodules (fresh clone)
git submodule update --init --recursive
```

## Validation & Testing

```bash
# Validate Hugo configuration
hugo config

# Check for build errors
hugo --minify 2>&1

# Validate JSON syntax (all data files)
for file in data/*.json; do echo "Checking $file"; python3 -m json.tool "$file" > /dev/null || echo "INVALID: $file"; done

# Validate single JSON file
python3 -m json.tool data/experience.json > /dev/null && echo "Valid JSON"

# Check TOML syntax
cat config.toml | grep -E '^[[:space:]]*([a-zA-Z_][a-zA-Z0-9_]*[[:space:]]*=|[[:space:]]*\[|\])' > /dev/null && echo "TOML appears valid"
```

## Code Style Guidelines

### TOML (config.toml)
- Use 4-space indentation
- Group related params under `[params]` sections
- Use lowercase with underscores for keys: `show_skills`
- Quote all string values consistently
- Order: base settings → markup → params → outputs → taxonomies

### JSON (data files)
- Use 4-space indentation
- Always use double quotes for keys and strings
- Trailing commas: NOT allowed (strict JSON)
- Order arrays chronologically (newest first for experience)
- Validate with `python3 -m json.tool` before committing

### Markdown (content files)
- Use YAML frontmatter between `---` delimiters
- Required frontmatter: `title`, `date`
- Optional: `description`, `image`, `tags`, `sitemap`
- Use ATX-style headers (`# Header` not underlines)
- Line length: max 120 characters
- Use semantic line breaks (one sentence per line)

### File Naming
- Content: lowercase-with-hyphens.md
- Images: descriptive-lowercase.jpg/png
- Data files: lowercase.json
- No spaces or special characters in filenames

## Content Guidelines

### Writing Style
- Professional, first-person tone ("I am...", "I specialize...")
- Experience summaries: 2-4 sentences max
- Focus on outcomes and technologies used
- No buzzwords or exaggerated claims

### Data File Schemas

**data/experience.json:**
```json
{
  "role": "Job Title",
  "company": "Company Name", 
  "range": "Month Year - Month Year",
  "summary": "2-4 sentence description"
}
```

**data/skills.json:**
```json
{
  "grouping": "Category Name",
  "skills": ["Skill 1", {"name": "Skill 2", "link": "https://..."}]
}
```

**data/certifications.json:**
```json
{
  "name": "Cert Name",
  "description": "Full certification title",
  "badge": "https://images.credly.com/...",
  "proof": "https://www.credly.com/badges/..."
}
```

### Accessibility Requirements
- The site owner has a visual impairment
- All images MUST have alt text
- Use semantic HTML when customizing layouts
- Ensure WCAG 2.1 AA color contrast
- Test with screen readers when making UI changes

## Common Tasks

**Add work experience:**
Edit `data/experience.json`, add new entry at top (chronological order)

**Add certification:**
Edit `data/certifications.json`, include Credly badge and proof URLs

**Toggle sections:**
Edit `config.toml` boolean flags: `showSkills`, `showExperience`, etc.

**Update theme:**
```bash
git submodule update --remote themes/hugo-resume
```

## Error Handling

**Build fails:**
1. Check JSON syntax in data files
2. Verify TOML syntax in config.toml
3. Ensure all required frontmatter fields present
4. Check theme submodule is initialized

**Changes not appearing:**
1. Verify section is enabled in config.toml
2. Restart `hugo server` (stop and restart)
3. Check for cached content in `public/`
4. Verify file is in correct location

**Theme issues:**
1. Ensure submodules initialized: `git submodule update --init --recursive`
2. Check Hugo version compatibility (requires 0.62+)
3. Review theme documentation: https://github.com/eddiewebb/hugo-resume

## External Rules

No Cursor rules (.cursor/rules/ or .cursorrules) found.
No Copilot instructions (.github/copilot-instructions.md) found.

## Project Structure

```
├── config.toml          # Site configuration
├── data/                # JSON data files
│   ├── experience.json  # Work history
│   ├── skills.json      # Technical skills
│   ├── education.json   # Education
│   └── certifications.json
├── content/             # Markdown content
│   ├── _index.md        # Homepage bio
│   └── projects/        # Project pages
├── static/              # Static assets
│   └── images/          # Photos, badges
├── layouts/             # Custom layouts (override theme)
└── themes/              # Git submodules
    └── hugo-resume/     # Active theme
```