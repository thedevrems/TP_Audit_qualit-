# 🎭 Projet d'évaluation accessibilité – B2 Ynov – Molière, le spectacle musical

Vous êtes développeur·se dans une agence web chargée de finaliser le site de réservation de la comédie musicale Molière, l’opéra urbain.

Un·e stagiaire ou développeur·se junior a livré un site contenant **plusieurs erreurs d’accessibilité**.
Votre mission est de les **identifier et de corriger le site** pour garantir sa conformité avec les bonnes pratiques vues en cours.

---

## 📂 Repository du projet

Ce projet est hébergé ici :

➡️ **https://github.com/mariegautron/eval-b2-ynov**

> ⚠️ **Attention : NE RIEN PUSHER SUR `main` !!**
>
> Vous devez créer **votre branche personnelle** pour travailler proprement (voir étapes plus bas).

---

## 🎯 Objectifs pédagogiques

- Identifier les erreurs d’accessibilité dans un projet existant
- Appliquer les bonnes pratiques HTML et CSS pour corriger les défauts d’accessibilité
- Versionner proprement votre travail avec Git
- Justifier vos choix de correction dans la merge request finale

---

## 📝 Consignes détaillées

### 🚦 Étapes du travail

1. Clonez le dépôt sur votre machine locale
2. Créez votre branche personnelle **avant toute modification**
3. Analysez l’accessibilité du site et notez les erreurs rencontrées
4. Corrigez les erreurs dans le code HTML et CSS existant
5. Commitez régulièrement avec des messages explicites
6. Poussez votre branche personnelle
7. Créez une **merge request** vers `main` pour proposer vos corrections

---

### 🚫 NE PAS FAIRE :

- 🚫 Ne pas pousser directement sur `main`

---

### ✅ À FAIRE :

- ✅ Utiliser les bonnes pratiques HTML sémantique
- ✅ **Ajouter un lien d'évitement**
- ✅ Vérifier la hiérarchie des titres
- ✅ Contrôler la navigation clavier
- ✅ Vérifier les contrastes de couleurs
- ✅ Vérifier les textes de remplacement (alt) sur toutes les images et icônes
- ✅ Corriger le focus visible pour tous les éléments interactifs
- ✅ Corriger le formulaire
- ✅ Faire des commits clairs et précis
- ✅ Documenter dans la merge request vos choix et corrections

---

## 🧩 Ressources à votre disposition

### 🛠️ Outils d’audit accessibilité :

- [Wave Accessibility Evaluation Tool](https://wave.webaim.org/)
- [axe DevTools – extension Chrome](https://www.deque.com/axe/devtools/)
- [Google Lighthouse (dans DevTools Chrome)](https://developer.chrome.com/docs/lighthouse/accessibility/)
- [Color Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [RGAA – Référentiel général d’amélioration de l’accessibilité](https://accessibilite.numerique.gouv.fr/)

Mais aussi le cours (tout est sur Moodle) et internet !

Attention :

> Les IA comme ChatGPT peuvent être utiles, mais avec précaution. Elles génèrent parfois des erreurs d’accessibilité, notamment sur les attributs alt ou la sémantique.
> Exemple : l’IA ne sait pas si une image est décorative ou informative, elle peut donc se tromper !

**C'est à vous d'évaluer la pertinence des solutions.**

---

## 🚀 Workflow Git recommandé

1. **Clonez le projet**

```bash
git clone https://github.com/mariegautron/eval-b2-ynov.git
cd eval-b2-ynov
```

2. **Créez votre branche personnelle**

Remplacez `prenom-nom` par votre prénom et nom :

```bash
git checkout -b prenom-nom
```

3. **Travaillez sur votre branche**

Modifiez les fichiers existants (`index.html`, `infos.html`, `style.css`).

4. **Commitez vos modifications**

Faites des commits clairs à chaque étape :

```bash
git add .
git commit -m "Correction contraste formulaire"
```

5. **Poussez votre branche sur le dépôt distant**

```bash
git push origin prenom-nom
```

6. **Créez votre merge request**

- Sur GitHub, cliquez sur **Compare & pull request**
- Renseignez :
  - ✅ Description des erreurs détectées
  - ✅ Liste des corrections apportées
  - ✅ Remarques ou suggestions éventuelles

---

## 🗓️ Date de rendu

**⚠️ À rendre impérativement avant le : 14 avril à 17h30**

Au-delà de cette date, la merge request ne sera plus prise en compte.

---

## 🎓 Critères d’évaluation

| Critère                                | Détail                                                         |
| -------------------------------------- | -------------------------------------------------------------- |
| 🧩 Qualité des corrections             | Pertinence et exhaustivité des corrections d’accessibilité     |
| 🛠️ Propreté du code                    | Code bien indenté, lisible, respect des conventions HTML/CSS   |
| 📝 Qualité des commits                 | Messages explicites et commits réguliers                       |
| 🔍 Documentation dans la merge request | Explication des erreurs détectées et des corrections apportées |
| ✅ Respect du process Git              | Travail dans une branche, merge request propre                 |

---

## 📩 Questions ?

En cas de doute, vous pouvez poser vos questions directement sur Discord.
