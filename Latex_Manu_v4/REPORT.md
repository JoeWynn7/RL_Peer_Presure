# Report on `Latex_Manu_v4`

This report explains the reasoning behind the final draft: what the paper's strengths are, how the narrative is built to show them, what changed from v3, and what is still open before submission.

## 1. What the paper claims, in one paragraph

Existing peer-pressure models decide in advance which behavior is pressured. We let the group decide: a group with enough cooperators pressures its defectors, and a group with too few pressures its cooperators. Individuals perceive which kind of group they are in and learn by Q-learning. The result is that pressure strengthens whatever already prevails in a group. It raises cooperation where cooperative groups can be maintained and removes it where they cannot, and the learning dynamics show why.

Every section of v4 is written to support this one statement.

## 2. Key strengths and where each is shown

| Strength | Why it matters to a referee | Where it appears |
|---|---|---|
| **A pressure rule in which the group environment decides who is pressured** | It is a qualitative change from the two existing rules, not a parameter variation. Under the mutual-penalty rule (Yang et al.) both behaviors are always penalized. Under the norm rule (Deng et al.) cooperators never are. | Introduction, paragraphs 3 and 4; Model, Sec. II B |
| **The threshold as a control parameter** | It turns "what counts as a cooperative group" into something that can be varied. The norm rule is the special case of the lowest threshold. | Sec. II B (limiting cases); Sec. III D; Fig. 5 |
| **Learning individuals who perceive the environment** | An imitator carries one strategy into all five of its groups. A Q-learner with the joint state can act differently in each. This is what makes a group-level rule meaningful. | Introduction, paragraph 5; Sec. II C; Fig. 6(b) |
| **A mechanism, not only an outcome** | Fig. 4 shows what individuals learn in each state and when. Earlier peer-pressure papers with imitation cannot show this. | Sec. III C |
| **Two opposing effects of pressure** | Weak pressure lets cooperation appear at lower synergy factors; strong pressure gives higher levels at higher ones. This is the clearest new result in Fig. 2. | Sec. III A |
| **A direct test against the existing rule** | Fig. 6(a) compares our rule with the mutual-penalty rule applied to groups. The paper reports honestly that neither is better everywhere, and explains why. | Sec. III E; Eq. (8) |
| **An analytical argument** | The reward difference in a single interaction explains the direction of every main result without being presented as a prediction. | Appendix; used in Secs. III A, III C, III E |

## 3. What is not claimed as new

Yang et al. (2015) and Gao et al. (2023) already report an optimal moderate pressure, and Gao et al. report discontinuous transitions. Yang et al. also show an initial decline followed by recovery. v4 cites them at exactly those points (Secs. III A and III B). This protects the paper: a referee who knows these papers will see that we know them too, and the novelty rests on the rule, the threshold, and the learning mechanism.

## 4. Narrative structure

**Introduction (six paragraphs, about 830 words).**
1. Cooperation is costly and can be exploited.
2. Evolutionary games, the public goods game, spatial structure, and added mechanisms, ending on environmental feedback.
3. Peer pressure, the two existing rules, and their shared assumption: the pressured behavior is fixed in advance.
4. In reality the same behavior gets different feedback in different groups. Evidence in both directions. The level of cooperation in a group is therefore a local environment, it changes with the members' actions, and the level at which expectations change need not be one half.
5. Responding to an environment requires learning; existing Q-learning states omit the group.
6. This work and its main findings.

Each paragraph ends on the idea that the next one starts from. Paragraph 4 carries the argument that the model is reasonable, so it has the most references.

**Model.** The rule is stated, then defended in two sentences at the point where a reader first meets pressure on cooperators: it represents disapproval of behavior that differs from what is typical, and it does not mean defection is desirable. The limiting thresholds are then tied to the existing norm rule.

**Results.** The order follows a question-and-answer logic.
- A. What does pressure do? (Fig. 2)
- B. How does it happen in time and space? (Fig. 3)
- C. What do individuals learn? (Fig. 4)
- D. What does the threshold change? (Fig. 5)
- E. Is the environment dependence needed, and is the joint state needed? (Fig. 6)

**Conclusion.** Background and gap in three sentences, the model, four findings, one sentence that states the general lesson, one sentence of limitations, and three directions for future work.

**Captions.** Each begins with the conclusion of the figure, then the panels, then only the parameters that differ from the defaults.

## 5. Questions a referee is likely to ask, and the paper's answers

