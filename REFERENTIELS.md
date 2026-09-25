# Référentiels externes

## Principe

Les normes techniques, conventions de code et socles réutilisables ne doivent pas être recopiés dans cette méthode.

La méthode décrit **comment les utiliser** ; leur dépôt d'origine reste la source canonique.

Lors de la phase amont d'un projet :

1. identifier les référentiels applicables ;
2. vérifier que le chef de projet peut les consulter ;
3. relever le commit ou la version consultée ;
4. déterminer les documents et socles applicables au projet ;
5. inscrire ces informations dans le projet ;
6. signaler explicitement les exceptions ;
7. demander à l'exécutant de confirmer qu'il a accès aux références requises avant de coder.

Si l'exécutant n'a pas accès à une référence obligatoire, il doit **STOPPER** au lieu d'inventer les conventions.

## Versionnement

Un projet référence une version précise du référentiel, idéalement un SHA Git.

Une évolution ultérieure du référentiel ne modifie pas implicitement les règles d'un projet existant. La mise à niveau est une décision explicite.

## Cowprod

Référentiel technique canonique :

`Cowprod/referenciel`

Il contient notamment les conventions SQL/PHP, frontend et les socles techniques Cowprod.

Les règles ne sont pas dupliquées ici.

## Hiérarchie

En cas de conflit :

1. décision explicite validée du projet ;
2. exception projet documentée ;
3. référentiel externe déclaré applicable ;
4. conventions générales de cette méthode ;
5. choix libre de l'exécutant.
