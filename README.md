# TogoSheets Marketplace — vitrine publique

⚠️ **Ce dépôt est une copie automatique de `togosheets-pro`. Ne pas modifier ses fichiers ici.**

Source unique : https://github.com/alban3886/togosheets-pro
Un workflow GitHub Actions (dans togosheets-pro) recopie à chaque push :

| togosheets-pro          | ->  | togosheets-marketplace |
|-------------------------|-----|------------------------|
| `public.html`           | ->  | `index.html` (liens "index.html" réécrits vers l'URL absolue de pro) |
| `boutique.html`, `employe.html`, `manifest-employe.json`, `sw-employe.js`, `icon-*.png` | -> | idem |
| `images/`               | ->  | `images/` |

Restent propres à ce dépôt : `404.html`, `validation-key.txt`, `netlify/functions/`.

Les boutiques et produits ne sont pas copiés : la page lit la collection Firestore
`public_shops` du même projet que togosheets-pro.

## Les liens du projet
| Rôle | URL | Fichier |
|------|-----|---------|
| Vitrine (toutes les boutiques) | `/togosheets-marketplace/` | `index.html` |
| Boutique d'un vendeur | `/togosheets-marketplace/boutique.html?tenant=...` | `boutique.html` |
| Lien court d'une boutique | `/togosheets-marketplace/<slug>` | `404.html` (redirige vers `boutique.html?tenant=...`) |
| Gestion + création de boutiques | `/togosheets-pro/` | dépôt togosheets-pro |
| Espace employés | `/togosheets-pro/employe.html` | dépôt togosheets-pro |

⚠️ **Ne jamais supprimer `404.html`** : les liens courts générés par togosheets-pro
(`.../togosheets-marketplace/<slug>`) n'existent pas comme fichiers. GitHub Pages sert `404.html`,
qui lit le slug dans Firestore (`shop_slugs`) puis redirige vers la bonne boutique.
Ce fichier n'est pas synchronisé : il n'existe que dans ce dépôt.
