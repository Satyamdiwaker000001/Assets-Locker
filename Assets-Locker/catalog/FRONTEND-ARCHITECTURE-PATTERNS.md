# Frontend Folder Architecture Patterns

A practical reference for choosing, structuring, and evolving frontend codebases. This guide covers common folder-organization patterns, their directory layouts, suitable project types, trade-offs, and selection criteria.

> **Important:** These patterns are not all mutually exclusive. A production application often combines them—for example, feature-based organization inside a domain-oriented application, or a monorepo containing several feature-based apps.

---

## 1. Layer-Based (Type-Based) Architecture

**Core idea:** Group files by their technical role or file type rather than by the business feature they support.

### Example structure

```text
src/
├── assets/
├── components/
│   ├── Button.tsx
│   ├── Modal.tsx
│   └── Navbar.tsx
├── pages/
│   ├── Home.tsx
│   ├── About.tsx
│   └── Contact.tsx
├── hooks/
│   ├── useAuth.ts
│   └── useDebounce.ts
├── services/
│   ├── api.ts
│   └── userService.ts
├── utils/
│   ├── formatDate.ts
│   └── validators.ts
├── types/
├── styles/
├── App.tsx
└── main.tsx
```

### How it works

Components live together in `components/`, hooks in `hooks/`, API calls in `services/`, and utility functions in `utils/`. A feature such as authentication may therefore have related files spread across several folders.

### Suitable for

- Small applications and prototypes
- Personal portfolios and simple marketing sites
- Learning projects where the codebase is still small
- CRUD applications with limited business logic

### Advantages

- Easy to understand and quick to establish
- Low initial setup and few organizational rules
- Common files are easy to locate by technical type

### Limitations

- Related feature code becomes scattered as the application grows
- Shared folders can become large and difficult to navigate
- Changes to one feature may require edits across many directories

**Use it when:** the application is small, feature boundaries are simple, and the team benefits from minimal structure.

---

## 2. Feature-Based Architecture

**Core idea:** Group code by the user-facing feature or capability it implements. Each feature keeps its own components, hooks, API logic, types, and tests close together.

### Example structure

```text
src/
├── app/
│   ├── router.tsx
│   ├── providers.tsx
│   └── store.ts
├── components/
│   └── ui/
│       ├── Button.tsx
│       ├── Input.tsx
│       └── Modal.tsx
├── features/
│   ├── auth/
│   │   ├── components/
│   │   │   ├── LoginForm.tsx
│   │   │   └── SignupForm.tsx
│   │   ├── hooks/
│   │   ├── services/
│   │   │   └── authApi.ts
│   │   ├── types/
│   │   ├── validation/
│   │   └── index.ts
│   ├── applications/
│   │   ├── components/
│   │   ├── hooks/
│   │   ├── services/
│   │   ├── types/
│   │   └── index.ts
│   └── analytics/
│       ├── components/
│       ├── hooks/
│       └── index.ts
├── shared/
│   ├── hooks/
│   ├── lib/
│   └── utils/
├── assets/
├── styles/
└── main.tsx
```

### How it works

Each feature owns the code specific to it. For example, `features/auth/` contains authentication forms and authentication API integration. Generic components such as `Button` and `Modal` remain in a shared UI area and should not depend on a specific feature.

### Suitable for

- Admin dashboards
- Job application trackers and job portals
- Project management tools
- LMS platforms
- Medium-sized SaaS applications
- React applications with distinct user workflows

### Advantages

- Related code stays together
- Features are easier to maintain, test, and extend
- Teams can work on separate features with fewer conflicts
- Features can sometimes be extracted or replaced more easily

### Limitations

- Teams need clear rules for what belongs in `shared/`
- Similar components may be duplicated if boundaries are poorly designed
- Cross-feature dependencies can become tangled without import conventions

**Use it when:** the application has identifiable capabilities and is expected to grow feature by feature.

---

## 3. Page-Based (Route-Based) Architecture

**Core idea:** Organize the application around pages or routes. A page directory represents the screens users navigate to.

### Example structure

```text
src/
├── pages/
│   ├── Home/
│   │   ├── HomePage.tsx
│   │   ├── components/
│   │   └── index.ts
│   ├── About/
│   │   ├── AboutPage.tsx
│   │   └── index.ts
│   ├── Contact/
│   │   ├── ContactPage.tsx
│   │   └── index.ts
│   └── Dashboard/
│       ├── DashboardPage.tsx
│       ├── components/
│       └── index.ts
├── components/
│   ├── Header.tsx
│   ├── Footer.tsx
│   └── ui/
├── layouts/
│   ├── PublicLayout.tsx
│   └── DashboardLayout.tsx
├── routes/
│   └── index.tsx
├── services/
├── hooks/
├── utils/
├── App.tsx
└── main.tsx
```

