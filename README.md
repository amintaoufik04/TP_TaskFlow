# TaskFlow Next - Réponses au TP (Séance 3)


### Q1 : Vérification avec Prisma Studio
* **Observation** : En exécutant `npx prisma studio`, une interface web s'ouvre. Elle permet de visualiser directement le contenu du fichier `dev.db`.
* **Données** : On y retrouve les données insérées par le script de seed : l'utilisateur admin (`admin@taskflow.com`) et les projets initiaux ("App Mobile", "API Back").

---

### Q2 : Gain de productivité (Prisma vs `fs`)
* **Comparaison** : L'ancien code nécessitait de lire manuellement le fichier, transformer le JSON, manipuler le tableau, puis réécrire le fichier. 
* **Résultat** : Avec Prisma, ces opérations se font en une seule ligne de commande asynchrone (ex: `prisma.project.findMany()`), ce qui réduit drastiquement le nombre de lignes et les risques d'erreurs de manipulation de fichiers.

### Q3 : Suppression de `db.json`
* **Fonctionnement** : L'application fonctionne toujours après la suppression de `db.json` car Prisma utilise désormais une véritable base de données relationnelle stockée dans `prisma/dev.db`.

---

### Q4 : Accès Prisma (Server vs Client)
* **Server Component** : Il peut appeler `prisma` directement car il s'exécute sur le serveur, là où la base de données et les variables d'environnement sont accessibles.
* **Client Component** : Il ne peut PAS appeler `prisma` directement pour des raisons de sécurité (ne pas exposer la BDD au navigateur) et de compatibilité (le client ne peut pas exécuter de code Node.js natif).

---

### Q5 : Optimisation des polices (`next/font`)
* **Observation** : Dans l'onglet Network, on voit **zéro** requête vers les serveurs de Google Fonts.
* **Explication** : Next.js télécharge la police au moment du build et l'héberge localement, ce qui améliore la confidentialité et les performances.

---


### Q6 : Moment de génération des pages
* **Réponse** : Avec `generateStaticParams`, les pages connues sont générées **au moment du build**. Cela permet un chargement instantané car le serveur envoie un fichier HTML déjà prêt.

---

### Q7 : Gestion des nouveaux projets (Fallback)
* **Réponse** : Si un projet est créé après le build, la page sera générée à la demande (dynamiquement) lors de la première visite. Elle sera ensuite mise en cache par Next.js pour les visites suivantes.

---

### Q9 : Tableau récapitulatif

| Caractéristique | React SPA (Vite) | Next.js Full-Stack |
| :--- | :--- | :--- |
| **Routing** | Client-side (React Router) | File-system App Router  |
| **Data fetching** | `useEffect` + Fetch/Axios | Server Components + Prisma direct  |
| **Mutations** | Appels API manuels | Server Actions  |
| **Auth** | Context + JWT local | Cookies HttpOnly + Middleware  |
| **Performance** | Chargement côté client | SSG / Streaming / Image optimization  |

### Q10 : Choix pour une Startup
* **Choix** : Next.js Full-Stack.
* **Pourquoi** : Il permet de déployer une application complète, performante et optimisée pour le SEO avec une seule base de code, tout en simplifiant la gestion de la base de données via Prisma.
