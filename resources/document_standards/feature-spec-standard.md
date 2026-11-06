# Feature Specification Standard

This standard defines the quality bar for high-level feature specifications
before implementation begins.

## Core Principle

A feature specification passes if a competent engineer (or fresh AI session) who
is unfamiliar with the codebase can understand the proposed feature, the
business motivation, and the design trade-offs, and confirm that all major risks
and alternatives have been addressed.

## The Alternatives Rule

The specification must include a **mandatory evaluation of alternatives**. It
fails this standard if it proposes a single path without proving that other
viable designs were considered and rejected for specific, documented reasons
(including, but not limited to, complexity, cost, performance, or scalability).

## Risks & Limits

The specification must explicitly call out its own constraints. It must identify
potential failure modes, security implications, scalability limits, and how they
will be mitigated.

## The Evidence Rule

Fork change (2026-11-06). Every statement about the current system (an
existing file, function, endpoint, table, configuration value, or behavior)
carries one label: **Confirmed** with a `path:line` citation, **Likely** with
the indication stated, or **Not verified** with the reason stated. Items that
do not exist yet are marked **(proposed)**. The specification fails this
standard if it states current-system facts without a label, cites a source
that does not support the statement, or omits the **Sources Used** table.

## Requirements (Non-Exhaustive Examples)

The specification must detail these areas if applicable to the changes:

*   **Problem Statement**: The business or user problem being solved.
*   **Goals & Non-Goals**: What the feature will and will not deliver.
*   **Proposed Architecture**: Component layout, data flows, and ecosystem
    integration.
*   **Alternatives Considered**: Rejected options and rationale for rejection.
*   **Risks & Mitigations**: Identified security, scalability, or complexity
    risks.
