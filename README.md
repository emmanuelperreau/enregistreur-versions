# Enregistreur : téléchargement

L'Enregistreur est une app de la barre des menus de macOS. Elle enregistre le son du Mac (vidéo, visio, appel) et le micro sur deux pistes, puis en écrit la transcription, sur le Mac.

Ce dépôt ne contient que les versions à installer. Il faut un Mac à puce Apple (M1 ou plus récent) sous macOS 26 ou plus récent.

## Installer

1. Télécharger le fichier `Enregistreur-<version>.dmg` de la [dernière version](../../releases/latest) et l'ouvrir.
2. Glisser « Enregistreur » sur le dossier « Applications ».
3. Ouvrir « Enregistreur » depuis Applications. macOS refuse la première fois : l'app n'est pas certifiée par Apple. Cliquer sur « Terminé » (pas sur « Placer dans la corbeille »).
4. Ouvrir Réglages Système › Confidentialité et sécurité, descendre jusqu'à « "Enregistreur" a été bloquée », cliquer sur « Ouvrir quand même », puis confirmer. C'est à faire une seule fois.
5. L'app apparaît dans la barre des menus : des guillemets « ». Elle demande où ranger les enregistrements, puis, au premier enregistrement, l'autorisation d'utiliser le micro et celle d'enregistrer le son du Mac.

Le mode d'emploi complet est dans le fichier « Lisez-moi » de l'image disque.

### Si une version plus ancienne était déjà installée

Si l'Enregistreur était déjà sur ce Mac avant la version 1.0.8 (ou compilé sur place), macOS garde ses anciennes autorisations et redemande sans fin celle d'enregistrer l'écran et le son, même si « Enregistreur » paraît activé dans les réglages. À faire une fois : quitter l'app, puis, dans le Terminal :

```bash
tccutil reset ScreenCapture fr.serviam.enregistreur
```
```bash
tccutil reset Microphone fr.serviam.enregistreur
```

Rouvrir l'app, cliquer sur les guillemets et accepter les deux demandes. Les mises à jour suivantes, proposées dans le menu, gardent les autorisations.

## Ce que l'app télécharge et envoie

- À son premier lancement, l'app télécharge chez NVIDIA l'outil qui distingue les voix d'une vidéo et son modèle (115 Mo, une fois). Rien n'est envoyé.
- Une fois par jour, l'app lit dans ce dépôt quelle est la dernière version, et la propose dans son menu. Rien n'est envoyé, et rien n'est installé sans un clic.
- Le son ne quitte jamais le Mac. Le texte d'une transcription n'est envoyé à Anthropic que si vous activez vous-même la synthèse par Claude, avec votre propre clé.

## Enregistrer d'autres personnes

Selon le pays et le contexte, enregistrer quelqu'un sans le prévenir peut être interdit. Prévenir les personnes enregistrées relève de la seule responsabilité de l'utilisateur.

## Composants tiers

L'Enregistreur ne contient et ne redistribue aucun de ces composants : l'app de chaque utilisateur les télécharge chez leur éditeur.

- NeMo-Speech.cpp, de NVIDIA (licence Apache 2.0) : [github.com/NVIDIA/NeMo-Speech.cpp](https://github.com/NVIDIA/NeMo-Speech.cpp).
- Nemotron 3 Diarization, de NVIDIA (licence « OpenMDW License Agreement, version 1.1 », [texte](https://openmdw.ai/license/1-1/)) : [huggingface.co/nvidia/Nemotron-3-Diarization](https://huggingface.co/nvidia/Nemotron-3-Diarization).
