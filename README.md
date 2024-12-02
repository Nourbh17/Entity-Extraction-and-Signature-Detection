# Extraction des Entités et Détection des Signatures 

Dans ce projet, je me suis concentré sur l'automatisation de deux tâches principales : l'extraction d'entités et la détection des signatures à partir de documents PDF, spécifiquement des contrats d'assurance ou des lettres formelles. L'objectif était d'extraire les informations essentielles contenues dans ces documents, telles que le nom de l'assuré, l'adresse, la date d'effet, et de vérifier si le document était signé par les deux parties concernées.

## Approche et Techniques Utilisées :

![image](https://github.com/user-attachments/assets/2c80d747-b1ac-40c9-9643-697a2bd6a45e) 


L'approche a été basée sur le traitement de documents structurés, suivant un modèle spécifique, comme le PDF de contrat d'assurance fourni. Ces documents contiennent souvent des informations répétitives et placées à des positions précises dans le texte, ce qui les rend adaptés à l'extraction automatisée.

### 1-Extraction de texte :

J'ai utilisé pdfplumber pour extraire le texte des documents PDF. Cela m'a permis d'extraire et d'analyser les données textuelles pour localiser les entités clés, telles que le nom de l'assuré et la date d'effet.

### 2-Expressions régulières pour l'extraction d'entités :

J'ai mis en place des expressions régulières (regex) pour rechercher des motifs spécifiques dans le texte. Par exemple, j'ai défini des motifs regex pour extraire le nom de l'assuré, l'adresse et la date au format "Jour Mois Année". Cette approche basée sur les expressions régulières est particulièrement efficace pour traiter des documents structurés où l'information se trouve souvent à des endroits prévisibles.

### 3-Détection des signatures :

Pour détecter les signatures, j'ai utilisé des techniques de traitement d'images. J'ai d'abord converti la dernière page du PDF en image à l'aide de la bibliothèque pdf2image. Ensuite, j'ai appliqué des techniques de reconnaissance d'images pour localiser la position de mots-clés spécifiques, tels que "Yours sincerely", et détecter les régions de signatures après ces mots-clés. Grâce au traitement de l'image, j'ai pu identifier et extraire les régions susceptibles de contenir des signatures.

### 4-Vérification :

Après avoir extrait les noms du document, j'ai utilisé une fonction de comparaison pour vérifier si le nom de l'assuré correspondait à l'un des noms extraits, confirmant ainsi si le document était signé par l'assuré. De plus, j'ai vérifié qu'il y avait au moins deux signatures dans les régions extraites pour valider la signature des deux parties.


## Outils et Bibliothèques Utilisées :

pdfplumber :  pour l'extraction de texte des PDF.

pdf2image : pour la conversion des pages PDF en images pour la détection des signatures.

OpenCV : pour le traitement d'image et la détection des régions de signatures.

Expressions régulières (regex) : pour l'extraction des entités à partir du texte.

## Conclusion :
Ce projet a démontré avec succès une méthode automatisée pour extraire des entités et détecter des signatures à partir de documents structurés tels que des contrats d'assurance ou des lettres formelles. En utilisant l'extraction de texte, le traitement d'image et les expressions régulières, j'ai pu automatiser l'extraction d'informations clés et valider les signatures.

Si plusieurs modèles de contrats existent, cette approche peut être améliorée en utilisant des modèles de langage de grande taille (LLMs) avec des systèmes RAG (Retrieval-Augmented Generation). Ces systèmes permettraient de mieux comprendre le texte et les informations présentes, et pourraient générer à la fin les entités demandées à partir de tout type de document, quel que soit son format spécifique.
