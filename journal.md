# 25.05
- Tests sur bobine linéaire


[gerrits Tagebuch #82](https://www.youtube.com/watch?v=3ujaGUFfgC0) : Parle des capteurs de Hall
[Gerrits Tagebuch #71](https://www.youtube.com/watch?v=D6jwZYrvSv4) : Début des prototypes. On voit les voitures à la fin et le réseau de hallbach au début

# [Gerrits Tagebuch #45](https://www.youtube.com/watch?v=bl5jziS66Zk)
Les débuts de Formel 1.
Ils en arrivent à la conclusion qu'il faut des bobines linéaires
![alt text](image.png)


# Simulation CST 
- Pas d'utilisation des macros
1. Faire des formes à la main
2. Boolean pour former un "méandre"
3. Copie en translation sur `nb_repetition`
4. Placer un Polygon3D pour relier les deux bouts
5. Current Port en selectionnant le polygon3D
6. Copie en décalant de largeur totale d'un méandre/3 (pour 3 bobines)

# 26.05 -> 31.05
Réalisation de simulations sur les bobines linéaires

# 01.06

Analyse des résultats.
Voir du coté des réseau de hallbach



9 fois


24x https://www.supermagnete.ch/fre/aimants-bloc-neodyme/parall-l-pip-de-magn-tique-8mm-4mm-3mm_Q-08-04-03-N
16x https://www.supermagnete.ch/fre/aimants-bloc-neodyme/parall-l-pip-de-magn-tique-8mm-8mm-4mm_Q-08-08-04-N

# 30.06
Après avoir fait les tests sur les aimants en réseau de Halbach, les aimants n'étaient pas attirés par mes champs magnétique même en y appliquant un courant de 5A.
Delphine m'a suggéré de prendre des aimants moins fort pour réduire la force de frottement induite par l'attirance plus élevée du réseau.
- Réaliser un Benchmark pour des aimants moins puissant et moins lourd.
- Calculer la force de l'aimant


# Tests des aimants du 07.07
## Objectif de Test
Vérifier le mouvement d'un réseau de Halbach sur des bobines planaires linéaires. Déterminer la valeur minimale d'intensité du courant nécessaire
## Conditions
- Température 22°C
- Alimentation 5V 5A
- Carte Linear Coils v0.1 par Jonas STIRNEMANN
  - 4x aller-retour de 0.6mm d'espacement et 0.8mm de largeur
  - 1 jumper d'alimentation comprenant 3 pins (noté VCC)
  - 1 jumper de bobines comprenant 3 pins pour l'axe horizontal (A,B et C) et 3 pins pour l'axe vertical (D,E et F).
## Mise en place
1. Connecter le GND de l'alimentation sur les pins du jumper d'alimentation 
2. Allumer l'alimentation en la paramétrant pour 5V et 5A. Il sera peut-être nécessaire d'annuler la protection court-circuit.
3. Placer son réseau de Halbach sur le plateau.
4. Alterner avec le VCC de l'alimentation sur les pins A,B et C.
## Variable
Varier le courant afin d'obtenir la limite avec laquelle le réseau puisse se déplacer.
## Réseau de Halbach N°1
- Aimants de la réalisations (1.2g)
  - 4 aimants 44H de 5x5x1mm
  - 4 aimants N45 de 5x1.5x1mm
- Fixé dans de la résine Epoxy UV
### Résultat Attendu
Je m'attends à voir le réseaux se déplacer à une intensité de 1A
### Résultat Obtenu
Déplacement du réseau sur les deux axes jusqu'à 2.5A
2.0A le déplacement sur l'axe horizontal est faible mais toujours correct sur l'axe vertical
1.5A le réseau ne se déplace plus sur l'axe horizontal
### Hypothèse sur résultat
Je devrais nettoyer un peu plus la résine et peut-être rajouter une surface plus lisse sur le dessous du réseau pour obtenir un mouvement à 1A.

## Réseau de Halbach N°2
- Aimants de la réalisation
  - 4 aimants N45 de 8x8x4mm
  - 4 aimants N45 de 8x4x3mm
- Fixé dans de la résine Epoxy UV
### Résultat Attendu
Je m'attends à ne pas voir se déplacer le réseau à moins de 5A
### Résultat Obtenu
Pas de déplacement du réseau.
### Hypothèse sur résultat
Le réseau est sûrement trop lourd

## Réseau alterné N°1
- Aimants de la réalisation (0.8g)
  - 2x2 aimant 44H de 5x5x1mm
- Placé avec pôles inversés un aimant sur deux 
### Résultat Attendu
Déplacement meilleurs qu'avec les réseaux de Halbach car moins lourd
Déplacement à 1A
### Résultat Obtenu
Déplacement à 1A corrects
Déplacements à 0.7A compliqués sur l'axe horizontal
### Hypothèse sur résultat
Plus le réseau est léger, mieux cela fonctionne.

## Réseau alterné N°2
- Aimants de la réalisation (1g)
  - 2x2 aimants N50 de 5x5x1.5mm
- Placé avec pôles inversés un aimant sur deux
### Résultat Attendu
Déplacement meilleurs qu'avec le réseau alterné N°1
Déplacement à 0.5A
### Résultat Obtenu
Déplacements à 0.7A corrects sur l'axe horizontal
Déplacements à 0.6A compliqués sur l'axe horizontal
### Hypothèse sur résultat
La force des aimants influe également sur le fonctionnement (Plus lourd que réseau alterné N°2 mais plus fort)

# Tests du 28.07
Réception des PCB, pas de composants
- Tests des différences de carte entre JLCPCB et Eurocircuits


**Problèmes repérés**
- GND manquant sur U22, U20, U13, U11, U10
- Texte GND et 5V non déplacés avec les composants (Celui du milieu est le GND)


| Paramètre | *JLCPcb* | *Eurocircuits* |
| - | - | - |
| Résistance bobines  |  $0.3\Omega$ | $0.5\Omega$ |
| Résistance DRV Out1-Out2 | $0.5\Omega$ | $0.6\Omega$ | 

# Tests Prototype
## Test 1 : Eurocircuit
- Pose des composants
- Relier le GND où il n'est pas relié
- Test de connection avec multimètre pour vérifier les courts-circuits

Pas de détection sur MCUXpresso

## Test 2 : JLCPCB
- Pose des composants
- Manque de pâte, Connexion non faite sur la plupart des composants
- La bobine consomme maximum 1A alors qu'elle est sensé consommé maximum 10A
## Test 3 et 4 : Pose de la pâte à la main
- Trop de pâte : Courts-circuits
- Magic Smoke sur composants

## Conclusion 
- Pas de mouvements réussis
- Complexité trop grande pour mouvement : Recommander d'utiliser le système utilisé dans ce lien https://www.youtube.com/watch?v=y-M5DxNqQVI

