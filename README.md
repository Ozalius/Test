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

Utilisation : 
=============

Les différentes routes du bundle : 

* /autodb_p1
* /autodb_p2?nbEntite=n
* /autodb_p3
* /autodb_p4
* /autodb_p5

