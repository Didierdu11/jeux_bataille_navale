# Bataille Navale — 2 téléphones, zéro installation

Jeu de bataille navale en une seule page web (`index.html`). Les deux joueurs ouvrent le même lien sur leur téléphone : l'un crée la partie, l'autre saisit le code à 4 caractères. Les deux téléphones se connectent **directement** (WebRTC, via [PeerJS](https://peerjs.com)) : aucun serveur à héberger, aucun compte.

- Navires vus du dessus, dessinés en SVG : porte-avions, cuirassé, croiseur, sous-marin, destroyer
- Placement par glisser-déposer, toucher pour pivoter, ou placement aléatoire
- Flammes, fumée, éclaboussures, secousse de l'écran, vibrations, sons synthétisés (aucun fichier audio)
- Option « rejouer après un tir touché », revanche en un clic
- L'écran reste allumé pendant la partie (Wake Lock)

## Publier sur GitHub Pages (2 minutes)

**Depuis le site GitHub, sans ligne de commande**

1. Créez un dépôt (par exemple `bataille-navale`), public.
2. *Add file → Upload files* : déposez tous les fichiers de ce dossier, puis *Commit*.
3. *Settings → Pages → Build and deployment* : Source `Deploy from a branch`, branche `main`, dossier `/ (root)`, *Save*.
4. Après une minute, le jeu est en ligne sur `https://VOTRE-NOM.github.io/bataille-navale/`.

**En ligne de commande**

```bash
git init -b main
git add .
git commit -m "Bataille navale"
git remote add origin https://github.com/VOTRE-NOM/bataille-navale.git
git push -u origin main
```

Puis activez Pages comme à l'étape 3.

## Jouer

1. Les deux joueurs ouvrent l'adresse du jeu.
2. Joueur 1 : **Créer une partie** → un code s'affiche (le bouton *Partager le lien* l'envoie par message).
3. Joueur 2 : **Rejoindre une partie** → saisit le code (ou ouvre le lien partagé, la connexion est automatique).
4. Chacun place sa flotte, touche **Prêt au combat**.
5. Touchez une case du radar, puis **Feu !**. Le premier à couler les 5 navires adverses gagne.

Astuce : sur iPhone ou Android, *Partager → Sur l'écran d'accueil* donne un plein écran sans barre de navigateur.

## Remarques techniques

- Le seul service externe est le serveur de mise en relation gratuit de PeerJS (il ne sert qu'à échanger le code au début). Ensuite, tout passe en direct entre les deux téléphones. La bibliothèque est chargée depuis unpkg, avec jsDelivr en secours.
- Les deux téléphones doivent avoir accès à Internet (Wi-Fi ou 4G/5G, pas besoin d'être sur le même réseau).
- Le résultat de chaque tir est calculé par le téléphone du défenseur : un joueur très motivé pourrait tricher en bidouillant son navigateur. C'est un jeu entre amis.
- Hébergement possible ailleurs : Netlify, Cloudflare Pages, ou n'importe quel serveur de fichiers statiques. Le jeu doit être servi en HTTPS.
- Pour utiliser votre propre serveur PeerJS, modifiez les deux appels `new Peer(...)` dans `index.html` (option `host`, `port`, `path`).

Licence MIT.
