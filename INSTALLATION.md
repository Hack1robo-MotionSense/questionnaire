# Envoyer les réponses vers un Google Sheet

Les réponses partent en une seule fois, quand le participant appuie sur « Arrêter et exporter les données ».
Le fichier CSV est aussi téléchargé sur l'appareil, en secours.

## 1. Créer le Google Sheet
1. Créez un Google Sheet vide (par exemple « MotionSense – réponses »).
2. Partagez-le uniquement avec les membres de l'équipe d'analyse.

## 2. Installer le script
1. Dans le Sheet : **Extensions › Apps Script**.
2. Effacez le contenu, collez celui de `google-apps-script.gs`, enregistrez.
3. **Déployer › Nouveau déploiement** › type **Application Web** :
   - Exécuter en tant que : **Moi**
   - Qui a accès : **Tout le monde**
4. Autorisez l'accès quand Google le demande, puis copiez l'**URL de l'application Web** (elle finit par `/exec`).

« Tout le monde » permet seulement d'*envoyer* des lignes au script. Le Sheet reste privé : personne d'autre que l'équipe ne peut le lire.

## 3. Brancher le questionnaire
Dans `index.html`, collez l'URL entre les guillemets :

```js
const URL_ENVOI = "https://script.google.com/macros/s/…/exec";
```

Si vous changez `CLE_ENVOI`, changez-la aux deux endroits (questionnaire et script).

## 4. Vérifier
Faites une passation rapide jusqu'à l'export : un onglet « Réponses » apparaît dans le Sheet, avec une ligne par réponse.
Le CSV se télécharge ensuite depuis le Sheet : **Fichier › Télécharger › CSV**.
