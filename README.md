![ui-ux-designer](assets/social-preview.png)

# ui-ux-designer

Un **Agent Skill portable de designer UI/UX senior**. Donne-lui un brief, un backlog, un
module isolé ou une demande de refonte, et il produit un unique **Interface & Journey
Guide** en Markdown — design system, tokens sur trois niveaux, specs écran par écran, les
neuf états, motion, UX copy, data-viz et accessibilité WCAG 2.1 AA.

Il **décrit et prescrit** les interfaces avec une précision de niveau développeur. Il **n'écrit
jamais de code et ne choisit jamais la stack technique**, et il **dérive la direction artistique
de ton sujet** (ou d'une palette que tu lui donnes) au lieu de retomber sur un template.

Fonctionne avec **Claude** (Skills, Claude Code, Desktop, Cowork), **OpenAI Codex** et les
autres agents compatibles `AGENTS.md` (Cursor, Windsurf, Aider…), et **tout outil qui accepte
un system prompt Markdown** via le bundle aplati.

---

## Ce qu'il fait

- Dérive un **Design System Blueprint** à partir du secteur et du sujet du produit (un moteur
  de raisonnement, pas une palette figée) : pattern → style → ambiance couleur → typographie
  → effets → règles conditionnelles → anti-patterns à éviter → l'unique élément signature.
- Spécifie des **design tokens sur trois niveaux** (primitive → semantic → component), la
  couleur (schémas d'harmonie, 60-30-10, rampes oklch, dark mode), une échelle typographique
  dérivée, l'espacement/la grille, une stratégie de profondeur unique + l'élévation de surfaces,
  et une motion systémique.
- Prescrit depuis une **bibliothèque de patterns** (input, navigation, contenu/données,
  onboarding, social) et spécifie **chaque état** (default, hover, focus, active, disabled,
  loading, empty, error, success) pour chaque composant et chaque écran — mobile-first.
- Intègre l'**accessibilité** (WCAG 2.1 AA), l'**UX writing**, la **data-viz**, un **mode audit**
  pour les refontes et une **QA de pré-livraison** (priority framework + auto-critique).

## Ce qu'il ne fait pas

- Écrire du code (HTML/CSS/React/quoi que ce soit) — il produit une spec, pas une
  implémentation.
- Choisir la stack technique ou le framework.
- Mener de la recherche utilisateur ou des tests d'utilisabilité, ni produire des livrables
  PM/stratégie — il *consomme* ces sorties, il ne les invente pas.

---

## Installation / utilisation

### Claude — en tant que Skill (claude.ai, Desktop, Cowork)
Télécharge [`dist/ui-ux-designer.skill`](dist/ui-ux-designer.skill) et importe-le dans
**Settings → Capabilities → Skills** (ou là où ta surface importe les skills). Il se déclenche
automatiquement sur les demandes de design UI/UX.

### Claude Code — en tant que plugin
Ce repo est une marketplace de plugin Claude Code. Ajoute-la, puis installe le plugin :
```
/plugin marketplace add dr-spook/ui-ux-designer-skill
/plugin install ui-ux-designer
```
Ou dépose [`skills/ui-ux-designer/`](skills/ui-ux-designer/) dans le `.claude/skills/` de ton projet.

### OpenAI Codex / Cursor / Windsurf / autres agents AGENTS.md
Clone ou intègre le repo ; l'agent lit [`AGENTS.md`](AGENTS.md), qui le pointe vers
[`skills/ui-ux-designer/SKILL.md`](skills/ui-ux-designer/SKILL.md) et ses `references/`.

### Tout autre LLM / GPT perso / system prompt brut
Colle [`dist/ui-ux-designer.bundle.md`](dist/ui-ux-designer.bundle.md) — le skill entier
(SKILL.md + toutes les références) aplati en un seul fichier — comme prompt système / instructions.

> **Divulgation progressive :** Claude en natif ne charge chaque `references/*.md` que quand
> la tâche en a besoin. Le bundle échange ça contre un seul long prompt, pour que les outils
> non-Claude fonctionnent aussi.

---

## Structure

```
ui-ux-designer-skill/
├─ skills/ui-ux-designer/       # le Agent Skill canonique (édite ici)
│  ├─ SKILL.md                  # noyau mince : identité, workflow, contraintes, sortie
│  ├─ references/               # chargées à la demande (reasoning-engine, visual-system,
│  │                            #   pattern-library, components/states, accessibility,
│  │                            #   copy-and-content, data-viz, delivery-and-qa, audit-mode)
│  └─ CHANGELOG.md
├─ dist/
│  ├─ ui-ux-designer.skill      # import 1 clic pour Claude (zip)
│  └─ ui-ux-designer.bundle.md  # build aplati en un seul fichier, pour n'importe quel agent
├─ .claude-plugin/              # manifestes plugin + marketplace Claude Code
├─ AGENTS.md · CLAUDE.md        # points d'entrée cross-agent
└─ LICENSE
```

Le skill dans `skills/ui-ux-designer/` est la source de vérité. `dist/ui-ux-designer.bundle.md`
en est généré — édite le skill, puis régénère le bundle.

## Versioning

Actuelle : **v1.2.0**. Voir [`skills/ui-ux-designer/CHANGELOG.md`](skills/ui-ux-designer/CHANGELOG.md)
pour l'historique complet (construit avec le workflow CREATE → IMPROVE de skill-hunter ; chaque
version consigne une analyse d'écart et un diff clair).

## Licence

[MIT](LICENSE) © 2026 Boubacar Sidiki ZANGO ([@dr-spook](https://github.com/dr-spook)).