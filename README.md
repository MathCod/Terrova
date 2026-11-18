# Terrova — Landing page responsive

Intégration de la page d'accueil vitrine de **Terrova**, une marque dédiée aux escapades et au tourisme nature en France.  
Ce projet a été réalisé **exclusivement en HTML5 et CSS3 natifs** (sans framework CSS ni bibliothèque JavaScript), en respectant les bonnes pratiques d'accessibilité, de SEO, de performance et de responsive design.

---

## 📁 Organisation des fichiers

```text
Terrova/
├── index.html                  # Structure sémantique HTML5 de la landing page
├── README.md                   # Documentation du projet et choix techniques
├── css/
│   └── style.css               # Feuille de styles CSS3 native (Desktop-first + Media Queries)
├── assets/
│   ├── fonts/                  # Polices locales Inter (400 & 700 en .woff2 et .otf)
│   │   ├── Inter-Regular.woff2
│   │   ├── Inter-Regular.otf
│   │   ├── Inter-Bold.woff2
│   │   └── Inter-Bold.otf
│   ├── icons/                  # Pictogrammes SVG et favicon
│   │   ├── community.svg
│   │   ├── favicon.svg
│   │   ├── heart.svg
│   │   └── leaf.svg
│   ├── images/                 # Photographies optimisées au format WebP
│   │   ├── foret.webp
│   │   ├── montagne.webp
│   │   ├── ocean.webp
│   │   └── paysage.webp
│   └── logo.svg                # Logo vectoriel Terrova
└── rapports/                   # Exports et analyses des audits obligatoires
    ├── html.pdf                # Validateurs W3C HTML5 et CSS3
    ├── wave.pdf                # Audit d'accessibilité WAVE + analyse
    └── lighthouse.pdf          # Audit Lighthouse + analyse
🛠️ Techniques CSS et choix d'implémentation
1. Charte graphique et typographie locale
Variables CSS (:root) : centralisation de la palette officielle (--vert-foret: #173F32, --vert-profond: #103328, --marron: #965f0c, --vert-sauge: #E8F0E6, --creme: #F8F7F1, --texte-fonce: #20312B, complétée par --blanc: #FFFFFF pour les cartes et les textes sur fond sombre).
Polices locales (@font-face) : intégration de la police Inter (graisses 400 et 700) en priorisant le format .woff2 (plus léger et optimisé pour le web), avec .otf en solution de secours et font-display: swap.
2. Mises en page (Flexbox & CSS Grid)
Flexbox utilisé pour les alignements sur un axe :
Barre de navigation (.header_inner, liste de liens nav ul).
Organisation verticale de la section Hero (.hero_inner) permettant de placer le badge en bas à droite (align-self: flex-end).
Structure interne des cartes de destinations (.dest_card, .dest_body) avec flex: 1 sur la description afin d'aligner horizontalement les liens d'action des 3 cartes.
Bas du pied de page (.footer_bottom).
CSS Grid utilisé pour les compositions en colonnes :
Grille des 3 destinations (.destinations_grid).
Grille des 3 engagements (.engagements_grid).
Grille des 4 colonnes du footer (.footer_top avec proportions 1.4fr 1fr 1fr 1.2fr).
3. Responsive Design & Breakpoints
L'approche adoptée est Desktop-first avec une classe .container (max-width: 1120px, margin: 0 auto, padding: 0 24px) et trois paliers d'affichage :
Desktop (> 1024 px) : affichage par défaut sur 3 colonnes pour les cartes et 4 colonnes pour le footer, avec une marge extérieure latérale de 20px sur body.
Tablette (769 px à 1024 px — @media (max-width: 1024px)) : passage des grilles à 2 colonnes (repeat(2, 1fr)) et réduction des espacements verticaux et du padding de l'encadré Nos engagements.
Mobile (≤ 768 px — @media (max-width: 768px)) : passage à 1 colonne (1fr), suppression de la marge sur body pour exploiter toute la largeur utile, alignement du badge Hero à gauche et passage du bas de footer en colonne centrée.
4. Choix techniques et adaptations par rapport à la maquette
Convention de nommage snake_case (header_inner, dest_card, footer_top, etc.) : choix volontaire permettant la sélection rapide des noms de classes en un double-clic dans l'éditeur.
Section Hero : le bloc vert de la maquette symbolisant l'emplacement visuel, la photographie paysage.webp a été intégrée en arrière-plan pleine largeur avec une opacité de 0.50 sur le fond crème --creme, assurant un bon équilibre visuel tout en préservant un contraste suffisant pour le titre et les textes foncés.
Fond principal : utilisation du crème --creme (#F8F7F1) conformément au tableau de la charte graphique, et du blanc --blanc (#FFFFFF) sur les cartes de destinations pour conserver un contraste net.
Logo du pied de page : réutilisation du même fichier assets/logo.svg inversé en blanc via filter: brightness(0) invert(1) afin d'éviter la duplication de ressource graphique tout en garantissant sa lisibilité sur --vert-profond.
Liens de navigation légale : les liens Mentions légales, Conditions générales et Politique de confidentialité pointent vers # afin d'éviter des erreurs 404 dans le cadre d'une landing page monopage sans pages annexes.
♿ Accessibilité, SEO et Performance
HTML5 sémantique : utilisation des balises structurantes (<header>, <nav>, <main>, <section>, <article>, <footer>) et respect strict de la hiérarchie des titres (h1 → h2 → h3).
Attributs ARIA et alternatives textuelles :
aria-labelledby sur les sections et aria-label sur les navigations et liens nécessitant du contexte.
Attributs alt descriptifs sur les photos informatives, et alt="" + aria-hidden="true" sur les icônes purement décoratives et les flèches typographiques.
Navigation clavier : états :focus-visible stylisés (outline: 3px solid var(--marron) dans le corps de page et var(--blanc) dans le footer).
SEO : balise <title> explicite, <meta name="description"> optimisée et attribut lang="fr" sur <html>.
Optimisation des images : utilisation du format .webp, redimensionnement des visuels pour alléger le poids total de la page, pas de loading="lazy" sur l'image Hero (LCP) et loading="lazy" activé sur les cartes situées sous la ligne de flottaison.
🖼️ Sources des images
Image Hero (assets/images/paysage.webp) : image trouvée sur google libre de droit.
Autres ressources (montagne.webp, ocean.webp, foret.webp, logo, icônes, polices) : ressources fournies avec le sujet du projet (converties/redimensionnées au format .webp pour optimiser le chargement).
📊 Synthèse des vérifications et audits
Tous les rapports détaillés accompagnés de leurs analyses sont disponibles dans le dossier rapports/ :
Outil	Résultat obtenu	Remarques
Validateur W3C HTML (rapports/html.pdf)	0 erreur, 0 avertissement	Structure HTML5 100 % conforme.
Validateur W3C CSS (rapports/html.pdf)	0 erreur	CSS3 valide sans erreur de syntaxe.
WAVE (rapports/wave.pdf)	AIM Score : 10/10 (0 erreur, 0 erreur de contraste, 0 alerte)	Structure, ordre de tabulation et textes alternatifs validés.
Lighthouse (rapports/lighthouse.pdf)	Accessibilité : 100 / Bonnes pratiques : 100 / SEO : 100 / Performance : 97	Tous les objectifs sont dépassés. Le redimensionnement des images .webp a permis d'atteindre 97 en Performance (TBT : 0 ms, CLS : 0.003).
