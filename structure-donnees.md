# Dictionnaire de données

## Table : **Auteurs**
|Champ|Type|Spécificités|Description|
|-|-|-|-|
|id|TINYINT|PRIMARY, A_I, UNSIGNED|Id de l'auteur.|
|prenom|VARCHAR(50)|Aucune|Prénom de l'auteur.|
|nom|VARCHAR(50)|Aucune|Nom de l'auteur.|
|email|VARCHAR(255)|UNIQUE|Email de l'auteur.|
|photo|VARCHAR(255)|NULL|Nom du fichier de la photo de l'auteur.|

## Table : **Articles**
|Champ|Type|Spécificités|Description|
|-|-|-|-|
|id|SMALLINT|PRIMARY, A_I, UNSIGNED|Id de l'article.|
|titre|VARCHAR(255)|Aucune|Titre de l'article.|
|resume|VARCHAR(511)|Aucune|Résumé de l'article.|
|corps|VARCHAR(8191)|Aucune|Contenu HTML de l'article.|
|date_publi|DATETIME|default = CURRENT_TIMESTAMP|Date et heure de publication de l'article.|
|nbr_vues|MEDIUMINT|default = 0, UNSIGNED|Nombre de visionnages de l'article.|
|auteur|TINYINT|INDEX, UNSIGNED|Index de l'auteur ayant écrit l'article.|
|categorie|TINYINT|INDEX, UNSIGNED|Index de la catégorie de l'article.|

## Table : **Catégories**
|Champ|Type|Spécificités|Description|
|-|-|-|-|
|id|TINYINT|PRIMARY, A_I, UNSIGNED|Id de la catégorie.|
|categorie|VARCHAR(63)|Aucune|Intitulé de la catégorie.|
|description|VARCHAR(255)|Aucune|Description de la catégorie.|
