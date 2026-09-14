---
name: site-builder-pipeline
description: "Coordinate a chain of isolated agents that turn one request (a business name plus a reference such as a social profile or an existing site) into a finished, deployed demo: research, an isolated visual read, a creative brief, copy, a build that reuses or originates a reusable template for the vertical, a test and fix loop, and an autonomous deploy. Use whenever the user asks to research and build a landing page or demo site for a named business from a handle or URL, wants the build divided across specialized agents instead of one session doing everything, or wants a repeatable pipeline for pre-contract showcase sites. Triggers on build a demo for, research and build a site for, run the site pipeline, generate a showcase site, divide the build across agents, pipeline for a new demo. Does NOT fire for one isolated step already covered by a skill it coordinates (use `creative-direction`, `landing-page-copy`, or `vertical-site-conventions` directly), or for editing an already deployed site."
category: process-and-team
catalog_summary: "Coordinates isolated research, brief, build, test, and deploy agents into one finished demo site"
display_order: 6
---

# Site Builder Pipeline

One request in, one deployed site out, built by a chain of agents that never share more context than the one artifact each needs.

This skill does not do any of the creative or technical work itself. It coordinates. Every stage below is a separate agent or session with no inherited conversation history, given only the specific input that stage requires. The isolation is the point: a build agent that has seen the research narrative starts anchoring to it instead of the brief, and a test agent that has seen the build agent's reasoning starts rationalizing instead of checking. Keeping each stage blind to everything upstream except its one required artifact is what keeps the later stages honest.

---

## When to use

- A business name and one reference (a social handle, an existing site, a physical address) come in, and the ask is a finished, deployed demo, not one step of the process
- The build needs to run unattended after the initial request. It should interrupt only for a genuine problem, an ambiguous fact that needs a human call, or a build that keeps failing its own test
- A vertical (restaurant, retail, clinic, etc.) may already have a reusable starter worth cloning instead of building from zero, and the pipeline should check for that automatically
- Producing another entry in a running series of pre-contract showcase sites, where consistency of process matters more than any single build

## When NOT to use

- Running one stage in isolation (research only, a brief only, a copy pass only). Invoke that stage's own skill (`creative-direction`, `landing-page-copy`, `vertical-site-conventions`) directly instead of the whole chain
- Editing or iterating on a site that is already built and deployed. This skill's scope ends at first deploy
- A project where the user wants to make every creative call personally, in one continuous conversation, rather than delegate stages to isolated agents
- Any step that needs the user's own visual curation (choosing among finished photo or aesthetic candidates). That judgment call is a required interrupt, not something a stage should resolve on its own

---

## Required inputs

- The business name
- One reference: a social handle, a URL, or an address the research stage can start from
- The vertical, if already known (this skips a research guess); otherwise the research stage infers it
- The path or handle for the vertical's reusable template store (a repository or directory the build stage checks before building from zero)
- Where the finished site is deployed to: a host, and separately a source control destination for the project's own repository

---

## The framework: seven stages, one artifact of handoff between each

Each stage is named by what it hands the next stage, not by who runs it. A stage is done when its one output artifact exists and nothing else about that stage's reasoning needs to survive.

