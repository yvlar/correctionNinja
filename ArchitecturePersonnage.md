# Architecture — Personnages jouables & Extensions (générique, tous jeux)

Deux nouvelles fonctionnalités à ajouter à la fiche-jeu, pensées pour être **génériques** dès le départ — un seul système réutilisable pour tous les jeux (Heroes Rising, Braque Jack, futurs jeux), pas une version codée à la main par jeu.

---

## 1. Section "Personnages jouables"

Nom de la section variable selon le jeu (ex: "Vos Héros" pour Heroes Rising, "Vos Rôles" pour Braque Jack) — champ texte dans le formulaire admin, pas codé en dur.

### Champs à ajouter dans le formulaire admin (section répétable, autant d'entrées que voulu)

| Champ | Type | Notes |
|---|---|---|
| Nom | Texte | |
| Descripteur court | Texte | Ex: "Tank", "Soutien", "Contrôle (glace)" |
| Image de la carte | Upload image | |
| Phrase-accroche | Texte court | Visible sans avoir à cliquer |
| Texte complet | Texte long, optionnel | Apparaît au clic (accordéon) |
| Est-ce un item mystère? | Case à cocher | Si cochée : affiche un carré orange avec "???" à la place de l'image, peu importe si une image est fournie ou non |

### Comportement d'affichage
- Grille responsive qui s'ajuste automatiquement au nombre d'entrées (fonctionne pour 6 héros comme pour 15 rôles)
- La palette de couleurs des cartes hérite automatiquement de la sous-palette déjà associée au jeu (pas de couleurs à recoder par jeu)
- Clic sur une carte → déplie le texte complet en dessous (même logique que l'accordéon "Règles complètes" déjà existant)

### Cas Heroes Rising (pour référence, contenu déjà rédigé)
6 héros + 1 carte mystère ("Héros mystère" / "Exclusif Kickstarter", carré orange plein avec "???", bordure pointillée pour la distinguer visuellement des cartes normales).

---

## 2. Section "Extensions"

Un seul type de composant "Extension" — pas deux composants séparés pour grande/petite. La mise en page s'ajuste automatiquement selon les champs remplis.

### Champs à ajouter dans le formulaire admin (section répétable)

| Champ | Type | Notes |
|---|---|---|
| Nom | Texte | |
| Description | Texte | |
| Image de couverture | Upload image, **optionnel** | Champ vide autorisé |
| Statut | Texte | Ex: "Détails à venir", "Disponible" |
| Note de déblocage | Texte, optionnel | Pour les conditions pas encore confirmées, ex: "peut-être incluse si un seuil est atteint" |

### Logique d'affichage automatique
- **Image de couverture présente** → carte large avec l'image en haut, badge "Grande extension"
- **Image de couverture absente** → carte compacte, texte seulement, bordure pointillée, badge "Extension"

Pas de choix manuel de gabarit à faire — le simple fait de fournir ou non une image détermine l'affichage. Fonctionne peu importe le nombre futur d'extensions (1 grande + 1 petite aujourd'hui, pourrait être 2 grandes + 3 petites plus tard sans retoucher le code).

### Cas Heroes Rising (pour référence)
- 1 grande extension avec sa propre couverture
- 1 petite extension sans couverture, avec la note : "à confirmer — peut-être incluse d'office si un seuil de la grande extension est atteint" (Jimmy n'a pas encore tranché)

---

## Pourquoi construire ça de façon générique plutôt que personnalisée par jeu

Si c'est codé à la main pour Heroes Rising, il faut tout refaire pour Braque Jack, Flickle Mania, et chaque jeu futur. En le rendant générique une fois (piloté par le formulaire admin), chaque nouveau jeu profite automatiquement de la fonctionnalité juste en remplissant les champs — aucun développement additionnel requis.

Merci! 🙏
