---
name: fiche-technique-monkey
description: >
  Générer une fiche technique détaillée aux couleurs de Monkey Lab, destinée à des novices.
  Déclencher ce skill dès que l'utilisateur demande à créer une fiche technique, un guide pratique,
  un tutoriel pas à pas, un mode d'emploi, ou toute documentation pédagogique sur un sujet donné.
  Utiliser aussi quand l'utilisateur dit "explique-moi X pour un débutant", "fais-moi un guide sur X",
  "comment faire X étape par étape", "fiche pratique sur X", ou quand il mentionne la "charte Monkey".
  Le format de sortie par défaut est DOCX (Word), avec HTML comme alternative pour publication web.
  Ce skill produit des documents professionnels, structurés, visuellement cohérents avec la charte Monkey Lab.
---

# Fiche Technique Monkey Lab

## Objectif

Produire une fiche technique détaillée (5–10 pages), pédagogique et accessible à des novices,
sur n'importe quel sujet lié à l'IA, l'automatisation, les outils numériques ou la gestion d'entreprise.
Le document respecte strictement la charte Monkey Lab et est livré en DOCX (+ HTML sur demande).

---

## 1. Collecte d'informations avant de générer

Avant de produire la fiche, vérifier ou demander à l'utilisateur :

| Info | Source |
|------|--------|
| **Sujet** | Prompt utilisateur ou champ Airtable |
| **Format** | DOCX (défaut) ou HTML |
| **Niveau** | Novice (défaut) — ajustable si le sujet l'implique |
| **Visuels** | L'utilisateur fournit-il des captures d'écran ? |
| **Logo** | Utiliser "Noir Jaune.png" (fond clair) ou "Blanc Jaune.png" (fond sombre) |

Si le sujet vient d'Airtable, récupérer les champs pertinents avant de commencer.

---

## 2. Structure de la fiche (12 sections)

Respecter cette structure dans l'ordre. Adapter la densité selon la complexité du sujet.

