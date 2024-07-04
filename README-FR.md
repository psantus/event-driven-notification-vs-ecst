# Event-Driven Architecture : réconcilier Notifications et Event-carried State Transfer

Ce repo contient le code d'exemple illustrant 
l'enrichissement d'un événement de type "Notification" 
pour en faire un événement de type "Event-carried State 
Transfer" (ou "événement pleinement qualifié") détaillé 
dans le [billet de blog disponible sur dev.to](https://dev.to/aws-builders/architecture-orientee-evenement-reconcilier-notifications-et-evenements-complets-79b-temp-slug-3688705?preview=557bcfdf9114fb9093567433dfe21b27b8a497d26a0f685fa7a18c7a3b28846d22fbeca68d79d52f7e5340db4ce8d25970ce20b12cd42bdb880929de).

## Contenu 

Deux stacks CloudFormaton permettant de déployer 
* Un bus d'événement
* Des règles de filtrage distribuant les événements vers
  * Des Lambdas pour enrichir les événements (via une API Gateway 
  pour obtenir des invocations synchrones) et bénéficier du retry
  * Des applications consommatrices de l'événement modélisée
  soit par des Lambdas soit par un appel vers une API tierce
  (hébergée sur webhook.site pour tester facilement que ça fonctionne)
* On illustre par ailleurs les capacités d'EventBridge: 
  * logging via Cloudwatch
  * archivage et replay
  * retry, gestion de dead-letter queue et notification 

Ces stacks supposent que le fichier `lambdalayer.zip` soit déposé
dans un bucket S3. Ce fichier contient juste une installation minimale
du aws-sdk (cf. le fichier `package.json`) qui permet de publier 
les Lambda avec le code fonctionnel
* déclaré directement inline dans le template CloudFormation
* lisible et modifiable immédiatement dans la console Lambda.

## Droits de reproduction

Vous pouvez reproduire et modifier cet exemple en citant 
l'auteur (Paul SANTUS - TerraCloud), avec un lient vers 
ce repo Github.

## Limitation de responsabilité

Ce code est fourni tel quel sans garantie d'aucune sorte. 
TerraCloud et Paul SANTUS déclinent toute responsabilité liée à son usage.