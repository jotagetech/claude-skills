# Visual Evidence Investigation

An optional step that runs before the axis walk, when the project already has real visual material to look at: a client's own product photos, a physical space, a social media feed, existing packaging. It produces evidence the user's own read can be checked against, instead of relying only on how the user remembers or describes that material.

## When to use

- The project has real photos, video stills, or a physical space that nobody has looked at yet with fresh eyes for this brief
- The user's description of the material ("it feels warm," "pretty simple") is the only input so far, and a second, independent read would sharpen or correct it

## When to skip

- Pure greenfield: no product, space, or existing presence exists yet to photograph
- The user already supplied curated reference URLs with clear notes on what resonates; that already satisfies the reference-gathering need this step exists to support

## Why isolation is the whole point

The value of this step comes entirely from the investigating agent knowing nothing about the project beyond the raw images. If it has seen the brief, a prior spike's aesthetic direction, or the user's stated preference, its report stops being independent evidence and becomes an echo of what it already expected to find. Run this as a session or subagent dispatch with no inherited conversation history: no access to `BRIEF.md`, no summary of what the user said they wanted, nothing but the images and the prompt below.

## Dispatch prompt

Hand the isolated agent the raw images (or a contact sheet of several) plus this instruction, unmodified beyond swapping in the actual count and source:

```
You are looking at N photos of [describe the source only: "a retail store's storefront and product shots," "a restaurant's dining room and dishes," etc, nothing about brand, project, or intended audience].

Describe only what is actually visible. Do not suggest a design direction, a tone, or a target audience. Report:

1. Dominant colors, named in plain visual language (e.g. "a warm terracotta," "a pale sage green"), not as hex codes.
2. Recurring materials, textures, or objects that show up across multiple photos.
3. Light quality: natural or artificial, warm or cool, time of day if it shows, harsh or soft.
4. Two or three mood or season words that an uninformed viewer would reach for looking at this set, and the specific detail in the photos that justifies each word.

If the photos disagree with each other (some warm, some cold; some sparse, some cluttered), say so instead of averaging it away.
```

## Output

A short report, four sections matching the four prompt items above. No recommendation, no axis position, no synthesis. That interpretation happens back in the main workflow, in step 3, where the report is weighed against the user's own read of the same material.

## Feeding it back in

When this report exists, the axis walk and the "capture inspiration references" step treat it as a reference alongside anything the user supplied directly: evidence from the project's own material, not outside inspiration. If the report and the user's stated preference disagree (the photos read as warm and cluttered, the user asked for cool and restrained), surface the gap explicitly and ask which one the brief should follow; don't silently pick one.
