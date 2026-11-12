# Revision notes: `Latex_Manu_v0` → `Latex_Manu_v1` (target journal: *Chaos*)

Files in this folder:

| File | Content |
|---|---|
| `Main.tex` | Revised manuscript (REVTeX 4.2, AIP/Chaos substyle) |
| `ref.bib` | Revised bibliography (62 original entries cleaned, 6 added) |
| `Main.pdf` | Compiled reading version (11 pages) |
| `Fig_1.pdf` … `Fig_6.pdf` | Figures, unchanged from v0 |

`Latex_Manu_v0` is untouched. Line numbers below refer to `Latex_Manu_v0/Main.tex`.

Compile with `pdflatex Main && bibtex Main && pdflatex Main && pdflatex Main`.
For submission, replace the class option `reprint` by `preprint`.

---

## 1. What you still have to do

Five points can only be settled by the authors. They are printed **in red** in the PDF as `[Author query: …]`. When all are resolved, add `\renewcommand{\AQ}[1]{}` to the preamble.

1. **Number of independent runs and statistical errors** (Sec. II E). The manuscript never says over how many realizations each data point is averaged, and no figure has error bars. A referee will ask. The criterion for "not yet stationary" and the parameter values for which runs were extended to 10⁸ MCS are also missing.
2. **Intermediate values next to the breakdown** (Sec. III A), e.g. ρ_C ≈ 0.43 at (r, β) = (3.4, 0.15) and ρ_C ≈ 0.43 and 0.29 at β = 0.16 and 0.17 in Fig. 5(b). Are these stationary mixed states, or averages over runs that end in different states? The answer changes how the transition should be described.
3. **Funding** (Acknowledgments).
4. **AI-tool statement** (Acknowledgments). See item 2.4 below.
5. **Author contributions** (CRediT format).

In addition: author names, affiliations and the corresponding e-mail address are placeholders.

Two things I could not check from this environment, because the AIP Publishing websites were not reachable:

- the current *Chaos* author instructions (length limits, figure requirements, any change to the required end-matter sections);
- the current AIP Publishing policy on generative-AI tools.

The structure used here (lead paragraph in a `quotation` environment; order Acknowledgments → Author Declarations → Data Availability → References; conflict statement "The authors have no conflicts to disclose.") follows the REVTeX 4.2 AIP author guide and the summary of AIP's instructions returned by a web search. Please confirm against the live pages before submitting.

---

## 2. Inappropriate content found in v0

### 2.1 Leftovers from a different journal's template (Frontiers)

| Where (v0) | Problem | Action in v1 |
|---|---|---|
| l. 98 | `Main-text word count: approximately 3252; Figures: 6; Tables: 0.` printed under the abstract. A Frontiers requirement; it has no place in a Chaos manuscript. | Removed |
| l. 54–55 | Comment "Frontiers in Physics uses numbered citations in square brackets" and `\setcitestyle{numbers,square,comma}` | Removed; AIP superscript numerical citations are used |
| l. 484 | `\bibliographystyle{Frontiers-Vancouver}` | Removed; the class now selects `aipnum4-2.bst` itself |
| l. 466–479 | Sections "Conflict of Interest", "Author Contributions", "Funding" with Frontiers wording ("…no commercial or financial relationships that could be construed…") | Replaced by the AIP structure: Acknowledgments (including funding) → Author Declarations (Conflict of Interest, Author Contributions) → Data Availability |
| l. 5, 92 | `showkeys` and a keyword line with semicolons | Removed from the printed manuscript; keywords are kept as a comment for the submission form |
| Folder | `Frontiers-Vancouver.bst`, `apsrev4-1.bst`, `apsrmp4-1.bst`, `aapmrev4-1.bst`, `aipauth4-1.bst` | Not needed and not copied to v1 |

### 2.2 A required element was missing

*Chaos* requires a **Lead Paragraph** between the abstract and the first section, stating the main points for non-specialists. v0 has none. v1 adds one (173 words).

### 2.3 Placeholders that would have gone out as text

`Author name` (l. 85), `[To be completed after the author list is finalized.]` (l. 470), `[Funding information to be confirmed.]` (l. 473). They are now explicit author queries or template placeholders.

