# Kéké Voyage projet

Ceci est un Brief, dans le cadre de la formation de Concepteur déceloppeur d'application chez Simplon.

Simplon propose une formation en alternance afin d'obtenir le titre de concepteur développeur d'application avec une option DevOp. Dans le cadre de la formation nous avons pour projets, la réalisation de briefs. Et voici le premier. L'objectif du projet est une vérification de la maitrise de MERISE.

Le projet

Kéké voyage notre client et souhaite proposer la possibilité de réserver en ligne des billets d'avion à leurs clients. Ma mission est de concevoir à l'aide du standard UML la modélisation de la plateforme. La plateforme devra permettre de :

* Un vol est ouvert à la réservation et refermé sur ordre de la compagnie.
* Un vol peut être annulé par la compagnie
* Un client peut réserver un ou plusierus vols, pour des passages différents.
* Une réservation concerne un seul vol et un seul passager.
* Une réservation peut être annulée ou confirmée.
* Un vol a un aéroport de départ et un aéroport d'arrivée.
* Un vol a un jour et une heure de départ, et un jour et une heure d'arrivée.
* Un vol peut comporter des escales dans les aéroports.
* Une escale a une heure d'arrivée et une heure de départ.
* Chaque aéroport dessert une ou plusieurs villes.
* Des compagnies aériennes proposent différents vols.

# Merise

Le principe de Merise est de séparer les données des traitements. L'organisation des données semble donc plus pérenne que la définition des traitements, car ils évoluent en fonction des utilisateurs, de l'évolution des métiers ainsi que des fonctionnalités.

# Règles de gestion

RESERVATION

* un email de contact
* un numéro de téléphone
* nom
* prenom
* un n° de passport
* peu être annuler par le CLIENT
* une réservation ne peu être que pour une seul personne et un seul vol
* numéro de réservation
* peu être confirmé par l'agence

VOL

* le vol contient un numero de vol
* aeroport de depart, une date, une heure
* aeroport d'arrive, une date, une heure
* vol avec un ou plusieur passager
* un vol ne peux pas être reservable ou non
* un vol peut faire des escale dans un AEROPORT
* le vol est un trajet d'un aeroport à un autre
* un vol peut être annulé par la compagnie
* numéro de vol

COMPAGNIE

* contiens un nom
* peu avoir un ou plusieurs vol

ESCALE

* une date et une heure d'arrivé
* une date et une heure de départ
* un aeroport d'arrivé
* un aeroport de dépar

AEROPORT

* ce trouve dans une ville

VILLE

* un nom
* un pays

<br>
## Dictionnaire de données

| Nom | Type | Désignation |
| --- | :---: | :---------- |
| nom\_compagnie | Alphanumérique | nom de la compagnie aérienne |
| numero\_vol | Numérique | id destination du vol |
| nombre\_billet | Numérique | nombre de billet réserver |
| reservation | Alphanumérique | réservation fait par le client |
| ouverture\_reservation | Boolean | ouverture/fermeture de la reservation par la compagnie |
| annulation\_reservation | Boolean | annulation ou non de la réservation par le client |
| annulation\_vol | Boolean | annulation du vol ou non par la compagnie |
| aeroport | Alphanumérique | annulation ou non de la réservation par le client |
| date\_depart | Date | date du depart du vol |
| date\_arriver | Date | date d'arriver du vol |
| nom\_ville | Alphanumérique | nom de l'aéroport |
| nom\_pays | Alphabétique | nom du pays |
| confirmation\_vol | Boolean | validation ou non d'un vol |
| depart\_escale | Date/heure | depart de l'escale |
| arriver\_escale | Date/heure | arriver de l'escale |
| email\_contact | Alphanumérique | email de contact de la personne ayant reserver |
| nom\_passager | Alphabétique | nom du passager |
| prenom\_passager | Alphabétique | prenom du passager |
| age\_passager | Numérique | age du passager |
| passeport\_passager | Alphanumérique | passeport du passager |
| price\_reservation | Numérique | prix de la réservation |
| date\_reservation | Date/heure | date de la réservation |


# Voici la représentation du MCD

Un schéma conceptuel est une description de haut niveau des besoins d'information sous-tendant la conception d'une base de données. Il comprend généralement uniquement les principaux concepts et les principales relations entre eux.

Réaliser sur Looping
Modèle Conceptuel de donnée

[MCD](MCD.png) 

# MLD

Réaliser via Looping
Modèle Logique de donnée

Le MLD est la transformation du MCD en un ensemble de tables. Il est la représentation des données  d'un système d'information et est généré à partir du MCD.

