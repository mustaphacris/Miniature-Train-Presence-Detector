# Description du détecteur de présence de train miniature

<img width="702" height="407" alt="image" src="https://github.com/user-attachments/assets/97ae18c7-4ffb-4f8a-aa9e-2c171a21d9dc" />


Le schéma électronique présenté permet de détecter la présence d’un train miniature sur une portion de voie alimentée en courant continu. Le principe repose sur la mesure du courant consommé par la locomotive ou par une résistance de détection placée sur les essieux du train. Lorsque le train est présent, un faible courant circule dans la voie, ce qui permet au circuit de le détecter et de générer un signal exploitable (par exemple pour commander un signal lumineux, une automatisation ou un système d’arrêt).

Le montage est composé de plusieurs blocs fonctionnels successifs :

## 1. Convertisseur courant/tension (U1A – LM358)

La présence du train provoque le passage d’un petit courant dans la voie. Ce courant circule à travers une résistance de shunt (R1), ce qui produit une tension proportionnelle.
L’amplificateur opérationnel U1A convertit cette variation de courant en une tension mesurable et l’amplifie.
→ Il transforme la présence de courant en un signal électrique exploitable.

## 2. Filtre passe–bande autour de 10 kHz (L1, C5, C6)

Pour éviter les fausses détections (bruits électriques, variations lentes), le signal passe dans un filtre passe-bande centré sur 10 kHz.
Ce filtre ne laisse passer que les variations rapides voulues, ce qui améliore la précision de détection.

## 3. Amplificateur non-inverseur (U1B – LM358)

Le signal filtré est ensuite amplifié à un niveau suffisant.
→ Cela garantit que le signal soit suffisamment fort pour être traité dans l’étape suivante.

## 4. Détecteur de crête (D2, R9, C9)

Ce circuit rectifie le signal et conserve sa valeur maximale dans le condensateur C9.
→ Le signal alternatif devient une tension continue, représentative de la présence du train.

## 5. Comparateur (U3 – LM393)

Le comparateur compare cette tension détectée à une tension de référence fixée par un potentiomètre.

Si la tension dépasse le seuil → présence du train détectée

Si elle est en dessous → aucun train sur la voie

La sortie du comparateur peut ensuite activer une LED, un relais ou envoyer un signal vers un système de commande.

##  6. Alimentation

Le montage fonctionne avec +5V et -5V.
Le -5V est généré automatiquement par un convertisseur DC-DC à pompe de charge (MAX1044).
→ Cela permet l’utilisation correcte des amplificateurs opérationnels.


# Description du routage de la carte électronique

Le routage de la carte électronique a été réalisé sur deux couches de cuivre : la couche F.Cu (face avant) et la couche B.Cu (face arrière). Cela permet d’optimiser le passage des pistes, de réduire les interconnexions et d’obtenir une implantation compacte.

## 1. Routage sur la couche F.Cu (Face Avant)

<img width="527" height="358" alt="image" src="https://github.com/user-attachments/assets/357ec3aa-e4bf-474a-8509-2646c5058862" />

L’image de la couche F.Cu montre principalement les pistes situées sur la face supérieure de la carte.
Sur cette face, on retrouve :

Les liaisons les plus courtes entre les composants sensibles, afin de réduire le bruit et les perturbations.

La majorité des connexions associées aux signaux analogiques, notamment celles liées aux amplificateurs opérationnels et aux étages de détection.

Le placement stratégique des condensateurs de découplage près des circuits intégrés pour une meilleure stabilité de l’alimentation.

Cette organisation permet de garantir une transmission du signal propre et stable.

## 2. Routage sur la couche B.Cu (Face Arrière)

<img width="509" height="356" alt="image" src="https://github.com/user-attachments/assets/452ce872-dc02-4fa4-a9fc-87d20a22f4ff" />

La couche B.Cu représente le routage sur la face inférieure.
Cette couche est principalement utilisée pour :

Les retours à la masse (GND), permettant de créer un plan de masse continu.

Certaines pistes d’alimentation +5V et −5V provenant du convertisseur DC-DC.

Le passage de pistes complémentaires lorsque la face avant ne permet pas à elle seule les interconnexions.

L’utilisation des deux couches facilite une séparation claire entre signaux sensibles et alimentation, ce qui améliore les performances globales du circuit.

## 3. Visualisation 3D de la carte électronique

<img width="500" height="412" alt="image" src="https://github.com/user-attachments/assets/d8f9fdaa-046b-44b8-ae38-0f36e373177b" />

<img width="547" height="353" alt="image" src="https://github.com/user-attachments/assets/03bb677e-fb3f-4717-915c-56914fb36474" />


La troisième image représente la vue 3D de la carte électronique.
Cette modélisation permet :

De visualiser l’implantation réelle des composants (résistances, condensateurs, circuits intégrés, connecteurs, etc.),

De vérifier les dimensions et l’encombrement physique de la carte,

De s’assurer qu’aucune collision ou superposition de composants n’existe,

De préparer plus facilement l’assemblage et la fabrication.

La vue 3D constitue une étape essentielle avant l’envoi en fabrication, car elle permet une validation visuelle complète du design.
