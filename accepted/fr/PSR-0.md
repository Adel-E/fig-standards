La section suivante décrit les exigences obligatoires qui doivent être respectées pour l'interopérabilité avec un autoloader.

Obligatoire
---------

* Une classe ou namespace complètement qualifiée doivent disposer de la structure suivante
  `\<Nom du Vendor>\(<Namespace>\)*<Nom de la Classe>`.
* Chaque namespace doit avoir un namespace racine. ("Nom du Vendor").
* Chaque namespace peut avoir autant de sous-namespace qu'il le souhaite.
* Chaque séparateur de namespace est converti en  `DIRECTORY_SEPARATOR` lors du chargement à partir du système de fichiers.
* Chaque "\_" dans le nom d'une CLASSE est convertis en `DIRECTORY_SEPARATOR`. Le caractère "\_" n'a pas de signification particulière dans le namespace.
* Les classes et namespace complètement qualifiés sont suffixés avec ".php" lors du chargement à partir du système de fichier.
* Les caractères alphabétiques dans les noms de vendors, namespace et noms de classes peuvent contenir n'importe quelle combinaison de minuscules et de majuscules.

Exemples
--------

* `\Doctrine\Common\IsolatedClassLoader` => `/chemin/vers/projet/lib/vendor/Doctrine/Common/IsolatedClassLoader.php`
* `\Symfony\Core\Request` => `/chemin/vers/projet/lib/vendor/Symfony/Core/Request.php`
* `\Zend\Acl` => `/chemin/vers/projet/lib/vendor/Zend/Acl.php`
* `\Zend\Mail\Message` => `/chemin/vers/projet/lib/vendor/Zend/Mail/Message.php`

Sous-tiret dans les Namespaces et Noms de Classes
-----------------------------------------

* `\namespace\package\Class_Name` => `/chemin/vers/projet/lib/vendor/namespace/package/Class/Name.php`
* `\namespace\package_name\Class_Name` => `/chemin/vers/projet/lib/vendor/namespace/package_name/Class/Name.php`

Les normes que nous établissons ici doivent être les moins douloureuses afin de permettre une interopérabilité avec un autoloader. Vous pouvez vérifier que vous respectez ces normes via l'utilisation de l'implémentation d'exemple de SplClassLoader qui est capable de charger les classes PHP 5.3.

Exemple d'Implementation
----------------------

Le code ci-dessous est une fonction d'exemple afin de montrer comment les normes proposées ci-dessus peuvent être chargées automatiquement.

```php
<?php

function autoload($className)
{
    $className = ltrim($className, '\\');
    $fileName  = '';
    $namespace = '';
    if ($lastNsPos = strripos($className, '\\')) {
        $namespace = substr($className, 0, $lastNsPos);
        $className = substr($className, $lastNsPos + 1);
        $fileName  = str_replace('\\', DIRECTORY_SEPARATOR, $namespace) . DIRECTORY_SEPARATOR;
    }
    $fileName .= str_replace('_', DIRECTORY_SEPARATOR, $className) . '.php';

    require $fileName;
}
```

SplClassLoader Implementation
-----------------------------

Le gist suivant est une implémentation d'exemple de SplClassLoader qui permet de charger vos classes si vous respectez les standards d'interopérabilité pour autoloader proposées ci-dessus. C'est la façon actuelle recommandée pour chargé des classes php 5.3 qui respectent ces normes.

* [http://gist.github.com/221634](http://gist.github.com/221634)

