# Application Ascenseur Control — v2

Outil FR/NL hors-ligne qui transforme une analyse de risques ou un rapport de visite ascenseur en tableau de remarques (constat, explication, solution, code Orona DR/MR, contrôles), pour tous les vendeurs.

**Ouvrir :** https://mbbouazza1975-sys.github.io/ascenseur-control/v2/ (ou double-clic sur le fichier HTML, sans installation).

## Ce qui change par rapport à la v1
- **Dossiers multi-appareils** : un dossier (client, adresse, réf. offre) contient plusieurs ascenseurs ; export Word/Excel du dossier complet ou d'un seul appareil, avec récapitulatif codes × quantité.
- **Référentiel des codes modifiable** : ajout, correction, désactivation de codes, règles « référence → code », remarques validées.
- **Circuit de validation** : les vendeurs proposent, le référent valide et publie un fichier versionné sur Teams.
- **Historique** des dossiers (stockage IndexedDB du navigateur) et sauvegarde complète en fichier.
- Base de connaissances auditée : 95 thèmes FR/NL (79 en v1, 56 corrections, 16 ajouts) ; mots-clés reconnus en mots entiers.
- Intitulé d'offre imposé par ligne (ex. téléphonie GOA en DR0000).

## Circuit du référentiel
1. Le référent dépose `referentiel-ascenseur-control-vN.json` dans un dossier Teams/SharePoint **en lecture seule pour les vendeurs**.
2. Chaque vendeur l'importe (onglet « Référentiel des codes »).
3. Un vendeur ajoute ou corrige un code : appliqué tout de suite sur son PC, puis « Envoyer mes propositions » → fichier JSON au référent.
4. Le référent importe les propositions, accepte/refuse (conflits signalés), publie la version N+1 et la dépose sur Teams.

## Technique
- Un seul fichier HTML (~3,4 Mo), JavaScript sans framework, aucun serveur, aucune requête réseau.
- Bibliothèques embarquées : pdf.js (lecture PDF), SheetJS (Excel), docx (Word).
- Sources dans `src/` ; `python3 build.py` produit `dist/index.html` (sans codes Orona, publiable) et la version complète (usage interne).
- Les codes Orona ne sont pas publiés ici : ils sont dans le fichier référentiel distribué en interne.

## Limites
- PDF scannés non lus (coller le texte).
- Les correspondances par mots-clés sont « Probables » : relecture par l'ingénieur obligatoire avant envoi.
- Données stockées dans le navigateur de chaque PC : sauvegarde régulière.

Version 2.0 — novembre 2026 — Mohamed Bouazza
