# Decisions

## ADR-001: Create a cross-project learning hub

- **Status:** accepted
- **Date:** 2026-09-14
- **Decision:** Centralize reusable mental models, protocols, patterns, labs, and
  review questions in one repository.
- **Reason:** The same concepts now appear across three or more sources. Continued
  duplication would create inconsistent explanations and increase maintenance.

## ADR-002: Keep project evidence in project repositories

- **Status:** accepted
- **Decision:** Requirements, project-specific ADRs, implementation, and verification
  remain with each project. The learning hub links to them.
- **Reason:** A project should remain independently understandable and auditable.

## ADR-003: Start with Markdown, not a documentation framework

- **Status:** accepted
- **Decision:** Use plain Markdown and GitHub navigation initially.
- **Reason:** MkDocs, Docusaurus, or another site generator would add dependencies and
  deployment work before navigation or search is a demonstrated problem.
- **Revisit when:** the hub has roughly 20 substantial notes, needs full-text public
  navigation, or has multiple contributors.

## ADR-004: Keep the initial repository private

- **Status:** completed
- **Decision:** Run the same privacy, secret, license, and anonymous-access publication
  gate used by the project repositories before making this hub public.
- **Outcome:** The gate passed on 2026-09-14 and the repository was published.
