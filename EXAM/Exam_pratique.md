# EXAMEN PRATIQUE

## Exercice 1

### Dictionnaire de données


![Alt text](Capture%20d'écran%202024-08-22%20112518.png)

### Modèle Conceptuel des Données.

![Alt text](EXAM_MCD_exercice1.png)

### Modèle Logique des Données.

![Alt text](EXAM_MLD_exercice1.png)

### Modèle Physique des Données

Fournisseur                 (ref_fournisseur, raison_sociale,adresse,code_postal)

ListeFournisseurs           (ref_produit, ref_fournisseur,ref_produit_fournisseur,ref_catalogue_fournisseur)

produit_approvisionne           (ref_produit,prix_achat_moyen)

produit_fabrique (
    ref_produit,nb_heure_moyen
)

reçoit  (#ref_produit,quantite)

Produit (ref_produit, designation_produit, description_produit, prix_HT)

Commande (ref_commande)

DAteLivraisonPrevue         (date_livraison)

Commande_groupee           (ref_commande, prix_negocie)

Date (date_commande)

acheter (#ref_produit, #ref_commande, quantite)



```SQL
CREATE DATABASE exercice1;
USE exercice1;

CREATE TABLE Produit (
    ref_produit VARCHAR(20) PRIMARY KEY,
    designation_produit VARCHAR(20),
    description_produit TEXT,
    prix_HT DECIMAL,
);

CREATE TABLE produit_fabrique (
    ref_produit VARCHAR PRIMARY KEY,
    nb_heure_moyen DECIMAL,
   
);

CREATE TABLE ProduitApprovisionne (
    ref_produit VARCHAR PRIMARY KEY,
    prix_achat_moyen DECIMAL,

);

CREATE TABLE Fournisseur (
    ref_fournisseur VARCHAR PRIMARY KEY,
    raison_sociale VARCHAR(20),
    adresse VARCHAR(40),
    ville VARCHAR(30),
    code_postal VARCHAR(5)
);

CREATE TABLE ListeFournisseurs (
    ref_produit VARCHAR PRIMARY KEY,
    ref_fournisseur VARCHAR,
    ref_produit_fournisseur VARCHAR,
    prix_catalogue_fournisseur DECIMAL,
    PRIMARY KEY (RefProduit, RefFournisseur),
   
);

CREATE TABLE Commande (
    ref_commande VARCHAR PRIMARY KEY,
    date_ommande DATE,
    ref_fournisseur VARCHAR,
    TotalCommandeHT DECIMAL,
  
);

CREATE TABLE LigneCommande (
    ref_commande VARCHAR(20),
    ref_produit VARCHAR(20),
    quantite INT,
    prix_negocie DECIMAL(10, 2),
    date_livraison DATE,
    PRIMARY KEY (RefCommande, RefProduit),

);
```


# Exercice 2

### Dictionnaire de données

![alt text](dico2.png)

### Modèle Conceptuel des Données.

![Alt text](exam_MCDex2.png)

![Alt text](exam_MLDex2.png)
### Modèle Physique des Données

sportif (id_sportif, nom, prenom, adresse, code_postal, email, fax, est_licencié, num_dossard, num_license, date_certificat_medical, num_dossier_inscription)

competition (id_competition, nom_competition, date_competition, libellé_competition, ville_competition)

EPREUVE(
    id_epreuve,type_epreuve,distance,conditions_epreuve)


````SQL
CREATE DATABASE exercice2;
USE exercice2;
CREATE TABLE Sportif (
    id_sportif INT(10) PRIMARY KEY AUTO_INCREMENT,
    nom VARCHAR(30),
    prenom VARCHAR(30),
    adresse VARCHAR(255),
    code_postal VARCHAR(5),
    num_tel VARCHAR(20),
    fax VARCHAR(20),
    email VARCHAR(100),
    est_licencié BOOLEAN,
    num_dossard INT(5),
    num_licence VARCHAR(10),
    club VARCHAR(100),
    certificat_medical DATE,
    num_dossier_inscription INT
);

CREATE TABLE Competition (
    id_competition INT PRIMARY KEY AUTO_INCREMENT,
    nom_competition VARCHAR(100),
    date_competition DATE,
    ville_compet VARCHAR(100),
    libelle VARCHAR(100)
);

CREATE TABLE Epreuve (
    id_epreuve INT PRIMARY KEY AUTO_INCREMENT,
    type_epreuve VARCHAR(50),
    Distance DECIMAL,
    conditions TEXT,
   
);
````
