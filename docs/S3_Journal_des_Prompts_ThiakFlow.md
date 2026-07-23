Markdown# 🤖 LIVRABLE SÉANCE 3 — ARCHITECTURE AGENTIQUE & JOURNAL DES PROMPTS (DIFY.AI)

> **Projet :** ThiakFlow — Optimisation Logistique Tiak-Tiak à Dakar  
> **Master :** GET 409 — Transformation Numérique & IA Générative (Swiss UMEF University — Campus de Dakar)  
> **Enseignant responsable :** M. Malick Faye Diagne  
> **Équipe :** Abdou Aziz Mbaye (PM), Ibrahima Faye (Prompt Eng.), Makhoudia Sène (Dev UI), Kalidou Baldé (Impact)

---

## 📌 1. Fiche d'Identité du Projet
* **Application :** ThiakFlow
* **Plateforme Agentique Backend :** Dify.ai (Workflow Multi-Nœuds)
* **Périmètre :** Structuration NLU des demandes de livraison et génération de feuilles de route optimisées par zone géographique à Dakar.

---

## 📐 2. Architecture Agentique Multi-Nœuds (Workflow Dify)

L'architecture backend développée sous Dify.ai repose sur un **Workflow séquentiel à deux nœuds complémentaires** :

[Entrée Utilisateur : Message brut WhatsApp/SMS]│▼[1. NŒUD CHERCHEUR (LLM NLU / Parsing)]• Extraction d'adresses & classification par zone│▼ Variable : {{output_chercheur}}[2. NŒUD RÉDACTEUR (Générateur de Layout)]• Synthèse visuelle & feuille de route pour Moussa│▼[Sortie : Feuille de Route Optimisée sur Smartphone]
### Justification de l'Architecture :
1. **Séparation des responsabilités (Separation of Concerns) :** L'extraction d'entités (NLU déterministe) et la rédaction visuelle (créativité de mise en page) sont deux tâches distinctes. Séparer ces rôles élimine les hallucinations d'adresses.
2. **Transfert de contextes via variables :** L'utilisation de la variable `{{output_chercheur}}` garantit qu'aucune donnée de livraison ne soit inventée ou déformée entre l'analyse et la synthèse.

---

## 📓 3. Journal des Prompts S3 (3 Techniques Expérimentées)

### 1️⃣ Technique 1 : Zero-Shot Data Extraction (Nœud CHERCHEUR)
* **Objectif :** Extraire et structurer les entités logistiques d'un message informel brut sans exemple préalable.

