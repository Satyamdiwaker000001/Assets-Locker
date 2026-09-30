# Assets Locker

A curated, reusable **Frontend Developer Knowledge & Asset Repository** for discovering, evaluating, organizing, and reusing design resources and engineering references.

**Workflow:** Discover → Save → Organize → Reuse

Assets Locker is more than a bookmark list. It brings together visual assets, UI patterns, design systems, and engineering references that can be reused across projects.

## Repository structure

```text
Assets-Locker/
├── README.md
├── CONTRIBUTING.md
├── catalog/
│   ├── design-inspiration.md
│   ├── icons-logos.md
│   ├── illustrations-imagery.md
│   ├── backgrounds-patterns.md
│   ├── typography-colors.md
│   ├── animation-3d.md
│   ├── ui-components.md
│   ├── design-systems.md
│   ├── responsive-patterns.md
│   ├── forms-ui-states.md
│   ├── data-visualization.md
│   └── frontend-engineering.md
├── docs/
│   ├── ARCHITECTURE.md
│   ├── TAXONOMY.md
│   ├── LIFECYCLE.md
│   └── REUSE-GUIDE.md
├── schema/
│   └── resource.schema.json
├── templates/
│   └── resource-template.md
└── projects/
    └── project-mapping.md
```

## Resource categories

### Design & Visual Assets
Design inspiration, icons and logos, illustrations, photos and mockups, backgrounds and patterns, typography and colors, animation and 3D.

### UI & Design Systems
UI component libraries, design systems, responsive patterns, forms and UI states, data visualization.

### Frontend Engineering
Frontend architecture, React and TypeScript, accessibility, testing, performance, security, CI/CD and deployment, documentation.

## Add a resource

1. Choose one primary category in `catalog/`.
2. Check for duplicates.
3. Copy `templates/resource-template.md`.
4. Include purpose, use case, applicable stack, project fit, and license notes.
5. Use `to-review` until the resource has actually been evaluated.
6. Record where it was used when applying it to a project.

## Resource status

- `to-review` — discovered, not yet evaluated
- `verified` — relevance and available terms reviewed; not a legal guarantee
- `used` — applied in a project
- `archived` — obsolete or no longer relevant

## Principles

- Curate for usefulness, not volume.
- Treat inspiration as a reference, not a design to copy wholesale.
- Do not assume free access grants commercial-use or redistribution rights.
- Verify current license and attribution terms at the source.
- Do not bundle third-party files without permission.
- Understand, adapt, and test code rather than blindly copying it.
- Keep descriptions factual and concise.

## Starter resources

The category files contain an initial shortlist. Starter entries are marked `to-review`; their current features, relevance, and licensing terms have not been independently verified in this repository.

## Evolution path

- **V1:** Markdown catalog, schema, templates, and conventions.
- **V2:** Validated structured records and a generated search index.
- **V3:** Optional local searchable interface.
- **V4:** Optional automated link and metadata checks.

See [CONTRIBUTING.md](CONTRIBUTING.md) for catalog conventions.
