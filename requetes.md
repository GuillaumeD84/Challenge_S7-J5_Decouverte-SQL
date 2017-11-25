# Ecritures de requêtes SQL

## Auteurs
* Lister les auteurs.
  * ``SELECT * FROM `auteurs` ``


* Lister les auteurs par ordre alphabétique (sur le nom).
  * ``SELECT * FROM `auteurs` ORDER BY `auteurs`.`nom` ASC ``


* Lister les auteurs dont l'e-mail est @gmail.com.
  * ``SELECT * FROM `auteurs` WHERE `email` LIKE '%@gmail.com' ``


* Lister les auteurs qui n'ont pas d'image de profil.
  * ``SELECT * FROM `auteurs` WHERE `photo` IS NULL ``



## Articles
* Lister le titre et la date de publication de tous les articles.
  * ``SELECT `titre`, `date_publi` FROM `articles` ``


* Afficher le titre d'un article en particulier (en passant l'id de l'article).
  * ``SELECT `titre` FROM `articles` WHERE `id` = 2 ``


* Afficher tous les articles dont la catégorie correspond au début d'une saisie type (exemple : tous les articles commençant par Lorem).
  * ``SELECT * FROM `articles` WHERE `categorie` IN
    (SELECT `id` FROM `categories` WHERE `categorie` LIKE 'Team%') ``
  * ``SELECT `articles`.* FROM `articles`, `categories` WHERE `articles`.`categorie` = `categories`.`id` AND `categories`.`categorie` LIKE 'Team%' ``


* Trier par ordre décroissant tous les articles par la date de publication.
  * ``SELECT * FROM `articles` ORDER BY `articles`.`date_publi` DESC ``


#### => avec relations (ou notion de table liée) :
* Lister tous les articles avec leur nom d'auteur et l'intitulé de la catégorie.
  * ``SELECT `articles`.`titre`, `auteurs`.`prenom`, `auteurs`.`nom`, `categories`.`categorie` FROM `articles`, `auteurs`, `categories` WHERE `articles`.`categorie` = `categories`.`id` AND `articles`.`auteur` = `auteurs`.`id` ``


* Lister tous les articles dont l'auteur est donné (via son nom).
  * ``SELECT `articles`.* FROM `articles`, `auteurs`
    WHERE `auteurs`.`nom` = 'Fluet' AND `articles`.`auteur` = `auteurs`.`id` ``


* Lister le nom de l'auteur des articles dont la catégorie est donnée (via son id).
  * ``SELECT `articles`.`titre`, `auteurs`.`nom`, `categories`.`categorie`
    FROM `articles`, `auteurs`, `categories`
    WHERE `articles`.`categorie`
    IN (SELECT `id` FROM `categories` WHERE `id` = 4)
    AND `auteurs`.`id` = `articles`.`auteur` AND `articles`.`categorie` = `categories`.`id` ``
