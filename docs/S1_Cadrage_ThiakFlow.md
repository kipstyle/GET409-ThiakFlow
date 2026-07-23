# LIVRABLE SÉANCE 1 — Cadrage, Persona & Value Proposition Canvas

**Projet : ThiakFlow** — Plateforme d'optimisation de tournées et de regroupement sectoriel de colis par IA pour livreurs moto (Tiak-Tiak) à Dakar

**Master GET 409 · Intégration des IA Génératives** — Swiss UMEF University, Campus de Dakar

---

## 1. Fiche d'identité & contexte

### 1.1 Titre du projet

**ThiakFlow** — *"Doublez vos livraisons, divisez votre carburant à Dakar."*

### 1.2 Équipe projet

| Membre | Rôle | GitHub |
|---|---|---|
| Abdou Aziz Mbaye | Chef de Produit (PM) | [@Azizmbaye221](https://github.com/Azizmbaye221) |
| Ibrahima Faye | Master Prompt Engineer | [@kipstyle](https://github.com/kipstyle) |
| Makhoudia Sène | Dev UI (No-Code) | [@Maksen](https://github.com/Maksen) |
| Kalidou Baldé | Responsable Impact | [@KalidouBaLde](https://github.com/KalidouBaLde) |

**Institution :** Swiss UMEF University — Campus de Dakar
**Module :** GET 409 — Transformation Numérique & IA Générative
**Enseignant responsable :** M. Malick Faye Diagne

### 1.3 Problème résolu

> **Un livreur Tiak-Tiak dakarois perd en moyenne 30 à 40 % de son carburant journalier dans des trajets à vide, faute de coordination entre commerçants d'un même quartier.**

Sur une journée type, un livreur moto indépendant à Dakar effectue entre 8 et 12 courses, dont près de **4 sur 10 sont des retours à vide** (aucun colis à récupérer sur le trajet de retour). Avec un prix du litre d'essence autour de **840 FCFA** et une consommation moyenne de 2,5 L pour 100 km sur une moto 125cm³, chaque kilomètre parcouru sans colis représente une perte sèche estimée à **environ 21 FCFA/km**, soit jusqu'à **2 500 FCFA de carburant gaspillé par jour** pour un livreur parcourant 120 km en trajets non productifs. À l'échelle d'un mois, cela représente **plus de 60 000 FCFA de manque à gagner**, soit près d'un tiers du revenu net mensuel d'un Tiak-Tiak.

Cette perte s'explique par l'absence totale de mutualisation : chaque commerçant appelle "son" livreur individuellement, sans visibilité sur les autres demandes de livraison dans le même secteur géographique (Colobane, Sandaga, VDN, Almadies…), ce qui multiplie les trajets redondants sur des axes déjà saturés (VDN, Autoroute, Corniche).

### 1.4 Solution proposée

**ThiakFlow** est une plateforme numérique légère (React/Tailwind, mobile-first, compatible réseaux 3G) qui utilise l'IA générative pour **analyser en temps réel les demandes de livraison brutes** (messages WhatsApp/SMS des commerçants) et **regrouper automatiquement les colis par secteur géographique** (Zone A, B, C) avant de générer une **feuille de route optimisée** pour chaque livreur.

Concrètement, un agent IA "Chercheur" extrait les informations clés de chaque demande (point de collecte, destination, urgence, zone), un second agent "Rédacteur" consolide ces données en tournées groupées, et le livreur reçoit une feuille de route unique lui permettant de regrouper plusieurs colis d'un même quartier en un seul passage — réduisant ainsi les trajets à vide et le carburant consommé pour un gain de revenu net à chaque tournée.

---

## 2. Fiche persona détaillée

### 👤 Moussa Diop, 26 ans — Livreur moto indépendant (Tiak-Tiak)

| Attribut | Détail |
|---|---|
| **Âge** | 26 ans |
| **Métier** | Livreur moto indépendant ("Tiak-Tiak"), autoentrepreneur informel |
| **Zone d'opération** | Colobane, axe VDN, Mermoz, Almadies |
| **Équipement** | Moto 125cm³, smartphone Android d'entrée de gamme (2 Go de RAM, écran fissuré), forfait DATA prépayé limité |
| **Connectivité** | Réseau 3G, parfois instable selon les zones (coupures fréquentes près de la Corniche et à Pikine) |
| **Revenu** | Environ 3 000 à 5 000 FCFA net par jour selon le nombre de courses effectuées |
| **Rythme de travail** | 6 jours/semaine, de 7h à 19h, avec une forte dépendance aux appels téléphoniques directs des commerçants |
| **Niveau de littératie numérique** | Utilisateur courant de WhatsApp, moins à l'aise avec des interfaces complexes ou en anglais |

#### 🔴 Frustrations / Pain Points

1. **Embouteillages chroniques sur l'axe VDN** : les heures de pointe (7h-9h et 17h-19h) doublent parfois le temps de trajet entre Colobane et Almadies, réduisant le nombre de courses possibles par jour.
2. **Retours à vide fréquents** : après une livraison à Mermoz ou Almadies, Moussa doit souvent rentrer à Colobane sans colis, faute de visibilité sur d'autres demandes dans le secteur — un trajet "perdu" financièrement.
3. **Hausse constante du prix de l'essence** : chaque augmentation du litre à la pompe (840 FCFA actuellement) réduit directement sa marge nette, sans qu'il puisse ajuster ses tarifs face à des commerçants habitués aux anciens prix.

#### 🟢 Objectifs / Gains recherchés

1. **Maximiser la rentabilité par course** : gagner plus par trajet en groupant plusieurs colis d'un même secteur au lieu d'un aller-retour pour un seul colis.
2. **Optimiser son temps de travail** : effectuer plus de livraisons par jour en réduisant les trajets improductifs et en évitant les axes engorgés (privilégier l'Ancienne Piste plutôt que la VDN aux heures de pointe).
3. **Sécuriser et professionnaliser son activité** : disposer d'un revenu plus prévisible, d'un historique de courses traçable, et réduire les risques liés à la conduite prolongée en horaires de forte affluence.

---

## 3. Value Proposition Canvas

### 3.1 Profil Client (Customer Profile)

| Customer Jobs (tâches à accomplir) | Pains (douleurs/freins) | Gains (bénéfices recherchés) |
|---|---|---|
| Récupérer et livrer plusieurs colis par jour pour différents commerçants dakarois | Perte de carburant sur les trajets à vide (~30-40 % du carburant journalier) | Augmenter son revenu net journalier sans travailler plus d'heures |
| Se coordonner avec les commerçants (souvent par appel téléphonique individuel) | Embouteillages récurrents sur la VDN aux heures de pointe, allongeant les trajets | Réduire le temps passé dans les embouteillages via un itinéraire optimisé |
| Anticiper les urgences de livraison (produits périssables, commandes express) | Absence de visibilité sur les autres demandes du même secteur géographique | Regrouper plusieurs colis d'un même quartier en un seul passage |
| Gérer son forfait DATA limité et une connexion 3G instable | Applications trop lourdes qui consomment data et batterie, ou ne fonctionnent pas hors connexion stable | Disposer d'un outil léger, rapide, lisible même en plein soleil et peu gourmand en données |
| Faire face à la hausse du prix du carburant sans pouvoir ajuster ses tarifs | Marge nette réduite par l'augmentation du prix de l'essence (840 FCFA/L) | Économiser du carburant grâce au regroupement sectoriel des livraisons |

### 3.2 Carte de Valeur (Value Map)

| Products & Services (produits/services) | Pain Relievers (soulageurs de douleurs) | Gain Creators (créateurs de gains) |
|---|---|---|
| Application web mobile-first ThiakFlow (React/Tailwind, Dark Mode) | Regroupement automatique des colis par secteur (Zone A/B/C) pour supprimer les trajets à vide | Feuille de route optimisée générée par IA, prête à l'emploi en un coup d'œil |
| Agents IA "Chercheur" (extraction NLU) et "Rédacteur" (feuille de route) sur Dify.ai | Alertes trafic en temps réel (ex. embouteillages VDN) pour privilégier des itinéraires alternatifs | Estimation du gain en FCFA par tournée avant acceptation de la course |
| Interface de filtrage par zone géographique (Zone A Centre, Zone B VDN/Almadies, Zone C Banlieue) | Interface légère et lisible en Dark Mode, optimisée pour un usage extérieur en plein soleil et une connexion 3G | Indicateurs de performance (distance, économie de carburant estimée, statut de disponibilité) |
| Support IA conversationnel pour signaler un imprévu (embouteillage, colis manquant) | Consentement explicite et masquage des numéros de téléphone, conforme à la loi CDP sénégalaise | Historique de tournées traçable, valorisant le professionnalisme du livreur auprès des commerçants |
| Système de prime de péréquation carburant pour les zones périurbaines (Zone C) | Compensation financière pour les trajets vers les zones moins rentables (Pikine, Keur Massar) | Revenu plus stable et prévisible, réduisant la précarité économique liée aux trajets à vide |

