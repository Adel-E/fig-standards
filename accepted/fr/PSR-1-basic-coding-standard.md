La norme de codage de base
==========================

Cette section de la norme comprend ce qu'il convient de prendre en compte des éléments standards de codage nécessaires pour assurer un niveau élevé d'interopérabilité technique pour le partage du Code PHP.

Les mots clés "DOIT", "NE DOIT PAS", "REQUIS", "DEVRA", "NE DEVRA PAS", "DEVRAIT", "NE DEVRAIT PAS", "RECOMMENDER", "POUVOIR" et "OPTIONEL" dans ce document doivent être interprétés comme décrit dans [RFC 2119][].

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/lesmyrmidons/fig-standards/accepted/fr/PSR-0.md

1. Overview
-----------

- Les fichiers DOIVENT utiliser seulement les tag's `<?php` et `<?=`.

- Les fichiers de code PHP DOIVENT encoder uniquement en UTF-8 sans BOM.

- Les fichiersFiles SHOULD *either* declare symbols (classes, fonctions, constantes, etc.)
*or* cause side-effects (e.g. générer une sortie, modifier les règlages .ini, etc.)
mais ne devra pas faire les deux.

2. Files
--------

3. Namespace and Class Names
----------------------------

4. Class Constants, Properties, and Methods
-------------------------------------------
