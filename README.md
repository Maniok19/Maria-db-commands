## Script de Création de Base de Données MariaDB pour la Gestion de Projet

### 🗃️ Création de la Base de Données

```sql
-- Création de la base de données
CREATE DATABASE IF NOT EXISTS gestion_projet;

-- Utilisation de la base de données
USE gestion_projet;
```

### 📋 Table des Projets

```sql
CREATE TABLE projets (
    id_projet INT AUTO_INCREMENT PRIMARY KEY,
    nom_projet VARCHAR(255) NOT NULL,
    date_debut DATE,
    date_fin DATE,
    budget DECIMAL(15,2) NOT NULL,
    statut ENUM('En cours', 'Terminé', 'Planifié') DEFAULT 'Planifié',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 👥 Table des Employés

```sql
CREATE TABLE employes (
    id_employe INT AUTO_INCREMENT PRIMARY KEY,
    prenom VARCHAR(50) NOT NULL,
    nom VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    date_embauche DATE NOT NULL,
    poste VARCHAR(100),
    departement VARCHAR(100)
);
```

### 🔗 Table des Affectations de Projet

```sql
CREATE TABLE affectations_projet (
    id_affectation INT AUTO_INCREMENT PRIMARY KEY,
    id_projet INT,
    id_employe INT,
    role VARCHAR(50) NOT NULL,
    date_debut DATE NOT NULL,
    date_fin DATE,
    charge_travail DECIMAL(5,2),
    FOREIGN KEY (id_projet) REFERENCES projets(id_projet),
    FOREIGN KEY (id_employe) REFERENCES employes(id_employe)
);
```

### 📝 Commentaires Additionnels

- Le script utilise des conventions de nommage en français
- Chaque table a une clé primaire auto-incrémentée
- Des contraintes de clés étrangères sont utilisées
- Des types de données appropriés sont sélectionnés
- Un horodatage automatique est inclus pour la traçabilité

### 🚀 Recommandations

- Adaptez les noms et types de colonnes selon vos besoins spécifiques
- Ajoutez des index si nécessaire pour optimiser les performances
- Pensez à la sécurité et aux droits d'accès lors de l'implémentation