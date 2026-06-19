# Les 5 familles de slides

Système extrait de l'analyse de "Efficacité Personnelle" (Celogik, 65 slides). Chaque slide du deck appartient à une de ces familles, choisie selon son **rôle pédagogique** — pas selon une rotation arbitraire.

Toutes les dimensions ci-dessous sont en pouces, pour `LAYOUT_WIDE` (13.3" × 7.5"). Couleurs d'exemple = palette Monkey Lab (`#23429F` bleu, `#E6A911` jaune, `#EF476F` rouge, `#06D6A0` vert, `#8DA7BE` acier) ; remplace par la charte demandée si différente.

---

## Tableau de décision

| Rôle de la slide dans la séquence | Famille à utiliser |
|---|---|
| Ouvre une nouvelle section/sous-thème, doit interpeller, créer un déclic émotionnel | **1. Accroche plein cadre** |
| Explique un concept, une liste, une méthode, un process | **2. Concept structuré** (4 variantes internes, voir plus bas) |
| Marque une pause rituelle : passage à l'exercice, ou moment Q&R | **3. Transition rituelle** |
| Appuie une idée avec une preuve externe (chiffre, étude, auteur reconnu) | **4. Citation / Stat choc** |
| Montre un outil, une capture d'écran, une démo concrète | **5. Capture / Démo** |

---

## 1. Accroche plein cadre

**Usage :** première slide d'une séquence, ou moment de respiration émotionnelle. Toujours une question ou affirmation courte qui fait réfléchir, en lien direct avec ce qui suit.

**Structure :** photo bord à bord (toute la slide), bandeau semi-transparent avec le titre, ombre portée sur le bandeau pour le détacher du fond.

```javascript
let slide = pres.addSlide();

// Image plein cadre
slide.addImage({
  path: imagePath, // ou URL
  x: 0, y: 0, w: 13.33, h: 7.5,
  sizing: { type: 'cover', w: 13.33, h: 7.5 }
});

// Bandeau titre semi-transparent
slide.addShape(pres.shapes.RECTANGLE, {
  x: 1.5, y: 0.6, w: 10.3, h: 1.1,
  fill: { color: '23429F', transparency: 22 }, // alpha ~78%
  shadow: { type: 'outer', color: '000000', blur: 8, offset: 3, angle: 90, opacity: 0.4 }
});

slide.addText("Vos journées ressemblent à ça ?", {
  x: 1.7, y: 0.6, w: 9.9, h: 1.1,
  fontSize: 32, bold: true, color: 'FFFFFF', align: 'center', valign: 'middle',
  fontFace: 'Arial'
});

// Logo Monkey Lab clair (fond image = traiter comme fond foncé par défaut)
slide.addImage({
  path: 'https://raw.githubusercontent.com/remicelogik-bot/Monkey-Logo/main/Mono-Blanc.png',
  x: 12.3, y: 6.7, w: 0.5, h: 0.83
});
```

**Variation possible :** bandeau positionné en bas plutôt qu'en haut, ou titre sans bandeau mais avec un fort dégradé sombre en bas de l'image (overlay) si le texte doit rester lisible sans bloc plein.