[MLD](MLD.PNG)

Représentation textuelle du MLD

Compagny = (id\_Compagny COUNTER, name VARCHAR(50), siret VARCHAR(50), country VARCHAR(50));
Airport = (id\_Aéroport COUNTER, name VARCHAR(50), location VARCHAR(50));
City = (id\_city COUNTER);
Country = (id\_country COUNTER):
Flight = (id\_flight COUNTER, flight\_number VARCHAR(50), departure\_day VARCHAR(50), arrival\_day VARCHAR(50), status VARCHAR(50), departure\_time VARCHAR(50), arrival\_time VARCHAR(50), #Id\_Aéroport\_come, #If\_Compagny\*, Id\_Aéroport\_departure);
Ticket = (id\_ticket COUNTER, ticket\_number VARCHAR(50), status VARCHAR(50), place\_departure VARCHAR(50), place\_arrival VARCHAR(50), name VARCHAR(50), first\_name VARCHAR(50), date\_of\_birth VARCHAR(50), mail VARCHAR(50), #id\_flight).
stopover = (#Id\_flight, #Id\_Aéroport, arrivla\_time VARCHAR(50), associated\_flight VARCHAR(50), departure\_time VARCHAR(50));
situates = (#Id\_Aéroport, #Id\_city):
contain = (#Id\_City, #Id\_country);

# MPD

Modèle physique de donnée

[MDP](MPD.png)

Script SQL

``` SQL
CREATE TABLE Compagny(

Id_Compagny
COUNTER,

name
VARCHAR(50),

siret
VARCHAR(50),

country
VARCHAR(50),

PRIMARY
KEY(Id_Compagny)

);



CREATE
TABLE Airport(

Id_Aéroport
COUNTER,

name
VARCHAR(50),

location
VARCHAR(50),

PRIMARY
KEY(Id_Aéroport)

);



CREATE
TABLE City(

Id_city
COUNTER,

PRIMARY
KEY(Id_city)

);



CREATE
TABLE Country(

Id_country
COUNTER,

PRIMARY
KEY(Id_country)

);



CREATE
TABLE Flight(

Id_flight
COUNTER,

flight_number
VARCHAR(50),

departure_day
VARCHAR(50),

arrival_day
VARCHAR(50),

status
VARCHAR(50),

departure_time
VARCHAR(50),

arrival_time
VARCHAR(50),

Id_Aéroport_come
INT NOT NULL,

Id_Compagny
INT,

Id_Aéroport_departure
INT NOT NULL,

PRIMARY
KEY(Id_flight),

FOREIGN
KEY(Id_Aéroport_come) REFERENCES Airport(Id_Aéroport),

FOREIGN
KEY(Id_Compagny) REFERENCES Compagny(Id_Compagny),

FOREIGN
KEY(Id_Aéroport_departure) REFERENCES Airport(Id_Aéroport)

);

status
VARCHAR(50),

place_departure
VARCHAR(50),

place_arrival
VARCHAR(50),

name
VARCHAR(50),

first_name
VARCHAR(50),

date_og_birth
VARCHAR(50),

mail
VARCHAR(50),

Id_flight
INT NOT NULL,

PRIMARY
KEY(Id_ticket),



CREATE
TABLE Ticket(

Id_ticket
COUNTER,

ticket_number
VARCHAR(50),

FOREIGN
KEY(Id_flight) REFERENCES Flight(Id_flight)

);



CREATE
TABLE stopover(

Id_flight
INT,

Id_Aéroport
INT,

arrival_time
VARCHAR(50),

associated_flight
VARCHAR(50),

departure_time
VARCHAR(50),

PRIMARY
KEY(Id_flight, Id_Aéroport),

FOREIGN
KEY(Id_flight) REFERENCES Flight(Id_flight),

FOREIGN
KEY(Id_Aéroport) REFERENCES Airport(Id_Aéroport)

);



CREATE
TABLE situates(

Id_Aéroport
INT,

Id_city
INT,

PRIMARY
KEY(Id_Aéroport, Id_city),

FOREIGN
KEY(Id_Aéroport) REFERENCES Airport(Id_Aéroport),

FOREIGN
KEY(Id_city) REFERENCES City(Id_city)

);



CREATE
TABLE contain(

Id_city
INT,

Id_country
INT,
PRIMARY
KEY(Id_city, Id_country),
OREIGN
KEY(Id_city) REFERENCES City(Id_city),

FOREIGN
KEY(Id_country) REFERENCES Country(Id_country)

);
```
<br>
