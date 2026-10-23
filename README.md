# Signalement Urbain (HTML → APK Android)

Application de signalement urbain en moins de 30 secondes : bouton « Signaler », photo + GPS, détection de doublons,
mode hors ligne, suivi Reçu → En cours → Résolu. Tout le code de l'app est dans `www/index.html`.
L'APK est généré par GitHub Actions avec Capacitor.

## Obtenir l'APK
1. Créez un dépôt GitHub et envoyez le projet (branche `main`) :
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/VOTRE_NOM/signalement-urbain.git
   git push -u origin main
   ```
2. Onglet **Actions** → **Build APK** → **Run workflow** (il se lance aussi à chaque push).
3. Après 5 à 10 minutes, ouvrez l'exécution terminée → **Artifacts** → téléchargez `signalement-urbain-apk`.
4. Décompressez, copiez le `.apk` sur le téléphone, installez (autoriser les « sources inconnues »).

## Tester dans le navigateur
```bash
npx serve www      # puis ouvrez l'adresse affichée (le GPS exige localhost ou https)
```

## Structure
- `www/index.html` : toute l'application (HTML + CSS + JavaScript)
- `www/lib/` : Leaflet (carte OpenStreetMap, aucune clé API)
- `capacitor.config.json` : identifiant et nom de l'app
- `.github/workflows/build.apk.yml` : compilation de l'APK

## À savoir
- L'envoi au serveur est simulé (`fakeSend` dans `index.html`) : remplacez-le par un appel `fetch` vers votre API.
- Le statut du suivi évolue pour la démo (1 min : En cours, 2 min : Résolu).
- Les tuiles de la carte nécessitent internet ; le reste fonctionne hors ligne.
- L'APK est un APK « debug » : parfait pour tester et partager. Pour le Play Store, il faut une signature de release.
