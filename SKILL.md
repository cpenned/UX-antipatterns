---
name: ux-antipatterns
description: Detect UX anti-patterns that frustrate users in frontend code. Use when reviewing, building, or refactoring UI components, pages, forms, or interactive flows. Triggers on frontend code review and building new UI features. Focuses on code-level heuristics that cause real user harm like layout shifts, silent failures, double-submits, focus theft, and missing feedback.
---

# UX Anti-Pattern Detection

Scan frontend code for patterns that cause user frustration. 

## Core Axioms

Before checking individual rules, internalize these. They are the "why" behind every item below.

| # | Axiom | One-liner |
|---|-------|-----------|
| 1 | **Acknowledge every action** | Every user action must produce visible feedback within 100ms, even if the result takes seconds. |
| 2 | **Never destroy user input** | Not on error, not on navigation, not on timeout, not on refresh. |
| 3 | **State survives the unexpected** | Refresh, double-clicks or double submits, network loss — code must handle edge cases. |
| 4 | **Most recent intent wins** | Stale responses must never overwrite a newer user action. |
| 5 | **Explain every constraint** | If it's disabled, say why. If it failed, say how to fix it. If it succeeded, say what happened. |
| 6 | **Don't fight the platform** | Browser conventions, OS gestures, native controls, and accessibility APIs encode billions of hours of UX research. |

## Workflow

1. Read [references/antipatterns.md](references/antipatterns.md) to load the full detection heuristics.
2. Scan the code under review against each applicable anti-pattern category.
3. Report findings grouped by anti-pattern, citing specific file:line locations.
4. For each finding, state: the anti-pattern name, the user harm, and a concrete fix.

## Anti-Pattern Categories

| # | Category | User Harm |
|---|----------|-----------|
| 1 | Layout Stability | Click target moves; wrong thing clicked. |
| 2 | Feedback & Responsiveness | Action feels ignored; user retries, waits, or loses trust that the system is working. |
| 3 | Error Handling & Recovery | User is stuck with no way forward; input destroyed; problem unsolvable without guessing. |
| 4 | Forms & Input Interference | Platform fights the user's typing; data mangled, basic editing broken. |
| 5 | Focus | User is typing and the UI yanks them elsewhere. |
| 6 | Notifications, Interruptions & Dialogs | User's flow broken; attention taxed by noise; forced to parse ambiguous choices under pressure. |
| 7 | Navigation, Routing & State Persistence | User can't go back; context evaporates on refresh or redirect. |
| 8 | Scroll & Viewport | Content unreachable or unstable; user fights the interface to see what they came for. |
| 9 | Timing, Debounce & Race Conditions | Actions fire twice, responses arrive stale, sessions expire mid-task; system behaves unpredictably under normal use. |
| 10 | Accessibility as UX | Entire interaction modes broken — keyboard users can't navigate, touch users locked out. |
| 11 | Visual Layering & Rendering | UI elements overlap, clip, or hide each other; controls become unreachable. |
| 12 | Mobile & Viewport-Specific | Keyboard covers input, layout jumps on scroll, tap targets unresponsive; basic mobile interaction degraded. |
| 13 | Cumulative Decay & Long-Term UX | App degrades over time; preferences lost, performance rots, stale experiments create inconsistencies. |

