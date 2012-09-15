La norme de codage de base
==========================

Cette section de la norme comprend ce qu'il convient de prendre en compte des éléments standards de codage nécessaires pour assurer un niveau élevé d'interopérabilité technique pour le partage du Code PHP.

Les mots clés "DOIT", "NE DOIT PAS", "REQUIE", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDER", "MAY" et "OPTIONEL" dans ce document doivent être interprétés comme décrit dans [RFC 2119][].

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/lesmyrmidons/fig-standards/accepted/fr/PSR-0.md

1. Overview
-----------

- Les fichiers DOIVENT utiliser seulement les tag's `<?php` et `<?=`.

- Les fichiers de code PHP DOIVENT encoder uniquement en UTF-8 sans BOM.

- Files SHOULD *either* declare symbols (classes, functions, constants, etc.)
	24 	*or* cause side-effects (e.g. generate output, change .ini settings, etc.)
	25 	but SHOULD NOT do both.

2. Files
--------

3. Namespace and Class Names
----------------------------

4. Class Constants, Properties, and Methods
-------------------------------------------
