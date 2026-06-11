# BrailleRap XL Automatic Feeder

Projet réalisé dans le cadre du stage de Master 1 EEA à l'ISTIC - Université de Rennes.

## Travaux réalisés

- Assemblage de la BrailleRap L
- Validation expérimentale sur banc de test
- Optimisation des paramètres de déplacement
- Développement d'un chargeur automatique de feuilles

## Système développé

Le chargeur automatique est constitué :

- d'une carte Arduino ;
- d'un moteur pas à pas 28BYJ-48 ;
- d'un driver ULN2003 ;
- d'un capteur infrarouge de détection ;
- d'un bouton poussoir ;
- d'un rouleau d'entraînement imprimé en 3D ;
- de poulies imprimées en 3D ;
- d'un support en bois découpé au laser ;
- de quatre ressorts assurant la compensation de hauteur de la pile de feuilles.

## Fonctionnement

1. L'utilisateur appuie sur le bouton.
2. Le moteur entraîne le rouleau.
3. La feuille avance vers la BrailleRap L.
4. Le capteur détecte l'arrivée de la feuille.
5. L'Arduino arrête automatiquement le moteur.
