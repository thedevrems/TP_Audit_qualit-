# Audit Qualité Web - Site Molière
## Référentiel Opquast - 245 règles (2025)

**Auditeur** : Consultant Qualité Web
**Date** : 12 janvier 2026
**Pages auditées** :
- Page Accueil (index.html)
- Page Infos & Réservation (infos.html)

---

## Constats identifiés (10 problèmes)

### CATÉGORIE : FORMULAIRES (3 constats)

#### Constat n°1 - Formulaire

**Règle Opquast** : Règle n°99 - Chaque champ de formulaire est associé dans le code source à une étiquette qui lui est propre
**Catégorie** : Formulaires
**Localisation** : Page Infos & Réservation - Section formulaire de réservation (lignes 100-118)

**Description factuelle**
Les champs de formulaire (Prénom, Nom, Email, Nombre de places) possèdent des balises `<label>` visuellement présentes, mais elles ne sont pas associées techniquement aux champs via les attributs `for` et `id`. Par exemple, ligne 101-103 :
```html
<label>Prénom</label>
<input type="text" name="prenom" />
```

**Impact utilisateur**
- **Pour qui** : Utilisateurs de lecteurs d'écran (NVDA, JAWS, VoiceOver)
- **Conséquence** : Le lecteur d'écran annonce uniquement "champ de texte vide" sans indiquer ce qu'il faut saisir. L'utilisateur doit deviner le contexte ou explorer manuellement la page.

**Priorité** : **P1 - Bloquant**

**Piste d'amélioration**
Associer chaque label à son champ en ajoutant un attribut `id` unique sur chaque input et l'attribut `for` correspondant sur chaque label. Exemple : `<label for="prenom">Prénom</label>` et `<input type="text" id="prenom" name="prenom" />`.

---

#### Constat n°2 - Formulaire

**Règle Opquast** : Règle n°98 - Les champs de formulaire sont regroupés par thématiques à l'aide de balises appropriées
**Catégorie** : Formulaires
**Localisation** : Page Infos & Réservation - Formulaire de réservation (lignes 95-164)

**Description factuelle**
Le formulaire de réservation n'est pas encapsulé dans une balise `<form>`. Les champs sont placés directement dans une `<div>` (ligne 99). Il n'y a pas de balise form avec attributs action et method.

**Impact utilisateur**
- **Pour qui** : Tous les utilisateurs, notamment ceux utilisant des technologies d'assistance
- **Conséquence** :
  - Les gestionnaires de mots de passe ne détectent pas le formulaire
  - Impossible de soumettre avec la touche Entrée
  - Les lecteurs d'écran n'annoncent pas le début/fin du formulaire
  - Navigation entre champs (Shift+Tab) moins intuitive

**Priorité** : **P1 - Bloquant**

