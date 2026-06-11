# Commande Arduino du chargeur automatique

## Composants utilisés

Arduino UNO
 Moteur pas à pas 28BYJ-48
 Driver ULN2003
 Capteur infrarouge de détection
 Bouton poussoir
 Alimentation 5 V

## Connexions

### Bouton poussoir

 Composant | Arduino 
  
 Bouton     D2      
 Bouton     GND     

### Capteur infrarouge

 Capteur  Arduino 
 -------  ------- 
 VCC      5V      
 GND      GND     
 OUT      D3      

### Driver ULN2003

 ULN2003 | Arduino 
 -------  -------
 IN1      D8      
 IN2      D10     
 IN3      D9      
 IN4      D11     

Le moteur 28BYJ-48 est directement connecté au driver ULN2003.

## Principe de fonctionnement

Le système fonctionne selon la séquence suivante :

1. L'utilisateur appuie sur le bouton poussoir.
2. L'Arduino démarre le moteur pas à pas.
3. Le rouleau entraîne une feuille vers l'entrée de la BrailleRap XL.
4. Lorsque la feuille atteint la position souhaitée, le capteur infrarouge la détecte.
5. L'Arduino arrête immédiatement le moteur.
6. La feuille est alors correctement positionnée pour l'impression.

## Description du programme

Le programme utilise la bibliothèque Stepper pour piloter le moteur pas à pas.

Le bouton poussoir permet de lancer un cycle d'alimentation. Une boucle surveille ensuite l'état du capteur infrarouge.

Tant qu'aucune feuille n'est détectée, le moteur continue de tourner. Dès que le capteur détecte la présence de la feuille, l'Arduino arrête le moteur afin de positionner correctement le papier à l'entrée de la machine.

Cette stratégie simple a permis d'obtenir une alimentation feuille par feuille fiable lors des essais réalisés sur le prototype.

## Explication du code

### Bibliothèque Stepper

```cpp
#include <Stepper.h>
```

Permet de piloter le moteur pas à pas à l'aide de la bibliothèque Arduino Stepper.

---

### Nombre de pas du moteur

```cpp
const int stepsPerRevolution = 2048;
```

Définit le nombre de pas nécessaires pour effectuer un tour complet du moteur 28BYJ-48.

---

### Déclaration du moteur

```cpp
Stepper myStepper(stepsPerRevolution, 8, 10, 9, 11);
```

Associe le moteur aux broches de commande du driver ULN2003.

---

### Déclaration des entrées

```cpp
const int buttonPin = 2;
const int sensorPin = 3;
```

Déclare les broches utilisées respectivement pour le bouton poussoir et le capteur infrarouge.

---

### Variable de mémorisation

```cpp
bool lastButtonState = HIGH;
```

Permet de mémoriser l'état précédent du bouton afin de détecter un nouvel appui.

---

### Fonction setup()

```cpp
void setup()
```

Fonction exécutée une seule fois au démarrage de l'Arduino.

```cpp
pinMode(buttonPin, INPUT_PULLUP);
```

Configure le bouton poussoir en entrée avec résistance interne.

```cpp
pinMode(sensorPin, INPUT);
```

Configure le capteur infrarouge en entrée.

```cpp
myStepper.setSpeed(10);
```

Définit la vitesse de rotation du moteur.

---

### Fonction loop()

```cpp
void loop()
```

Fonction exécutée en continu pendant le fonctionnement du système.

---

### Lecture du bouton

```cpp
bool currentButtonState = digitalRead(buttonPin);
```

Lit l'état actuel du bouton poussoir.

---

### Détection d'un appui

```cpp
if (lastButtonState == HIGH && currentButtonState == LOW)
```

Détecte un nouvel appui sur le bouton.

---

### Rotation du moteur

```cpp
while (digitalRead(sensorPin) == HIGH)
{
    myStepper.step(10);
}
```

Le moteur tourne tant que le capteur ne détecte pas la présence d'une feuille.

---

### Détection de la feuille

```cpp
digitalRead(sensorPin)
```

Lit l'état du capteur infrarouge.

* HIGH : aucune feuille détectée.
* LOW : feuille détectée.

---

### Arrêt du moteur

Lorsque le capteur détecte la feuille, la boucle s'arrête automatiquement et le moteur cesse de tourner.

---

### Temporisation

```cpp
delay(300);
```

Ajoute une courte temporisation afin d'éviter plusieurs déclenchements successifs.

---

### Mise à jour de l'état du bouton

```cpp
lastButtonState = currentButtonState;
```

Met à jour l'état précédent du bouton pour préparer le cycle suivant.

