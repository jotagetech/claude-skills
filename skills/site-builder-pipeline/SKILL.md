---
name: site-builder-pipeline
description: "Coordinate isolated agents that turn one request (a business name plus a reference such as a social profile or an existing site) into a finished demo, pushed to its own repository and ready for a human to deploy: research, an isolated visual read, a creative brief, copy, a build reusing or originating a vertical template, and a test and fix loop. Also runs maintenance mode: scoped, isolated edits (copy, visual, structural, factual, or a bug fix) to a project already pushed. Use to research and build a demo for a named business, to divide a build across agents instead of one session doing everything, for a repeatable showcase site pipeline, or for a scoped edit to an existing project. Triggers on build a demo for, research and build a site for, run the site pipeline, edit the site for, update the menu for, fix a bug on the site. Does NOT fire for one step already covered by a skill it coordinates (`creative-direction`, `landing-page-copy`, `vertical-site-conventions`), or for the deploy step, which is manual."
category: process-and-team
catalog_summary: "Coordinates isolated research, brief, build, and test agents into one finished, repository-ready demo site"
display_order: 6
---

# Site Builder Pipeline

One request in, one finished site out, pushed to its own repository and ready for a human to deploy, built by a chain of agents that never share more context than the one artifact each needs.

This skill does not do any of the creative or technical work itself. It coordinates. Every stage below is a separate agent or session with no inherited conversation history, given only the specific input that stage requires. The isolation is the point: a build agent that has seen the research narrative starts anchoring to it instead of the brief, and a test agent that has seen the build agent's reasoning starts rationalizing instead of checking. Keeping each stage blind to everything upstream except its one required artifact is what keeps the later stages honest.

---

## When to use

- A business name and one reference (a social handle, an existing site, a physical address) come in, and the ask is a finished demo, pushed and ready to deploy, not one step of the process
- The build needs to run unattended after the initial request. It should interrupt only for a genuine problem, an ambiguous fact that needs a human call, or a build that keeps failing its own test
- A vertical (restaurant, retail, clinic, etc.) may already have a reusable starter worth cloning instead of building from zero, and the pipeline should check for that automatically
- Producing another entry in a running series of pre-contract showcase sites, where consistency of process matters more than any single build
- A named, already pushed project needs a scoped change rather than a rebuild: a copy tweak, a visual adjustment, a structural change, a factual update, or a bug fix. See maintenance mode below

## When NOT to use

- Running one stage in isolation (research only, a brief only, a copy pass only). Invoke that stage's own skill (`creative-direction`, `landing-page-copy`, `vertical-site-conventions`) directly instead of the whole chain
- Redoing a site from scratch under the banner of maintenance. A request broad enough to touch nearly every section is a new pipeline run, not a scoped edit; maintenance mode is for pointed changes to a project that already exists
- A project where the user wants to make every creative call personally, in one continuous conversation, rather than delegate stages to isolated agents
- Any step that needs the user's own visual curation (choosing among finished photo or aesthetic candidates). That judgment call is a required interrupt, not something a stage should resolve on its own

---

## Required inputs

- The business name
- One reference: a social handle, a URL, or an address the research stage can start from
- The vertical, if already known (this skips a research guess); otherwise the research stage infers it
- The path or handle for the vertical's reusable template store (a repository or directory the build stage checks before building from zero)
- A source control destination for the project's own repository (the pipeline pushes here; connecting the repository to a host and deploying it is a manual step a human does afterward, outside this pipeline)
- For a maintenance run instead of a fresh build: the existing project (by name or repository) and the specific change requested. See maintenance mode below

---

## The framework: seven stages, one artifact of handoff between each

Each stage is named by what it hands the next stage, not by who runs it. A stage is done when its one output artifact exists and nothing else about that stage's reasoning needs to survive.

