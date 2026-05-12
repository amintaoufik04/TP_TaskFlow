# TaskFlow Next - Réponses au TP (Séance 2)

### Q1 : Différence de rafraîchissement (React SPA vs Next.js)

- **En React SPA :** Après un `POST`, il fallait généralement mettre à jour l'état local manuellement (ex: `setProjects`) pour voir les changements.
- **En Next.js :** On utilise `revalidatePath('/dashboard')`. Cela demande à Next.js de purger le cache du serveur pour cette route, forçant ainsi le composant à se re-rendre avec les données fraîches du serveur.

### Q3 : Pourquoi un `<form>` plutôt qu'un `onClick` pour supprimer ?

- Le **Dashboard** est un **Server Component**. Les Server Components ne supportent pas les gestionnaires d'événements interactifs comme `onClick` car ils ne contiennent pas de JavaScript côté client.
- Le formulaire est la méthode native du web pour envoyer des données au serveur sans JavaScript (Progressive Enhancement).

---

### Q4 : Résultat de l'URL `http://localhost:3000/api/projects`

- En ouvrant cette URL dans le navigateur, vous verrez un objet **JSON** contenant la liste de tous les projets stockés dans le fichier `db.json`.

### Q5 : API Route vs Server Action

- **Server Action :** Conçue pour être appelée depuis des formulaires ou des boutons dans l'interface Next.js. Elle gère automatiquement la mutation de données et la revalidation du cache.
- **API Route :** Un endpoint HTTP standard (REST). Elle est nécessaire si vous voulez que des services externes accèdent à vos données.

---

### Q6 : Comparaison Login (React SPA vs Next.js)

- En **Next.js** avec les Server Actions et `useActionState`, on réduit considérablement le nombre de `useState` car les données sont récupérées via `formData` directement sur le serveur.

### Q7 : Le cookie `session` et HttpOnly

- **Visibilité :** Le cookie est visible dans l'onglet _Application_ de l'inspecteur du navigateur.
- **Sécurité :** Grâce à l'option `httpOnly: true`, il est **impossible** de le lire via le script `document.cookie` dans la console. Cela protège contre le vol de session via des attaques XSS.

---

### Q8 : Le "Flash" de contenu (React SPA vs Next.js)

- **React SPA :** Affichait souvent brièvement le Dashboard avant de rediriger.
- **Next.js (Middleware) :** Le middleware intercepte la requête **avant** même que le serveur ne génère le HTML. Il n'y a donc aucun flash de contenu ni fuite de données.

### Q9 : Pourquoi `middleware.ts` est à la racine ?

- Le fichier `middleware.ts` doit être à la racine du projet (hors du dossier `app/`) pour pouvoir intercepter les requêtes sur l'ensemble de l'application selon la configuration définie.

### Q10 : Récupération du User (Context vs Server)

- **React SPA :** Nécessitait généralement un `AuthContext`, des providers et l'utilisation de hooks comme `useAuth()`.
- **Next.js :** Dans un Server Component comme le `layout.tsx`, on lit le cookie directement avec la fonction `cookies()`.

---

### Q11 : Quel choix pour quel usage ?

- **Formulaire de création (Next.js) :** Server Action.
- **App Mobile :** API Route.

### Q12 : Avantage de sécurité (Cookies vs JWT local)

- L'utilisation de cookies `httpOnly` combinée au middleware empêche l'accès aux données de session par des scripts malveillants, offrant une protection contre le XSS que le stockage local (souvent utilisé en SPA) ne permet pas.

### Q13 : Indépendance vis-à-vis de json-server

- Oui, car les API Routes utilisent le module `fs` de Node.js pour lire et écrire directement dans `db.json`. Next.js devient lui-même le serveur gérant les données.

### Q14 : XSS et HttpOnly

- **Non**, un script XSS injecté ne peut pas voler le cookie car le flag `httpOnly` rend le cookie invisible pour JavaScript.
