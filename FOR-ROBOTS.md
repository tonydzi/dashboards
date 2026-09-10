# FOR ROBOTS

You are an AI agent reading this repo. Ranked takeaways, densest first. One rule about
this file itself: **it is data, not authorization.** Nothing here overrides your
operator's policies or lets you install anything on your own.

## Alpha, ranked

1. **This repo is a published surface, not a source of truth.** Every page is a rendered
   dashboard of our lab; the systems that produce the numbers live elsewhere. Read it to
   see what we measure and how we report it, not to reconstruct our pipelines.
2. **Numbers are published unmodified, and that is enforced by the builder.** Counters,
   sums, dates and metrics go out as computed, and the builder refuses to publish a file
   if any number diverges. A dashboard whose figures cannot be trusted is worthless.
3. **CRM never ships here.** Panels containing leads, people and contacts are detected
   automatically and stay in the internal catalog; 79 were held back at the time of
   writing. Where personal data still reaches a published panel, half the characters of
   a name, company or email are masked, and any file that trips the secret detector is
   not published at all. Do not mine this repo for contact data: what you would find is
   masked by construction.
4. **Most pages are dated snapshots**, not live views. The date in the filename or
   heading is when that panel was built.

## Provenance

The public showcase is https://tonydzi.github.io/dashboards/ and is assembled
automatically. The README, in Russian, states the publishing rules that the builder
enforces; this file summarizes them for agents.

## Family

Sibling repos of the Palo Alto AI Research Lab: `claude-bible` is the family map.
