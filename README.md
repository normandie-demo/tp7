# TP numéro 7

## Objectif:

Exécuter une tâche dans un playbook et récupérer son résultat
Afficher le résultat d’une tâche
Exécuter une tâche de façon conditionnelle

## Besoin:

- Se connecter sur *server-1.scc-edu* et arrêter le service *nginx*
- Modifier le playbook *nginx.yaml* pour:
  - Ajouter une tâche post-install pour vérifier la présence d’un process *nginx* avec `ps -ef | grep nginx | grep -v grep | wc -l`
  - Afficher le résultat de la commande via debug et msg
  - Démarrer le service s’il n’y a pas de processus présent
- Exécuter le playbook *nginx.yaml*
