# Description du détecteur de présence de train miniature


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
