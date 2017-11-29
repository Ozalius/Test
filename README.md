INSTRUCTIONS D'UTILISATION DU BUNDLE "AutoDbBundle"
===================================================

Bundle développé sous Symfony 3

Versions conseillées : 

* Symfony = 3.3.x
* Twig = 1.35.0
* Php : >= 5.3.3
* Doctrine 2.5.12

(Bien évidemment fonctionnel sous Symfony 3.0.0 et Twig 1.23.1 via une installation normale, voir : https://symfony.com/doc/current/setup.html )

Installation : 
==============

- Insérez le "Vendor" Guillaume avec son Bundle "AutoDbBundle" dans le dossier src/ de votre projet Symfony.

- Ajoutez le bundle dans le fichier composer.json qui se trouve à la racine dans la partie psr-4, si une erreur "Class not found" s'affiche, remplacez les bundles par :

<pre>
<code>
"psr-4": {
    "": "src/"
 },
</code>
</pre>

- Ajoutez cette ligne dans le fichier AppKernel.php : 

<pre>
<code>
new Guillaume\AutoDbBundle\GuillaumeAutoDbBundle(),
</code>
</pre>

- Modifiez votre fichier routing.yml dans votre dossier config :

<pre>
<code>
guillaume_auto_db:
    resource: "@GuillaumeAutoDbBundle/Resources/config/routing.xml"
    prefix:   /
</code>
</pre>

- Mettez à jour votre autoloader pour inclure vos nouvelles Class :
<pre><code>composer dump-autoload</code></pre>

Vous trouverez les différentes routes de votre projet via la commande :
<pre><code>php bin/console debug:router</code></pre>

Guide d'utilisation : 
=============

Ce projet est une première version sous Symfony 3, il permet de créer des entités fonctionant sous Doctrine.

***Seul les associations unidirectionnelles sont disponibles.***

Les différentes routes du bundle : 

* /autodb_p1
* /autodb_p2?nbEntite=n
* /autodb_p3
* /autodb_p4
* /autodb_p5

/autodb_p1
==========

Page permettant de choisir le nombre d'entités.

/autodb_p2?nbEntite=n
=====================

Choix du nom de chaque entités

/autodb_p3
==========

Partie attributs et associations.

Chaque entités possède des attributs et associations, pour l'instant seul les types integer, string, text et boolean sont disponibles, javascript doit être activé pour profiter des différentes possibilités de la page.

Pour ajouter des attributs à une entité, il suffit de cliquer sur le bouton "+", à chaque nouvelle balise input et checkbox, le numéro à la fin de chaque attribut name s'additionne au précédent, exemple :
- name="EntiteA_x0" <- par défaut lors du chargement de la page
- name="EntiteA_x1" <- ajout via javascript
- name="EntiteA_x2" <- ajout via javascript

Ce type de nommage servira pour les associations

Une fois les différents attributs sélectionnés, il faut choisir une association, s'il n'en existe pas, laissez la balise select sur "Aucune"
Si il en existe une, il faut choisir l'une des associations existantes,

Une association contient un choix d'entité à sélectionner, un "nameForeignKey" et un "referencedColumnName" à choisir, qui pointe vers la clé primaire, le "nameForeignKey" est le nom qui sera enregistré dans la base de données et "referencedColumnName" est la clé primaire de l'entité choisit, sélectionnez la clé primaire souhaité.


Exemple : 
* Choix = EntiteB
* nameForeignKey = EntiteB_x0
* referencedColumnName = EntiteB_x0

Résultat final dans la base de données :

> Select : ManyToOne

* EntiteA
* -id
* -EntiteB_id null
-------------------
* EntiteB
* -id
