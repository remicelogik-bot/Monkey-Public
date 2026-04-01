---
name: charte-monkey
description: "Charte graphique complète de Monkey Lab à appliquer sur tous les documents produits. Déclencher ce skill dès qu'un document visuel est produit : PDF, DOCX, présentation, fiche pédagogique. Il définit les couleurs, typographies, logos et règles de mise en page obligatoires."
---

# Skill : Charte graphique Monkey Lab

Ce skill est **obligatoire** pour tout document produit au nom de Monkey Lab.
Il définit **comment appliquer le style visuel** — couleurs, typographie, logos, mise en page.

---

## 🔴 Règles absolues — interdictions strictes

1. **JAMAIS de reconstruction SVG du logo** — utiliser uniquement les fichiers PNG du projet
2. **JAMAIS la police Congenial** — Inter uniquement (ou Helvetica/Arial en fallback)
3. **JAMAIS de serif ni de police décorative**
4. **JAMAIS mélanger rouge (#EF476F) et vert (#06D6A0)** sauf usage fonctionnel (alerte/validation)
5. **JAMAIS un fond surchargé** — style sobre, beaucoup d'espace blanc

---

## 🖼️ Logos — règle de sélection OBLIGATOIRE

> ⚠️ **La règle est simple : le logo doit toujours être lisible sur son fond. En cas de doute, appliquer le tableau ci-dessous sans exception.**

| Fond de la zone | Fichier à utiliser | Emplacement typique |
|---|---|---|
| **Fond blanc ou clair** | `Noir_Jaune.png` | En-tête sur fond blanc, diapos internes |
| **Fond bleu (#23429F), noir ou foncé** | `Blanc_Jaune.png` | Bandeau titre, diapo de couverture, en-tête coloré |
| **Pied de page sur fond blanc/clair** | `Mono_noir.png` | Bas de page discret, filigrane |
| **Pied de page sur fond foncé** | `Mono_Blanc_.png` | Bas de page sur fond bleu ou noir |

### ❌ Erreurs interdites
- `Noir_Jaune.png` sur fond bleu → **INTERDIT** (logo sombre sur fond sombre = illisible)
- `Blanc_Jaune.png` sur fond blanc → **INTERDIT** (logo blanc sur fond blanc = invisible)
- Reconstruire le logo en SVG ou HTML → **INTERDIT**

### Chemins des fichiers logo dans le projet
```
/mnt/project/Noir_Jaune.png       → logo complet, à utiliser sur fond clair uniquement
/mnt/project/Blanc_Jaune.png      → logo complet, à utiliser sur fond foncé uniquement
/mnt/project/Mono_noir.png        → monogramme discret, fond clair
/mnt/project/Mono_Blanc_.png      → monogramme discret, fond foncé
```

---

## 🎨 Palette de couleurs

| Rôle | Nom | Hex | Usage |
|---|---|---|---|
| Primaire | Bleu | `#23429F` | En-têtes, titres H1, bandeaux, bordures structurelles |
| Secondaire | Jaune | `#E6A911` | Badges, séparateurs, call-to-action, numéros de module |
| Accent | Rouge | `#EF476F` | Alertes uniquement |
| Accent | Vert | `#06D6A0` | Validations uniquement |
| Neutre | Acier | `#8DA7BE` | Sous-titres H2, textes secondaires, fonds très légers |
| Neutre | Noir | `#000000` | Corps de texte |
| Neutre | Blanc | `#FFFFFF` | Fonds, texte sur bleu ou noir |

### Règles d'usage couleurs
- **Bleu** : toujours dominant — couleur structurelle principale
- **Jaune** : accent uniquement — jamais couleur de fond principale sur une page entière
- **Fond** : toujours blanc ou très clair (#F5F5F5 max)
- **Texte sur fond bleu** : blanc `#FFFFFF` obligatoire
- **Texte sur fond jaune** : noir `#000000` obligatoire

---

## 🔤 Typographie

| Niveau | Police | Graisse | Taille document |
|---|---|---|---|
| Titre / H1 | Inter | Bold 700 | 18–24 pt |
| Sous-titre / H2 | Inter | Semi-Bold 600 | 14–16 pt |
| Section / H3 | Inter | Semi-Bold 600 | 12–13 pt |
| Corps | Inter | Regular 400 | 10–11 pt |

- **Fallback** : Helvetica, Arial, sans-serif
- Hiérarchie stricte : Bold pour titres, Regular pour corps — jamais inversé
- L'italique est réservé aux citations, pas à la décoration

---

## 📐 Mise en page générale

- **Style** : sobre, clean, épuré — moins c'est plus
- **Marges** : généreuses (minimum 2 cm pour documents imprimés)
- **Espace blanc** : laisser respirer les sections, ne pas surcharger
- **Séparateurs** : ligne fine bleue (`#23429F`) ou jaune (`#E6A911`) entre sections
- **Tableaux** : en-tête fond bleu `#23429F` texte blanc / lignes alternées blanc + gris clair `#F0F0F0`
- **Badges** : fond bleu ou jaune, texte contrasté (blanc sur bleu, noir sur jaune)

---

## 📄 Application par type de document

### Documents Word / PDF
```
EN-TÊTE :
  - Bandeau bleu (#23429F) pleine largeur
  - Logo "Blanc_Jaune.png" aligné à gauche dans le bandeau  ← fond bleu = logo blanc
  - Nom du document aligné à droite en blanc, Inter Semi-Bold

TITRES :
  - H1 : Inter Bold, couleur #23429F
  - H2 : Inter Semi-Bold, couleur #8DA7BE ou #E6A911
  - Corps : Inter Regular, couleur #000000

PIED DE PAGE :
  - Logo "Mono_noir.png" à droite (petit, discret)  ← fond blanc = monogramme noir
  - Texte centré : monkey-lab.fr | hello@monkey-lab.fr en gris discret
  - Numéro de page centré ou à droite
```

### Présentations (PowerPoint / Canva)
```
DIAPO TITRE (couverture) :
  - Fond bleu (#23429F)
  - Titre : Inter Bold, blanc
  - Sous-titre : Inter Regular, jaune (#E6A911)
  - Logo "Blanc_Jaune.png"  ← fond bleu = logo blanc obligatoire

DIAPOS INTERNES :
  - Fond blanc
  - Titre : Inter Bold, bleu (#23429F)
  - Corps : Inter Regular, noir
  - Logo "Mono_noir.png" en pied de page discret  ← fond blanc = monogramme noir

PIED DE PAGE DIAPOS :
  - "Mono_noir.png" à droite
  - Numéro de page centré
```

### Fiches & supports pédagogiques
```
  - Numéro de module : badge fond jaune (#E6A911), texte noir, Inter Bold
  - Titre du module : Inter Bold, bleu (#23429F)
  - Encadrés objectifs : bordure gauche épaisse bleue (#23429F), fond blanc
  - Encadrés points-clés : fond jaune très clair (#FFF8E1), bordure jaune
  - Mascotte Monki : illustration d'ambiance, coin de page
```

---

## ✅ Checklist avant livraison

- [ ] Logo choisi selon le contraste exact du fond (tableau logos ci-dessus)
- [ ] Aucun logo sombre (Noir_Jaune) sur fond bleu ou foncé
- [ ] Aucun logo clair (Blanc_Jaune) sur fond blanc
- [ ] Police Inter utilisée partout
- [ ] H1 en bleu #23429F
- [ ] Texte sur fond bleu = blanc
- [ ] Texte sur fond jaune = noir
- [ ] Fond général blanc ou très clair
- [ ] Style sobre — pas de surcharge décorative
- [ ] Pied de page avec monogramme discret + coordonnées monkey-lab.fr
