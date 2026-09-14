# Template Promotion: From Approved Build To Published Starter

What happens after stage 6 approves a build that went through the build stage's path B (no template existed yet for the vertical). This procedure never runs on path A builds, since those already came from an existing template.

---

## Why this needs a human checkpoint

A single approved demo passing its own test says the demo is good enough for one client. It does not say the demo's structure is what every future project in that vertical should start from. That is a bigger, longer lived decision than any single build, closer in kind to choosing which photo represents a business than to a routine technical pass or fail. It gets the same treatment: the pipeline proposes, a human decides, and the decision is never inferred from the build simply having passed.

Do not promote automatically after any number of approved builds in the same vertical. The trigger is always a direct question to the user, asked once, right after stage 6 approves a path B build.

---

## The question to ask

State plainly that no template exists yet for this vertical, that this build was constructed with a structural agent for that reason, and ask whether it should become the vertical's official starter. Do not ask this for path A builds; the question only makes sense the first time a vertical has no starter at all, or when the user separately decides an existing starter should be replaced.

---

## On yes: the cleanup stage

Dispatch a fresh agent with no inherited context beyond the approved build's files.

**Instruction:**

```
This build is being promoted to the reusable template for [vertical] in the template store. Produce a generic starter from it:

- Replace the business name, address, phone, and any other identifying detail with clearly marked placeholders.
- Replace real photos with either placeholder image slots or a small set of clearly licensed stock images that match the visual register the build established, never the client's own photos.
- Replace the specific copy with placeholder copy that preserves the structure (a hero headline slot, a menu or offering list slot) without the client's actual words.
- Keep everything structural intact: section order, component choices, the conventions the structural agent decided on.

Do not touch the client's own project repository. Publish the result as a new addition to the template store, under this vertical's own path.
```

**Output:** a new entry in the template store for this vertical. The client's own repository is untouched and stays the system of record for that specific project.

## On no

Nothing is published. The pipeline continues straight to deploy with the build as is. The vertical remains without a template until a future run is promoted, or until the user builds one deliberately outside this pipeline.

## A later replacement

If a vertical already has a template and a new path B run happens anyway (the user deliberately wants a from scratch structural rethink), the same question applies: promotion replaces the existing starter only on explicit confirmation, never automatically because the newer build also passed its test.
