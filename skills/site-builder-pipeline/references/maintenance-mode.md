# Maintenance Mode: Dispatch Shape Per Category

Concrete dispatch instructions for a scoped change to a project whose repository already exists. Each block below is what the coordinator hands to a fresh agent with no inherited context: only the named input, plus the instruction text. The check that follows any of these never sees the maker agent's reasoning, only the files it produced, the same isolation the fresh build pipeline already holds between stage 5 and stage 6.

---

## Before dispatching anything

Locate the project's repository and its `BRIEF.md`. If `BRIEF.md` cannot be found, ask the user for it or for enough of the original brief to reconstruct one; do not proceed on a guess about the project's established creative direction.

---

## Copy or text change

**Input handed to the fresh agent:** the current file(s) the change touches, `BRIEF.md`, the specific request.

**Instruction:**

```
Change only what is asked: [the specific request]. Use BRIEF.md for tone and voice, the same way the original copy pass did. Do not touch any other text, section, or structural element. Do not resolve an ambiguous fact into a more specific reading; if the request itself is ambiguous, log the question instead of guessing.
```

**Output:** the changed file(s) only.

---

## Visual or stylistic change

**Input handed to the fresh agent:** the current file(s), `BRIEF.md`, the specific request.

**Instruction:**

```
Apply this visual change: [the specific request], consistent with BRIEF.md's four axis positions. If the request itself shifts one of those axes, say so explicitly rather than applying it silently; a real axis change is a decision for the human requesting it, not something to infer.
```

**Output:** the changed file(s), plus a note if the request implied a brief change.

---

## Structural change

**Input handed to the fresh agent:** the current file(s), `BRIEF.md`, the vertical's shape file, the specific request.

**Instruction:**

```
Add, remove, or reorder the section requested: [the specific request]. Keep every other section exactly as it is. Check the change against the vertical's shape file so the result still reads as a credible site in this vertical, not just a patch.
```

**Output:** the changed file(s).

---

## Factual update

**Input handed to the fresh agent:** the current file(s), the specific request.

**Instruction:**

```
Update the fact requested: [the specific request]. This is a direct edit, not a creative decision; do not touch tone, structure, or any other content. Do not record a price; if this fact is a new priced item, follow the same no price rule the original build used (a curated link out if the business runs its own digital platform, a conversation CTA otherwise).
```

**Output:** the changed file(s).

---

## Bug or broken build

**Input handed to the fresh agent:** the current file(s), a description of the defect.

**Instruction:**

```
Fix this specific defect: [the description]. Do not use this as an opportunity to also improve unrelated parts of the build.
```

Once this agent finishes, a second fresh agent, with no visibility into how the fix was made, checks the result the same way stage 6 checks a fresh build (see below).

---

## The mandatory check, every category, no exception

Dispatch a fresh checking agent with no context beyond the changed file(s), the vertical's shape file, and the no price rule.

**Instruction:**

```
Check these changed files against the vertical's conventions checklist, the same bar a fresh build is held to. Separately, scan for any price, currency figure, or numeric rate attached to an item or service; this fails on its own regardless of the checklist score. Report a pass or fail with specific reasons only.
```

On fail, the coordinator sends the specific reason back to the agent that made the change: a fresh attempt, given the current files and the reason, not the original request alone.

---

## Opening the pull request

Once the check passes, create a branch on the project's repository, commit the change, and open a pull request. Never push directly to the branch a live deploy watches. The pull request is where a human reviews and merges, the same review this pipeline's manual deploy step already expects for a fresh build.
