# Lessons learned — rules discovered the hard way

Not agreed procedures (those are in `conventions.md`) — these are rules I must act on
with conviction, kept with enough of the story that I remember *why* they bind.

## ★ MATERIALS-QUALITY RULE (2026-07-14)

He caught an **ungrammatical example sentence in vocab.md**: `Lībertātem servitūtī
mālumus` — *mālō* is comparative (*magis* + *volō*) and demands **quam**, never a dative.
The acc.+dat. "prefer X to Y" pattern belongs to *praeferō* / *antepōnō* (dative governed
by the *prae-/ante-* prefix), not to *mālō*.

**Failure mode to guard against: English-shaped syntax mapped onto a Latin verb.** The
dative "felt" right because English says "prefer X **to** Y". Every other defect found in
the same audit was the same class — governance/valency assumed rather than checked
(*nōlō* + bare acc.; *parō* + dat. of purpose, which is post-Augustan and *not in Cic. or
Caes.* per L&S; intransitive *incipiō*, rare though attested).

**RULE: any Latin sentence I author for study materials (vocab examples, homework,
readings, lesson examples) must have its verb's GOVERNANCE checked against a real
dictionary — L&S via Perseus/Logeion — not composed from feel.** He is hand-typing these
into Anki. A bad example sentence gets *memorized*, and it costs more to un-teach than it
ever cost to check.

**AUDIT TRAIL — vocab.md is now fully swept (2026-07-14).** Week 1 (72 examples, 5
changed); Weeks 2–4 (~220 examples, 20 changed across 19 lines) swept by 6 parallel
Opus auditors, each required to cite L&S/primary texts; every claimed defect
independently re-verified by me before editing.

### Defect taxonomy from the Wk 2–4 audit — what to check first next time

1. **False/missing macrons** — `īgnī` (ignis has a SHORT i), `periculum`, `Piratae` ×2,
   `Cato`. He types these into Anki; a wrong quantity is memorized forever. **Macron
   errors were the single largest category. Check quantities, not just syntax.**
2. **Misquotation / broken excerpting** — a Nepos "quote" that was a sentence FRAGMENT
   (bare nominative, verb only inside a relative clause); a Caesar quote that was a
   HEADLESS RELATIVE (`Quī...` with its antecedent left behind in the source); Cato's
   `ōrātor est vir bonus dīcendī perītus` garbled with a doubled *bonus*; the
   Terence/Cicero proverb *fortis fortuna **adiuvat*** spliced with Vergil's *iuvat*.
   **If it carries a citation, pull the source text.**
3. **Wrong collocation with right grammar** — `proelium gerere` (Latin *wages* bellum but
   *joins* proelium: committere/facere); passive `memoriā tenentur` (the idiom is active);
   camp fortified with a `mūrus` (it's `vallum`); `classis nāvēs solvit` (the fleet IS the
   ships — incoherent).
4. **English syntax in Latin clothes** — a shouted word left in the NOMINATIVE inside
   quotes (`clāmō` takes the acc. of the thing shouted).

## ★ VERIFY THE VERIFIERS (2026-07-14)

One auditor flagged bare `tōtō orbe` as poetic-only and wanted `orbis terrārum` — but a
DIFFERENT auditor had quoted Eutropius 6.12 verbatim: *"Rōmānīs **tōtō orbe**
victōribus"*. The sentence is lifted from the very author the week reads. **Left
unchanged.** A subagent citing a dictionary can still be confidently wrong; cross-check
claims against the other agents' evidence before editing.

## Deliberately KEPT after the 2026-07-14 review

Grammatical + classical in construction; collocation preference only — do not re-flag:
`Nihil novī sub sōle` (Vulgate but impeccable partitive gen.), `Sīc semper tyrannīs`
(18th-c. motto, not Roman — but legal Latin), `portās rūpērunt`, `potentiam iūnxērunt`,
`crīmen maiestātis` (Tacitean register, not a Republican-era collocation, but *crīmen* +
gen. of the charge is Ciceronian).