### PAGE DE COUVERTURE
- Logo Monkey Lab (variant selon fond)
- Titre de la fiche (grand, gras, couleur #23429F ou #E6A911)
- Sous-titre : "Guide pratique — Niveau débutant"
- Date de création / version
- monkey-lab.fr | hello@monkey-lab.fr

### SECTION 1 — C'est quoi ?
- Définition claire et simple du sujet (2–3 paragraphes max)
- Analogie concrète pour ancrer la compréhension
- Encadré **"En une phrase"** : résumé ultra-court

### SECTION 2 — À quoi ça sert ? Pourquoi l'utiliser ?
- Cas d'usage concrets pour un dirigeant ou indépendant
- Bénéfices clés (gain de temps, qualité, simplicité...)
- Encadré ⚠️ **"Ce que ce n'est pas"** : clarifier les idées reçues

### SECTION 3 — Ce qu'il vous faut avant de commencer
- Prérequis techniques (compte, logiciel, abonnement...)
- Niveau de compétence attendu
- Temps estimé pour réaliser le tutoriel

### SECTION 4 — Tutoriel pas à pas
Structure de chaque étape :
```
ÉTAPE N — [Titre de l'étape]
📌 Ce que vous allez faire : ...
🔧 Comment faire :
   1. Action précise
   2. Action précise
   3. ...
💡 Astuce : conseil pratique
📸 [Espace capture d'écran si fournie]
```
Numéroter toutes les étapes séquentiellement (Étape 1, Étape 2...).
Utiliser un langage direct, à la 2e personne du pluriel (vous).

### SECTION 5 — Erreurs fréquentes et comment les éviter
- Tableau 2 colonnes : Erreur | Solution
- 3 à 6 erreurs typiques pour un novice

### SECTION 6 — Bonnes pratiques
- Liste de 5 à 8 conseils concrets
- Encadré ✅ **"Les règles d'or"** (3 max, en gras)

### SECTION 7 — Cas pratique / Exemple concret
- Mini-scénario réaliste (PME, solopreneur, indépendant)
- Montrer le "avant / après" ou le résultat attendu

### SECTION 8 — Pour aller plus loin
- 3 à 5 ressources recommandées (liens, outils complémentaires)
- Suggestion de prochaine étape ou formation Monkey Lab associée

### SECTION 9 — Récapitulatif / Checklist
- Checklist à cocher : les actions clés de la fiche
- Format : ☐ Action 1 / ☐ Action 2...

### PIED DE PAGE (toutes les pages)
- Logo Monkey Lab (petit, discret)
- monkey-lab.fr | hello@monkey-lab.fr
- Numéro de page
- © Monkey Lab [année]

---

## 3. Charte graphique Monkey Lab à appliquer

### Couleurs
| Rôle | Couleur | Hex |
|------|---------|-----|
| Titres principaux | Bleu Monkey | `#23429F` |
| Accents / highlights | Jaune Monkey | `#E6A911` |
| Alertes / attention | Rouge Monkey | `#EF476F` |
| Succès / bonnes pratiques | Vert Monkey | `#06D6A0` |
| Fond encadrés neutres | Gris acier | `#8DA7BE` |
| Texte courant | Noir | `#000000` |
| Fond document | Blanc | `#FFFFFF` |

### Typographie
- **Titres** : Inter Bold (fallback : Helvetica Bold / Arial Bold)
- **Sous-titres** : Inter SemiBold
- **Corps de texte** : Inter Regular (11–12pt)
- **Taille titre H1** : 24–28pt
- **Taille H2** : 18–20pt
- **Taille H3** : 14–16pt

### Logo
- Fond clair → `Noir Jaune.png`
- Fond sombre → `Blanc Jaune.png`
- Ne jamais déformer — ratio horizontal : 2.102
- Toujours placer en haut à gauche de la couverture et en pied de page

### Encadrés types
| Icône | Couleur de fond | Usage |
|-------|----------------|-------|
| 💡 Astuce | Jaune pâle (`#FFF3CC`) | Conseil pratique |
| ⚠️ Attention | Rouge pâle (`#FFE0E8`) | Risque ou erreur fréquente |
| ✅ À retenir | Vert pâle (`#D6FFF5`) | Point clé à mémoriser |
| 📌 Étape | Bleu pâle (`#E8ECFF`) | Contexte d'une étape |

---

## 4. Format DOCX — Instructions techniques

Consulter le skill `docx` pour la génération technique. Points critiques pour ce skill :

```javascript
// Styles à appliquer
const COLORS = {
  blue: "23429F",
  yellow: "E6A911",
  red: "EF476F",
  green: "06D6A0",
  steel: "8DA7BE"
};

// Taille de page : A4 (format européen)
page: {
  size: { width: 11906, height: 16838 }, // A4 en DXA
  margin: { top: 1134, right: 1134, bottom: 1134, left: 1134 } // ~2cm marges
}

// Encadré coloré = tableau 1 cellule avec bordure gauche colorée
// Ne jamais utiliser unicode bullets — toujours LevelFormat.BULLET
// Pied de page : logo + texte + numéro de page via PositionalTab
```

**Flux de génération DOCX :**
1. `npm install -g docx` (si pas déjà installé)
2. Écrire le script JS dans `/home/claude/fiche-[sujet].js`
3. Exécuter : `node fiche-[sujet].js`
4. Valider : `python scripts/office/validate.py fiche-[sujet].docx`
5. Copier vers `/mnt/user-data/outputs/`
6. Appeler `present_files` pour livrer à l'utilisateur

---

## 5. Format HTML — Instructions

Quand l'utilisateur demande une version web (pour monkey-lab.fr) :

- Fichier HTML standalone (tout inline : CSS + contenu)
- Même structure de sections que le DOCX
- Responsive (mobile-first)
- Palette et typographie identiques à la charte
- Google Fonts : `Inter` via CDN
- Impression CSS (`@media print`) : masquer la nav, afficher les couleurs
- Livrer en `.html` via `present_files`

---

## 6. Règles qualité obligatoires

- [ ] Toutes les étapes sont numérotées séquentiellement
- [ ] Chaque étape contient : contexte + actions + astuce
- [ ] Au moins 1 encadré par section (💡 ⚠️ ou ✅)
- [ ] Aucun jargon non expliqué — chaque terme technique est défini à sa première occurrence
- [ ] Ton direct, bienveillant, à la 2e personne du pluriel (vous)
- [ ] Charte couleur respectée (pas d'autres couleurs que les 7 définies)
- [ ] Logo présent en couverture ET en pied de page
- [ ] Numérotation des pages active
- [ ] Relecture de cohérence : la fiche est-elle auto-suffisante pour un novice complet ?

---

## 7. Exemple de prompt déclencheur

> "Fais-moi une fiche technique sur Make (ex-Integromat) pour un dirigeant qui n'a jamais fait d'automatisation."

> "Crée un guide pas à pas sur comment utiliser ChatGPT pour rédiger des emails professionnels."

> "Fiche technique sur la prise en main d'Airtable — format DOCX, charte Monkey."
