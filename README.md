Séance 3 :

Q1.
Parce que <Navigate /> sert à rediriger directement dans le composant.

Q2.
navigate(from) ajoute une page dans l’historique tandis que replace: true remplace la page actuelle.

Q3.
Parce que c’est plus rapide et ça évite de refaire un GET.

Q4. Résultats des scénarios :
a) /dashboard sans connexion → redirection vers /login
b) /projects/1 sans connexion → redirection vers /login
c) /nimportequoi → redirection vers /dashboard
d) / → redirection vers /dashboard
e) Bouton retour → revient ou non selon replace: true

Q5.
Link sert à naviguer tandis que NavLink sert à naviguer et montre aussi le lien actif.

Q6.
POST = créer un projet tandis que PUT = modifier un projet

Q7. Si json-server est arrêté et on fait un POST, le message s’affiche ?
Oui, le message d’erreur s’affiche.

Q8. Avec Axios, que fait un 404 ?
Axios envoie directement une erreur dans le catch.

Séance 4 :

Gemini a dit
Voici les réponses aux questions (Q1 à Q10) basées sur le document TP Séance 4 et les concepts de développement front-end associés.

Comparaison MUI vs Bootstrap (UI)
Q1. Pour le Header MUI, vous n'écrivez généralement aucune ligne de CSS dans un fichier externe. Tout le style est géré via la prop sx={{...}} directement sur les composants. En comparaison, un fichier Header.module.css classique contiendrait plusieurs classes et de nombreuses lignes de code CSS traditionnel.

Q2.  Bootstrap est souvent plus court et perçu comme plus lisible pour les habitués du CSS, car il utilise des classes utilitaires (ex: ms-auto, fw-bold).

MUI est plus verbeux (plus de composants imbriqués comme <Box>, <Toolbar>, <Typography>), mais il offre un contrôle plus granulaire et typé via TypeScript.

Q3. Option A (sx) : Préféré pour l'intégration totale dans le JS/TS (pas de switch de fichier), l'accès direct au "thème" (espacements, couleurs) et la puissance du CSS-in-JS.

Option B (className) : Préféré pour la séparation des préoccupations, la légèreté visuelle du JSX et la familiarité avec le standard CSS.


Après avoir testé les deux bibliothèques dans le projet TaskFlow, voici une synthèse des différences observées:

| Critère | Material UI (MUI) | React-Bootstrap |
| :--- | :--- | :--- |
| **Installation** | `npm install @mui/material @emotion/react @emotion/styled @mui/icons-material`  | `npm install react-bootstrap bootstrap`  |
| **Nombre de composants** | Très élevé (système complet de design)  | Modéré (composants essentiels du web)  |
| **Lignes de CSS écrites** | Généralement 0 (utilisation de props)  | 0 (utilisation de classes utilitaires)  |
| **Système de style** | Prop `sx={{...}}` (CSS-in-JS)  | Classes CSS (`className`)  |
| **Personnalisation** | Via un objet de thème centralisé  | Via des variables Sass ou classes globales  |
| **Responsive** | Props réactives (ex: `display: { xs: 'none', md: 'block' }`) | Système de grille standard (Col, Row) et classes mobiles |
| **Lisibilité du code** | Plus verbeux (beaucoup de composants structurels)  | Plus compact et proche du HTML classique  |
| **Documentation** | Très exhaustive, riche en exemples interactifs | Claire, concise, basée sur la logique Bootstrap |

---

Q4. MUI est souvent choisi pour des applications professionnelles complexes (Tableaux de bord, ERP) grâce à sa bibliothèque de composants très riche et son design "Material" rigoureux.

Bootstrap est privilégié pour sa rapidité de mise en œuvre, sa légèreté et la facilité de trouver des intégrateurs connaissant déjà les classes standards.

Q5. Pour des raisons de sécurité et d'architecture. React s'exécute dans le navigateur du client. Si React se connectait directement à MySQL, les identifiants de la base de données seraient visibles par tous les utilisateurs (F12 > Network). De plus, un navigateur ne possède pas les protocoles natifs pour communiquer directement avec un moteur SQL ; il faut une API (Backend) pour faire l'intermédiaire.

Q6.

1) Sécurité : Aucune gestion réelle de l'authentification ou des permissions (tout le monde peut tout modifier).

2) Performance/Scalabilité : Les données sont stockées dans un simple fichier .json qui est lu/écrit entièrement à chaque modification.

3) Concurrence : Il n'est pas conçu pour gérer des centaines d'utilisateurs simultanés écrivant dans le même fichier sans risque de corruption de données.

Q7. Firebase fournit un SDK client qui gère la sécurité via des "Security Rules" définies sur le serveur Firebase. Ce n'est pas une connexion directe à une base brute, mais une communication via une API sécurisée gérée par Google qui remplace le rôle du backend traditionnel.

Q8. 

=> Remplacer json-server par un véritable Backend (Node/Express, Python, etc.).

=> Remplacer db.json par une Base de données robuste (PostgreSQL, MongoDB, MySQL).

=> Mettre en place une authentification sécurisée (JWT, OAuth) et non un simple filtrage par email.

=> Héberger l'API et la BDD sur un serveur de production (Cloud, VPS).

Q9. 

=> Taille du bundle : Elles augmentent le poids de l'application, ralentissant le chargement initial.

=> Maintenance : Si la library n'est plus mise à jour, vous risquez des failles de sécurité ou une incompatibilité avec les futures versions de React.

=> Difficulté de personnalisation : Parfois, sortir du design "standard" de la library devient plus complexe que de coder son propre CSS.

Q10. Firebase est le meilleur choix ici. Il possède des fonctionnalités natives de Real-time Database ou Firestore qui poussent les nouveaux messages instantanément vers les clients sans avoir à rafraîchir la page (Websockets gérés par Firebase). Un backend custom est aussi possible mais plus long à développer.
