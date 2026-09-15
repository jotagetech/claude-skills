# Repository And Deploy: The Final Stage In Detail

The pipeline's automated scope ends with a pushed, ready to deploy repository. Going live is a separate, manual step, done by a human, not dispatched as a stage of this pipeline.

---

## The repository, always created and pushed

Every project gets its own repository in source control. Create it and push the approved build's files as the first commit. This is the pipeline's actual last automated action; nothing past this point runs unattended.

## Going live is manual, and linked to the repository

Once the repository exists, a human connects it to the hosting platform and triggers the deploy themselves, using the platform's own repository linked deploy (so a future push redeploys automatically once it is set up). No agent in this pipeline calls a direct file deploy or triggers a live deploy on its own. This is a deliberate reversal of an earlier version of this pipeline that deployed autonomously; that approach produced a live, public deploy before anyone had looked at it, which is more than this project wants automated for now.

**This project's current tooling:** repositories live in the team's GitHub organization. Once a repository is pushed, connecting it to Vercel (via the dashboard or a repository linked deploy tool) and triggering the first deploy is something a person does, on request, not something a stage of this pipeline does on its own.

## What this stage reports back

The repository's location, and a note that it is ready for a human to connect and deploy. If a template was promoted earlier in the run, note that too, since it is easy to lose track of a decision made a few stages earlier. This stage does not report a live URL, because producing one is no longer part of what it does.
