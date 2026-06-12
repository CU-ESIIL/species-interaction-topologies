# Species interaction network topologies

Climate change and human disturbance are rapidly transforming plant communities. Yet, we still struggle to recognize when and how ecological communities are reorganizing. This working group will create new ways to detect these hidden transformations by studying the networks of relationships that link species together. Instead of looking only at which plants are present or how much ground they cover, we focus on the web of connections that keep ecosystems functioning--and how these connections shift under stress. Around the world scientists have been collecting detailed records of plant communities for decades, but these rich datasets haven’t been used to understand the relationships among species. By combining decades of long-term vegetation data from drought, grazing, nutrient, and climate experiments we will ask: do similar environmental pressures trigger similar patterns of ecological reorganization?

## How this repository is organized

The repository has two connected layers. Top-level files configure the project and its automation. The `docs/` folder contains the website content. `mkdocs.yml` tells MkDocs how to turn that content into the public site. Analysis folders hold the working scientific materials that generate the results shown on the website.

```text
.
├── README.md              # Repository overview and setup notes
├── mkdocs.yml             # Website navigation, theme, plugins, and edit links
├── docs/                  # Markdown source for the public website
├── scripts/               # Build helpers and site health checks
├── templates/             # Reusable meeting-note templates
├── containers/            # Optional runtime and environment setup
└── other working folders  # Add data, notebooks, scripts, workflows, outputs, or figures here as the group's science grows
```

Use these rules of thumb when deciding where to put something:

- Top-level files and folders are for project configuration, automation, contribution guidance, licensing, environment setup, and repo-wide metadata.
- `docs/` is for public website pages and assets. Markdown files here become website pages through MkDocs.
- `mkdocs.yml` controls how the website is rendered, including navigation, theme settings, plugins, and GitHub edit links.
- Scientific working materials belong in working folders such as data, notebooks, scripts, workflows, outputs, and figure directories.

## Common places to edit

- `docs/index.md` is the homepage for the public site.
- `docs/work-plan.md` tracks milestones, meetings, and outputs for the working group.
- `docs/how-this-group-works.md` holds collaboration norms, working group guides, and data and methods galleries.
- `docs/esiil-resources/team-trainings.md` and `docs/esiil-resources/code-of-conduct.md` are under ESIIL and Team Resources.
- `docs/community-care.md` is nested under ESIIL and Team Resources and links to ESIIL community care and team science resources.
- `docs/instructions/` contains practical working group instructions for GitHub, persistent storage, lifecycle phases, and landmarks.
- `docs/resources/` contains reusable resource guides such as the Cloud Triangle and Cite and Reuse guidance.
- `docs/assets/images/slots/` contains named image slots for the homepage and other shared visuals.
- `docs/assets/images/process/` contains folder-driven process galleries that render automatically on the site.

## Preview locally

```bash
pip install -r requirements.txt
python scripts/generate_image_slots.py
python scripts/site_health.py
mkdocs serve
```

## Build site

```bash
python scripts/generate_image_slots.py
python scripts/site_health.py
mkdocs build --strict --clean
```

## Swapping homepage images

The site uses semantic image slots so Working Group members do not need to edit Markdown links every time an image changes.

1. Open the relevant folder in `docs/assets/images/slots/`.
2. Delete the old image file.
3. Add one new `.png`, `.jpg`, `.jpeg`, `.webp`, or `.svg` file.
4. Run `python scripts/generate_image_slots.py`.
5. Commit the image change and the regenerated slot references.

If a slot folder contains multiple images, the generator uses the first image alphabetically and the site health report will warn you to clean it up. The cleanest workflow is still one image per slot folder.

## Using process galleries

Process galleries are folder-driven. Add files to a gallery folder, commit them, and the site updates automatically.

1. Open the relevant folder in `docs/assets/images/process/`.
2. Add images or supported deliverable files.
3. Optionally add a `captions.txt` file with lines like `filename.png | Caption text`.
4. Run `python scripts/generate_image_slots.py`.
5. Commit the new files and the regenerated gallery includes.

Supported image files:

- `.png`
- `.jpg`
- `.jpeg`
- `.webp`
- `.svg`

Supported linked deliverable files:

- `.pdf`
- `.html`
- `.csv`
- `.xlsx`
- `.docx`
- `.pptx`

## Site Health

The site generates a non-blocking health report during the build.

The report flags common issues such as missing files, placeholder links, outdated navigation, or incomplete template fields.

Warnings do not prevent the site from publishing. They are intended to help Working Group admins improve the site.

## GitHub Pages

This site is automatically built and deployed using GitHub Actions.

## TO DO

- [ ] Decide on how we want to use this repo
- [ ] Decide on roles
