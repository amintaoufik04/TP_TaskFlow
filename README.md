# Réponses aux questions – TP Next.js S1

## Q1. Comparez la structure de votre projet React (Vite) avec Next.js. Quelles différences ?

Dans un projet React avec Vite, on trouve généralement un dossier `src/`, un fichier `main.tsx`, un composant `App.tsx` et le routing est géré dans le code avec `react-router-dom`.

Dans Next.js, la structure repose sur le dossier `app/`. On y trouve notamment `layout.tsx`, `page.tsx` et des dossiers qui représentent directement les routes.

La différence principale est que, dans React, le routing se fait dans le code, tandis que dans Next.js, le routing dépend de la structure des dossiers. 

## Q2. Combien de fichiers avez-vous créé pour cette route ? Comparez avec React Router.

Pour créer la route `/login` en Next.js, un seul fichier suffit : `app/login/page.tsx`.

Avec React Router, il faut en général :
- créer le composant,
- l’importer dans `App.tsx`,
- ajouter la route dans le routeur.

Donc Next.js demande moins de configuration. 

## Q3. En React, on utilisait `useParams()` pour récupérer l’id. En Next.js, comment est-il récupéré ? Quelle différence fondamentale ?

En Next.js, l’identifiant est récupéré grâce à `params`, qui est passé en prop au composant.

En React, `useParams()` est un hook exécuté côté client.

La différence fondamentale est donc que, dans Next.js, la valeur est fournie côté serveur, alors qu’en React SPA elle est récupérée côté client. 

## Q5. En React SPA, combien de lignes fallait-il pour charger les projets ? Combien ici ?

En React SPA, il fallait plusieurs lignes avec `useState`, `useEffect`, `fetch`, `.then()`, la mise à jour du state et parfois une gestion du loading.

En Next.js, quelques lignes suffisent avec un simple `fetch` dans un composant asynchrone.

Le code est donc beaucoup plus court et plus simple en Next.js. 

## Q6. Ouvrez F12 > Network. Voyez-vous la requête GET `/projects` ? Pourquoi ?

Non, on ne voit pas la requête `GET /projects` dans l’onglet Network du navigateur.

La raison est que la requête est exécutée par le serveur Next.js, pas par le navigateur. Le client reçoit directement le HTML déjà rempli avec les données. 

## Q7. Pourquoi faut-il `'use client'` ici et pas dans la page Dashboard ?

Il faut `'use client'` dans la page Login parce qu’elle contient de l’interactivité : `useState`, `onChange`, `onSubmit` et `useRouter()`.

La page Dashboard, elle, affiche seulement des données récupérées côté serveur. C’est donc un Server Component et elle n’a pas besoin de `'use client'`. 

## Q8. En React, on utilisait `useNavigate()` de `react-router-dom`. En Next.js, quel est l’équivalent ?

L’équivalent de `useNavigate()` en Next.js est `useRouter()` avec `router.push()`. 

## Q9. Que voyez-vous dans le code source HTML de React SPA ? Y a-t-il les noms des projets ?

Dans React SPA, le code source HTML contient surtout un `<div id="root"></div>` et un script JavaScript.

Les noms des projets ne sont pas présents directement dans le HTML source, car ils sont ajoutés après le chargement par JavaScript. 

## Q10. Que voyez-vous cette fois dans Next.js ? Les noms des projets sont-ils dans le HTML ?

Dans Next.js, le HTML contient déjà le contenu de la page.

Oui, les noms des projets sont présents directement dans le code source HTML, car la page est rendue côté serveur. 

## Q11. Le Header dans `layout.tsx` ne se re-monte pas quand on navigue. En React Router, comment faisait-on pour obtenir ce comportement ?

En React Router, on plaçait généralement le Header dans un composant parent commun, souvent `App.tsx` ou un layout partagé, puis on affichait les pages à l’intérieur.

Cela permettait de garder le Header fixe pendant que seul le contenu principal changeait. 

## Q12. En Next.js, si je veux un layout spécifique au Dashboard (avec Sidebar), où est-ce que je crée le fichier ?

Il faut créer un fichier `layout.tsx` dans le dossier `app/dashboard/`.

Ce layout s’appliquera uniquement à la route Dashboard et à ses sous-routes. 

## Q13. Le Dashboard est un Server Component. Peut-il utiliser `onClick` ? Pourquoi ?

Non, un Server Component ne peut pas utiliser `onClick`.

La raison est que les événements interactifs comme `onClick` nécessitent du JavaScript côté client, alors qu’un Server Component est rendu côté serveur. 

## Q14. Si je veux ajouter un bouton « + Nouveau projet » sur le Dashboard, dois-je transformer TOUTE la page en Client Component ?

Non, ce n’est pas obligatoire.

On peut garder la page Dashboard en Server Component et créer seulement un petit composant client pour le bouton interactif. Cela permet de conserver les avantages du rendu serveur tout en ajoutant de l’interactivité localement.

## Q15. Le navigateur ne voit jamais l’URL `:4000`. Quel avantage de sécurité cela apporte ?

Cela permet de masquer l’URL réelle de l’API au navigateur.

Ainsi, le client n’accède pas directement au serveur de données. Cela réduit l’exposition de l’architecture interne et limite certains accès directs ou abus côté client.