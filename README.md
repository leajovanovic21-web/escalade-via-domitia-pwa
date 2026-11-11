# ESCALADE VIA DOMITIA — PWA

Application web progressive pour gérer les cordées, les performances et le classement du challenge d'escalade.

## Fonctionnalités
- Challenges Benjamin (6e/5e) et Minime (4e/3e)
- Cordées de 1 à 3 grimpeurs
- Cotations de 3A à 6C selon le barème fourni
- En tête : points de la voie multipliés par 2
- Bonus collectif : `3 × valeur de la cotation` lorsqu'au moins une performance de chaque membre de la cordée correspond à la même voie et à la même cotation
- Classement actualisé automatiquement, avec détail individuel
- Sauvegarde locale automatique, export JSON et import JSON
- Cache PWA pour le lancement hors connexion après le premier chargement

## Tester sur ordinateur
Un service worker PWA nécessite un contexte sécurisé (HTTPS ou localhost). Dans le dossier du projet, lancez par exemple :

```bash
python -m http.server 8000
```

Puis ouvrez `http://localhost:8000`.

## Installer sur un téléphone ou une tablette Samsung
1. Hébergez le contenu du dossier sur une adresse HTTPS (voir ci-dessous).
2. Ouvrez cette adresse dans Chrome ou Samsung Internet sur l'appareil.
3. Attendez que l'application soit chargée une première fois avec internet.
4. Dans le menu du navigateur, choisissez **Installer l'application** ou **Ajouter à l'écran d'accueil**.
5. Lancez-la depuis sa nouvelle icône. Après le premier chargement, les fichiers de l'application sont mis en cache et l'interface fonctionne hors connexion.

## Hébergement gratuit simple : Netlify
1. Allez sur https://app.netlify.com/drop
2. Décompressez le ZIP.
3. Glissez-déposez le dossier `escalade_via_domitia` (celui qui contient `index.html`) dans la zone de dépôt Netlify.
4. Netlify fournit une URL HTTPS publique. Ouvrez-la sur le Samsung et installez l'application.

Alternative : GitHub Pages (créer un dépôt, déposer les fichiers à la racine, puis activer Pages dans Settings > Pages).

## Données et précautions
- Les données sont conservées dans le stockage local du navigateur de l'appareil : elles ne sont pas synchronisées entre plusieurs téléphones/tablettes.
- Ne videz pas les données du navigateur et ne désinstallez pas l'application avant d'avoir exporté une sauvegarde.
- Pour utiliser plusieurs appareils avec une base commune, il faudra ajouter un serveur et une base de données partagée. Ce projet fonctionne volontairement sans serveur de données.
- Pour une utilisation hors connexion, ouvrez l'application une première fois en ligne afin que le service worker mette les fichiers en cache.

## Règle du bonus
Le bonus est compté une seule fois par combinaison **numéro de voie + cotation** et par cordée, lorsque chaque grimpeur de cette cordée possède au moins une performance correspondante. Le bonus s'ajoute au total de la cordée, mais n'est pas attribué à un grimpeur individuel.
