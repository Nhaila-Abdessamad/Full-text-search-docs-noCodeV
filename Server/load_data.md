> Ce module est un script permettant de lire le contenu de chaque livre et d'ajouter ces données à Elasticsearch.

### Structure et Contenu du Module

![load_data_Module](https://github.com/Nhaila-Abdessamad/Full-text-search-docs-noCodeV/blob/main/Server/figs/load_data.PNG)

- Class Diag

### Dependencies du module
- Ce module depends sur le module connection.

### La fonction parseBookFile(filePath) 
Cette fonction effectue quelques tâches importantes:

- Lire le texte du livre à partir du système de fichiers.
- Utiliser des expressions régulières (consultez cet article pour une introduction à l'utilisation de regex) pour analyser le titre du livre et l'auteur.
- Identifier le début et la fin du contenu du livre, en faisant 
- Correspondre l'en-tête et le pied de page "Projet Guttenberg" tout en majuscules.
- Extraire le contenu du texte du livre.
- Diviser chaque paragraphe dans son propre tableau.
- Nettoyer le texte et supprimez les lignes vides.

En tant que valeur de retour, nous formerons un objet contenant le titre du livre, l'auteur et un tableau de paragraphes dans le livre.


### La fonction insertBookData (title, author, paragraphs)


- Cette fonction indexera chaque paragraphe du livre, avec les métadonnées d'auteur, de titre et d'emplacement de paragraphe jointes.
- Nous insérons les paragraphes en utilisant une opération groupée, ce qui est beaucoup plus rapide que d'indexer chaque paragraphe individuellement.

### La fonction readAndInsertBooks

- Cette fonction utilse les deux dernières fonction et la liaison avec le module connection pour indexer les lparagraphes et Metadata dans Elasticsearch.

