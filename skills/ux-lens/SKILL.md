---
name: ux-lens
description: Apply Nielsen's 10 usability heuristics when building or reviewing any user interface (web, app, dashboard, form, CLI output). Use when creating UI code, reviewing a screen or component, or when asked for a usability or heuristic review.
---

# UX Lens

Built on the foundation of [Nielsen's Heuristics - The Decision Lab](https://thedecisionlab.com/reference-guide/design/nielsens-heuristics), covering Jakob Nielsen's 10 usability heuristics.

Rules of thumb for user-friendly interfaces (Jakob Nielsen, 1994). They are general guidance, not hard rules. A heuristic review finds likely problems early; it does not replace testing with real users.

## Modes

- **Build mode** (writing UI code): apply the checks below silently while coding. Mention only trade-offs you made.
- **Review mode** (asked to review/audit): walk every heuristic against the code or screen, then output the findings table.

## Commands

Read the first word of the arguments:

- `review <target>` - full audit of a file, folder or screen. Output the findings table. Change no code.
- `fix <target> [min-severity]` - review, then fix only issues at or above min-severity (default 3). List what changed.
- `check <numbers> <target>` - review only the listed heuristics, e.g. `check 5,9 app/form.tsx`.
- `build <description>` - build the UI in build mode, applying all checks.
- No command word - treat as `review`.

## The 10 heuristics and what to check in code

1. **Visibility of system status** - users always know what is happening.
   - Loading, saving, empty and success states exist for every async action.
   - Buttons show pressed/disabled/busy state; no silent submits.
   - Current page/step is highlighted in nav or wizards.

2. **Match between system and real world** - speak the user's language.
   - Labels use everyday words, not DB field names, enum codes or internal jargon.
   - Dates, numbers and currency follow the user's locale.
   - Icons have text labels or tooltips.

3. **User control and freedom** - give an easy way out.
   - Cancel, Back, Close and Undo are available where actions happen.
   - Modals close on Esc and outside click (unless destructive in progress).
   - Multi-step flows can be exited without losing entered data, or warn first.

4. **Consistency and standards** - follow platform conventions and stay consistent internally.
   - Same action = same label, color, icon and position across screens.
   - Reuse existing components and design tokens; do not invent new patterns for solved problems.
   - Links look like links, primary action looks primary.

5. **Error prevention** - stop mistakes before they happen.
   - Confirm irreversible actions (delete, submit payment, bulk changes).
   - Validate inputs inline; constrain with pickers, masks, min/max.
   - Disable actions that are not valid in the current state.

6. **Recognition rather than recall** - show options, do not make users remember.
   - Use dropdowns, autocomplete, recent items and visible filters.
   - Keep context visible across steps (e.g. selected client, chosen plan).
   - Field labels stay visible (placeholder is not a label).

7. **Flexibility and efficiency of use** - serve novices and experts.
   - Keyboard support (Enter to submit, Tab order, shortcuts for frequent actions).
   - Bulk actions, saved filters, sensible defaults.

8. **Aesthetic and minimalist design** - remove what does not help the task.
   - One clear primary action per screen; clear visual hierarchy.
   - No duplicate info, decorative clutter or walls of text pushing key content below the fold.

9. **Help users recognize, diagnose and recover from errors** - plain-language errors with a fix.
   - Messages say what went wrong and how to fix it; no raw stack traces or error codes alone.
   - Error shown next to the field that caused it; input is preserved.
   - Offer a next step (retry, support link).

10. **Help and documentation** - self-explanatory first, help when needed.
    - Tooltips or inline hints on complex fields.
    - Empty states explain what to do next.
    - Link to docs/support for complex workflows.

## Severity scale (review mode)

- 0 - Not a problem
- 1 - Cosmetic: fix if time allows
- 2 - Minor: low priority
- 3 - Major: important to fix
- 4 - Catastrophe: must fix before release

## Review output format

| # | Heuristic | Location (file:line or screen) | Issue | Severity | Fix |
|---|-----------|-------------------------------|-------|----------|-----|

After the table:
- Top 3 fixes by severity.
- Note anything the heuristics cannot judge (real user behavior, context-specific needs like mobile, voice or children) and suggest a quick user test for those.

## Rules

- Prefer the smallest fix that resolves the issue; do not redesign unasked.
- Do not report the same issue under several heuristics; pick the best fit.
- Skip heuristics with no findings in the table, but list them as "no issues found".
