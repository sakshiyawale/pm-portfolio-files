# Handshake: Product Teardown

## Overview

Handshake is a job platform used by students to find internships and early-career roles. This teardown looks at one core problem: bad job matching. It affects both students and recruiters.

---

## Problem

Students search for specific roles. But they often see jobs that don't match at all.

Example: searching "software engineer" can show construction or sales jobs. This happens to real users. It happened to me too.

Recruiters have the same problem in reverse. They message students about jobs that don't fit their major or skills.

Example: a tech major getting a "truck driver" alert. In my case, I got outreach for a Sales Representative role at Power Home Remodeling, despite a CS background.

**Root cause:** These are not two separate bugs. They come from the same source: how Handshake categorizes and ranks jobs.

Handshake has said that when students see an irrelevant job, it's usually because of a filter or keyword they set themselves, not a system error. That's a fair point in general. But it doesn't fully explain cases like these two, since neither of us searched for or expressed interest in those role types at all. That gap is what this teardown focuses on.

---

## How Handshake's Matching Works Today

Handshake's process appears to work in two main phases.

**Phase 1: Retrieval**
This step finds a pool of possible jobs. Handshake maintains more than 380 Job Role Groups, and automatically assigns each job posting to the right group based on its title and description.

**Phase 2: Ranking**
This step orders the jobs a student sees, based on search-term match, profile fit (major, grad date), and past student behavior.

**The real bug:** Phase 1 can put a job in the wrong Job Role Group. If "software" search results get mapped into a "construction" group, nothing downstream can fully fix that. Bad input breaks the rest of the pipeline.

**A second bug:** Handshake already has a "Most relevant" sort option, and it works. But switching to "Newest jobs" throws away that ranking entirely. A brand-new but irrelevant job (like a school teacher role) can jump above a highly relevant one. The ranking effort becomes pointless the moment someone changes the sort.

---

## Goals & Success Metrics

**Goal:** Make job matches genuinely relevant for students. Make recruiter outreach relevant for students too. This should increase real platform usage, not just browsing.

**Success metrics:**
1. **Apply rate on recommended jobs** — not just "opened," but actually clicked "Apply." Opening a job doesn't mean it was a good match. Applying does.
2. **Search relevance rate** — the % of results for a search that actually match the role, major, and level searched for.
3. **Recruiter message reply rate** — the % of recruiter messages that get a reply. A student replies to a message that actually fits them.

**Personal experience:** I stopped using Handshake because of irrelevant results. If matching improved, I would come back and use it to apply for jobs.

---

## Solution Options & Trade-offs

### 1. Fix Job Role Group mapping (Phase 1)
Mapping today is likely based on keyword or text overlap. That's too loose. Move to semantic matching, matching by meaning, not just shared words.

**Why fix this first:** every later step depends on this pool being correct. If the pool is wrong, better ranking or sorting can't fix it.

**Trade-off:** even semantic matching won't be perfect. Some jobs are genuinely hard to rank. Example: a job that says skills matter more than experience creates an ambiguous case, even with good matching.

### 2. Keep Phase 2 ranking as-is
The current ranking logic (relevance + profile fit + behavior history) is already reasonably solid. The problem isn't here. No major change needed at this layer.

### 3. Let sort options combine with relevance, instead of replacing it
Right now, choosing "Newest jobs" fully overrides relevance ranking. Instead, sort options should combine: for example, "Relevance + Newest." Not every combination makes sense (e.g., "Relevance + Oldest" is an odd pairing), so only sensible combinations should be offered.

**Why not remove the sort options?** Some users genuinely want a pure "newest first" view. Removing choice isn't the fix, blending it with relevance is.

### 4. Show a visible match score
Like LinkedIn's "% match," show students a score or star rating for each job. This uses signals Handshake's ranking model already computes. It's a UI layer, not new backend work.

### 5. Strengthen the existing feedback loop
Handshake already lets students hide a job that isn't a fit, and saving jobs improves future recommendations, since the system learns from what a student bookmarks. But this loop clearly isn't catching every case, the Power Home Remodeling example still got through. The opportunity isn't building a feedback loop from scratch, it's making the existing one act earlier, at the categorization step, instead of only after a bad match has already reached the student.

---

## Open Question: Who Tags the Jobs?

Fixing Job Role Groups raises a new question: who decides which group a job belongs to?

**Option A: Recruiter tags manually.** Accurate, but adds extra work. Recruiters likely resist this.

**Option B (recommended): AI tags automatically, recruiter reviews and corrects it.** This is faster for recruiters. It also strengthens the feedback loop earlier in the pipeline: every correction teaches the model to tag better next time, rather than waiting for a student to hide a bad result after the fact.

---

## Risks & Assumptions

- **Ambiguous jobs will still exist.** Some job descriptions are unclear even to a human reader (e.g., skills-focused vs. experience-focused). Better matching reduces bad matches, but won't remove all of them.
- **Recruiter messaging is broader than just job postings.** Recruiters also message students about events and open opportunities, not only specific roles. This teardown focuses on job matching. Fixing recruiter-to-student messaging fully would need a separate, larger effort.
- **Sort-combination design needs limits.** Letting users combine any two sort options could create confusing or meaningless combinations. The design needs to define which combinations actually make sense.

---

## Key Learnings

- A surface-level symptom (irrelevant search results) can point to a much deeper cause, a pipeline where bad early data breaks good later logic.
- Fixing the "obvious" layer (ranking) isn't always where the real bug lives. Here, the bug was upstream (categorization) and downstream (sort overriding rank), not in the ranking model itself.
- Removing user control isn't always the right fix. Combining options (relevance + sort) respects user choice while still solving the core problem.
- A platform's existing safeguards (like Handshake's hide/save feedback loop) can still fail if they only act after a bad match reaches the user. The stronger fix is moving correction earlier in the pipeline.

---

*Status: Independent teardown based on personal experience and Handshake's public Help Center documentation. Not affiliated with or reviewed by Handshake.*
