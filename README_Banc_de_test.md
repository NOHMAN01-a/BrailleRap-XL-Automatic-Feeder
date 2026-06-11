# Banc de test de la BrailleRap XL

## Objectif

Le banc de test a été réalisé afin de déterminer les paramètres optimaux de fonctionnement des axes X et Y avant l'intégration complète sur la BrailleRap XL.

Les essais ont porté principalement sur l'influence du feedrate sur le temps de déplacement, le niveau sonore, la stabilité du mouvement et la précision du retour à la position de référence.

---

# Résultats expérimentaux – Axe X

| Distance (mm) | Feedrate | Temps (s) | Bruit (dB) | Observation                 |
| ------------- | -------- | --------- | ---------- | --------------------------- |
| 50            | 3000     | 1.04      | 53         | Stable                      |
| 50            | 5000     | 0.70      | 54         | Stable                      |
| 50            | 8000     | 0.56      | 49         | Stable                      |
| 50            | 9000     | 0.53      | 50.5       | Stable                      |
| 50            | 13000    | 0.49      | 51         | Stable                      |
| 50            | 15000    | 0.40      | 57         | Stable                      |
| 50            | 18000+   | 0.40      | Variable   | Vibrations plus importantes |

## Conclusion Axe X

La valeur F15000 a été retenue comme valeur optimale. Au-delà de cette valeur, aucune amélioration significative n'a été observée et les vibrations augmentent.

---

# Résultats expérimentaux – Axe Y

| Distance (mm) | Feedrate | Temps (s) | Bruit (dB) | Observation |
| ------------- | -------- | --------- | ---------- | ----------- |
| 100           | 3000     | 2.18      | 51.7       | Stable      |
| 100           | 5000     | 1.65      | 47.1       | Stable      |
| 100           | 9000     | 1.25      | 55         | Stable      |
| 100           | 11000    | 1.00      | 57.5       | Stable      |
| 100           | 13000    | 1.00      | 57         | Stable      |
| 100           | 15000    | 1.00      | 55         | Stable      |

## Conclusion Axe Y

La valeur F11000 a été retenue comme valeur optimale. L'augmentation du feedrate au-delà de cette valeur n'apporte pas d'amélioration supplémentaire.

---

# Validation sur la BrailleRap XL

Les paramètres déterminés sur le banc de test ont ensuite été appliqués à la BrailleRap XL complète.

Les essais réalisés sur la machine ont montré une concordance d'environ 98 % avec les résultats obtenus sur le banc de test, validant ainsi la méthodologie utilisée pour le choix des paramètres de fonctionnement.
