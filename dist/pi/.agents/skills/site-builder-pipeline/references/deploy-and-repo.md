# Deploy And Repository: The Final Stage In Detail

Two separate outputs, not one. Keep them decoupled: neither has to wait on the other.

---

## The repository, always created

Every project gets its own repository in source control, regardless of how the live deploy itself happens. This is for version history and later handoff (if the project ever needs to change ownership), not a dependency the deploy step needs. Create it and push the approved build's files as the first commit.

## The live deploy, autonomous once stage 6 approves

Once the build has passed stage 6, deploy the approved files straight to the host. Prefer whichever mechanism does not require the repository to already be linked and building; a host that accepts a direct file tree and returns a live URL immediately is faster and has fewer failure points than one that requires a repository connection to be wired up first. If the host also offers a repository linked deploy (so that a future push redeploys automatically), that is a separate, optional convenience layered on top of the repository already created above, not a substitute for the direct deploy.

**This project's current tooling:** repositories live in the team's GitHub organization. Live deploys go to Vercel, using a direct file deploy rather than a repository linked one, since the direct path does not depend on the repository push succeeding first (source control permission prompts or a blocked push should never block the live URL from existing).

## No approval gate before going live

This stage does not pause for a human sign off before publishing. That is a deliberate change from how earlier builds in this project were handled, where every deploy waited for explicit confirmation. The whole point of this pipeline is a finished, live demo at the end of one unattended run; a mandatory pause here would defeat that. The only thing that stops this stage is the deploy mechanism itself failing (a tool error, a naming collision, an authentication problem), which is a genuine problem and gets reported as one, not treated as a routine status update.

## What to report back

The live URL and the repository's location, together, as the pipeline's closing message. If a template was promoted earlier in the run, note that too, since it is easy to lose track of a decision made a few stages earlier.
