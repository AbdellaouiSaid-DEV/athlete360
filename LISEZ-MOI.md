# Athlete 360 : installation sur Android, sans Play Store

Deux façons d'obtenir l'application sur ton téléphone. Les deux fonctionnent **hors ligne** et gardent tes données **uniquement sur le téléphone**.

| | A. Application web installée (PWA) | B. Vrai fichier APK |
|---|---|---|
| Difficulté | la plus simple (10 min) | un peu plus longue (20 min) |
| Ce qu'il te faut | un compte GitHub | un compte GitHub **ou** Android Studio sur PC |
| Résultat | icône sur l'écran d'accueil, plein écran | application installée comme une autre |
| Polices d'origine | oui (au premier chargement en ligne) | polices du téléphone (l'APK n'a pas Internet) |

## A. Version PWA (recommandée pour commencer)

1. Crée un dépôt GitHub (public ou privé), envoie-y le contenu du dossier `pwa/` (index.html, manifest.webmanifest, sw.js, dossier icons).
2. Dépôt → Settings → Pages → Branch `main` / dossier racine → Save. Tu obtiens une adresse en `https://…github.io/…`.
3. Sur le téléphone, ouvre cette adresse **dans Chrome**, laisse la page se charger une fois en ligne.
4. Menu ⋮ → **Installer l'application** (ou « Ajouter à l'écran d'accueil »).

Ensuite elle s'ouvre sans Internet.

## B. APK

### Option 1 : GitHub compile pour toi (sans rien installer sur ton PC)

1. Crée un dépôt GitHub **vide**, envoie-y **tout le contenu de `android-app/`** (le dossier `.github` caché doit y être, `gradlew` aussi).
2. Onglet **Actions** → « Build APK » → Run workflow (il se lance aussi à chaque envoi).
3. Quand c'est vert, ouvre l'exécution → **Artifacts** → `Athlete360-apk` → télécharge le zip → extrais `app-debug.apk`.
4. Envoie l'APK sur ton téléphone (câble, Drive, e-mail), ouvre-le, autorise « Installer des applications inconnues » pour l'application utilisée, puis installe.

### Option 2 : Android Studio

Ouvre le dossier `android-app/` → attends la synchronisation → Build → Build APK(s). Le fichier est dans `app/build/outputs/apk/debug/`.

Exigence : Android 10 ou plus récent.

## Ce qui est déjà réglé d'après ton fichier Excel

Taille 181 cm, poids de référence 75,5 kg, sommeil 8 h, 8 000 pas, eau 2,5 L, protéines minimum 1,6 g/kg, échéance 30/06/2027, plan Push / Pull / Legs / Recovery / Upper / Lower / Recovery, cibles hebdomadaires (5 séances, marche 25 min, mobilité 3, core 3, skills 2), tractions 20 et pompes 100, créatine 3 g notée « non validée », liste de sujets à voir avec ton médecin. Tout est modifiable dans **Réglages**. À renseigner toi-même : date de naissance (pour les besoins énergétiques) et ton premier check-in.

Le **score 360° hebdomadaire** reprend la logique de l'onglet ANALYSE_360 : 8 axes, score affiché seulement si au moins 4 axes sont renseignés.

## Tes données

- Elles sont stockées dans l'application, sur ce téléphone. Rien n'est envoyé nulle part.
- **Désinstaller l'application ou effacer ses données supprime l'historique.** Fais une sauvegarde JSON régulière : Réglages → Sauvegarde complète. Le fichier arrive dans Téléchargements.
- Changer de téléphone : installe l'application, puis Réglages → Restaurer un JSON.
- Import d'un export Lyfta ou d'une balance : Réglages → Import CSV (choix des colonnes, doublons ignorés).

## Limites à connaître

- Je n'ai pas pu compiler l'APK moi-même : le SDK Android n'est pas accessible depuis mon environnement. Le code Android est minimal et sans dépendance, mais la première compilation est à confirmer chez toi. Si une erreur apparaît, envoie-moi le message.
- Français uniquement pour l'instant (pas d'arabe ni de lecture droite-gauche).
- Pas de synchronisation entre appareils, pas de connexion directe à Lyfta ou à une montre.
- Export en CSV et JSON, pas encore d'Excel ni de PDF.
- L'APK « debug » est signé avec une clé de test : parfait pour un usage personnel, pas pour une publication.
