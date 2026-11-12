# Tiếng Việt Miền Nam — PWA

Application web progressive (PWA) pour apprendre le vietnamien du Sud :
66 unités (7 niveaux, du débutant au C1), vocabulaire avec audio, grammaire, et 4 compétences travaillées dans chaque unité : compréhension écrite, compréhension orale, expression écrite, expression orale.

## Contenu du package

```
.
├── index.html          → l'application (tout le contenu est ici)
├── manifest.json        → métadonnées PWA (nom, icônes, couleurs)
├── sw.js                 → service worker (cache hors-ligne)
├── icons/
│   ├── icon-192.png
│   ├── icon-512.png
│   └── icon-maskable-512.png
└── README.md             → ce fichier
```

Aucune étape de build n'est nécessaire : ce sont des fichiers statiques,
prêts à héberger tels quels.

---

## 1. Mettre le projet sur GitHub

1. Va sur [github.com](https://github.com) et connecte-toi (ou crée un compte).
2. Clique sur **New repository** (bouton vert en haut à droite, ou
   [github.com/new](https://github.com/new)).
3. Donne-lui un nom, par exemple `tieng-viet-mien-nam`.
   Laisse-le en **Public**, ne coche aucune case d'initialisation
   (pas de README, pas de .gitignore — on a déjà nos fichiers).
4. Clique sur **Create repository**.
5. Sur ton ordinateur, ouvre un terminal dans le dossier que tu viens
   de télécharger (celui qui contient `index.html`, `manifest.json`...)
   et lance :

   ```bash
   git init
   git add .
   git commit -m "Premier envoi du site"
   git branch -M main
   git remote add origin https://github.com/TON-NOM-UTILISATEUR/tieng-viet-mien-nam.git
   git push -u origin main
   ```

   (Remplace `TON-NOM-UTILISATEUR` par ton pseudo GitHub. Si tu n'as jamais
   utilisé Git en ligne de commande, GitHub te proposera aussi un lien
   "uploading an existing file" pour glisser-déposer les fichiers
   directement depuis le navigateur — ça marche tout aussi bien pour
   un projet aussi simple.)

---

## 2. Déployer sur Vercel

1. Va sur [vercel.com](https://vercel.com) et connecte-toi **avec ton
   compte GitHub** (bouton "Continue with GitHub").
2. Clique sur **Add New... → Project**.
3. Vercel te montre la liste de tes dépôts GitHub : choisis
   `tieng-viet-mien-nam` et clique sur **Import**.
4. Vercel détecte un simple site statique — tu n'as **rien à changer**
   dans les réglages (pas de "Build Command", pas de "Output Directory"
   à préciser ; laisse tout par défaut).
5. Clique sur **Deploy**.
6. Après ~30 secondes, Vercel te donne une URL du type
   `https://tieng-viet-mien-nam.vercel.app` — le site est en ligne.

### Mises à jour futures

Chaque fois que tu modifies un fichier et fais :
```bash
git add .
git commit -m "description du changement"
git push
```
Vercel redéploie automatiquement le site en quelques secondes.

### Installer la PWA sur un téléphone

Une fois le site en ligne (Vercel fournit du HTTPS automatiquement,
ce qui est obligatoire pour qu'une PWA s'installe) :
- **Android/Chrome** : ouvrir le lien → menu ⋮ → "Ajouter à l'écran
  d'accueil" (ou une bannière d'installation apparaît automatiquement).
- **iPhone/Safari** : ouvrir le lien → bouton Partager (carré avec
  flèche) → "Sur l'écran d'accueil".

L'app s'ouvre alors en plein écran, sans barre d'adresse, avec une icône
comme une app native, et fonctionne partiellement hors-ligne grâce au
service worker.

---

## Remarque sur le cache

Si tu modifies `index.html` plus tard et que les changements
n'apparaissent pas tout de suite pour les visiteurs qui ont déjà
utilisé le site, c'est le service worker qui sert une version en
cache. Il suffit d'augmenter le numéro de version en haut de `sw.js` :

```js
const CACHE_NAME = "tieng-viet-mien-nam-v3"; // v2 → v3
```

Cela force la mise à jour automatique du cache au prochain chargement.

---

## Mise à jour vers cette version (66 unités, niveau C1)

Si tu as déjà le site sur GitHub/Vercel : remplace simplement les fichiers
`index.html` et `sw.js` (et `manifest.json`) dans ton dépôt par ceux de ce
dossier — via « Add file → Upload files » sur GitHub — puis fais « Commit changes ».
Vercel redéploie tout seul en 30 secondes. Ta progression (unités validées) est
sauvegardée dans le navigateur de ton téléphone.

## Micro et reconnaissance vocale

- L'enregistrement micro et la reconnaissance vocale ne fonctionnent qu'en **HTTPS**
  (donc sur ton site Vercel) ou sur `localhost` — pas en ouvrant le fichier
  directement depuis le disque.
- La reconnaissance automatique marche surtout sur Chrome/Edge/Android. Sur iPhone,
  utilise « M'enregistrer » puis l'auto-évaluation.

## Mise à jour v4
- 90 unités (24 nouvelles unités de vocabulaire thématiques), ≈1100 mots/expressions
- Mode « Cartes mémoire » (révision espacée, progression enregistrée sur l'appareil)
- Page Ressources réorganisée (filtres, Académie Cô Ba) + plan « vietnamien + chinois »
- Pour mettre à jour : remplacer index.html, sw.js et manifest.json sur GitHub.
