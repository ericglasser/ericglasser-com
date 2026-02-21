# Eric Glasser - Personal Website

This is the source code for [ericglasser.com](https://ericglasser.com), a personal resume and portfolio website built with Hugo.

## Tech Stack

- **Static Site Generator**: [Hugo](https://gohugo.io/)
- **Theme**: [hugo-resume](https://github.com/eddiewebb/hugo-resume) (submodule)
- **Syntax Highlighting**: Pygments with Monokai theme
- **Hosting**: GitHub Pages
- **Domain**: ericglasser.com

## Project Structure

```
ericglasser-com/
├── archetypes/          # Content templates
├── content/             # Website content (markdown)
│   ├── _index.md        # Homepage content
│   ├── search.md        # Search page
│   ├── projects/        # Project portfolios
│   │   ├── contributions/   # Open source contributions
│   │   └── creations/       # Personal projects
│   └── publications/    # Publications and talks
├── data/                # Structured data (JSON)
│   ├── boards.json          # Board positions (disabled)
│   ├── certifications.json  # AWS certifications
│   ├── education.json       # Education history
│   ├── experience.json      # Work experience
│   └── skills.json          # Technical skills
├── layouts/             # Custom layouts (overrides theme)
├── resources/           # Generated resources
├── static/              # Static assets (images, files)
├── themes/              # Hugo themes (submodules)
│   ├── coder/               # Alternate theme
│   └── hugo-resume/         # Active theme
├── config.toml          # Hugo configuration
└── README.md           # This file
```

## Key Files

- **`config.toml`**: Site configuration, personal info, social links, enabled sections
- **`content/_index.md`**: Homepage bio and introduction
- **`data/experience.json`**: Work history (12 positions)
- **`data/skills.json`**: Technical skills grouped by category
- **`data/education.json`**: Education background
- **`data/certifications.json`**: AWS professional certifications

## Local Development

### Prerequisites

- Hugo (extended version recommended)
- Git

### Running Locally

```bash
# Clone with submodules
git clone --recursive https://github.com/ericglasser/ericglasser.github.io.git
cd ericglasser.github.io

# Or if already cloned, initialize submodules
git submodule update --init --recursive

# Start development server
hugo server -D

# Build for production
hugo --minify
```

The site will be available at `http://localhost:1313`

### Content Management

**Enable/Disable Sections:**
Edit `config.toml` and toggle these flags:
- `showSkills`
- `showExperience` 
- `showEducation`
- `showCertifications`
- `showProjects`
- `showPublications`

**Update Experience:**
Edit `data/experience.json` - each entry has:
```json
{
  "role": "Job Title",
  "company": "Company Name",
  "range": "Start Date - End Date",
  "summary": "Description of responsibilities and achievements"
}
```

**Update Skills:**
Edit `data/skills.json` - skills are grouped by category with optional links.

**Update Certifications:**
Edit `data/certifications.json` - includes badge images and Credly proof links.

## Deployment

This site is automatically deployed to GitHub Pages. The production build outputs to the `public/` directory.

## Theme Submodules

This repo uses Git submodules for themes:

```bash
# Update theme submodules
git submodule update --remote

# Or update specific theme
git submodule update --remote themes/hugo-resume
```

## Current Sections Enabled

- ✅ Experience (12 positions)
- ✅ Skills (4 categories)
- ✅ Education (Vanderbilt University)
- ✅ Certifications (3 AWS certifications)
- ❌ Projects (data exists, disabled in config)
- ❌ Publications (data exists, disabled in config)
- ❌ Boards (data exists, disabled in config)

## Contact

- Email: eric@ericglasser.com
- LinkedIn: https://www.linkedin.com/in/ericglasser/
- GitHub: https://github.com/ericglasser/
- Stack Overflow: https://stackoverflow.com/users/2063495/ericglasser

---

Built with ❤️ using Hugo