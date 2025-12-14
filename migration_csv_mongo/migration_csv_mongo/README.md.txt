* Ce projet permet de transférer les données du fichier CSV healthcare_dataset.csv dans une base MongoDB, à l’aide d’un script Python très simple.

Le script fait uniquement :

- une connexion à MongoDB

- une lecture du fichier CSV

- une insertion des lignes dans une collection MongoDB


* Structure du projet : 

migration_csv_mongo/

healthcare_dataset.csv        # Fichier CSV source
import_csv_to_mongo.py        # Script Python simple de migration
README.md                     # Documentation



* Logique de la migration :

1. Connexion à MongoDB

Le script se connecte à un serveur MongoDB local via :

mongodb://localhost:27017


Il travaille dans :

la base : healthcare_db

la collection : patients


2. Lecture du fichier CSV

Le fichier healthcare_dataset.csv contient des informations sur des patients, par exemple :

Name

Age

Gender

Medical Condition

Room Number

Billing Amount

etc.

Le script lit le CSV ligne par ligne avec csv.DictReader.

Chaque ligne devient un dictionnaire Python.


3. Conversion minimale des types

Certaines colonnes sont converties pour correspondre à des types numériques :

Age → int

Room Number → int

Billing Amount → float

Les autres colonnes restent telles quelles (texte).


4. Insertion dans MongoDB

Toutes les lignes sont insérées d’un coup avec :

insert_many()


