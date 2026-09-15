# TogoSheets Marketplace — site public

⚠️ Ce dépôt est le **vrai site en ligne** que les visiteurs utilisent
directement (https://alban3886.github.io/togosheets-marketplace/) —
ce n'est pas un prototype abandonné, contrairement à ce qu'on pensait
au départ.

## Ce qui a été corrigé (session du 2026-09-15)
- `index.html` était désynchronisé de la version de référence
  (`togosheets-pro/public.html`) : il manquait l'appel à
  `window.buildAllProducts()`, ce qui faisait que la page d'accueil
  affichait toujours "Aucun article trouvé" même quand des boutiques
  avaient des produits. Corrigé.
- Le paiement Pi Network a été retiré entièrement (SDK, bouton de
  test, drawer de paiement Pi dans la boutique) — remplacé par les
  options déjà existantes : Cash, Flooz, Wave.
- `boutique.html` et `employe.html` (+ leurs fichiers nécessaires :
  `manifest-employe.json`, `sw-employe.js`, `icon-192.png`,
  `icon-512.png`) ont été copiés depuis `togosheets-pro` : avant,
  cliquer sur une boutique depuis ce site donnait une erreur 404
  car ces pages n'existaient que dans l'autre dépôt.

## ⚠️ Important : deux copies, une seule vérité
`togosheets-pro` et ce dépôt contiennent maintenant chacun leur
propre copie de `boutique.html` et `employe.html`. **Ce ne sont pas
des fichiers liés automatiquement** : si tu modifies l'un, il faut
recopier le changement dans l'autre à la main, sinon ils vont
diverger à nouveau exactement comme avant.

La solution durable serait de choisir UN SEUL site officiel et de
faire pointer l'app Android + tous les liens partagés vers celui-là
uniquement, pour ne plus avoir à synchroniser deux copies. À décider.
