# Pipeline Phases: Dispatch Shape Per Stage

Concrete dispatch instructions for each stage of `site-builder-pipeline`. Each block below is what the coordinator hands to a fresh agent or session with no inherited context: only the named input, plus the instruction text.

---

## Stage 1: data collection

**Input handed to the fresh agent:** the business name and the one reference (handle, URL, or address). Nothing else.

**Instruction:**

```
Research [business name], starting from [reference]. Produce a factual document covering: address and hours, offering or menu with prices where visible, review volume and rating if public, and real photos (download and keep the actual files, do not just link to a source that may expire).

For anything you read that supports more than one plausible interpretation (a generic term versus a proper name, a one off event versus something recurring, especially anything that reads as the business claiming ownership of a person, pet, or object), do not resolve it into the more specific, confident reading. Log it as an open question next to the fact it touches, with the two readings named.

Output only the factual document and the photo files. Do not draft any copy, do not suggest a design direction.
```

**Output:** a facts document plus a folder of real photo files. This is the only thing that survives to stage 2 and stage 3.

---

## Stage 2: visual investigation

This stage is not new. It is the isolated pass already defined in `creative-direction`'s `references/visual-evidence-investigation.md`. Dispatch it exactly as that file describes, handing it only the photo files from stage 1, nothing about the business name, the vertical, or any preference anyone has stated.

---

## Stage 3 and 4: creative direction and copy

Run these as the `creative-direction` and `landing-page-copy` skills already describe, with one addition: stage 3's input is the facts document from stage 1 plus the visual read from stage 2, not a user conversation about preferences. If the user has already registered reference URLs they admire, those are folded in as `creative-direction` already expects.

---

## Stage 5: build

### Path A, a template exists

**Input handed to the fresh agent:** the template's location, `BRIEF.md`, the copy, and the facts document.

**Instruction:**

```
Clone the template at [location]. Fill it with the brief, copy, and facts provided. Do not change the template's structure; that decision is already made. Replace placeholder content, wire in the real facts, and apply the brief's four axis positions to whatever the template leaves open (imagery treatment, microcopy tone).
```

### Path B, no template exists

Two agents run this path together, in sequence, each still only seeing what it needs.

**5a, the structural agent.** Input: the facts document, the brief, and `vertical-site-conventions`'s general checklist and framework (not a specific shape, since none exists for this vertical yet).

```
No shape file exists yet for [vertical] in vertical-site-conventions. Using the seven dimension framework that skill already defines (primary task prominence, layout register and density, merchandising and category surface, navigation and search paths, brand register, trust and conversion signals, and the synthesis checklist), decide the page's structure for this vertical: which sections exist, in what order, and which of the ten or so conventions a credible site in this vertical is expected to carry. Do not decide palette, type, or any other purely aesthetic register; that stays with creative-direction and design-standards.

Output two things: a structural plan for this specific build, and a new shape reference file for vertical-site-conventions, written in the same format as its existing shape files, so the next project in this vertical does not have to repeat this work.
```

**5b, the build agent.** Input: the structural plan from 5a, `BRIEF.md`, the copy, and the facts document.

```
Build the site to the structural plan provided, filling it with the brief, copy, and facts. This build is simultaneously the client's demo and a candidate for the vertical's next template; keep client specific content clearly separable from structural and stylistic choices, since the candidate may later need those two things split apart.
```

**Committing the new shape file:** the shape file 5a produces is a change to the shared skills repository, the same kind of change this project has always pushed only with the user's explicit confirmation. Commit it locally and hold the push until the user has said yes, exactly as prior shape and rule additions to this repository have been handled.

---

## Stage 6: test and review

**Input handed to the fresh agent:** the built files, the vertical's shape file (existing or the one just produced in path B), and the ambiguous data rule from stage 1's facts document.

**Instruction:**

```
Check the build against the vertical's conventions checklist. Mark each convention present, absent with a reason, or routed elsewhere. Three or more absences means this is not ready; state which ones and why.

Separately, check every factual claim on the page against the facts document's open questions. Any claim that resolves a logged ambiguity into the more specific reading is a failure on its own, independent of the composition score.

Report a pass or fail. On fail, state the specific reasons only; do not restate everything that already passed.
```

**On fail:** the coordinator hands this exact failure report to a fresh stage 5 attempt, along with the current build files. It does not hand back the original brief and copy alone; the fresh attempt needs the files to fix, not just the original spec to redo from zero.
