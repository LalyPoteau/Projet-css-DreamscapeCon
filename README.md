# Rendu — DreamscapeCon

Site vitrine fictif de **DreamscapeCon**, convention cosplay et culture pop à Lille. Ce README localise les exigences de l’énoncé et résume les vérifications déjà réalisées. Compléter les champs personnels et exécuter les vérifications signalées avant le dépôt final.

## Groupe

| Champ | Valeur |
|---|---|
| Organisation | Travail individuel (solo), à la place du trinôme prévu par l’énoncé |
| Nom de l’étudiante |Poteau Laly |
| Événement / thème | DreamscapeCon — convention cosplay, culture pop et imaginaire |
| Dépôt Git | Aucun lien communiqué; à compléter si nécessaire |
| Convention de nommage | BEM : blocs tels que `.speaker-card`, éléments `__portrait`, `__role`, variantes `--featured`; utilitaire `u-visually-hidden` |

## Localisation des exigences

| Exigence | Emplacement | Mise en œuvre / statut |
|---|---|---|
| A1 — ordre des layers | `css/main.css:16` | Ordre déclaré une seule fois; chaque feuille importée est enveloppée dans son layer. |
| A2 — tokens primitifs | `css/tokens.css:21` | Palette DreamscapeCon et échelles d’espacement, rayons et durées. |
| A2 — tokens sémantiques et thèmes | `css/tokens.css:57` | Rôles sémantiques avec `light-dark()`; thème clair par défaut et bascule clair/sombre CSS-only dans l’en-tête. |
| A3 — nesting natif | `css/components.css:12` | Nesting dans les composants, par exemple `&:hover`; convention BEM annoncée ci-dessus. |
| A4 — couches, validité et `!important` | `css/main.css:16` et feuilles `css/*.css` | Pas de `!important` dans les styles applicatifs. Diagnostics de l’éditeur sans erreur sur les fichiers contrôlés. Rapport W3C reçu; les rôles signalés ont été corrigés, revalidation à effectuer. |
| B1 — grille nommée | `css/layout.css:20` | `.programme` réorganise ses zones entre une colonne mobile et les journées sur desktop. |
| B2 — `subgrid` | `css/components.css:175` | Les cartes intervenants partagent cinq pistes pour aligner portrait, nom, rôle, bio et lien entre cartes. |
| B3 — Flexbox | `css/layout.css:198` | Navigation sur un axe, avec `gap` et `flex-wrap`. |
| C1 — mobile-first et typographie fluide | `css/tokens.css:113` | Échelle typographique fluide avec `clamp()`; les media queries élargissent les grilles. |
| C2 — container queries | `css/layout.css:234`, `css/components.css:265` et `css/components.css:335` | Le même composant `.btn` s’adapte dans le contenu du hero et dans les cartes de billets via le conteneur nommé `action-area`. Les portraits intervenants ont aussi leur query dédiée. |
| C3 — robustesse à 320 px | `css/layout.css:20` et `css/layout.css:72` | Test navigateur à 320 px : `scrollWidth` ne dépasse pas le viewport; les cartes passent en une colonne. Tests également réalisés à 768 et 1440 px. |
| D1 — `:has()` | `css/components.css:339` | L’offre portant le badge « Le plus populaire » reçoit automatiquement son traitement visuel. |
| D1 — `:is()` et `:where()` | `css/components.css:161` et `css/base.css:32` | `:is()` regroupe les états hover/focus; `:where()` garde une spécificité nulle pour les titres de base. |
| D2 — clair/sombre | `css/tokens.css:57` et `css/tokens.css:60` | Tokens sémantiques avec `light-dark()` et contrôle par checkbox CSS `:has()`; états clair/sombre vérifiés dans le navigateur. |
| E1 — transitions | `css/components.css:23` et `css/components.css:400` | Transitions ciblées sur boutons, liens, FAQ et propriétés nommées; pas de `transition: all`. |
| E2 — keyframes | `css/components.css:550` | `billet-brille`, animation brève de l’éclat du bouton de réservation. |
| E3 — mouvement réduit | `css/components.css:448` et `css/components.css:556` | Les transitions d’étoile, FAQ, navigation et boutons sont neutralisées ou réduites sans masquer de contenu. |
| F1 — structure et titres | `index.html:1`, `index.html:14`, `index.html:32`, `index.html:36`, `index.html:218` | `lang="fr"`, header/nav/main/footer et un unique `h1`. Les cinq réponses utilisent `<details>/<summary>`. |
| F1 — alternatives textuelles | `index.html:16`, `index.html:38`, `index.html:102` | Logo et étoile décoratifs ont un `alt` vide; les illustrations de profils portent un nom accessible. |
| F2 — focus clavier | `css/base.css:42` | `:focus-visible` visible; le menu mobile est utilisable au clavier. |
| F2 — contrastes | `css/tokens.css:60` et `css/tokens.css:65` | Paires représentatives contrôlées dans le navigateur en clair/sombre. Exemples : texte/page 13,05:1; texte secondaire sombre/surface 6,78:1; badge blanc/violet 10,6:1. Refaire une vérification complète au zoom 200 % avant le rendu. |
| G — contenu et finition | `index.html:33`, `index.html:52`, `index.html:94`, `index.html:145`, `index.html:187`, `index.html:218` | Hero, programme (6 créneaux), intervenants (6 profils), billetterie (3 offres), FAQ (5 questions) et footer sont présents. Les réservations sont fictives et utilisent `mailto:`. |

