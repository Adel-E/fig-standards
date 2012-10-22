La norme de codage de base
==========================

Cette section de la norme comprend ce qu'il convient de prendre en compte des éléments standards de codage nécessaires pour assurer un niveau élevé d'interopérabilité technique pour le partage du Code PHP.

Les mots clés "DOIT", "NE DOIT PAS", "REQUIS", "DEVRA", "NE DEVRA PAS", "DEVRAIT", "NE DEVRAIT PAS", "RECOMMENDER", "POUVOIR" et "OPTIONEL" dans ce document doivent être interprétés comme décrit dans [RFC 2119][].

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/lesmyrmidons/fig-standards/accepted/fr/PSR-0.md

1. Overview
-----------

- Les fichiers DOIVENT utiliser seulement les tag's `<?php` et `<?=`.

- Les fichiers de code PHP DOIVENT être encodé uniquement en UTF-8 sans BOM.

- Les fichiersFiles SHOULD *either* declare symbols (classes, fonctions, constantes, etc.)
*or* cause side-effects (e.g. générer une sortie, modifier les règlages .ini, etc.)
mais ne devra pas faire les deux.

- Les espaces de noms et les classes DOIVENT suivre [PSR-0][].

- Les noms des classes DOIVENT être déclaré comme `StudlyCaps`.

- Les constantes de classe DOIVENT être déclarée en majuscules avec un sous-tiret en séparateurs.

- Les noms des méthodes DOIVENT être déclaré comme `camelCase`.


2. Files
--------

### 2.1. Les tag's PHP

Tous le code PHP DOIT uniquement utiliser les tag's long `<?php ?>` ou bien uniquement les tag's court `<?= ?>`. On NE DOIT PAS utiliser les deux variantes.

### 2.2. Encodage des caractères

Le code PHP DOIT utiliser uniquement UTF-8 sans BOM.

### 2.3. Les effets secondaires


```php
<?php
// side effect: change ini settings
ini_set('error_reporting', E_ALL);

// side effect: loads a file
include "file.php";

// side effect: generates output
echo "<html>\n";

// declaration
function foo()
{
    // function body
}
```



```php
<?php
// declaration
function foo()
{
    // function body
}

// conditional declaration is *not* a side effect
if (! function_exists('bar')) {
    function bar()
    {
        // function body
    }
}
```

3. Namespace and Class Names
----------------------------

4. Class Constants, Properties, and Methods
-------------------------------------------
