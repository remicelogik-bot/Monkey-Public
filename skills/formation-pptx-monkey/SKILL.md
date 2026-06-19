---
name: formation-pptx-monkey
description: "Génère des présentations PowerPoint pour les formations de Rémi (Monkey Lab et organismes partenaires) dans un style didactique et rythmé inspiré de sa présentation 'Efficacité Personnelle'. À déclencher dès que Rémi demande une présentation, un support de formation, un deck ou des slides pour une formation — qu'il donne un thème, un plan de cours, ou un module Airtable existant. Produit un .pptx où chaque slide appartient à une 'famille' visuelle choisie automatiquement selon son rôle pédagogique (accroche, concept, transition rituelle, citation/stat, mise en pratique), pour éviter l'effet 'toutes les slides se ressemblent' typique des générateurs IA classiques (Gamma etc.), sans tomber non plus dans le chaos visuel. Couvre aussi le cas où Rémi veut insérer ses propres screenshots ou demande d'appliquer la charte d'un autre établissement (Connect 3S, etc.) plutôt que Monkey Lab."
---

# Slides de formation — style Monkey Lab

## Pourquoi ce skill existe

Rémi a analysé une de ses anciennes présentations ("Efficacité Personnelle", marque Celogik) et a identifié ce qui la rend efficace pédagogiquement : **ce n'est pas un template unique répété 65 fois**, c'est un vocabulaire de 5 familles de slides qui se recombinent selon le rôle de chaque slide dans la séquence pédagogique. C'est ce qui évite l'effet "Gamma" (une seule grille, reconnaissable et fatigante) tout en gardant une cohérence de marque forte.

Ce skill encode ce système pour les formations IA / process / organisation de Rémi, habillé avec la charte Monkey Lab par défaut.

**Lire `references/familles-de-slides.md` avant de générer quoi que ce soit** — il contient les 5 familles avec leur structure XML/pptxgenjs précise, quand utiliser laquelle, et des exemples de code.

---

## Workflow

### 1. Comprendre le contenu à transformer en slides

Rémi peut arriver avec :
- Un thème libre ("fais-moi un deck sur le prompting pour des artisans BTP")
- Un plan de cours déjà rédigé
- Un module de son catalogue Airtable (base `appvHDakBMMSTZyhS`, table `tblW8DAXljrKQPoLI`) — si c'est le cas, va chercher le contenu pédagogique (objectifs, déroulé, durée) dans Airtable plutôt que de l'inventer
- Le skill `cours-structuration` ou `programme-formation` peuvent avoir déjà produit la matière — si un de ces documents existe dans la conversation, pars de là plutôt que de redemander le plan

Si le sujet, le public, et la durée/nombre de slides ne sont pas clairs, demande — mais ne bloque pas sur des détails que tu peux raisonnablement déduire (ex: durée de slide ≈ nombre de slides / temps de formation).

### 2. Découper le contenu en séquences pédagogiques

Le rythme de la présentation source suit ce pattern, séquence après séquence :

```
[Accroche/transition de section] → [2-5 slides concept] → [citation/stat optionnelle] → [Mise en application] → [Q&R / Parking]
```

Découpe le contenu de Rémi en blocs de ce type (une "séquence" = un sous-thème complet, ex: "Gestion des mails", "Gestion de l'agenda"). Chaque séquence démarre par un slide-accroche (image plein cadre + question qui interpelle) et se termine par un slide "Mise en application" + un slide "Questions & Réponses".

### 3. Assigner une famille à chaque slide

Pour CHAQUE slide du plan, choisis automatiquement une famille parmi les 5 définies dans `references/familles-de-slides.md` selon le rôle de la slide (voir tableau de décision dans ce fichier). Note la famille choisie dans ton plan avant de générer le code — ça te permet de vérifier la variété (voir contrainte ci-dessous) avant d'écrire quoi que ce soit.

**Contrainte de variété — vérifie-la explicitement sur ton plan avant de coder :**
- Jamais la même famille sur 2 slides consécutives, sauf la famille "Concept structuré" qui peut s'enchaîner 2 fois max (elle a elle-même plusieurs variantes de mise en page internes — voir le fichier de référence — donc utilise des variantes différentes si elle s'enchaîne)
- Sur une séquence de 8-10 slides, vise au moins 4 des 5 familles représentées

### 4. Charte graphique

**Par défaut : Monkey Lab.** Le skill `charte-monkey` définit logos, couleurs (`#23429F`, `#E6A911`, `#EF476F`, `#06D6A0`, `#8DA7BE`), typographie (Arial pour PPTX) — **lis-le et applique-le**, il est complémentaire à ce skill-ci. Ce skill-ci gère la *variété de mise en page*, `charte-monkey` gère *la marque*.

Si Rémi demande explicitement une autre charte (Connect 3S ou un autre OF partenaire) :
- Demande-lui les couleurs/logo si tu ne les as pas déjà en mémoire ou dans un skill dédié
- Applique le même système de 5 familles, juste avec une autre palette/logo — la structure ne change pas, seul l'habillage change

### 5. Images

Pour les slides qui ont besoin d'une photo d'illustration (familles "Accroche plein cadre" et "Citation/Stat") :
- Propose une recherche via `image_search` avec une requête descriptive du sentiment/thème de la slide (pas juste le mot-clé littéral — ex. pour "Vos journées ressemblent à ça ?" chercher "pompier feu urgence chaos" plutôt que "journée travail")
- Présente 3-4 options à Rémi avant de les intégrer définitivement au pptx, sauf s'il a dit explicitement de ne pas s'arrêter pour valider
- Si Rémi veut insérer ses propres screenshots (captures d'outils, démonstrations), laisse des slides dédiées dans le plan avec un placeholder clair (texte "📷 Remplacer par capture : [description]") et signale-les-lui à la fin plutôt que de deviner un visuel

### 6. Génération technique

Utilise PptxGenJS (`/mnt/skills/public/pptx/pptxgenjs.md` pour la syntaxe de base). Layout `LAYOUT_WIDE` (13.3" × 7.5", équivalent 16:9 grand format, comme la présentation source).

Construis le deck slide par slide en suivant le plan validé à l'étape 3, en piochant le code de chaque famille dans `references/familles-de-slides.md`.

### 7. QA

Suis le processus QA standard du skill `pptx` (conversion en images, vérification visuelle par sous-agent, vérification des débordements de texte). Vérifie en plus, spécifiquement à ce skill :
- La variété : regarde la planche de miniatures et confirme qu'on ne voit pas la même mise en page 3 fois de suite
- Le logo Monkey Lab est bien la bonne variante (clair/sombre) selon le fond de chaque slide — voir `charte-monkey`

---

## Ce que ce skill n'est PAS

- Ce n'est pas un générateur "un thème → un coup de baguette magique sans validation". Le contenu pédagogique (les idées, la pédagogie) vient de Rémi ou des skills `cours-structuration`/`programme-formation` — ce skill-ci s'occupe de la **mise en forme visuelle et du rythme**.
- Ce n'est pas limité à la thématique "organisation personnelle" du deck source — le système de familles est générique et s'applique à n'importe quel sujet de formation (IA, Lean, process...).
