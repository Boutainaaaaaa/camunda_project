# camunda_project
## requete POST : 
http://localhost:8080/engine-rest/process-definition/key/Process_api/start

## le 2ème script 
à chaque exécution il crée un nouveau répertoire de destination d'extraction,

Explications :

Fonction getUniqueDestinationPath() :
-Cette fonction utilise SimpleDateFormat pour générer un timestamp au format yyyyMMdd_HHmmss.
-Elle retourne un chemin de répertoire de destination unique basé sur le timestamp généré. Par exemple, "CNI_plugins_20240627_154230".

Modification de extractCommand :
-extractCommand utilise maintenant getUniqueDestinationPath() pour obtenir le chemin de destination d'extraction dynamiquement à chaque exécution.

Exécution du téléchargement :
-La commande de téléchargement curl est exécutée comme précédemment pour télécharger le fichier à partir de l'URL spécifiée.

-Validation des étapes :
Après chaque étape (téléchargement et extraction), le script vérifie le code de sortie du processus. Si le processus échoue (code de sortie différent de 0), une exception est levée.
Gestion des messages de statut :

Les messages de statut sont affichés pour indiquer si le téléchargement et l'extraction ont réussi ou échoué.
La variable de processus process_status est mise à jour en conséquence pour refléter l'état de l'opération.