1. **Data collection, producing real facts.** Research the business from the reference given. Output a factual document: address, offering (menu or service list, item names and descriptions, never a price), reviews, real photos, and whether the business already runs a digital menu, ordering, delivery, or booking platform of its own. Anything read from an ambiguous source (a caption or comment that supports more than one interpretation, especially an ownership or "we have X" claim) gets logged as an open question next to the facts, not resolved into a confident claim. This is the same discipline `landing-page-copy` and `creative-direction` already apply to ambiguous source material; this stage is where the ambiguity first gets noticed.
2. **Visual investigation, producing an objective read.** Hand only the real photos from stage 1 to a fresh agent with nothing else: no brief, no prior build, no stated preference. It reports palette, materials, light, and mood, and is not allowed to recommend a direction. This is exactly the isolated pass `creative-direction` already documents in its [`references/visual-evidence-investigation.md`](references/visual-evidence-investigation.md); reuse it rather than re-deriving it.
3. **Creative direction, producing a brief.** Run `creative-direction`'s four axis workflow, feeding it the facts (1) and the visual read (2) as required inputs. Output is its standard `BRIEF.md`.
4. **Copy, producing page text.** Run `landing-page-copy` (or the project's equivalent) against the brief (3) and the facts (1). Output is the page's written content, with the same ambiguous data caution already baked into that skill.
5. **Build, producing the site.** See the vertical template branch below; this is the one stage with two distinct paths.
6. **Test and review, producing an approved build or a return trip.** Check the build against `vertical-site-conventions`'s composition checklist for the vertical's shape (eight or more of ten conventions present is the bar), against the same ambiguous data rule from stage 1, and against the no price rule below. A pass hands the build to deploy. A fail hands the build back to stage 5 with the specific reason, not a summary of everything else; see the correction loop below.
7. **Repository, producing a pushed, ready to deploy project.** Once approved, create the project's own repository and push the approved files. This is the pipeline's last automated step. Going live from there is manual: a human connects the repository to a host and triggers the deploy themselves, on their own schedule. See [`references/deploy-and-repo.md`](references/deploy-and-repo.md).

### The build stage's two paths

- **A template already exists for this vertical.** The build stage clones it and fills it with the brief (3), the copy (4), and the real facts (1). No new structural decisions are needed; the template already made them.
- **No template exists yet for this vertical.** The build stage brings in a second agent for this stage only, the one making the structural call: which sections exist and in what order, the same call `vertical-site-conventions` already makes for verticals it has a shape for. That agent's job is structure and composition, not aesthetics; palette and type stay with `creative-direction` and `design-standards` and the visual read from stage 2. The two agents deliver one site together, which is simultaneously this project's demo and a candidate for the vertical's next template. See [`references/pipeline-phases.md`](references/pipeline-phases.md) for the exact dispatch shape of this pairing, and [`references/template-promotion.md`](references/template-promotion.md) for what happens to that candidate after stage 6 approves it.

### The no price rule

No build produced by this pipeline ever shows a price, a duration-plus-rate, or any other number a client's own pricing decision could make stale. This holds across every vertical this pipeline builds for, not only the ones with an obvious menu or service list. In its place, every priced item carries a call to action decided by one fact stage 1 collects: if the business already runs a digital menu, ordering, delivery, or booking platform with its own current pricing, feature a small, deliberately chosen set of standout items and send the CTA straight to that platform for the complete list; if no such platform exists, carry the complete offering on the page itself and give the CTA a conversation channel instead (a message pre-filled with the item or service name). Never offer both destinations on the same item. `vertical-site-conventions`'s hospitality-food and local-service-booking shapes already encode this; stage 6 checks for it explicitly regardless of what the shape's own checklist happens to say.

### The correction loop, stage 6 back to stage 5

A failed check is not an interrupt by default. Send the specific failure back to stage 5 (a fresh build attempt, not a continuation of the one that failed, given only the current files and the stated reason) and let it try again. Cap the attempts (three is a reasonable default). Only after the cap is reached does this become a genuine interrupt to the user, framed as "the build keeps failing this specific check" rather than a vague status update.

---

## Workflow

1. Take the single request (business name plus reference) and confirm the vertical if it is not already stated.
2. Dispatch stage 1 (data collection). Wait for the facts document. That agent's session ends here; nothing beyond the document survives to the next stage.
3. Dispatch stage 2 (visual investigation) with only the real photos from stage 1's output. Wait for the objective read.
4. Dispatch stage 3 (`creative-direction`) with the facts and the visual read. Wait for `BRIEF.md`.
5. Dispatch stage 4 (`landing-page-copy`) with the brief and the facts. Wait for the page copy.
6. Check whether a template exists for the vertical. Dispatch stage 5 down the matching path (clone and fill, or build with a structural agent). Wait for the site's files.
7. Dispatch stage 6 (test and review) against the built files. On fail, loop back to step 6 with the stated reason, up to the attempt cap; on cap out, interrupt the user. On pass, continue.
8. If stage 5 ran the no template path, ask the user once whether this approved build should become the vertical's official template. On yes, dispatch the cleanup stage described in [`references/template-promotion.md`](references/template-promotion.md) before continuing. On no, continue without publishing anything as a template.
9. Dispatch stage 7 (repository creation and push). Report the repository back to the user as ready for a manual deploy. This is the pipeline's normal end state; nothing here waits for approval, and nothing here goes live on its own.
10. Any stage that hits a genuinely ambiguous fact, a blocked tool, or an exhausted correction loop stops and asks the user directly, naming the specific stage and the specific question, rather than surfacing a general status update.

---

## Maintenance mode: scoped changes to an existing project

Not every request is a new build. Once a project's repository exists, most requests about it are small and pointed: fix this phrase, adjust this color, add this menu item, add a section, fix this bug. Maintenance mode handles these without re-running the full seven stage pipeline.

**Trigger.** The request names an existing project (by name or by its repository) and describes the change. Locate the project's repository and its `BRIEF.md`, which stage 3 keeps with every project precisely so a later edit has that reference without needing the original conversation.

**Classify the request, then dispatch the matching isolated agent:**

| Kind of change | Stage dispatched | What it receives |
|---|---|---|
| Copy or text | `landing-page-copy`, isolated | the current file(s), `BRIEF.md`, the specific request |
| Visual or stylistic, inside the existing structure | `creative-direction`, isolated | the current file(s), `BRIEF.md`, the specific request |
| Structural (a section added, removed, or reordered) | a structural agent, the same role stage 5's path B plays | the current file(s), `BRIEF.md`, the vertical's shape file, the specific request |
| A factual update (address, hours, a menu item, a new photo) | a direct edit, no creative agent involved | the current file(s), the specific request |
| A bug or broken build | a build and test pair, the same roles stage 5 and 6 play | the current file(s), a description of the defect |

A request that bundles more than one kind (a new menu item and a hero rewrite) dispatches one isolated agent per kind, not one agent doing both. Nothing one agent reasons through reaches the others.

**The tester stays blind to the maker, same as always.** Whichever agent made the change, the check that follows never sees its reasoning, only the resulting files, exactly like the stage 5 to stage 6 handoff in a fresh build. This does not change for maintenance.

**Every change, regardless of kind, passes the same mandatory check before becoming a pull request:** the vertical's conventions checklist, the ambiguous data rule, and the no price rule. A maintenance edit is exactly the kind of small, later change that can reintroduce a price without anyone deciding to.

**Output: a branch and a pull request, never a direct push to the branch a live deploy watches.** The change goes live only once a human reviews and merges it, the same caution behind this pipeline's manual deploy step.

**When this stops being maintenance.** A request broad enough to touch nearly every section, or to change the vertical's structure wholesale, is a new pipeline run, not a chain of scoped edits. Say so and suggest rerunning the full pipeline instead.

See [`references/maintenance-mode.md`](references/maintenance-mode.md) for the exact dispatch shape per category.

---

## Failure patterns

- **Letting a later stage read an earlier stage's reasoning instead of its output artifact.** The whole design depends on each stage seeing only the one document it needs. A build agent shown the research agent's exploratory notes anchors on whatever half formed idea appears there first.
- **Skipping the visual investigation's isolation because "it's the same project anyway."** The isolation is the entire value of that stage; a contaminated read is worse than no read, because it looks like independent evidence when it is an echo.
- **Treating a stage 6 failure as an automatic interrupt.** Most failures are correctable by a fresh build attempt with the specific reason in hand. Reserve the interrupt for the attempt cap, not the first failure.
- **Promoting a build to the vertical's template without the human checkpoint.** The pipeline can propose; only a human decision turns a one off demo into the thing every future build in that vertical starts from. Do not infer approval from a demo simply passing its own test.
- **Publishing a client's actual data as the vertical template.** A promoted template gets cleaned of the client's name, photos, and text before it is committed as a starter; the client's own project stays a separate, untouched repository.
- **Reintroducing an autonomous deploy step.** An earlier version of this pipeline deployed automatically once stage 6 approved a build. That was deliberately reversed: going live is a manual, human triggered step now, not something any stage of this pipeline does on its own.
- **Reporting the pushed repository as if it were already live.** Stage 7 produces a repository ready for deploy, not a live URL. Do not imply the site is up until a human has actually deployed it.
- **Letting a shape's own checklist push a price back onto the page.** Some vertical shapes still name a visible price as a convention; this pipeline's no price rule overrides that regardless of what the shape file says. Stage 6 checks for a stray price independently of the composition score for exactly this reason.
- **Resolving an ambiguous source fact into a confident claim to keep the pipeline moving.** The same rule `landing-page-copy` and `creative-direction` already apply: log the open question, do not silently pick the more specific, more confident reading.
- **Pushing a maintenance change straight to the branch a live deploy watches.** Every scoped edit goes through a branch and a pull request; going live from a maintenance change still needs the same human review a fresh build's deploy does.
- **Skipping the mandatory check on a maintenance edit because it looks small.** A one line change can reintroduce a price or break a convention as easily as a full build can; the check is not optional just because the edit is small.
- **Treating a broad rewrite as a string of scoped maintenance edits instead of a fresh pipeline run.** Maintenance mode is for pointed changes; a request that touches nearly everything should rerun the pipeline instead of chaining edits that were never meant to add up to a rebuild.

---

## Output format

- The project's own repository, created and pushed, ready for a human to connect to a host and deploy.
- `BRIEF.md` from stage 3, kept with the project as reference for any future edit.
- If a template was promoted: a note of which vertical now has an official starter and where it lives.
- If any stage interrupted: a short, specific record of what was asked and how it was resolved, so the next run through the same vertical benefits from it.
- For a maintenance run: a branch and pull request on the project's own repository, never a direct push to the branch a live deploy watches.

---

## Reference files

- [`references/pipeline-phases.md`](references/pipeline-phases.md) - the exact dispatch shape for each stage, including the structural design pairing used when no template exists yet.
- [`references/template-promotion.md`](references/template-promotion.md) - the human gated path from an approved, template candidate build to a published starter for its vertical.
- [`references/deploy-and-repo.md`](references/deploy-and-repo.md) - what happens after stage 6 approves a build: repository creation and push, and why going live from there is a manual, human step rather than part of this pipeline.
- [`references/maintenance-mode.md`](references/maintenance-mode.md) - the exact dispatch shape for a scoped change to an existing project, one per category of request.
