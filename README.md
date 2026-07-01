# Usability Recommendations Ruleset for Gamified Systems

This repository provides the rule base of usability recommendations used to evaluate the usability of gamified systems, supplementary to the article on the usability of gamified systems.

- [usabilityRecommendationsForGamifiedSystems.xlsx](usabilityRecommendationsForGamifiedSystems.xlsx) — the complete rule base.

## Overview

The workbook encodes usability knowledge as a set of **input/output rules**. Every sheet follows the same pattern:

- **INPUT** columns describe the applicability conditions of a rule — the context in which it applies (e.g., age group, application domain, disorder, usability goal, gamification element).
- **OUTPUT** columns provide the resulting recommendation, often together with an illustrative example.

Given a system's context (its target audience, domain, supported accessibility needs, gamification goals, and implemented elements), the matching rules yield the usability recommendations that should be satisfied. Those recommendations are what an evaluation checks the system against.

The rules are grouped into five sheets by the kind of recommendation they produce.

## Sheets

### 1. `Generalised recommendations`

General usability recommendations applicable at the system level (GUR), independent of any specific gamification element.

- **INPUT:** `usabilityGoal`, `usabilityPrinciple`, `ageGroup`, `applicationDomain`, `disorder`, `gamificationGoal`
- **OUTPUT:** `genRecommendation`, `example`

INPUT conditions are expressed as membership/quantifier predicates (e.g., `"children" in ageGroup`, `"education" in applicationDomain`, `some x in disorder satisfies x in [...]`), so a single rule can apply across a range of contexts.

### 2. `Suitable gamification elements`

Gamification elements that are **recommended** for a given context, paired with the usability recommendations to apply when they are implemented. Feeds the evaluation of usability recommendations for recommended gamification elements (URSIGE).

- **INPUT:** `ageGroup`, `applicationDomain`, `disorder`, `gamificationGoal`, `usabilityGoal`
- **OUTPUT:** `gamificationElement`, `usabilityRecommendation`

### 3. `Not suitable gamification elements`

Gamification elements that are **not** recommended for a given context. Used to identify elements that a system implements despite not being recommended, whose usability is then evaluated separately (URUIGE).

- **INPUT:** `ageGroup`, `applicationDomain`, `disorder`, `usabilityGoal`, `gamificationGoal`
- **OUTPUT:** `notSuitableGamificationElement`

### 4. `ISO`

Usability recommendations for gamification elements derived from the ISO 9241 family of standards. Scoped by the gamification element they apply to.

- **INPUT:** `gamificationElement`
- **OUTPUT:** `ISOrecommendation`, `elementUsabilityRecommendation`, `example`

### 5. `WCAG`

Usability recommendations for gamification elements derived from WCAG 2.2, scoped by both the gamification element and the relevant disorder (e.g., hearing impairment, visual impairment).

- **INPUT:** `gamificationElement`, `disorder`
- **OUTPUT:** `WCAGrecommendation`, `elementUsabilityRecommendation`, `example`

## How the sheets fit together

An evaluation of a gamified system draws on these sheets as follows:

- **`Generalised recommendations`** yields the general usability recommendations (GUR) to check at the system level.
- **`Suitable gamification elements`** determines which elements are recommended for the system's context and the usability recommendations that come with them (URSIGE). The ISO- and WCAG-derived recommendations (sheets 4 and 5) supply element-specific rules for those elements.
- **`Not suitable gamification elements`** flags recommended-against elements; if a system still implements them, their usability is assessed under URUIGE, again using the ISO and WCAG rules.
