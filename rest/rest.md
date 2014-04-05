# Architecture REST

* * *

Une architecture **REST**, ça s'articule autour de 4 *verbes* (`method`) HTTP : 

* **GET** : lecture
* **POST** : création
* **PUT** : édition
* **DELETE** : suppression

* * *

## URL de module

Ce que j'appelle une URL de module, c'est quand on appelle le serveur avec un chemin comme ceci : `http://api.monsite.com/module`.

Dans le cadre de ce document, notre module se nommera `elements`, et représentera - *surprise* - des éléments indéterminés. Mais ça pourrait se nommer `users`, `articles`, ou `marshmallows`.

### [GET] `/elements`

Récupère une liste d'éléments.

**Nom suggéré pour la procédure:** `list`

**Code de retour:** `200 - OK`

**Valeur de retour:** une liste d'éléments

**Paramètres:** l'utilisation de paramètres permet de filtrer le retour (par `querying` côté serveur)

### [POST] `/elements`

Ajoute un nouvel utilisateur.

**Nom suggéré pour la procédure:** `create`, `add`

**Code de retour:** `201 - Created`

**Valeur de retour:** l'élément nouvellement créé

**Paramètres:** les paramètres contiennent les informations nécéssaires à la création du nouvel élément.

### [PUT] `/elements`

Mise à jour de masse.

**Nom suggéré pour la procédure:** *bonne question, Edmond*.

**Code de retour:** `204 - No Content`

**Valeur de retour:** Un *update de masse* ne *devrait* pas avoir de valeur de retour, d'où le code `204`.

**Paramètres:** les paramètres contiennent les informations nécéssaires à la mise à jour des multiples éléments.

> **Note:** cette requête-là, je n'en ai jamais eu besoin. Elle me semble carrément violente, et ne devrait être utilisée que dans des cas extrêmement spécifiques.

### [DELETE] `/elements`

Suppression de masse.

> **Je n'ai jamais vu cette requête implémentée en REST.** C'est *forcément* potentiellement très vilain, donc... on oublie.

**Code de retour:** `405 - Method Not Allowed`

* * * 

## URL de document

Une *URL de document*, c'est quand on appelle le serveur avec un chemin comme ceci : `http://api.monsite.com/module/1234`, où `1234` représente un identifiant unique de document.

**Note:** les avis divergent quant à l'utilisation de `/elements/1234` ou `/element/1234`. C'est une querelle de chapelles, personnellement, j'aime l'approche du nom de module au pluriel, par pure cohérence des chemins.

### [GET] `/elements/1234`

Récupère un élément.

**Nom suggéré pour la procédure:** `read`, `details`

**Code de retour:** `200 - OK` ou `404 - Not found` (si l'élément n'existe pas)

**Valeur de retour:** l'élément en question (s'il existe)

**Paramètres:** les paramètres peuvent éventuellement permettre de filtrer les données retournées.

### [POST] `/elements/1234`

**Cette requête n'existe pas, en toute logique.**

**Code de retour:** `405 - Method Not Allowed`

### [PUT] `/elements/1234`

Mise à jour d'un élément.

**Nom suggéré pour la procédure:** `edit`, `update`

**Code de retour:** `204 - No Content`

**Valeur de retour:** Un *update* ne *devrait* pas avoir de valeur de retour, d'où le code `204`. Ceci dit, on peut retourner l'élément modifié, dans ce cas, le code de retour passe à un code `200`.

**Paramètres:** les paramètres contiennent les informations nécéssaires à la mise à jour de l'élément.

### [DELETE] `/elements/1234`

Suppression d'un élément.

**Nom suggéré pour la procédure:** `destroy`, `remove`, `delete`

**Code de retour:** `204 - No Content`.

**Valeur de retour:** Un *suppression* ne *devrait* pas avoir de valeur de retour, d'où le code `204`.

**Paramètres:** les paramètres contiennent les informations nécéssaires à la suppression de l'élément, si besoin.

* * *