1. **Data collection, producing real facts.** Research the business from the reference given. Output a factual document: address, offering, pricing where visible, reviews, real photos. Anything read from an ambiguous source (a caption or comment that supports more than one interpretation, especially an ownership or "we have X" claim) gets logged as an open question next to the facts, not resolved into a confident claim. This is the same discipline `landing-page-copy` and `creative-direction` already apply to ambiguous source material; this stage is where the ambiguity first gets noticed.
2. **Visual investigation, producing an objective read.** Hand only the real photos from stage 1 to a fresh agent with nothing else: no brief, no prior build, no stated preference. It reports palette, materials, light, and mood, and is not allowed to recommend a direction. This is exactly the isolated pass `creative-direction` already documents in its [`references/visual-evidence-investigation.md`](references/visual-evidence-investigation.md); reuse it rather than re-deriving it.
3. **Creative direction, producing a brief.** Run `creative-direction`'s four axis workflow, feeding it the facts (1) and the visual read (2) as required inputs. Output is its standard `BRIEF.md`.
4. **Copy, producing page text.** Run `landing-page-copy` (or the project's equivalent) against the brief (3) and the facts (1). Output is the page's written content, with the same ambiguous data caution already baked into that skill.
5. **Build, producing the site.** See the vertical template branch below; this is the one stage with two distinct paths.
6. **Test and review, producing an approved build or a return trip.** Check the build against `vertical-site-conventions`'s composition checklist for the vertical's shape (eight or more of ten conventions present is the bar) and against the same ambiguous data rule from stage 1. A pass hands the build to deploy. A fail hands the build back to stage 5 with the specific reason, not a summary of everything else; see the correction loop below.
7. **Deploy, producing a live URL.** Once approved, create the project's own repository (every project gets one, independent of whether the host needs it) and deploy the approved files straight to the host. This stage does not wait for a human sign off before going live; it only stops if the deploy itself fails. See [`references/deploy-and-repo.md`](references/deploy-and-repo.md).

### The build stage's two paths

- **A template already exists for this vertical.** The build stage clones it and fills it with the brief (3), the copy (4), and the real facts (1). No new structural decisions are needed; the template already made them.
- **No template exists yet for this vertical.** The build stage brings in a second agent for this stage only, the one making the structural call: which sections exist and in what order, the same call `vertical-site-conventions` already makes for verticals it has a shape for. That agent's job is structure and composition, not aesthetics; palette and type stay with `creative-direction` and `design-standards` and the visual read from stage 2. The two agents deliver one site together, which is simultaneously this project's demo and a candidate for the vertical's next template. See [`references/pipeline-phases.md`](references/pipeline-phases.md) for the exact dispatch shape of this pairing, and [`references/template-promotion.md`](references/template-promotion.md) for what happens to that candidate after stage 6 approves it.

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
9. Dispatch stage 7 (deploy). Report the live URL and the repository back to the user. This is the pipeline's normal end state; nothing here waits for approval.
10. Any stage that hits a genuinely ambiguous fact, a blocked tool, or an exhausted correction loop stops and asks the user directly, naming the specific stage and the specific question, rather than surfacing a general status update.

---

## Failure patterns

- **Letting a later stage read an earlier stage's reasoning instead of its output artifact.** The whole design depends on each stage seeing only the one document it needs. A build agent shown the research agent's exploratory notes anchors on whatever half formed idea appears there first.
- **Skipping the visual investigation's isolation because "it's the same project anyway."** The isolation is the entire value of that stage; a contaminated read is worse than no read, because it looks like independent evidence when it is an echo.
- **Treating a stage 6 failure as an automatic interrupt.** Most failures are correctable by a fresh build attempt with the specific reason in hand. Reserve the interrupt for the attempt cap, not the first failure.
- **Promoting a build to the vertical's template without the human checkpoint.** The pipeline can propose; only a human decision turns a one off demo into the thing every future build in that vertical starts from. Do not infer approval from a demo simply passing its own test.
- **Publishing a client's actual data as the vertical template.** A promoted template gets cleaned of the client's name, photos, and text before it is committed as a starter; the client's own project stays a separate, untouched repository.
- **Treating the deploy stage's autonomy as license to skip the repository.** Every project gets its own repository regardless of how the live deploy itself is triggered; the repository is for control and history, not gated behind the live URL going up.
- **Resolving an ambiguous source fact into a confident claim to keep the pipeline moving.** The same rule `landing-page-copy` and `creative-direction` already apply: log the open question, do not silently pick the more specific, more confident reading.

---

## Output format

- A live URL for the deployed site.
- The project's own repository, created regardless of the deploy mechanism.
- `BRIEF.md` from stage 3, kept with the project as reference for any future edit.
- If a template was promoted: a note of which vertical now has an official starter and where it lives.
- If any stage interrupted: a short, specific record of what was asked and how it was resolved, so the next run through the same vertical benefits from it.

---

## Reference files

- [`references/pipeline-phases.md`](references/pipeline-phases.md) - the exact dispatch shape for each stage, including the structural design pairing used when no template exists yet.
- [`references/template-promotion.md`](references/template-promotion.md) - the human gated path from an approved, template candidate build to a published starter for its vertical.
- [`references/deploy-and-repo.md`](references/deploy-and-repo.md) - what the deploy stage actually does: repository creation and the direct file deploy, and why the two are independent of each other.
