---
name: academic-humanizer
description: |
  General-purpose academic paper humanization and AI-style reduction for Chinese or English manuscripts, reviews, proposals, abstracts, introductions, related work, methods, results, discussions, and conclusions. Use when the user asks to remove AI-like writing, reduce AIGC traces, make academic prose less template-like, lower repetition while preserving meaning, compare before/after revisions, or rewrite while keeping citations, terminology, data, formulas, and claims intact. Also trigger on Chinese requests such as “论文去 AI 味”, “降 AIGC 痕迹”, “论文润色但不要模板化”, “降重并说明前后差异”, and “保留引用和术语重新表述”. This skill is domain-general and must not assume medicine, engineering, computer science, social science, humanities, or any other single field.
---

# Academic Humanizer

## Core Purpose

Rewrite academic text so it reads like careful work by a real researcher: specific, restrained, coherent, and sensitive to the conventions of the field. Do not treat the task as simple synonym replacement. Do not turn papers into casual prose, promotional copy, or broad summary.

Preserve facts, variables, data, formulas, citation markers, proper nouns, technical terms, conceptual boundaries, and the main argumentative sequence. Do not invent literature, results, experiments, data, mechanisms, or causal claims.

## Operating Principles

1. Preserve scholarly credibility
   Keep the research object, method, result, limitation, and evidential strength intact. Adjust expression, not factual content.

2. Remove template-like writing without removing academic style
   Cut mechanical transitions, stock phrases, vague praise, and formulaic structure. Keep necessary rigor. Do not add casualness, first-person commentary, emotional judgment, or unsupported opinions merely to sound human.

3. Let section context determine style
   Abstracts should be compact. Introductions should motivate a specific problem. Literature reviews should compare lines of work. Methods should be precise. Results should be direct. Discussions should explain boundaries and implications. Do not use the same voice for every section.

4. Stay domain-general
   Infer the research object, terminology, evidence type, and writing purpose from the user’s text. Do not assume any medical, AI, engineering, or social-science scenario unless it appears in the source.

5. Avoid detection guarantees
   Reduce AI-like writing patterns and repetitive phrasing, but never promise to pass an AIGC detector, plagiarism checker, or reviewer screening.

## Diagnose First

Before rewriting, scan for patterns that are actually present:

- Generic openings: stacked phrases such as “with the development of...”, “in recent years...”, or “has attracted wide attention”.
- Empty significance: “plays an important role”, “is of great significance”, “lays a foundation”, or “promotes development” without a concrete object.
- Mechanical parallelism: forced three-part lists, long noun chains, repeated “not only... but also...” or equivalent structures.
- Synonym-substitution damage: terminology shifted merely to reduce repetition, weakening conceptual precision.
- Excessive hedging: too many weak qualifiers that blur the claim.
- Vague attribution: “studies show”, “experts believe”, or “previous work indicates” without a citation or clear context.
- Translationese or machine-like syntax: long sentences with weak main clauses, dense connectors, and abstract nouns.
- Repeated explanation: adjacent sentences restate the same fact with only minor wording changes.
- Stock endings: “future work is still needed” or “has broad application prospects” without a specific limitation or direction.

## Rewrite Strategy

1. Compress the main claim
   Identify the core proposition of each paragraph. Remove padding, unsupported value judgments, and repeated explanations.

2. Rebuild logic where needed
   Prefer a clear sequence: research object, problem, method or evidence, result or limitation. If the original logic is already sound, make local edits only.

3. Replace vague praise with concrete content
   Turn “important role”, “key challenge”, and similar phrases into specific mechanisms, variables, costs, risks, or boundaries.

4. Preserve stable terminology
   Do not replace technical terms, model names, metrics, dataset names, theory names, abbreviations, or citation markers merely for variation. Standardize full names and abbreviations on first mention when useful.

5. Vary sentence rhythm
   Use longer sentences for conditions and causal relations, shorter sentences for claims or conclusions. Avoid several consecutive sentences with the same grammatical frame.

6. Use transitions only when they carry logic
   Remove automatic connectors such as “moreover”, “therefore”, “however”, and “meanwhile” when the relation is already clear or not actually present.

7. Edit by paper section
   - Abstract: reduce background and foreground the problem, method, result, and contribution.
   - Introduction: begin from a concrete gap rather than a grand trend.
   - Related work or review: show categories, differences, and tensions instead of listing papers.
   - Methods: prioritize accuracy; keep definitions, steps, parameters, and assumptions.
   - Results: state observations, comparisons, and trends without inflated interpretation.
   - Discussion: explain mechanisms, scope, limitations, and open questions.
   - Conclusion: return to the main finding; avoid generic future-prospect language.

## Deduplication Guidance

When the user asks for “降重”, “reduce repetition”, or “summarize before/after differences”, treat deduplication as reducing repeated content and template-like phrasing, not as making the text drift away from its meaning.

Use these moves:

- Merge neighboring sentences that repeat the same idea.
- Replace broad background with background directly tied to the study.
- Turn flat item lists into hierarchical argumentation.
- Alternate between higher-level concepts and specific details to avoid dense repetition.
- Keep necessary high-frequency terms, especially keywords and standard names.
- Preserve the position of citation markers unless the user asks to reorganize references.

Do not:

- Change data, metrics, sample sizes, statistical claims, years, or citation markers.
- Replace standard terms just to lower surface repetition.
- Add experiments, literature, conclusions, or application scenarios not present in the source.
- Remove caveats in a way that strengthens the claim.
- Convert all objective academic expression into subjective authorial commentary.

## Output Format

Default output:

1. Revised text
2. Summary of before/after differences
3. Explanation of the AI-style reduction and deduplication strategy

Follow the user’s requested format if they ask for only the revised text, no explanation, tracked changes, a table, or another structure.

The before/after summary should be concrete:

- Which stock phrases or repeated content were removed.
- Which sentences were merged, split, or reordered.
- Which terms, citations, data, or formulas were preserved.
- How the logical focus changed.
- Whether any facts or citations should not be changed.

## Quality Checklist

Before delivering, verify:

- Citation markers, formulas, variables, abbreviations, figure/table labels, and data are not lost.
- No unsupported facts were added.
- Domain terms were not replaced with nonstandard alternatives.
- Each paragraph has a clear main proposition.
- Sentence patterns do not repeat mechanically.
- Connectors are not overused.
- Claim strength matches evidence strength.
- The revised text still reads like a paper, not a news article, marketing copy, or casual explanation.

## Example Pattern

Source:

> With the rapid development of related technologies, this field has attracted increasing attention and plays an important role in multiple aspects, while still facing a series of challenges.

Revision direction:

> Recent studies have focused on three stages: data processing, model training, and deployment cost. Existing methods improve processing efficiency, but data quality control, resource overhead, and cross-scenario reproducibility remain unresolved.

Explanation:

- Removes generic trend and significance language.
- Replaces “multiple aspects” and “a series of challenges” with specific analytical categories.
- Keeps a cautious academic tone without stock phrasing.