**Piste d'amélioration**
Encapsuler tous les champs dans une balise `<form>` avec les attributs `action` et `method` appropriés. Structurer les groupes de champs connexes avec des `<fieldset>` et `<legend>` (déjà partiellement fait pour l'accessibilité lignes 133-153).

---

#### Constat n°3 - Formulaire

**Règle Opquast** : Règle n°103 - Les boutons d'envoi de formulaire ont un intitulé explicite
**Catégorie** : Formulaires
**Localisation** : Page Infos & Réservation - Bouton d'envoi du formulaire (lignes 159-161)

**Description factuelle**
Le bouton d'envoi du formulaire ne contient qu'une icône Font Awesome sans texte :
```html
<button class="btn">
  <i class="fas fa-paper-plane"></i>
</button>
```
Aucun texte visible ni attribut `aria-label` pour expliciter l'action.

**Impact utilisateur**
- **Pour qui** : Utilisateurs de lecteurs d'écran, utilisateurs ayant désactivé les icônes, utilisateurs avec déficience cognitive
- **Conséquence** :
  - Le lecteur d'écran annonce uniquement "bouton" sans préciser son rôle
  - Utilisateurs visuels ne comprennent pas forcément qu'une icône d'avion en papier signifie "envoyer"
  - Confusion possible avec d'autres actions

**Priorité** : **P1 - Bloquant**

**Piste d'amélioration**
Ajouter un texte explicite dans le bouton ("Envoyer ma réservation" ou "Valider") accompagné de l'icône, ou à défaut ajouter un attribut `aria-label="Envoyer ma réservation"` sur le bouton.

---

### CATÉGORIE : CONTENUS (3 constats)

#### Constat n°4 - Images

**Règle Opquast** : Règle n°1 - Chaque image porteuse d'information est dotée d'une alternative textuelle appropriée
**Catégorie** : Contenus
**Localisation** :
- Page Accueil - Image héros (ligne 45)
- Page Accueil - Galerie photos (ligne 157)

**Description factuelle**
Deux images ne possèdent pas d'attribut `alt` :
1. L'image principale du héros `<img src="images/moliere.png" class="hero-image" />` (ligne 45)
2. Une image de la galerie `<img src="images/scene1.png" />` (ligne 157)

Une autre image possède un alt trop vague : `alt="Image d'une belle scène"` (ligne 96) qui ne décrit pas le contenu informationnel.

**Impact utilisateur**
- **Pour qui** : Utilisateurs de lecteurs d'écran, utilisateurs avec images désactivées, référencement
- **Conséquence** :
  - Le lecteur d'écran ignore complètement l'image ou annonce le nom du fichier ("moliere.png")
  - Perte d'information contextuelle importante
  - Mauvaise compréhension du contenu de la page

**Priorité** : **P1 - Bloquant**

**Piste d'amélioration**
Ajouter des alternatives textuelles descriptives et pertinentes pour toutes les images porteuses d'information. Exemples :
- Image héros : `alt="Affiche du spectacle musical Molière avec les acteurs principaux en costume d'époque"`
- Image galerie : `alt="Scène du spectacle montrant les comédiens dans une chorégraphie"`

---

#### Constat n°5 - Icônes décoratives

**Règle Opquast** : Règle n°2 - Chaque image de décoration est dotée d'une alternative textuelle vide
**Catégorie** : Contenus
**Localisation** :
- Page Accueil - Bouton CTA (ligne 50)
- Page Accueil - Section chiffres clés (lignes 130, 135)
- Page Accueil - Réseaux sociaux (lignes 229, 237, 245)

**Description factuelle**
Les icônes décoratives Font Awesome utilisent incorrectement l'attribut `alt` qui n'est pas valide sur les balises `<i>` :
```html
<i class="fas fa-ticket-alt" alt="Icône billet"></i>
<i class="fas fa-users" alt="Icône utilisateurs"></i>
```

Seule une icône utilise correctement `aria-hidden="true"` (ligne 140).

**Impact utilisateur**
- **Pour qui** : Utilisateurs de lecteurs d'écran
- **Conséquence** :
  - Les lecteurs d'écran peuvent lire le caractère Unicode de l'icône de façon incompréhensible
  - L'attribut `alt` sur `<i>` n'est pas reconnu et crée du code HTML invalide
  - Pollution sonore inutile pour les utilisateurs de technologies d'assistance

**Priorité** : **P2 - Important**

**Piste d'amélioration**
Pour les icônes purement décoratives (accompagnées de texte), ajouter `aria-hidden="true"` sur toutes les balises `<i>` et supprimer les attributs `alt` invalides. Si l'icône porte une information seule, utiliser `role="img"` et `aria-label` avec une description pertinente.

---

#### Constat n°6 - Liens explicites

**Règle Opquast** : Règle n°127 - Le libellé de chaque lien décrit sa fonction ou la nature du contenu vers lequel il pointe
**Catégorie** : Contenus
**Localisation** : Page Accueil - Bouton CTA héros (lignes 49-52)

**Description factuelle**
Le bouton d'action principal de la page contient uniquement le texte "Cliquez ici" :
```html
<a href="infos.html#billetterie" class="btn">
  <i class="fas fa-ticket-alt" alt="Icône billet"></i>
  <span>Cliquez ici</span>
</a>
```

**Impact utilisateur**
- **Pour qui** : Utilisateurs de lecteurs d'écran naviguant par liste de liens, utilisateurs avec déficiences cognitives, référencement
- **Conséquence** :
  - Hors contexte, le lien "Cliquez ici" n'indique pas vers quoi il pointe
  - Les lecteurs d'écran peuvent lister tous les liens : plusieurs "Cliquez ici" identiques perdent leur sens
  - Mauvaise expérience utilisateur et mauvaises pratiques SEO

**Priorité** : **P2 - Important**

**Piste d'amélioration**
Remplacer "Cliquez ici" par un intitulé explicite décrivant l'action, par exemple : "Réserver vos places", "Accéder à la billetterie" ou "Voir les tarifs et réserver".

---

### CATÉGORIE : STRUCTURE ET NAVIGATION (3 constats)

#### Constat n°7 - Hiérarchie de titres

**Règle Opquast** : Règle n°226 - La hiérarchie des titres de contenu est cohérente
**Catégorie** : Structure
**Localisation** : Page Accueil - Plusieurs sections

**Description factuelle**
La hiérarchie des titres présente plusieurs incohérences :
1. Un `<h3>` (ligne 47) apparaît avant le premier `<h2>` (ligne 74)
2. Passage direct de `<h3>` à `<h6>` (ligne 59) sans niveaux intermédiaires
3. Utilisation de `<h4>` (ligne 109) après `<h2>` de manière incohérente
4. Pas de `<h1>` sur la page Accueil (présent uniquement sur infos.html)

**Impact utilisateur**
- **Pour qui** : Utilisateurs de lecteurs d'écran, utilisateurs naviguant par titres, robots d'indexation
- **Conséquence** :
  - Navigation par titres (raccourci clavier H) devient confuse et non logique
  - Structure du document incompréhensible pour les technologies d'assistance
  - Mauvaise hiérarchisation de l'information
  - Impact négatif sur le référencement (absence de H1)

**Priorité** : **P1 - Bloquant**

**Piste d'amélioration**
Restructurer la hiérarchie des titres de manière logique et séquentielle :
- Ajouter un `<h1>` unique en haut de page (par exemple sur "Molière, le spectacle musical")
- Respecter l'ordre h1 > h2 > h3 > h4 sans sauter de niveaux
- Utiliser les niveaux selon l'importance sémantique du contenu, pas selon le style visuel souhaité

---

#### Constat n°8 - Indicateur de focus

**Règle Opquast** : Règle n°185 - Les éléments interactifs sont visuellement identifiables au focus clavier
**Catégorie** : Navigation
**Localisation** :
- style.css - Boutons (ligne 196)
- style.css - Champs de formulaire (ligne 453)

**Description factuelle**
Le CSS supprime l'indicateur visuel de focus sur les éléments interactifs :
```css
.btn:hover,
.btn:focus {
  outline: none; /* ligne 196 */
}

.section-intro input:focus,
.section-intro select:focus,
.section-intro textarea:focus {
  outline: none; /* ligne 453 */
}
```

**Impact utilisateur**
- **Pour qui** : Utilisateurs naviguant au clavier (mobilité réduite, handicap moteur, utilisateurs experts)
- **Conséquence** :
  - Impossible de savoir visuellement quel élément a le focus lors de la navigation au clavier (Tab)
  - Perte de repères et confusion lors du remplissage de formulaires
  - Navigation clavier totalement inaccessible

**Priorité** : **P1 - Bloquant**

**Piste d'amélioration**
Ne jamais supprimer `outline` sans le remplacer par un indicateur visuel équivalent. Conserver `outline` ou créer un style de focus personnalisé visible (bordure épaisse, changement de couleur, ombre portée, etc.) respectant un ratio de contraste suffisant (3:1 minimum avec l'état par défaut).

---

#### Constat n°9 - Rôles ARIA redondants

**Règle Opquast** : Règle n°227 - Les rôles, propriétés et états ARIA sont utilisés en respectant les règles de l'API ARIA
**Catégorie** : Structure
**Localisation** :
- Page Accueil - Section héros (ligne 34)
- Page Infos & Réservation - Header (ligne 36)

**Description factuelle**
Des rôles ARIA sont utilisés de manière redondante ou inappropriée :
1. `<div class="hero" role="banner">` (index.html, ligne 34) - une div avec role="banner" au lieu d'un `<header>`
2. `<header class="hero" role="banner">` (infos.html, ligne 36) - role="banner" redondant car `<header>` a déjà ce rôle implicite au niveau racine

**Impact utilisateur**
- **Pour qui** : Utilisateurs de lecteurs d'écran
- **Conséquence** :
  - Code HTML non conforme aux bonnes pratiques ARIA
  - Risque de confusion avec plusieurs éléments banner (maximum 1 par page)
  - Pollution sémantique inutile
  - Maintenance du code plus difficile

**Priorité** : **P3 - Amélioration**

**Piste d'amélioration**
Utiliser les balises HTML sémantiques natives plutôt que des rôles ARIA :
- Remplacer `<div role="banner">` par `<header>` (qui a le rôle banner implicite)
- Supprimer `role="banner"` sur les `<header>` déjà présents
- Réserver ARIA aux situations où HTML natif ne suffit pas

---

### CATÉGORIE : PRÉSENTATION (1 constat)

#### Constat n°10 - Iframe

**Règle Opquast** : Règle n°146 - Chaque iframe est dotée d'un titre (title) pertinent
**Catégorie** : Présentation
**Localisation** : Page Infos & Réservation - Carte Google Maps (lignes 81-90)

**Description factuelle**
L'iframe Google Maps possède bien un attribut `title="Carte du Zénith de Paris"` (ligne 88), ce qui est conforme. Cependant, l'attribut `tabindex="-1"` (ligne 89) retire complètement l'iframe de l'ordre de navigation au clavier.

**Impact utilisateur**
- **Pour qui** : Utilisateurs naviguant au clavier souhaitant interagir avec la carte
- **Conséquence** :
  - Impossible d'accéder à la carte avec le clavier seul (Tab)
  - Les fonctionnalités de zoom, déplacement de la carte sont inaccessibles au clavier
  - Discrimination envers les utilisateurs ne pouvant pas utiliser une souris

**Priorité** : **P2 - Important**

**Piste d'amélioration**
Supprimer l'attribut `tabindex="-1"` pour permettre l'accès au clavier. Si l'objectif était d'éviter un piège au clavier, ajouter plutôt un lien d'évitement avant l'iframe permettant de la contourner ("Passer la carte"), tout en la laissant accessible.

---

## Synthèse de l'audit

### Répartition des constats
- **Formulaires** : 3 constats (conformité atteinte ✓)
- **Contenus** : 3 constats (conformité atteinte ✓)
- **Structure et Navigation** : 3 constats (conformité atteinte ✓)
- **Présentation** : 1 constat

### Répartition par priorité
- **P1 - Bloquant** : 5 constats
- **P2 - Important** : 4 constats
- **P3 - Amélioration** : 1 constat

### Recommandations prioritaires

Les 3 problèmes les plus critiques à corriger en priorité :

1. **Formulaire sans structure** (Constat n°2) - Encapsuler dans une balise `<form>`
2. **Labels non associés** (Constat n°1) - Associer tous les labels avec for/id
3. **Indicateurs de focus supprimés** (Constat n°8) - Rétablir les indicateurs visuels

Ces corrections amélioreront significativement l'accessibilité du site pour les utilisateurs de technologies d'assistance et de navigation clavier.

### Points positifs observés

- Présence de `aria-current="page"` sur les liens de navigation active
- Utilisation de `rel="noopener noreferrer"` sur les liens externes
- Certaines régions ARIA bien utilisées avec `aria-labelledby`
- Fieldset correctement utilisé pour les checkboxes d'accessibilité
- Attribut `lang="fr"` présent sur le HTML
- Responsive design mis en place

---

**Fin de l'audit**
