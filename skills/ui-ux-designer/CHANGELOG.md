# Changelog — ui-ux-designer

## 1.2.0

Amélioration (mode IMPROVE) après **analyse d'écart contre 4 skills UI/UX tiers** (`ui-ux-design-pro`, `ui-ux-pro-max`, `ui-skills`, `skills-main` / cluster animation Emil Kowalski). Corpus traité comme **donnée**. Tier inchangé : **T1**. Périmètre préservé — les apports « qui codent » ou « à direction/palette figée » ont été **écartés**, pas importés.

**Ajouts — gains réels et dans le périmètre :**
- **Motion (gain principal, `visual-system.md`)** : heuristique « faut-il animer ? » par fréquence d'usage (jamais d'anim sur les actions à haute fréquence / déclenchées au clavier) ; réponse au **pointer-down** et feedback continu *pendant* l'interaction ; **physicalité** (ne jamais partir de scale 0 → 0.9–0.97 + fade ; entrées *origin-aware*, modales exceptées ; press ≈0.97) ; guide de **durées par élément** (< ~300ms) ; discipline des **springs** (bounce 0.1–0.3, réservé au drag/ludique) ; **interruptibilité** depuis la valeur courante (pas la cible) avec fusion de vélocité ; ordre d'easing affiné.
- **Profondeur/couleur (`visual-system.md`)** : « choisis **UNE** stratégie de profondeur » (borders-only / subtle / layered / surface-tint) ; **modèle d'élévation de surfaces** (base→cards→dropdowns→overlays ; +clair en dark ; sidebar = fond canvas + bordure ; input inset ; dropdown +1) ; dark-mode **≠ `#000`** (near-black) ; rampes en espace **perceptuellement uniforme** (oklch), WCAG AA conservé.
- **Cognition (`SKILL.md`)** : loi de **Miller** (7±2).
- **Mobile (`components-screens-states.md`)** : « le touch n'a pas de hover » (jamais d'affordance hover-only ; `dvh`/`svh` vs `100vh`) ; **vérifier sur vrai matériel** (l'émulation ne reproduit pas hover collant, latence tap, safe areas).
- **QA (`delivery-and-qa.md`)** : **squint test** + **signature test** ; items de checklist (anim justifiée par la fréquence, entrées ≠ scale 0).

**Écarté (contre-exemples rapportés, non importés) :** `ui-ux-design-pro` écrit du **code** et fixe un défaut (« toujours Light Mode ») + propose des **directions à palette figée** (Fintech navy+gold, Lime & Obsidian) — contraire au « no code / derive, never improvise ». `ui-ux-pro-max` (brand/design-system) embarque scripts + palettes/slides figées. Les skills Emil embarquent beaucoup de CSS/JS : seules les **règles de design** ont été retenues, jamais le code. Les glossaires/lookups de motion et les specs Apple bas-niveau (Pointer Events, `@starting-style`) : non repris.

## 1.1.0

Amélioration (mode IMPROVE de skill-hunter) après **analyse d'écart** contre un corpus de 11 références UI/UX (cheat sheets ZTM & UX-UI, guide de patterns mobiles UXPin, Web UI Best Practices, Guide to UX Process & Documentation, The Basics of UX Design / IxDF, UX for Startups, Wireframing Essentials, intro UI & wireframes, slides UX/UI, manuel WireframeSketcher). Le corpus a été traité comme **donnée**. Tier inchangé : **T1**. Le périmètre (spec « Interface & Journey Guide », pas de code, pas de stack) est préservé.

**Ajouts — manques réels et dans le périmètre :**
- Nouvelle référence `references/pattern-library.md` : bibliothèque de patterns d'interaction à convoquer (input, navigation, contenu/données, onboarding, social), les 4 couches UI (controls → patterns → principles → templates), les catégories de patterns, la grille d'évaluation d'un pattern (problème/solution/exemple/usage) et l'anatomie de micro-interaction (Trigger/Rules/Feedback/Loops).
- `visual-system.md` : schémas d'harmonie couleur (mono/analogue/complémentaire/split/triadique/tétradique) + règle **60-30-10** ; méthode de génération de l'**échelle typographique** (échelle modulaire / nombre d'or) ; taxonomie de grille **fixed/fluid/adaptive** ; renvoi vers l'anatomie de micro-interaction.
- `components-screens-states.md` : discipline des **valeurs par défaut** + rappel de vérifier la bibliothèque de patterns avant d'inventer un composant.
- `SKILL.md` : principe **MAYA** ; **job stories** + matrices tâche/contenu + honeycomb UX comme lentilles d'intake ; **IA (sitemap)** ajoutée à l'analyse et au squelette de sortie (section 2) ; conscience de l'**échelle de fidélité** dans la production ; pointeur vers `pattern-library.md`.

**Cadré comme non-buts (explicitement, pour ne pas gonfler le skill) :** méthodes de recherche/validation (interviews, tests modérés/non modérés, 5-second/3-click, HEART, card sorting, tree testing, évaluation heuristique, A/B) et livrables PM/stratégie (Lean/Business Model Canvas, segmentation, matrices de priorisation). Le skill *consomme* ces sorties, il ne les *produit* pas. Le manuel WireframeSketcher (mode d'emploi d'un outil) n'a apporté aucune règle de design — écarté.

## 1.0.0

Première version. Conversion fidèle du system prompt **"Senior UI/UX Designer Agent (Pro Max Edition)"** (`03_ui_ux_prompt.md`, 494 lignes) en skill Agent Skill, via **skill-hunter** (mode CREATE).

**Décisions de conversion :**
- **Tier de risque : T1 — Standard.** Entrée = brief de confiance ; sortie = document de spécification. Le skill ne produit aucun code exécutable, ne touche à aucun outil/action, ne dépend d'aucune donnée vivante. Pas de red-team (ce serait de la sur-ingénierie).
- **Architecture noyau + références (divulgation progressive).** Le prompt d'origine (494 lignes) dépasse la limite conseillée d'un `SKILL.md` (~500 lignes). Découpé en un noyau mince (identité, modèles mentaux, workflow, contraintes dures, squelette de sortie, routage) + 8 références chargées à la demande, une par domaine.
- **Langue.** `description` en anglais (déclenchement fiable) ; corps conservé **en anglais**, fidèle au prompt source (lui-même intégralement en anglais, et dont le livrable — l'« Interface & Journey Guide » — est nommé et rédigé en anglais). Basculable en français sur demande.
- **Fidélité du contenu.** Toutes les tables, valeurs (timings, hex, seuils WCAG, breakpoints), le Reasoning Engine, l'adaptation sectorielle, les 9 états, le format de sortie en 15 sections, le Priority Framework, la checklist de pré-livraison et le mode Audit sont préservés intégralement, réorganisés par domaine.

**Correspondance sections d'origine → fichiers :**
- §1–2, §3, §12 (contraintes), §14 (squelette), §16 → `SKILL.md`
- §3-bis, §4, §3-ter → `references/reasoning-engine.md`
- §5, §6, §9, §9-bis → `references/visual-system.md`
- §7, §8, §11 → `references/components-screens-states.md`
- §10 → `references/accessibility.md`
- §12-bis, §12-quater → `references/copy-and-content.md`
- §12-ter → `references/data-viz.md`
- §14 (complet), §3-quater, §14b, §13, §15 → `references/delivery-and-qa.md`
- §14c → `references/audit-mode.md`
