# 🏍️ ThiakFlow — Optimisation Logistique & Tournées Tiak-Tiak à Dakar

> **Projet de Master GET 409** · *Intégration des IA Génératives & Transformation Numérique* 
> **Institution :** Swiss UMEF University — Campus de Dakar (Année 2025-2026)
> **Enseignant Responsable :** M. Malick Faye Diagne 
> **Étape :** Séance 4 — MVP Web No-Code

---

## 📌 1. Description du Projet

**ThiakFlow** est une plateforme numérique de mobilité et de dispatching logistique conçue pour les livreurs moto indépendants (*Tiak-Tiak*) et les commerçants de Dakar. En s'appuyant sur un algorithme d'analyse NLU et de regroupement par secteur géographique, ThiakFlow planifie des tournées intelligentes en temps réel, réduisant la consommation de carburant et éliminant les trajets à vide sur les axes saturés comme la VDN.

* **Problème résolu :** Les livreurs Tiak-Tiak dakarois perdent jusqu'à 40 % de leurs revenus quotidiens en carburant gâché et en trajets à vide faute d'optimisation et de regroupement sectoriel des colis.
* **Solution :** ThiakFlow centralise les demandes de livraison, extrait les adresses dakaroises via un agent IA (Dify) et regroupe les courses par zones géographiques clés (*Zone A - Centre*, *Zone B - Axe VDN/Almadies*, *Zone C - Banlieue*). La plateforme génère une feuille de route optimisée permettant au livreur de doubler ses livraisons tout en divisant ses frais de transport.

---

## 👥 2. Membres de l'Équipe & Rôles

| Prénom & Nom | Rôle dans le projet | Pseudo GitHub | E-mail GitHub |
| :--- | :--- | :--- | :--- |
| **Abdou Aziz Mbaye** | **Chef de Produit (PM)** | `@Azizmbaye221` | `abdouaziz.mbaye1990@gmail.com` |
| **Ibrahima FAYE** | **Master Prompt Engineer** | `@kipstyle` | `thekipstyle@gmail.com` |
| **Makhoudia Sène** | **Dev UI (No-Code)** | `@Maksen` | `Makhoubryant24@gmail.com` |
| **Kalidou Baldé** | **Responsable Impact** | `@KalidouBaLde` | `khalidoubalde96@gmail.com` |

---

## 🚀 3. Fonctionnalités Principales (MVP V1)

* 📊 **Tableau de Bord Temps Réel (Dashboard Hero) :** Suivi dynamique des livraisons en cours (24), des gains cumulés (FCFA) et de l'indice d'efficience.
* 🗺️ **Layout Split-Screen & Cartographie :** Visualisation spatiale des points de ramassage (Colobane, Sandaga, HLM) et des zones de dépôt sur la presqu'île de Dakar.
* 🎯 **Filtrage Dynamique par Zone :** Tri instantané des livraisons par secteur géographique (*Zone A - Centre*, *Zone B - Axe VDN/Almadies*, *Zone C - Banlieue*).
* 🟢 **Badges de Statut en Temps Réel :** Indicateurs visuels phosphorescents (*Disponible* / *Indisponible*) sur chaque carte d'offre logistique.
* 🤖 **Assistant Support IA Chatbot :** Module interactif simulant l'interaction avec notre Agent Dify (S3) pour le suivi de colis et le signalement de trafic.
* 📱 **Interface 100% Mobile-First :** Ergonomie sombre à contraste élevé (*Urban Tech / Night Ride*), optimisée pour la lecture sur smartphone en extérieur.

---

## 🔗 4. Guide de Démarrage & Liens de Démo

Le MVP est entièrement déployé en ligne et utilisable sans installation préalable[cite: 2, 3] :

* 🌐 **URL Démo Live (L1) :** https://thiakflow-dakar-pro.lovable.app
* 📦 **Dépôt GitHub Public (L2) :** [https://github.com/Azizmbaye221/GET409-ThiakFlow](https://github.com/Azizmbaye221/GET409-ThiakFlow)

### Procédure de Test Rapide (2 min) :
1. Ouvrez l'**URL Démo Live** sur smartphone ou navigateur web.
2. Naviguez sur la page **Tournées & Offres** pour tester le filtrage dynamique par secteur géographique.
3. Ouvrez la page **Support IA** pour tester les requêtes de suivi de colis auprès de l'assistant.

---

## 🛠️ 5. Outils & Technologies Utilisés

* **Génération UI / IDE No-Code :** [Lovable.dev](https://lovable.dev) 
* **Stack Frontend :** React + Tailwind CSS + Vite
* **Orchestration Agentique IA (S3) :** [Dify.ai](https://dify.ai) (Agents Chercheur NLU + Rédacteur Classificateur)
* **Ingénierie de Prompts & Audit :** Claude 3.5 Sonnet / Claude.ai
* **Hébergement & Versioning :** GitHub (Dépôt Public) & Lovable Publish / Vercel

---

## 📸 6. Aperçu de l'Application (Captures d'Écran)

![Aperçu du MVP ThiakFlow](https://via.placeholder.com/1200x630/0B0B14/06B6D4?text=ThiakFlow+MVP+V1+-+Dashboard+%26+Split+Map+Dakar)

*Figure 1 : Interface Mobile & Desktop de ThiakFlow — Style Urban Tech / Night Ride.*[cite: 1]

---

> **Note d'Évaluation S4 :** Ce dépôt est public et conforme aux exigences du cours GET 409 dispensé par M. Malick Faye Diagne à la Swiss UMEF University (Campus de Dakar)[cite: 2, 3, 4].
