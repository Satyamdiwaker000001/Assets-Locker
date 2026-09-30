# Assets Locker Architecture

## Purpose

Assets Locker is an evolving personal repository for frontend design resources and engineering knowledge. It supports discovery, evaluation, retrieval, and reuse across projects without binding the catalog to one framework.

## Information architecture

Resources are grouped by their primary purpose:

- **Design & Visual Assets:** references and media used to shape the visual experience.
- **UI & Design Systems:** reusable interaction patterns, components, and consistency guidance.
- **Frontend Engineering:** knowledge used to build, validate, ship, and maintain interfaces.

A resource should have one primary category. Use tags for cross-cutting concerns instead of duplicating records.

## Repository responsibilities

| Location | Responsibility |
|---|---|
| `catalog/` | Human-readable, categorized resource indexes |
| `docs/` | Architecture, taxonomy, lifecycle, and reuse guidance |
| `schema/` | Machine-readable metadata contract |
| `templates/` | Copy-ready resource entry |
| `projects/` | Project-oriented resource selection guidance |

## Resource record

Each resource should capture its name, canonical URL, primary category, type, tags, purpose, use case, applicable stack, project fit, license and attribution notes, status, review date, usage, and limitations.

See `schema/resource.schema.json` for the structured contract and `templates/resource-template.md` for the human-readable record.

## Retrieval model

Start with category files and descriptive tags. Keep records short enough to scan. If the catalog grows substantially, introduce structured data and generate a searchable index rather than adding a database prematurely.

## Constraints

- Keep the top-level catalog framework-agnostic.
- Keep project-specific notes in `projects/`.
- Do not bundle third-party assets by default.
- Verify current license and attribution terms at the point of use.
- Avoid duplicate dependencies and redundant entries.

## Evolution path

1. V1 — curated Markdown catalog, schema, conventions, and project mapping.
2. V2 — validated structured records and generated search index.
3. V3 — optional local searchable UI if scale justifies it.
4. V4 — optional automated link and metadata checks.

Introduce automation only when it reduces real maintenance effort.
