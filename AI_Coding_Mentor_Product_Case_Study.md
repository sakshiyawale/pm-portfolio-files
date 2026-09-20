# AI Coding Mentor: Product Case Study

## Overview

A conversational tool that lets engineers ask natural-language questions about an unfamiliar GitHub repository and get grounded, workflow-level answers, instead of manually tracing code across files.

---

## Problem

New-hire engineers spend anywhere from a day to a week manually tracing through an unfamiliar codebase to understand core workflows (e.g., how authentication is handled), because documentation is typically limited to a single README and code comments are function-scoped with no visibility into cross-file data flow.

**Root cause:** Existing documentation formats don't match how engineers actually need to understand code.

- Architecture diagrams describe system structure, but not implementation-level behavior (e.g., what gets called when a user clicks a button).
- Comments explain individual functions in isolation, not how data flows between them.
- Tutorials give a user's-eye view of the product, not an engineer's-eye view of the codebase.

**Who this affects most:** New-hire engineers onboarding onto an unfamiliar codebase, who need to build working understanding quickly enough to start contributing to real tickets.

---

## Goals & Success Metrics

**Goal:** Reduce the time it takes a new-hire engineer to build a working understanding of an unfamiliar codebase, so they can start contributing meaningfully sooner and with broader coverage of the system, not just the area they were initially assigned to.

**Success metrics:**

1. **Time to first meaningful contribution** — time to first PR merged addressing a real ticket
2. **Time spent reading/tracing code before implementation** — time between starting a task and writing the first line of code
3. **Breadth of contribution** — % of a new hire's commits touching modules outside their initially assigned area within the first 30-60 days, as a proxy for whether they understand the system beyond their immediate task, not just memorized one corner of it

**Baseline comparison:** Manually tracing similar-complexity repos took ~5-6 days to build full understanding before being able to independently pick up a ticket. Using the AI coding mentor on comparable repos reduced this to roughly 1 day (based on informal, self-measured use across repos of similar complexity, with and without the tool).

---

## Solution Options Considered

| Option | Why it fell short |
| --- | --- |
| Architecture diagrams | Useful for system-level structure, but too high-level to answer implementation questions engineers actually have |
| Tutorials / walkthroughs | Give a user's-eye view, not an engineer's-eye view; solve only part of the problem |
| **Conversational Q&A (chosen)** | Matches how people naturally build understanding — unscripted, driven by whatever the person is actually confused about, not a fixed FAQ list. Also builds a persistent chat history in one place |

**Why conversational Q&A:** Asking and answering questions is the most natural way humans build understanding of something new. Users aren't limited to pre-formed or frequently-asked questions; they can ask whatever is actually on their mind, and the conversation history accumulates in one place as their understanding builds.

---

## Competitive Landscape

IDE-integrated AI tools (GitHub Copilot, Cursor, Gemini in VS Code) already put AI models directly into the developer workflow, so it's fair to ask where this tool fits alongside them.

**The distinction is comprehension vs. generation:**
Copilot and Cursor are optimized for "help me write the next line of code right now," anchored to the cursor position and whatever files are currently open. That's a generation problem. This tool is optimized for "help me understand how this entire system works before I touch anything," which is a comprehension problem, and it's a distinct moment in an engineer's workflow that happens before generation starts.

**Retrieval scope is different:**
IDE copilots mostly reason over open files or a limited local workspace window. This tool's semantic chunking was built specifically to preserve cross-file workflow understanding across an entire repo, a harder and differently-scoped retrieval problem than autocomplete-style local context.

**Onboarding is an underserved, specific use case:**
None of Copilot, Cursor, or Gemini position themselves around new-hire onboarding time as a metric to move. That's a narrower, more defensible wedge than "AI coding assistant" as a category, and it's where this tool's value proposition is strongest.

**Honest limitation:**
As IDE copilots add more repo-wide context windows and codebase indexing over time, this gap could narrow. The durable differentiator isn't the underlying retrieval technology, which competitors can replicate, but the framing around a specific user moment (onboarding) and outcome (time-to-contribution) that general-purpose coding assistants aren't optimizing for.

---

## Design Decisions

**Code snippets as an optional output, not a default feature.**
The right depth of answer depends on who's asking. An engineer implementing something wants citations and code snippets. A PM or manager trying to understand a workflow at a conceptual level doesn't need that detail. Rather than hard-coding snippet output, the tool offers it as an option the user can request, adapting the answer to the asker's role.

**Semantic chunking with overlapping sliding windows for large repos.**
Repos too large to fit in a single context window needed to be chunked. Fixed-line chunking was rejected because it risks cutting functions or logical blocks mid-definition. Instead, used semantic chunking with a sliding window (~10-line overlap), which preserves context across chunk boundaries so answers stay grounded in complete logic rather than fragments.

---

## Risks & Assumptions

**Risk: misleading or hallucinated answers.**
Currently, no relevance threshold exists for retrieved chunks. If no chunk is truly relevant to a question, the tool may still generate a plausible-sounding but incorrect answer rather than saying "I couldn't find anything relevant." Planned fix: introduce a relevance threshold, and prompt the user to rephrase when no chunk clears it.

**Unverified assumption: works across languages.**
The tool has only been tested against Python codebases. Its behavior on other languages hasn't been verified.

**Known limitation & fix: language dependency.**
Current chunking logic isn't validated outside Python. Planned fix: move to AST (abstract syntax tree) parsing, which traverses code structure hierarchically rather than relying on language-specific patterns, making the approach language-agnostic.

---

## Key Learnings

- The biggest product insight wasn't a technical one: different users (engineers vs. PMs) need fundamentally different depths of answer from the same underlying data, which shaped the optional-snippet design.
- Chunking strategy has an outsized effect on answer quality. Naive approaches (fixed-line splits) would have undermined the core value proposition (grounded, accurate answers) regardless of how good the retrieval or LLM layer was.
- Shipping without a relevance threshold was a reasonable v1 trade-off, but it's the clearest gap between "works for a demo" and "trustworthy for daily use."

---

*Status: Personal project, self-tested across similar-complexity Python repos. Language-agnostic support (AST-based chunking) and relevance thresholding are planned next steps.*