### How it works

Page-specific UI is placed with the page it supports. Shared navigation, layouts, and generic components live outside the page directories. This is a folder convention and can be used with routing libraries or frameworks that use file-based routing.

### Suitable for

- Portfolios
- Company and product websites
- Documentation sites
- Content-driven websites
- Small-to-medium applications whose main complexity is screen composition

### Advantages

- The relationship between routes and code is easy to see
- Page-level work is straightforward
- Page-specific components can stay near their page

### Limitations

- Business logic shared by several pages can become duplicated
- Large pages may turn into oversized directories
- A route is not always the same thing as a business feature

**Use it when:** the site is primarily organized around a set of distinct pages, and cross-page business logic is limited.

---

## 4. Atomic Design Architecture

**Core idea:** Build interfaces from small reusable elements and compose them into increasingly complex UI structures. Atomic Design is a component-design methodology; it is not, by itself, a complete application architecture.

### Example structure

```text
src/
├── components/
│   ├── atoms/
│   │   ├── Button/
│   │   ├── Input/
│   │   ├── Icon/
│   │   └── Label/
│   ├── molecules/
│   │   ├── SearchField/
│   │   └── FormField/
│   ├── organisms/
│   │   ├── Header/
│   │   ├── LoginForm/
│   │   └── DataTable/
│   ├── templates/
│   │   ├── AuthTemplate/
│   │   └── DashboardTemplate/
│   └── pages/
│       ├── LoginPage/
│       └── DashboardPage/
├── design-tokens/
│   ├── colors.ts
│   ├── spacing.ts
│   └── typography.ts
├── hooks/
├── services/
├── App.tsx
└── main.tsx
```

### How it works

- **Atoms:** Small UI primitives, such as buttons, labels, and icons.
- **Molecules:** Small combinations, such as a search field with an input and button.
- **Organisms:** Larger interface sections, such as a header, form, or data table.
- **Templates:** Page-level layouts that define content structure.
- **Pages:** Concrete screens populated with real content.

The exact boundaries vary by team. Components should be grouped by meaningful responsibility, not forced into a level just to follow the naming system.

### Suitable for

- Design systems
- Component libraries
- UI-heavy products with consistent visual patterns
- Multi-page products that need shared interface standards
- Teams with design tokens and reusable component requirements

### Advantages

- Encourages consistent and reusable UI
- Supports systematic component documentation
- Helps designers and developers discuss component composition
- Works well with visual testing and component showcases

### Limitations

- Can introduce unnecessary hierarchy for small projects
- Business logic and data ownership still need a separate organization strategy
- Not every component fits neatly into one atomic level

**Use it when:** reusable interface composition and design consistency are major goals. Combine it with feature-based or domain-based organization for application logic.

---

## 5. Domain-Based (Domain-Driven) Architecture

**Core idea:** Organize code around business domains and concepts, such as identity, billing, courses, orders, or inventory. The aim is to reflect the business language and boundaries in the codebase.

### Example structure

```text
src/
├── app/
│   ├── router.tsx
│   └── providers.tsx
├── domains/
│   ├── identity/
│   │   ├── components/
│   │   ├── model/
│   │   ├── api/
│   │   ├── hooks/
│   │   ├── types/
│   │   └── index.ts
│   ├── learning/
│   │   ├── courses/
│   │   │   ├── components/
│   │   │   ├── model/
│   │   │   ├── api/
│   │   │   └── index.ts
│   │   ├── enrollment/
│   │   └── assessments/
│   ├── commerce/
│   │   ├── orders/
│   │   ├── payments/
│   │   └── subscriptions/
│   └── reporting/
├── shared/
│   ├── ui/
│   ├── hooks/
│   ├── api/
│   └── utils/
├── layouts/
├── assets/
└── main.tsx
```

### How it works

The top-level domains represent meaningful business areas. Each domain can contain its own UI, state/model logic, API integration, and types. Domain boundaries should be based on business responsibility rather than simply mirroring backend database tables.

### Suitable for

- Banking and financial applications
- ERP and inventory platforms
- Healthcare administration systems
- Large LMS platforms
- Enterprise applications with complex business rules
- Products with several related business capabilities

### Advantages

- Aligns code organization with business concepts
- Helps isolate domain-specific rules
- Makes ownership and responsibility clearer
- Supports long-term evolution of complex applications

### Limitations

- Requires understanding of the business domain
- Initial design can be more involved
- Poorly chosen boundaries can cause excessive cross-domain dependencies
- Does not automatically provide backend-style Domain-Driven Design

**Use it when:** business rules and domain relationships are more complex than the UI screens themselves.

---