**Règles :**
- Le bandeau ne doit JAMAIS être à 100% opaque (perd l'effet "fenêtre sur l'image") ni en dessous de 60% (perd la lisibilité)
- Texte centré uniquement sur cette famille — c'est l'exception à la règle générale "ne pas centrer le texte"
- Choisir une photo dont le sujet ET le cadrage laissent de la place pour le bandeau sans masquer l'élément clé de l'image

---

## 2. Concept structuré

**Usage :** la famille la plus fréquente, mais elle a 4 variantes internes — alterne entre elles pour ne pas créer un effet répétitif même au sein de cette famille.

### 2a. Cartes/post-it

Pour : lister des éléments de même nature (outils, étapes, questions). Utiliser des rectangles arrondis avec rotation légère aléatoire (entre -4° et +4°) pour casser l'effet grille trop carré.

```javascript
const items = [
  { text: "Communiquer en l'absence d'une personne", color: 'FFE0E8' },
  { text: "Confirmer un RDV", color: 'D6FFF5' },
  { text: "Informer", color: 'FFF3CC' },
];

slide.addText("À quoi sert un mail ?", {
  x: 0.6, y: 0.4, w: 12, h: 0.8, fontSize: 30, bold: true, color: '23429F', fontFace: 'Arial'
});

items.forEach((item, i) => {
  const col = i % 3, row = Math.floor(i / 3);
  const x = 0.8 + col * 4.1;
  const y = 1.6 + row * 2.0;
  const rotation = (i % 2 === 0 ? 1 : -1) * (1.5 + Math.random() * 2.5);

  slide.addShape(pres.shapes.ROUNDED_RECTANGLE, {
    x, y, w: 3.6, h: 1.6, rectRadius: 0.08,
    fill: { color: item.color },
    rotate: rotation,
    shadow: { type: 'outer', color: '000000', blur: 4, offset: 2, angle: 45, opacity: 0.25 }
  });
  slide.addText(item.text, {
    x: x + 0.15, y: y + 0.15, w: 3.3, h: 1.3,
    fontSize: 13, color: '111111', align: 'center', valign: 'middle',
    fontFace: 'Arial', rotate: rotation
  });
});
```

**Règle de rotation :** jamais plus de 4°, jamais deux cartes adjacentes avec la même direction de rotation.

### 2b. Matrice 2×2 / Pyramide / Process en étapes

Pour : méthodes structurées (type Eisenhower), hiérarchies, séquences à étapes numérotées.

```javascript
// Matrice 2x2 type Eisenhower
const quadrants = [
  { label: 'PLANIFIER', color: '06D6A0', x: 3.5, y: 1.5 },
  { label: 'A FAIRE', color: 'EF476F', x: 7.6, y: 1.5 },
  { label: 'ABANDONNER', color: '8DA7BE', x: 3.5, y: 3.6 },
  { label: 'DELEGUER', color: 'E6A911', x: 7.6, y: 3.6 },
];
quadrants.forEach(q => {
  slide.addShape(pres.shapes.RECTANGLE, {
    x: q.x, y: q.y, w: 4.0, h: 2.0, fill: { color: q.color }
  });
  slide.addText(q.label, {
    x: q.x, y: q.y, w: 4.0, h: 2.0, fontSize: 20, bold: true, color: 'FFFFFF',
    align: 'center', valign: 'middle', fontFace: 'Arial'
  });
});
// Axes : utiliser addText avec rotate:-90 pour l'axe vertical, jamais de ligne épaisse colorée en bordure de slide
```

**Process en étapes numérotées :** cercles numérotés (1, 2, 3) + texte court dessous, alignés horizontalement, espacés régulièrement — pas de flèches discount entre eux, un alignement clair suffit.

### 2c. Texte + image (deux colonnes)

Pour : un concept qui bénéficie d'un visuel d'ambiance à côté du texte (ex: "La To-Do List : Pilier de la Productivité" avec une photo de bureau).

```javascript
slide.addImage({
  path: imagePath, x: 0, y: 0, w: 5.5, h: 7.5, sizing: { type: 'cover', w: 5.5, h: 7.5 }
});
slide.addText("La To-Do List : Pilier de la Productivité", {
  x: 6.1, y: 1.0, w: 6.6, h: 1.3, fontSize: 26, bold: true, color: '23429F', fontFace: 'Arial'
});
slide.addText("Structurer ses tâches améliore l'efficacité personnelle...", {
  x: 6.1, y: 2.5, w: 6.6, h: 2.5, fontSize: 15, color: '333333', fontFace: 'Arial'
});
```

### 2d. Icône + texte en lignes (liste de recommandations/outils)

Pour : comparer des options, lister des outils avec description courte. Icône ou émoji dans un petit cercle coloré, titre en gras, description en dessous — empilé verticalement ou en grille 2×2.

**Règle commune à 2a-2d :** ne jamais utiliser deux fois la même variante (2a/2b/2c/2d) sur deux slides "Concept structuré" consécutives.

---

## 3. Transition rituelle

**Usage :** marque un repère appris par le stagiaire — "on change de mode". Toujours la même structure simple à l'intérieur d'un type donné (Mise en application / Q&R), pour que la répétition SOIT le signal. C'est la seule famille où la répétition de mise en page est volontaire et bénéfique.

```javascript
// Type "Mise en application"
slide.addShape(pres.shapes.RECTANGLE, { x: 0, y: 0, w: 13.33, h: 7.5, fill: { color: 'F5F5F5' } });
slide.addText("MISE EN APPLICATION", {
  x: 0.5, y: 1.3, w: 12.3, h: 0.6, fontSize: 16, bold: true, color: '06D6A0',
  align: 'center', fontFace: 'Arial', charSpacing: 3
});
slide.addShape(pres.shapes.ROUNDED_RECTANGLE, {
  x: 2.5, y: 2.3, w: 8.3, h: 2.0, rectRadius: 0.15, fill: { color: '23429F' }
});
slide.addText("Crée tes listes de tâches", {
  x: 2.8, y: 2.3, w: 7.7, h: 2.0, fontSize: 26, bold: true, color: 'FFFFFF',
  align: 'center', valign: 'middle', fontFace: 'Arial'
});

// Type "Questions & Réponses / Parking" — même logique, fond différent (ex: acier #8DA7BE),
// texte "QUESTIONS & RÉPONSES" + "PARKING" en sous-titre
```

**Règle :** toujours fond uni (pas de photo), toujours composition centrée, toujours peu de texte (une phrase max). Garde le même habillage visuel pour CE type de transition à travers tout le deck (toutes les "Mise en application" se ressemblent entre elles — c'est l'intention).

---

## 4. Citation / Stat choc

**Usage :** appuyer un point avec une preuve externe — chiffre marquant, citation d'un auteur reconnu, référence à un livre/étude. Crée une pause de crédibilité.

```javascript
// Variante stat
slide.addImage({ path: imagePath, x: 0, y: 0, w: 6.5, h: 7.5, sizing: { type: 'cover', w: 6.5, h: 7.5 } });
slide.addText("5 secondes\nde perturbation", {
  x: 6.9, y: 1.2, w: 6.0, h: 1.4, fontSize: 20, color: '333333', fontFace: 'Arial'
});
slide.addText("26", {
  x: 6.9, y: 2.6, w: 6.0, h: 1.6, fontSize: 80, bold: true, color: 'EF476F', fontFace: 'Arial'
});
slide.addText("Minutes de concentration perdues", {
  x: 6.9, y: 4.1, w: 6.0, h: 0.7, fontSize: 16, color: '333333', fontFace: 'Arial'
});
slide.addText("Source : Cal Newport, \"Deep Work\"", {
  x: 6.9, y: 6.8, w: 6.0, h: 0.4, fontSize: 10, italic: true, color: '8DA7BE', fontFace: 'Arial'
});

// Variante citation : portrait N&B ou symbolique à gauche, citation en grand à droite en italique,
// nom de l'auteur en dessous en petit caps
```

**Règle :** un seul chiffre OU une seule citation par slide — ne jamais combiner plusieurs stats sur cette famille (sinon ça devient une slide "Concept structuré" déguisée).

---

## 5. Capture / Démo

**Usage :** montrer un outil réel, une capture d'écran, une démonstration. C'est la famille où Rémi insère ses propres screenshots de formation IA.

```javascript
// Cadre "device/navigateur" autour du screenshot pour donner un effet pro plutôt que "image collée"
slide.addText("Démo : configurer ton assistant", {
  x: 0.6, y: 0.4, w: 12, h: 0.7, fontSize: 24, bold: true, color: '23429F', fontFace: 'Arial'
});

slide.addShape(pres.shapes.RECTANGLE, {
  x: 1.0, y: 1.4, w: 11.3, h: 5.6, fill: { color: 'FFFFFF' },
  line: { color: 'CCCCCC', width: 1 },
  shadow: { type: 'outer', color: '000000', blur: 10, offset: 3, angle: 90, opacity: 0.2 }
});
// Barre de titre simulée façon navigateur (3 points)
slide.addShape(pres.shapes.RECTANGLE, { x: 1.0, y: 1.4, w: 11.3, h: 0.35, fill: { color: 'EEEEEE' } });
[0,1,2].forEach(i => {
  slide.addShape(pres.shapes.OVAL, { x: 1.15 + i*0.25, y: 1.5, w: 0.13, h: 0.13, fill: { color: 'CCCCCC' } });
});

slide.addImage({
  path: screenshotPath, x: 1.15, y: 1.9, w: 11.0, h: 5.0,
  sizing: { type: 'contain', w: 11.0, h: 5.0 }
});
```

**Si le screenshot n'est pas encore disponible** (cas le plus fréquent en phase de plan), insère un placeholder explicite plutôt qu'une image générique :

```javascript
slide.addShape(pres.shapes.RECTANGLE, {
  x: 1.15, y: 1.9, w: 11.0, h: 5.0, fill: { color: 'F5F5F5' }, line: { color: 'CCCCCC', width: 1, dashType: 'dash' }
});
slide.addText("📷 Remplacer par capture : [décrire ce que montre la capture]", {
  x: 1.5, y: 4.0, w: 10.3, h: 0.8, fontSize: 14, italic: true, color: '8DA7BE',
  align: 'center', fontFace: 'Arial'
});
```

Signale tous les placeholders restants à Rémi à la fin de la génération, avec le numéro de slide et la description attendue.

---

## Logo et pied de page (toutes familles, sauf transitions rituelles)

Applique la règle du skill `charte-monkey` : `Mono-Noir.png` sur fond clair, `Mono-Blanc.png` sur fond foncé/image, en petit (`w: 0.45 h: 0.75` environ) en bas à droite. Ne pas mettre de logo sur les slides "Transition rituelle" (ça casse l'effet de rupture volontaire) ni sur les slides "Accroche plein cadre" si le bandeau de titre est déjà en haut (mettre le mono discret en bas à droite dans ce cas).
