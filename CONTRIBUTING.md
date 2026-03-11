# Contributing

This repository is maintained as a shared documentation standard for infrastructure naming.

Contributions should improve consistency, clarity, and long-term maintainability.

## Contribution Scope

Typical contributions include:

- clarifying existing naming rules
- adding approved examples
- proposing new role codes
- documenting new infrastructure patterns
- improving cross-links and navigation

## Contribution Principles

- Write all content in English.
- Keep naming rules technology-independent where possible.
- Prefer short, stable, machine-readable codes.
- Avoid introducing local or team-specific variants without strong justification.
- Update related pages when adding or changing a rule.

## Repository Areas

- [Documentation Hub](./docs/index.md)
- [Standard Overview](./docs/standard/overview.md)
- [Field Definitions](./docs/standard/fields.md)
- [Patterns and Resource Naming](./docs/standard/patterns.md)
- [Role Code Catalog](./docs/reference/role-codes.md)
- [Templates](./docs/templates/index.md)
- [Governance](./docs/governance.md)

## How To Propose a Change

1. Identify whether the change is a rule change, an example update, or a catalog extension.
2. Update the relevant document.
3. Add or adjust links in related pages so the change is discoverable.
4. If the change affects naming semantics, update examples and governance references.
5. Keep the proposal concise and operationally justified.

## How To Propose a New Role Code

Before adding a new role code, verify that an existing code does not already cover the same function.

Each role code proposal should include:

- proposed code
- short description
- category
- justification
- expected usage examples
- overlap analysis with existing codes

Suggested proposal format:

```md
## Proposed Role Code

- Code: `xyz`
- Category: `Platform`
- Description: Short functional description
- Justification: Why the existing catalog is insufficient
- Example hostnames:
  - `zrh-lan-prd-platform-core-xyz-01-g1`
  - `fra-lan-stg-platform-core-xyz-01-g1`
- Notes: Constraints, alternatives considered, or migration notes
```

## Review Criteria

Changes are more likely to be accepted when they:

- preserve naming stability
- reduce ambiguity
- improve automation compatibility
- generalize across teams and environments
- avoid encoding vendors, products, or versions in hostnames

## Editing Guidance

- Use sentence case for prose headings unless the document already follows a different style.
- Keep examples realistic and consistent with the standard.
- Prefer relative Markdown links for GitHub navigation.
- When adding a new file, link it from at least one index page.

## Templates

Use the reusable templates in [docs/templates/index.md](./docs/templates/index.md):

- [Standard Template](./docs/templates/standard-template.md)
- [Appendix Template](./docs/templates/appendix-template.md)

## Related Pages

- [Project README](./README.md)
- [Documentation Hub](./docs/index.md)
- [Governance](./docs/governance.md)
- [Role Code Catalog](./docs/reference/role-codes.md)
