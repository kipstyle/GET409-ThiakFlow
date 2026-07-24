# 📓 LIVRABLE SÉANCE 5 — JOURNAL DES PROMPTS RAG & WEBHOOK

> **Projet :** ThiakFlow — Optimisation Logistique Tiak-Tiak à Dakar
> **Master :** GET 409 — Transformation Numérique & IA Générative (Swiss UMEF University — Campus de Dakar)
> **Enseignant responsable :** M. Malick Faye Diagne
> **Équipe :** Abdou Aziz Mbaye (PM), Ibrahima Faye (Prompt Eng.), Makhoudia Sène (Dev UI), Kalidou Baldé (Impact)
> **Livrable :** L4 — Journal de Prompts S5 (20 pts) — min. 3 prompts documentés

⚠️ Le handout officiel est écrit pour **bolt.new** — notre équipe utilise **Lovable.dev** (puis MagicPatterns pour l'itération webhook page Tournées). La logique webhook/RAG reste identique ; seul l'outil no-code cible change.

---

## 1. Fiche d'identité

| Champ | Valeur |
|---|---|
| MVP V2 | https://thiakflow-dakar-pro.lovable.app |
| Base de connaissances | ThiakFlow_KB_v1 — Dify Knowledge |
| Document indexé | tournees_thiakflow_s5_2026.csv — 10 tournées réelles Dakar |
| Agent Dify | Workflow ThiakFlow — RÉCUPÉRATION → CHERCHEUR → RÉDACTEUR |
| URL API Dify | https://api.dify.ai/v1/workflows/run |

---

## 2. Prompt 1 — Base de connaissances RAG (Étape A du handout)

**Objectif :** Indexer les données réelles de tournées ThiakFlow dans Dify Knowledge pour ancrer les réponses de l'agent dans des chiffres vérifiables plutôt que dans des estimations génériques.

**Données préparées (CSV, en-têtes en ligne 1) :**
```
Reference,Zone,Point_Depart,Destinations,Nombre_Colis,Gain_Estime_FCFA,Statut,Urgence,Semaine,Source
TF-D101,Zone B (Axe VDN),Marché Colobane,Mermoz et Almadies,3,1800,Disponible,Élevée,S23-2026,ThiakFlow
TF-D102,Zone A (Centre),Marché Sandaga,Médina et Rebeuss,2,800,Disponible,Normale,S23-2026,ThiakFlow
... (10 lignes au total)
```

**Configuration Dify Knowledge :**
| Paramètre | Valeur | Justification |
|---|---|---|
| Nom de la base | ThiakFlow_KB_v1 | Convention d'équipe cohérente avec Agent_ThiakFlow (S3) |
| Chunk size | 300 tokens | CSV = données courtes, petits chunks suffisent |
| Overlap | 50 tokens | Évite de couper une ligne de tournée en plein milieu |
| Mode d'index | Économique — Index inversé | Plan gratuit Dify, correspondance par mots-clés |
| Top K | 3 | Bon équilibre précision/vitesse |

**Résultat obtenu :** ✅ Base indexée, statut "Indexed" (vert). Test de récupération sur "gain Colobane Almadies" retourne le chunk TF-D101 attendu.

---

## 3. Prompt 2 — Webhook Lovable/MagicPatterns ↔ Dify (Étape C du handout)

**Objectif :** Générer automatiquement le composant frontend (champ + bouton + zone résultat) connecté au workflow Dify, sans écrire de code manuellement.

**Prompt envoyé (adapté ThiakFlow, remplace GreenSprint/bolt.new du handout officiel) :**
```
Dans mon MVP ThiakFlow, ajoute une fonctionnalité de consultation de l'agent IA sur
la page [Accueil / Tournées].

INTERFACE À AJOUTER :
1. Un champ de texte avec placeholder :
   "Posez votre question sur une tournée ou une zone..."
2. Un bouton bleu électrique "Demander à l'agent 🏍️" (#1D4ED8)
3. Une zone de résultat sous le formulaire (fond gris clair)
4. Un spinner de chargement pendant la requête
5. Un message d'erreur rouge si la requête échoue

CONNEXION WEBHOOK DIFY :
URL : https://api.dify.ai/v1/workflows/run
Méthode : POST
Headers :
  Authorization: Bearer [CLÉ_API]
  Content-Type: application/json
Body JSON :
  { "inputs": {"query": valeurDuChampTexte},
    "response_mode": "blocking",
    "user": "user-thiakflow-" + Date.now() }

TRAITEMENT DE LA RÉPONSE :
- Succès : afficher response.data.answer dans la zone résultat
- Erreur réseau : "Service temporairement indisponible"
- Timeout (>10s) : "La réponse prend trop de temps — réessayez"

STYLE : cohérent avec le MVP — fond sombre #0B0B14, bleu électrique #1D4ED8,
orange #F97316 pour les alertes. Responsive mobile.
```

**Note d'adaptation technique :** le handout officiel place `query` hors de `inputs` (`{ "inputs": {}, "query": ... }`). Notre workflow Dify expose `query` comme variable du nœud DÉBUT — la forme correcte pour notre cas est `{ "inputs": { "query": ... } }`. Documenté également dans `S5_Webhook_ThiakFlow.md`.

**Résultat obtenu :** ⚠️ En cours de correction — première itération a retourné "Service temporairement indisponible" (erreur webhook, probablement clé/URL ou workflow non publié). Deuxième itération : "Réponse indisponible" (le fetch aboutit mais l'agent ne renvoie pas encore de `data.answer` exploitable — base RAG pas encore connectée / prompt RÉDACTEUR à publier).

---

## 4. Prompt 3 — Prompt système du nœud RÉDACTEUR (ancrage RAG)

**Objectif :** Contraindre l'agent à ne répondre qu'à partir des données réelles du CSV indexé, avec repli explicite en cas de question hors-base (principe de "Transparence des limites", slide 16).

```
Tu es le RÉDACTEUR de ThiakFlow, l'agent Ai-da qui répond aux questions des livreurs
et commerçants dakarois sur les tournées, zones et gains estimés.

DONNÉES DE LA BASE DE CONNAISSANCES :
{{#context#}}

RÈGLES STRICTES :
1. Réponds UNIQUEMENT à partir des données ci-dessus.
2. N'invente JAMAIS un chiffre, une zone ou une distance absente de {{#context#}}.
3. Si aucune donnée pertinente n'est présente, réponds exactement :
   "Information non disponible dans ma base."
4. Reste concis : 2 à 4 phrases maximum.

TON : direct, chaleureux, professionnel — comme un dispatcher dakarois expérimenté.
```

**Résultat obtenu :** À valider après connexion complète du nœud RÉCUPÉRATION → ThiakFlow_KB_v1 et publication du workflow.

---

## 5. Tests de cohérence (Étape D — obligatoires avant S6)

| # | Question test | Résultat attendu | Statut |
|---|---|---|---|
| 1 | "Quel est le gain estimé pour la tournée Colobane → Mermoz et Almadies ?" | 1 800 FCFA, Zone B, Disponible | ⏳ À valider |
| 2 | "Quelle zone a le plus de tournées disponibles ?" | Réponse construite depuis comptage CSV | ⏳ À valider |
| 3 (hors-base) | "Quelle est la météo à Dakar demain ?" | "Information non disponible dans ma base" | ⏳ À valider |

---

## 6. Synthèse critique

Le pipeline RAG + webhook expose une difficulté classique documentée dans le tableau de débogage du cours (slide 15) : un webhook peut réussir techniquement (statut 200) sans que l'agent produise de contenu exploitable, si la base RAG n'est pas encore connectée en amont. Notre équipe a validé le webhook lui-même (passage de "Service indisponible" à "Réponse indisponible" entre les deux itérations), la prochaine étape est de finaliser la connexion RAG → RÉDACTEUR → publication avant de pouvoir valider les 3 tests de cohérence.

*Document établi dans le cadre du GET 409 — Swiss UMEF University, Campus de Dakar — Juin 2026*
