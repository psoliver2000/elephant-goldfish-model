# Test Plan: EGM Brainstorm Skill

Frontmatter and link checks run in `pytest tests/unit` (see [TESTING.md](../../TESTING.md)).

## Protocol Verification Checklist

When evaluating or exploring `egm-brainstorm` interactively in chat, verify:

-   **Step 1 (Open-Ended Clarification & Gate):** Drills down into half-baked concepts
    using open-ended questions (in Claude Code, `AskUserQuestion` forms with neutral, unranked
    options, per this fork's `docs/claude.md`; no recommended or ranked menus)
    and enforces a user readiness checkpoint gate before subagent invocation.
-   **Step 2 (Upstream Multi-Lens Ideation):** Evaluates feature concepts across the
    6 specialized Goldfish perspective lenses (Contrarian/YAGNI, Cost/Quota Economics,
    UX Ergonomics, Migration & Compatibility, Observability & SRE, Tech Debt & Maintenance).
-   **Step 3 & 4 (Concepts Brief Deliverable & Handoff):** Compiles and saves the
    synthesized `concepts_brief.md` artifact for user review and handoff to
    `/egm-draft`.