## 6. Feature-Sliced Design (FSD)

**Core idea:** Use standardized architectural layers and controlled dependency directions to organize a frontend application. Feature-Sliced Design provides conventions for separating application-wide concerns, pages, features, entities, and shared code.

### Example structure

```text
src/
├── app/
│   ├── providers/
│   ├── router/
│   ├── styles/
│   └── index.tsx
├── pages/
│   ├── home/
│   ├── sign-in/
│   └── application-list/
├── widgets/
│   ├── app-header/
│   ├── sidebar/
│   └── application-table/
├── features/
│   ├── sign-in/
│   ├── filter-applications/
│   ├── create-application/
│   └── update-status/
├── entities/
│   ├── user/
│   ├── application/
│   └── company/
└── shared/
    ├── api/
    ├── ui/
    ├── lib/
    ├── config/
    └── assets/
```

### How it works

Common FSD layers include:

- **app:** Global setup, providers, routing, and styles.
- **pages:** Route-level screens.
- **widgets:** Independent, substantial UI blocks composed from lower layers.
- **features:** User actions or capabilities that deliver business value.
- **entities:** Core business objects and their UI/model logic.
- **shared:** Generic, business-agnostic utilities, UI, and infrastructure.

The intended dependency direction is from higher-level layers toward lower-level layers. Lower layers should not import from higher layers. Segments within a slice are commonly organized by responsibility, such as `ui`, `model`, `api`, and `lib`. Public entry points help control imports.

### Suitable for

- Large React or other component-based frontend applications
- Growing SaaS products
- Complex dashboards with many independent capabilities
- Multi-team frontend codebases
- Products where consistent architectural boundaries are important

### Advantages

- Provides explicit conventions for organizing large codebases
- Helps limit uncontrolled dependencies
- Separates business entities, user actions, and page composition
- Supports independent development across teams

### Limitations

- Has a learning curve and more conventions to follow
- Can feel heavyweight for small projects
- Requires discipline to maintain correct layer boundaries
- Incorrect slicing can create excessive abstraction

**Use it when:** the application is large or expected to become large, and the team is prepared to follow architectural rules consistently.

---

## 7. Monorepo / Multi-App Architecture

**Core idea:** Keep multiple applications and shared packages in one repository. A monorepo is a repository strategy, not a specific way of organizing each app internally.

### Example structure

```text
frontend-platform/
├── apps/
│   ├── web/
│   │   ├── src/
│   │   └── package.json
│   ├── admin/
│   │   ├── src/
│   │   └── package.json
│   └── docs/
│       ├── src/
│       └── package.json
├── packages/
│   ├── ui/
│   ├── design-tokens/
│   ├── api-client/
│   ├── shared-utils/
│   └── eslint-config/
├── tooling/
├── package.json
├── pnpm-workspace.yaml
└── turbo.json
```

### How it works

Each app is independently runnable or buildable, while shared packages provide common UI, design tokens, API clients, or tooling. Workspace tools such as pnpm workspaces, Nx, or Turborepo can coordinate dependencies and tasks. Each app can use feature-based, domain-based, or another internal architecture.

### Suitable for

- Products with separate customer and admin applications
- Platforms sharing UI across web apps
- Organizations maintaining several related frontend products
- Design systems consumed by multiple applications
- Large teams needing shared tooling and packages

### Advantages

- Encourages reuse across applications
- Makes coordinated changes to shared code easier
- Centralizes tooling and standards
- Can simplify dependency and version alignment

### Limitations

- Requires workspace and build-tool knowledge
- Shared-package changes can affect several apps
- CI, dependency boundaries, and access rules may need additional setup
- Can add overhead when there is only one small application

**Use it when:** multiple applications genuinely need shared code or coordinated development. Avoid adopting a monorepo only because the product may grow someday.

---

## 8. Hybrid Architecture

**Core idea:** Combine patterns to meet the needs of a real application. Hybrid architecture is a practical approach rather than a single prescribed standard.

### Example structure: Feature + Domain + Shared UI

```text
src/
├── app/
│   ├── router/
│   ├── providers/
│   └── config/
├── domains/
│   ├── identity/
│   │   ├── model/
│   │   ├── api/
│   │   └── types/
│   ├── learning/
│   │   ├── courses/
│   │   ├── enrollment/
│   │   └── assessments/
│   └── billing/
├── features/
│   ├── sign-in/
│   │   ├── components/
│   │   ├── hooks/
│   │   └── index.ts
│   ├── enroll-course/
│   ├── submit-assessment/
│   └── manage-subscription/
├── widgets/
│   ├── app-header/
│   ├── course-overview/
│   └── analytics-panel/
├── pages/
│   ├── dashboard/
│   ├── course-details/
│   └── billing/
├── shared/
│   ├── ui/
│   ├── hooks/
│   ├── lib/
│   ├── api/
│   └── utils/
└── main.tsx
```