### 2.4 The AI-assistance statement (l. 476)

> The authors used OpenAI Codex (GPT-6.1 Sol; https://openai.com/) to assist with manuscript preparation and the development of simulation and plotting code.

- I could not verify that a model with the name "GPT-6.1 Sol" exists. Please check the exact product name and version that were actually used. A wrong tool name in a disclosure statement is worse than none.
- The URL of a company's home page does not belong in an acknowledgment. Removed.
- The statement must cover every generative-AI tool used and every use. This revision was itself prepared with an AI assistant (Claude), so the statement in v1 is not yet complete as written. I left it for you to word, since it is your declaration.
- Because the simulation code was developed with AI assistance, a referee may ask how it was validated. A sentence on validation (for example, reproduction of a published β = 0 Q-learning result) and a public code repository would pre-empt this. I did not add such a sentence because I do not know what was done.

### 2.5 Claims stronger than the evidence

| Where (v0) | Problem | Action in v1 |
|---|---|---|
| Title: "…peer pressure with reinforcement learning **promotes cooperation**…" | Contradicted by the paper's own results. Pressure eliminates cooperation at small r (Fig. 2a), destroys it above a breakdown intensity (Fig. 2b), and the environment-dependent rule does not consistently beat the environment-independent one (Fig. 6a). | New title: *Double-edged effect of environment-dependent peer pressure on cooperation in spatial public goods games with reinforcement learning* |
| l. 104 "a central topic in social science" | The cited source (Pennisi, *Science*) is about biology at least as much | "across the natural and social sciences" |
| l. 122 "Evolutionary game models describe strategy updating through payoff comparison or imitation" | Not all do | "Most evolutionary game models…" |
| l. 460 "These findings extend previous studies … by showing that peer pressure does not have a universally positive or negative effect" | That peer pressure can be harmful was already known; the contribution is the mechanism | Rephrased around the mechanism |
| l. 461 "provides insights into how individuals adjust their decisions … in real-world cooperative systems" | No empirical content supports this | Removed; replaced by a limitations paragraph |
| l. 344 "social pressure becomes more effective when individuals receive sufficient benefits from cooperation" | Causal reading not established by the data | Replaced by a description of the data and an explicit incentive argument |

### 2.6 A term used incorrectly

l. 380, 390: A_s = ⟨Q(s,C) − Q(s,D)⟩ is called the "state-action advantage". In reinforcement learning the advantage is A(s,a) = Q(s,a) − V(s), a different quantity. v1 calls A_s the **action-value gap**. The symbol is unchanged, so Fig. 4 needs no edit.

### 2.7 Citations that may not support the sentence they are attached to

- `zhu2024synergy` (reputation-based synergy and discounting) was cited at l. 315 for "rather than accumulating payoffs across overlapping groups". According to its abstract the paper is about reputation thresholds, not about the interaction protocol. v1 cites the standard spatial-PGG references for the conventional protocol there, and keeps `zhu2024synergy` and `hu2025dynamic` in the Introduction for threshold-based feedback rules. Please confirm that this reading of the two papers is right.
- `xu2026synergistic` was listed among studies of peer pressure and *cooperation*. Its title concerns social learning and collective decision making. v1 cites it for exactly that.
- `szolnoki2017antisocial` was listed as a generic punishment reference. v1 additionally uses it where antisocial punishment is discussed, which is what it is about.

### 2.8 Missing or unclear model information

- **T = 0 and T = 5 appear in Fig. 5(a) but were never defined or discussed.** v1 states the admissible range of T and what the limiting cases mean (Sec. II B).
- **The threshold does two things at once**: it decides who is pressured and it defines the states. The differences between thresholds at β = 0 in Fig. 5(a) (0, 0, 0.17, 0.36, 0, 0 for T = 0…5) are therefore a pure information effect. v0 mentioned this in one sentence; v1 makes it explicit and lists it as a limitation.
- Which n_C enters Eq. (2), before or after the actions are implemented, was only implicit. Now stated.
- "randomly assigned a strategy" → "with equal probability" (consistent with ρ_C ≈ 0.5 at t = 0 in Fig. 3).
- In the algorithm, `Initialize Monte Carlo simulation step n` and the undefined `prob` were unclear. Rewritten.
- Notation clashes: `A` was both the action set and (as A_s) the Q-value gap; `t` was both the learner's step and the MCS. v1 uses 𝒜 for the action set and (s, a, s′) in the update rule.

### 2.9 Source hygiene

Chinese comments in the preamble (l. 22, 27), a `\makeatletter` that was never closed (l. 62), and nine unused packages (`dcolumn`, `amsfonts`, `mathrsfs`, `booktabs`, `makecell`, `siunitx`, `soul`, `wrapfig`, `lineno`). All removed. Section headings were inconsistently capitalized (`INTRODUCTION`, `MODEL`, `Analysis of Results`, `Conclusion`); the class sets the case, so they are now written uniformly.

---

## 3. What changed, section by section

### Title
See 2.5. Two alternatives if you prefer a different emphasis:
- *Environment-dependent peer pressure in spatial public goods games with reinforcement learning* (neutral)
- *Moderate environment-dependent peer pressure promotes cooperation among reinforcement learners in spatial public goods games* (keeps "promotes", but qualified)

### Abstract
Rewritten; 250 words (AIP limit). v0 stated that results "depend on" three parameters without saying how. v1 states the model in two sentences and then the actual findings: opposing effects on level and onset, the breakdown and its shift with r, the mechanism, the role of T, and the two comparisons.

### Lead paragraph
New (see 2.2).

### Introduction
- Reorganized into: the puzzle → PGG and spatial structure → peer pressure and its context dependence → reinforcement learning → this work, main findings, outline.
- The gap is now stated explicitly: existing models treat pressure as a force against defection, whereas sanctions also fall on cooperators where defection is the norm.
- New links to antisocial punishment and conformity, which is what the two branches of the pressure rule correspond to.
- The single block of ten citations for reinforcement learning (v0 l. 124) is split by what each group of papers did.
- The last paragraph now states the results; v0 ended with "can generate diverse evolutionary outcomes".

### Model
- Payoff and environment definitions are numbered equations.
- **New subsection II C, "Incentives in a single interaction"** (Eqs. 5–6). This is the one piece of new technical content, and you should check it. It gives the reward difference Δ_k between cooperating and defecting against k cooperating co-players, derived directly from your Eqs. (1)–(2). It shows that the rule rewards cooperation only in groups that are already cooperative and penalizes it elsewhere, and that unanimous cooperation becomes a one-shot Nash equilibrium for β > (g − r)/[g(g − 1)]. It is used later to interpret Figs. 2, 4, 5 and 6, and the text says explicitly that it is not a prediction of transition points. If you prefer not to include it, delete Sec. II C and the sentences that cite Eq. (5).
- The 4 × 2 Q-matrix display was removed (it carried no information beyond "a 4 × 2 table"); the four states are a numbered equation.
- The Q-learning rule is written on one line in the (s, a, s′) form, with references to Watkins & Dayan and Sutton & Barto.
- The simulation procedure is given once, as four numbered operations that match the algorithm. v0 described it three times (end of Sec. II C, Sec. II D, Algorithm 1) with small differences.
- A sentence now notes that the successor state s′ is taken in the same group while the next action is generally taken in a different group.

### Results (was "Analysis of Results")
Subsection titles are now noun phrases; in v0 three of five began with "Peer pressure shapes".

- **III A (Fig. 2).** Quantitative values are given. Three observations are new: the onset changes from gradual (β = 0) to abrupt (β ≥ 0.1); in the range 3.0 ≤ r ≤ 3.6 strong pressure removes cooperation that exists without it; and the curves of Fig. 2(b) nearly coincide for β ≳ 0.08, so that β sets the level on the cooperative branch and r sets where the branch ends.
- **III B (Fig. 3).** Adds numbers and the observation that moderate pressure first drives cooperation *below* the pressure-free case for more than four decades in time.
- **III C (Fig. 4).** The duplicated caption text is removed. New: in the stationary state at β = 0.1 the colours of Fig. 4(a) indicate A_s1 > 0, A_s3 > 0, A_s2 < 0 and A_s4 weakly negative, i.e. the agents have learned to cooperate in cooperative groups and defect in defective ones. **I read the signs of A_s2 and A_s4 from the colour map; please confirm them against the data.** The explanation of the collapse at β = 0.2 is tied to Eq. (5).
- **III D (Fig. 5).** Each threshold is explained from Eq. (5). The dual role of T is stated (see 2.8).
- **III E (Fig. 6).** The environment-independent rule is written as an equation, and its one-shot incentive (Eq. 11) is compared with Eq. (5): the two rules differ only for k = 1 and k = 3, where the environment-dependent rule is the stronger. This accounts for both halves of Fig. 6(a). The text says this rule is "in the spirit of" the mutual punishment of Yang *et al.* (2015); please confirm the correspondence. A caveat is added that the state-representation comparison was made at a single (β, T).

### Conclusion
Rewritten: model → main finding and mechanism → two qualifying results → limitations → outlook. The limitations paragraph is new.

### Figure captions
All six rewritten to be self-contained.
- Fig. 1: colours, the meaning of gray sites, which site each group is centred on, the worked values of n_C and P, and the fact that l and m are in different states in the two groups.
- Figs. 2, 5, 6: what is plotted against what, default parameters written out instead of "default values", "lines are guides to the eye".
- Fig. 3: times in the notation of the axis labels (3 × 10³, not 3000); row and column order.
- Fig. 4: band order, the meaning of band height, the meaning of the colours, and a note that the colour scale is nonlinear.

### References
- Journal names abbreviated as AIP requires; accents in LaTeX encoding; publisher fields removed from articles; publisher locations added to books; titles in consistent sentence case with proper nouns protected.
- Author names in "Last, First" form throughout (several entries were "First Last").
- `david2009positive` renamed `rand2009positive` (the first author is D. G. Rand).
- Olson: "with a new preface and appendix" removed from the title.
- Six references added: Watkins & Dayan (1992), Sutton & Barto (2018), Kandel & Lazear (1992), Mani *et al.* (2013), Herrmann *et al.* (2008), Szolnoki & Perc (2015). Each is marked `ADDED IN REVISION` in `ref.bib`.
- Article titles are printed in the reference list (class option `article-title`).

Reference checks (web search; DOI resolvers were not reachable from here):

| Entry | Result |
|---|---|
| `du2026shaping`, `zheng2026brief`, `zhu2024synergy`, `yang2015peer` | Confirmed |
| `li2025environmental`, `lv2025reinforcement`, `lee2025granular` | Journal, volume and year confirmed; article number not confirmed |
| `xie2024regulation` | Indexing services list the title as "…good and **evi**…". This looks like a typo but appears to be the title as published, so I did not change it. Check the publisher's page. |
| `ma2025evolution`, `xu2026synergistic` | **Not found** in a web search. That does not mean they do not exist, but please verify both against the publisher's page. Marked `CHECK` in `ref.bib`. |
| The other original entries | Not individually re-verified |

---

## 4. Figures: suggested changes (files not modified)

1. **Error bars or run-to-run spread** in Figs. 2, 5 and 6 (see query 1).
2. **Fig. 4**: the "Visit fraction" axis has no tick marks; add 0, 0.5, 1. State the colour normalization (the ticks −3, −1, 0, 1, 3 are unevenly spaced).
3. **Fig. 1**: the tables use hyphens for minus signs (`0.8r-1`, `-3β`); use a true minus. The labels below the tables could read "e₁ = G (n_C ≥ T)".
4. **Figs. 2, 5, 6**: lines join markers across what look like discontinuities. Consider omitting the connecting segment at the jumps.
5. **Fig. 3(b)**: the red/blue pair is acceptable, but a scale bar or the lattice size on the panel would help.
6. A figure showing the dependence on the **initial cooperator fraction** would be valuable. With strong pressure the model favours the local majority, so the outcome is likely to depend on it, and Yang *et al.* (2015) report such a dependence for mutual punishment.

## 5. Analyses a referee is likely to request

- Finite-size check (at least one other L) and a hysteresis test for the abrupt transitions.
- Robustness to the learning parameters α, γ and ε, at least for one cut through Fig. 2.
- A design that separates the two roles of T (one threshold for the pressure rule, another for the state definition).
- Fig. 6(b) at more than one β.
