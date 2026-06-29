# ⬡ Néro — Site web (prêt pour Vercel)

Ce dossier contient le site complet, fichiers renommés et liens connectés.
Il se déploie tel quel sur Vercel, puis se branche sur `nero-immo.fr`.

## Contenu

| Fichier | URL une fois en ligne | Rôle |
|---|---|---|
| `index.html` | nero-immo.fr | Accueil / landing |
| `home.html` | nero-immo.fr/home | Diagnostic + dossier PDF |
| `invest.html` | nero-immo.fr/invest | Simulateur investisseur |
| `pilote.html` | nero-immo.fr/pilote | Demande de rappel courtier |
| `paiement.html` | nero-immo.fr/paiement | Page de paiement |
| `vercel.json` | — | Active les URL propres (/home au lieu de /home.html) |

Les liens entre les pages sont déjà connectés (boutons d'offres, logos, CTA).

## Déploiement — 3 étapes

### 1. Mettre les fichiers sur GitHub
- Crée un dépôt (ex. `nero-site`) sur github.com
- Dépose **tout le contenu de ce dossier** à la racine du dépôt
  (les fichiers .html et vercel.json, pas le dossier lui-même)

### 2. Importer dans Vercel
- Va sur vercel.com, connecte-toi avec GitHub
- **Add New → Project → Import** ton dépôt `nero-site`
- Laisse les réglages par défaut (Framework: Other) → **Deploy**
- Tu obtiens une URL de test `nero-site.vercel.app` : vérifie que tout marche

### 3. Brancher nero-immo.fr
- Dans Vercel : **Settings → Domains → Add** → `nero-immo.fr`
- Vercel affiche 2 enregistrements DNS à créer chez OVH :
  - un **A** pour `nero-immo.fr` → l'IP indiquée par Vercel
  - un **CNAME** pour `www` → l'adresse indiquée par Vercel
- Dans ton espace OVH → zone DNS, ajoute ces 2 enregistrements
- Le HTTPS s'active automatiquement (quelques minutes à quelques heures)

> ⚠️ NE TOUCHE PAS aux enregistrements **MX** chez OVH : ce sont eux qui
> font fonctionner `support@nero-immo.fr`. On ne modifie que A et CNAME.

## Ce qui reste à brancher après mise en ligne

Ces éléments sont aujourd'hui en mode démo (ils n'envoient/n'encaissent rien) :

- **Paiement** (`paiement.html`) : à relier au serveur Stripe (dossier `nero-stripe`).
  Voir le guide dans ce dossier.
- **Formulaire Pilote** (`pilote.html`) : le bouton « Demander mon rappel » doit
  envoyer les données vers ton e-mail / Google Sheet / CRM. À l'endroit marqué
  `// en prod : POST des données` dans le code.
- **Génération PDF** (`home.html`) : fonctionne déjà côté navigateur (jsPDF via CDN).
  Le paiement devra la déverrouiller une fois Stripe branché.

## Conformité (rappel)

Avant d'ouvrir au public, compléter les mentions réglementaires : ORIAS,
carte T, ACPR, médiateur, CGV, mentions légales, RGPD. Voir le plan de mise
en ligne. À valider avec tes conseils professionnels.
