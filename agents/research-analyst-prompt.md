# Research Analyst Prompt

Use this prompt when you want the `research-analyst` agent to turn a rough research idea or partial notes into a decision-ready brief.

```text
Read the research brief template at `/home/ilhyeonchu/dotfiles/agents/research-brief-template.md` and draft a concrete research brief for the current project.

Goal:
- Produce a brief that future agents can use for investigation, implementation, experiment planning, result analysis, and synthesis.

Requirements:
- Use the structure of the template, but remove sections that are clearly unnecessary.
- Keep the output decision-oriented, not just descriptive.
- Separate confirmed facts from working inferences and open questions.
- Do not invent numbers, datasets, experiment IDs, or results that were not provided.
- If something is unknown, keep it explicit as a placeholder or open question.
- Make trade-offs and risks explicit, especially for quality, convergence speed, runtime, and VRAM.
- End with the highest-value next questions and recommended next actions.

Current project context:
- Research area: 3D Gaussian Splatting.
- Active track 1: reduce VRAM by controlling the data passed to the viewer side.
- Active track 2: improve optimization convergence speed and final quality by inserting object-level Gaussian-set priors from a reusable library at the start of optimization.
- Planned track 3: solve quality degradation near block boundaries in block-wise training setups similar to CityGaussian.
- Some experiments are already in progress.
- If the running experiments are not fully specified in the provided notes, keep them as incomplete records instead of fabricating detail.

What I want from you:
- Fill the brief as far as the available context allows.
- Preserve uncertainty honestly.
- Make the active vs planned tracks explicit.
- Highlight what evidence is still missing before a strong recommendation can be made.
- Suggest which agent should be used next for each major need, if that is helpful.

Output format:
- Return the completed research brief in markdown.
- Keep it concise but concrete.
- Prefer direct, reusable wording over narrative prose.

Here is the project-specific context to use:
[PASTE PROJECT NOTES HERE]
```