## Vérifications faites

- Contrôle dans le navigateur aux largeurs 320, 768, 1365 et 1440 px : pas de défilement horizontal mesuré.
- Présence vérifiée : 6 créneaux, 6 profils, 3 offres et 5 questions.
- Tests navigateur des thèmes clair/sombre, hover/focus, FAQ native et préférence `prefers-reduced-motion`.
- Diagnostics de l’éditeur : aucun problème signalé dans les fichiers HTML/CSS contrôlés.
- tester sur firefox et en x200



## Avertissements du validateur W3C

Le rapport W3C fourni signalait un rôle `img` sur une figure légendée et des rôles `list`/`listitem` redondants ou incompatibles. Ces rôles ont été retirés; une nouvelle validation W3C reste à effectuer pour confirmer la correction. Syntaxes modernes présentes à vérifier : cascade layers, nesting CSS, `light-dark()`, container queries, `subgrid`, `color-mix()` et transitions de `max-block-size`. -> après correction le W3C ne met plus aucun avertissement
Dans les W3C de css on a surtout eu des warning pours les @containers @import

## JavaScript

Aucun JavaScript n’est présent

## Déclaration d’usage d’outils d’IA

| Outil | Usage déclaré | Fichiers concernés |
|---|---|---|
| ChatGPT | Aide à la création et à l’adaptation des SVG de logo et d’étoile à partir de la direction visuelle/planche DreamscapeCon.  | `dreamscape-logo.svg`, `dreamscape-star.svg` |
| GitHub Copilot | Assistance à l’implémentation, à la revue et aux tests HTML/CSS responsive.| `index.html`, `css/` |

## Qui a fait quoi

| Contributeur·rice | Contribution |
|---|---|
| **Nom à compléter — travail individuel** | Direction DreamscapeCon, contenu fictif, intégration HTML/CSS, tests responsive et préparation du rendu. Outils d’IA déclarés dans la section précédente. |

## Crédits

- Typographies **Fascinate** et **Kedebideri**, chargées depuis Google Fonts.
- Éléments vectoriels DreamscapeCon : planche `dreamscape_con_elements.svg` fournie dans le starter; variantes autonomes du logo et de l’étoile dans `dreamscape-logo.svg` et `dreamscape-star.svg`.
- Les portraits de la maquette finale sont des illustrations colorées CSS, sans photographie externe.