| Question | Answer in v4 |
|---|---|
| Why are cooperators pressured in a group of defectors? | Introduction paragraph 4 (Lindström et al.; Herrmann et al.; Irwin and Horne; Parks and Stone) and the two sentences in Sec. II B. The lowest thresholds remove this pressure entirely, and Fig. 5 shows those cases. |
| Is this just the majority rule? | No. The threshold is varied from 0 to 5; the majority rule is one value. The Introduction no longer uses the word "majority". |
| Is "moderate pressure is best" new? | Not claimed. Yang et al. and Gao et al. are cited at that point. |
| Is the environment dependence actually beneficial? | Not always, and the paper says so (Fig. 6(a)), with the reason from Eq. (8). |
| Does the threshold change the pressure or the information? | Both. Sec. III D states that the differences at zero pressure come from the state definition alone, and the Conclusion lists separate thresholds as future work. |
| How many runs? | Twenty per data point; Figs. 3 and 4 are single runs. Stated in Sec. II D. |

## 6. Changes from v3

- **Abstract and Lead Paragraph:** the gap is now stated as "existing models specify in advance which behavior receives pressure". The phrase "what most members of a group do" is gone, in line with the environment framing. The abstract is 249 words and has no symbols.
- **Introduction:** paragraph 3 is shorter (the extensions of the first rule are folded into its citation). Paragraph 4 is tighter, with the same six steps. The final paragraph now mentions the comparison with the rule that penalizes both behaviors.
- **Model:** one sentence added on which results are averages and which are single runs.
- **Sec. III A:** the explanation speaks of cooperative and defective environments, not of the local majority. Yang et al. and Gao et al. are cited for the optimal intensity and abrupt transitions.
- **Sec. III B:** Yang et al. cited for the decline followed by recovery.
- **Sec. III D:** the lowest threshold is linked to the rule of Deng et al.
- **Sec. III E:** the comparison rule is identified as the first existing rule applied to groups, citing Yang et al.
- **Conclusion:** first paragraph rewritten to match the Introduction; a sentence added stating the general lesson.
- **Data Availability:** now gives the public code repository.
- **References:** 69 entries. The two entries I could not confirm earlier (Ma et al. 2025; Xu et al. 2026) have since been confirmed and are no longer flagged.

## 7. Decisions you may want to reverse

1. **Citing Yang et al. in Sec. III E.** You were earlier concerned that this might suggest the problem was already solved. Now that the Introduction describes their rule, I think naming it is safer than leaving a knowledgeable referee to notice it. To undo it, delete the sentence beginning "This is the first kind of rule discussed in Sec. I".
2. **The repository link in Data Availability.** Remove the first sentence if you do not want the code linked.
3. **"Similar to a discontinuous phase transition."** Kept with "similar to", because there is no finite-size or hysteresis analysis.

## 8. What is still open before submission

These cannot be completed without you.

- **Author block, Acknowledgments, Author Contributions.** All three are placeholders. Two print in red.
- **AI-use statement.** It was removed with the old Acknowledgments. AIP expects such use to be disclosed, and this manuscript was revised with an AI assistant.
- **Three bibliography entries** (marked `CHECK` in `ref.bib`):
  - Zhu et al., Commun. Phys. 7 (2024): the article number is missing.
  - Li et al., Chaos 36, 083114 (2026): only the first author is confirmed.
  - Xie and Liu (2024): the indexed title reads "good and evi"; confirm the published spelling.
- **Two sentences worded from abstracts only.** The descriptions of Lindström et al. and Irwin and Horne in Introduction paragraph 4.
- **One sentence read from a figure.** In Sec. III C, "A_{s2} is negative and A_{s4} remains slightly negative" in the stationary state comes from the colours of Fig. 4(a). Please confirm it when the data are at hand.
- **Unverified statements about cited models.** That Hu et al. and Ma et al. use the mutual-penalty rule is taken from their abstracts.
- **Runs extended to 10⁸ MCS.** The text says some parameter sets were extended, but which ones is not recorded.
- **Journal requirements.** I could not open the Chaos author instructions from this environment. For submission, change `reprint` to `preprint` in the class options. If the editorial office asks for the house citation style, remove the `\setcitestyle` line and move the citations after the punctuation.
- **Figures.** Unchanged. Error bars on Figs. 2, 5, and 6 would be easy to add now that there are 20 runs per point, and a referee may ask for them.

## 9. Length

About 3,900 words of main text (Introduction to Conclusion, without captions and the Appendix), 10 pages in the two-column layout, 6 figures, 69 references.