### How it works

A hybrid structure combines complementary ideas:

- Domain-based grouping establishes business boundaries.
- Feature-based grouping organizes user actions and capabilities.
- Shared UI or Atomic Design principles promote visual consistency.
- Route-based pages compose screens from features and widgets.
- Monorepo tooling can be added if multiple applications need shared packages.

The exact combination should be deliberate. Avoid creating multiple folders that represent the same responsibility or allowing unrestricted imports between them.

### Suitable for

- LMS platforms
- Enterprise SaaS
- ERP and inventory systems
- Multi-role platforms with complex workflows
- Products combining dashboards, user management, reporting, and transactions

### Advantages

- Can reflect both business structure and user workflows
- Flexible enough for complex product requirements
- Encourages reuse without forcing all code into one pattern
- Can evolve incrementally as complexity grows

### Limitations

- Requires clear boundaries and documented dependency rules
- Can become over-engineered if too many patterns are combined
- New developers may need guidance to understand where code belongs

**Use it when:** a product has several kinds of complexity—business domains, user workflows, shared UI, and multiple screens—and one organizational pattern alone is insufficient.

---

## Comparison at a Glance

| Architecture | Organizes primarily by | Typical scale | Common examples |
|---|---|---|---|
| Layer-Based / Type-Based | Technical file type | Small | Portfolio, prototype |
| Feature-Based | Product capability | Small to large | Dashboard, job portal |
| Page-Based / Route-Based | Screen or route | Small to medium | Marketing site, documentation |
| Atomic Design | UI composition level | Component-system focused | Design system, UI library |
| Domain-Based | Business domain | Medium to large | ERP, banking, LMS |
| Feature-Sliced Design | Standardized layers and slices | Medium to large | Complex SaaS, enterprise frontend |
| Monorepo / Multi-App | Applications and shared packages | Multi-app | Admin + customer apps |
| Hybrid | Deliberate combination | Medium to large | Enterprise SaaS, LMS |

*Scale is indicative, not a strict rule. Team size, domain complexity, release needs, and dependency boundaries matter as much as application size.*

## Choosing an Architecture

Use these questions to guide the decision:

1. **Is the application small and mostly static?** Start with layer-based or page-based organization.
2. **Does it have distinct user workflows?** Consider feature-based organization.
3. **Is the main challenge reusable visual components?** Apply Atomic Design principles to the UI layer.
4. **Are business rules and domain boundaries complex?** Consider domain-based organization.
5. **Is the frontend large, with many slices and dependencies to govern?** Evaluate Feature-Sliced Design.
6. **Are multiple apps sharing packages and tooling?** Consider a monorepo.
7. **Does the application have several overlapping needs?** Use a carefully scoped hybrid architecture.

### Practical project mapping

| Project | Architecture to consider | Reason |
|---|---|---|
| Personal portfolio | Page-Based or Layer-Based | Small number of mostly independent pages |
| Company landing page | Page-Based | Route and content focused |
| Student dashboard | Feature-Based | Distinct dashboard capabilities |
| Job application tracker | Feature-Based | Applications, companies, analytics, and reminders are separate capabilities |
| LMS | Feature-Based + Domain-Based | Learning, enrollment, assessments, and identity have distinct responsibilities |
| E-commerce frontend | Feature-Based + Domain-Based | Catalog, cart, checkout, orders, and payments are related but distinct |
| Banking / ERP | Domain-Based or Hybrid | Complex business rules and domain boundaries |
| Design system | Atomic Design principles | Reusable components and consistent UI standards |
| Large SaaS platform | Feature-Based or FSD | Many workflows and growing dependency complexity |
| Customer app + admin app | Monorepo with internal app architecture | Shared packages and coordinated development |

These are starting points, not mandatory prescriptions. A small application does not need an enterprise architecture to be professional.

## Recommended Folder-Design Practices

- Keep business-specific code close to the feature or domain that owns it.
- Keep shared code genuinely generic; avoid turning `shared/` into a dumping ground.
- Define public entry points for modules when useful.
- Avoid circular dependencies and uncontrolled cross-feature imports.
- Co-locate tests, stories, and styles with the code they validate when practical.
- Separate application composition from business logic.
- Introduce abstraction only when it solves a real maintenance or reuse problem.
- Refactor structure as the product's complexity becomes visible rather than predicting every future need.

## Key Takeaway

There is no universally correct frontend folder structure. Choose the simplest structure that clearly represents the application's responsibilities today and can evolve with its expected complexity.

**Start simple, define boundaries, and add architectural rules when they solve an actual problem.**