```markdown
# SYSTEM PROMPT — AGENT CHERCHEUR (Dify)
Tu es l'Agent CHERCHEUR NLU de la plateforme ThiakFlow à Dakar.
Ta mission est d'analyser la demande de livraison brute envoyée par un commerçant et d'extraire les entités logistiques au format Key-Value strict.

ANALYSE & DÉCOUPAGE TERRITORIAL DAKAR :
- Zone A (Centre) : Sandaga, Plateau, Médina, Rebeuss, Port, Point E, Fann.
- Zone B (Axe VDN) : Colobane, Mermoz, Sacré-Cœur, VDN, Ouest Foire, Ngor, Almadies.
- Zone C (Banlieue) : HLM, Pikine, Guédiawaye, Parcelles Assainies, Keur Massar, Thiaroye.

ENTITÉS À EXTRAIRE :
- POINT_RAMASSAGE : [Quartier/Marché de départ]
- DESTINATIONS : [Liste des quartiers de livraison]
- NOMBRE_COLIS : [Nombre total de colis à transporter]
- URGENCE : [Haute / Normale]
- ZONE_CIBLE : [Zone A / Zone B / Zone C]

RÈGLE D'OR : Si le point de ramassage OU la destination est absente du message, réponds exactement : "STATUT: INSUFFISANT".
Exemple d'Entrée : "Salam ThiakFlow, j'ai 3 colis de vêtements au marché Colobane à livrer rapidement aux Almadies et Mermoz.
"Sortie Dify : POINT_RAMASSAGE : Marché Colobane | DESTINATIONS : Mermoz, Les Almadies | NOMBRE_COLIS : 3 | URGENCE : Haute | ZONE_CIBLE : Zone B (Axe VDN)

2️⃣ Technique 2 : Few-Shot Prompting (Nœud RÉDACTEUR)Objectif : Imposer un gabarit visuel strict et lisible sur smartphone pour la feuille de route du livreur Moussa.Markdown# SYSTEM PROMPT — AGENT RÉDACTEUR (Dify)
Tu es le Dispatcher Logistique de ThiakFlow. À partir de la variable {{output_chercheur}}, génère la feuille de route pour le livreur.

VOICI UN EXEMPLE STRICT DU FORMAT À REPRODUIRE (FEW-SHOT) :

=== FEUILLE DE ROUTE THIAKFLOW ===
📍 DEPART : Marché Sandaga
🎯 DESTINATIONS : Médina ➔ Rebeuss
📦 CHARGE : 2 colis
⚡ SECTEUR : Zone A (Centre-Ville)
----------------------------------
🗺️ ITINÉRAIRE CONSEILLÉ :
1. Ramassage : Marché Sandaga (Magasin #12)
2. Etape 1 : Médina (Rue 6 x 11)
3. Etape 2 : Rebeuss (Près du commissariat)
💡 GAIN ESTIMÉ : 800 FCFA d'économie carburant
==================================

SUR CE MODÈLE EXACT, rédige la feuille de route pour les données reçues : {{output_chercheur}}.
Si {{output_chercheur}} contient "INSUFFISANT", réponds : "⚠️ Données de livraison incomplètes."

3️⃣ Technique 3 : Chain-of-Thought / CoT (Calcul de Tournée & Gain FCFA)Objectif : Guider l'IA pas à pas pour déterminer l'ordre optimal des étapes et calculer l'économie de carburant en FCFA.Markdown# SYSTEM PROMPT — MODULE RAISONNEMENT DIFY (CoT)
Tu es le moteur d'optimisation d'itinéraires de ThiakFlow. Pour déterminer le gain de carburant et l'ordre des étapes, raisonne étape par étape.

Méthode de calcul CoT :
1. Analyse la distance spatiale entre le point de départ et les destinations.
2. Identifie les goulots d'étranglement du trafic (ex: VDN aux heures de pointe).
3. Regroupe les livraisons se trouvant dans le même secteur pour éviter les trajets à vide.
4. Applique le barème d'économie : 500 FCFA (Zone A), 1 200 FCFA (Zone B), 1 800 FCFA (Zone C).

ENTRÉE :
Point départ : Marché HLM | Destinations : Pikine & Guédiawaye.

RAISONNEMENT PAS À PAS :
- Étape 1 : HLM, Pikine et Guédiawaye appartiennent à la Zone C (Banlieue).
- Étape 2 : L'axe HLM -> Pikine -> Guédiawaye forme une trajectoire linéaire continue.
- Étape 3 : Le groupement permet d'éliminer un aller-retour inutile vers la banlieue.
- Étape 4 : Économie calculée = 1 aller-retour évité = 2 000 FCFA d'essence économisés.

SORTIE FINALE :
"Tournée optimisée Banlieue (Zone C). Trajet linéaire HLM ➔ Pikine ➔ Guédiawaye. Gain carburant estimé : 2 000 FCFA."

⚖️ 4. Note d'Analyse Éthique sur les Agents Autonomes (½ Page)

1. Risque d'Hallucination Logistique & Impact Financier Direct
Dans un système logistique urbain comme celui de Dakar, une hallucination d'adresse par l'IA (ex: orienter un livreur vers Mermoz au lieu de Pikine) se traduit immédiatement par une perte financière directe pour le livreur (carburant consommé à perte, temps gâché dans les embouteillages). 
Pour parer à ce risque, notre workflow Dify intègre une règle de validation déterministe qui bloque la génération et renvoie un statut d'erreur dès qu'une adresse n'est pas reconnue formellement.

2. Risque de Biais d'Attribution & Équité Territoriale
Un algorithme d'optimisation pur risque de privilégier les zones aisées à forte densité (Zone B - VDN/Almadies) au détriment des zones périphériques (Zone C - Banlieue). 
Afin de garantir une équité de service et d'éviter l'isolement des commerçants de la banlieue dakarois, le prompt de l'agent intègre un coefficient de péréquation qui attribue une prime de carburant sur les tournées desservant la Zone C.

📊 5. Tableau Récapitulatif des Livrables S3

### 📊 Tableau Récapitulatif des Livrables S3 (Dify.ai)

| # Code | Livrable / Composant | Technique IA | Objectif Métier (ThiakFlow Dakar) | Outil | Statut |
| :---: | :--- | :--- | :--- | :---: | :---: |
| **S3-L1** | **Agent V1 Fonctionnel** | Workflow d'Agent | Application interactive publiée avec URL publique | Dify.ai | ✅ Validé |
| **S3-L2** | **Schéma d'Architecture** | Workflow Séquentiel | Flux à 2 nœuds : Chercheur (NLU) ➔ Rédacteur (Layout) | Dify / Canvas | ✅ Validé |
| **S3-P1** | **Agent Chercheur** | Zero-Shot NLU | Extraction des points de ramassage/dépôt à Dakar et classification par zone | Dify.ai | ✅ Validé |
| **S3-P2** | **Agent Rédacteur** | Few-Shot Prompting | Génération de la feuille de route mobile au format structuré pour Moussa | Dify.ai | ✅ Validé |
| **S3-P3** | **Moteur d'Optimisation** | Chain-of-Thought (CoT) | Raisonnement étape par étape sur le trafic et calcul du gain carburant en FCFA | Dify.ai | ✅ Validé |
| **S3-L4** | **Note d'Analyse Éthique** | Analyse d'Impact | Réflexion ½ page : Risque d'hallucination d'adresses et péréquation banlieue (Zone C) | Markdown | ✅ Validé |
