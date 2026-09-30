# Assets Locker

### Frontend Developer Knowledge & Asset Repository

A curated library of design resources, UI patterns, development tools, and engineering references for discovering, evaluating, organizing, and reusing resources across frontend projects.

[**Download Assets Locker (.zip)**](./Assets-Locker.zip)

**Discover → Save → Organize → Reuse**

---

## Overview

Assets Locker is more than a bookmark list. It organizes useful frontend resources with practical metadata so they can be reviewed, found, and reused in real projects.

## Repository Structure

```text
Assets-Locker/
├── README.md
├── Assets-Locker.zip
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

## Resource Categories

- **Design & Visual Assets:** Inspiration, icons, illustrations, imagery, backgrounds, typography, colors, animation, and 3D.
- **UI & Design Systems:** Components, design systems, responsive patterns, forms, UI states, and data visualization.
- **Frontend Engineering:** Architecture, React, TypeScript, accessibility, testing, performance, security, CI/CD, deployment, and documentation.

## Resource Metadata

Catalog entries use consistent information to make resources easier to evaluate and reuse:

- Name and official URL
- Category and purpose
- Use case, relevant stack, and project fit
- License and attribution notes
- Status, review date, and projects used in

The structure is supported by `schema/resource.schema.json` and `templates/resource-template.md`.

## Resource Lifecycle

`to-review` → `verified` → `used` → `archived`

- **to-review:** Added but not yet evaluated.
- **verified:** Relevance and available usage terms reviewed; not a legal guarantee.
- **used:** Applied in a project.
- **archived:** No longer relevant or maintained.

## Add a Resource

1. Choose a category in `catalog/` and check for duplicates.
2. Copy `templates/resource-template.md`.
3. Add the resource URL, purpose, use case, stack, project fit, and license notes.
4. Set its status to `to-review`.
5. Update its status after evaluation and record projects where it is used.

See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

## Principles

- Curate for usefulness, not volume.
- Use inspiration as a reference, not something to copy wholesale.
- Verify current licensing and attribution terms at the original source.
- Do not redistribute third-party assets without permission.
- Understand, adapt, and test code before reusing it.

## Documentation

- [Architecture](docs/ARCHITECTURE.md)
- [Taxonomy](docs/TAXONOMY.md)
- [Lifecycle](docs/LIFECYCLE.md)
- [Reuse Guide](docs/REUSE-GUIDE.md)
- [Project Mapping](projects/project-mapping.md)
- [Resource Template](templates/resource-template.md)
- [Contributing](CONTRIBUTING.md)

## Roadmap

- **V1:** Markdown catalog, schema, and templates.
- **V2:** Structured records, validation, and search index.
- **V3:** Optional searchable interface.
- **V4:** Optional link and metadata checks.

## License & Third-Party Resources

Third-party resources remain subject to their owners' licenses and terms. Inclusion in this repository does not grant permission to use or redistribute them. Verify the original terms before use.
