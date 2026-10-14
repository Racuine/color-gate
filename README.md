# Color Gate V7 — génération automatique d'un APK Android

Ce dépôt contient le jeu HTML5 dans `www/` et un workflow GitHub Actions qui génère un **APK Android de test** (debug), sans installer Android Studio sur votre PC.

## Télécharger l'APK via GitHub Actions

1. Créez un dépôt GitHub **privé** ou public (par exemple `color-gate`).
2. Extrayez le ZIP, puis envoyez **tout le contenu** du dossier `color-gate-v7` à la racine du dépôt, y compris le dossier caché `.github/workflows/` (indispensable). Vous pouvez utiliser **Add file > Upload files** sur GitHub, ou Git en ligne de commande. Vérifiez que `.github/workflows/build-android.yml` apparaît bien dans le dépôt.
3. Ouvrez l'onglet **Actions** du dépôt. Si GitHub demande d'activer les workflows, autorisez-les.
4. Cliquez sur **Build Color Gate Android APK** puis **Run workflow** (ou attendez la compilation déclenchée par l'envoi sur la branche `main` ou `master`).
5. Lorsque l'exécution est verte, ouvrez-la, descendez à **Artifacts** et téléchargez **ColorGate-V7-APK**. GitHub livre un ZIP contenant `ColorGate-V7-debug.apk`.
6. Extrayez l'APK du ZIP et transférez-le sur votre téléphone Android. Ouvrez-le pour l'installer. Android peut demander l'autorisation d'installer des applications depuis cette source ; n'autorisez cela que pour ce fichier provenant de votre propre dépôt.

## Important

- L'APK est signé automatiquement avec une **clé de développement** (debug). Il est destiné aux tests personnels, **pas** à une publication Google Play.
- Les builds déclenchés par `push` fonctionnent sur les branches `main` et `master` ; le bouton manuel est disponible sur la branche par défaut lorsque le workflow est présent.
- Les fichiers APK générés restent disponibles en tant qu'artifacts pendant 30 jours (selon les limites et réglages GitHub).
- Une connexion Internet et un compte GitHub sont nécessaires pour la compilation ; aucune installation d'Android Studio n'est requise sur votre ordinateur.
- La première compilation télécharge Android/Gradle et peut prendre plusieurs minutes. Elle n'a pas été exécutée dans cet environnement : si une dépendance externe change, le workflow pourrait nécessiter un ajustement.
- `com.colorgate.neonrush` est un identifiant provisoire. Avant publication, choisissez votre identifiant définitif et une signature de production.

## Jouer sur PC

Ouvrez `www/index.html` dans un navigateur. Pour un serveur local, exécutez `npm install` puis `npm run serve`.

## Personnalisation

Modifiez les fichiers de `www/`, envoyez les changements sur GitHub, puis relancez le workflow. Le build reconstruit automatiquement l'APK.
