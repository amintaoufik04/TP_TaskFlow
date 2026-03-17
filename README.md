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
