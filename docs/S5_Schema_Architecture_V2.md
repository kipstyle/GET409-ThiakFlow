# 🏗️ LIVRABLE SÉANCE 5 — SCHÉMA D'ARCHITECTURE V2

> **Projet :** ThiakFlow — Optimisation Logistique Tiak-Tiak à Dakar
> **Livrable :** L3 — Schéma d'architecture V2 (20 pts)

---

## Architecture complète — MVP ↔ Agents Dify ↔ Base RAG

```
┌─────────────────────────┐
│   UTILISATEUR (Moussa    │
│   ou commerçant Dakar)   │
└────────────┬─────────────┘
             │ saisit une question
             ▼
┌─────────────────────────────────────┐
│   MVP LOVABLE.DEV                     │
│   thiakflow-dakar-pro.lovable.app     │
│   Page Accueil / Tournées & Offres    │
│   → Champ texte + bouton "Ai-da"      │
└────────────┬───────────────────────────┘
             │ POST HTTP (webhook)
             │ { inputs: { query }, response_mode, user }
             ▼
┌─────────────────────────────────────┐
│   WEBHOOK / API DIFY                  │
│   https://api.dify.ai/v1/workflows/run│
│   Authorization: Bearer [clé API]     │
└────────────┬───────────────────────────┘
             ▼
┌─────────────────────────────────────┐
│   NŒUD RÉCUPÉRATION DE CONNAISSANCES  │
│   Interroge la base ThiakFlow_KB_v1   │
│   Top K = 3 · Index inversé           │
└────────────┬───────────────────────────┘
             │ passages pertinents (context)
             ▼
┌─────────────────────────────────────┐
│   NŒUD CHERCHEUR                      │
│   NLU — extraction zone/tournée/gain  │
└────────────┬───────────────────────────┘
             ▼
┌─────────────────────────────────────┐
│   NŒUD RÉDACTEUR                      │
│   Génère la réponse finale à partir   │
│   de {{#context#}} — règle anti-      │
│   hallucination + repli explicite     │
└────────────┬───────────────────────────┘
             │ { "answer": "...", "metadata": {...} }
             ▼
┌─────────────────────────────────────┐
│   RÉPONSE AFFICHÉE DANS LE MVP        │
│   Zone résultat sous le formulaire    │
└─────────────────────────────────────┘

┌─────────────────────────────────────┐
│   BASE DE CONNAISSANCES (source)      │
│   ThiakFlow_KB_v1 — Dify Knowledge    │
│   tournees_thiakflow_s5_2026.csv      │
│   10 tournées réelles Dakar (Zone A/B/C)│
└─────────────────────────────────────┘
```

## Légende des étapes

| # | Étape | Description |
|---|---|---|
| 1 | Saisie utilisateur | L'utilisateur tape sa question dans le formulaire MVP (Accueil ou Tournées) |
| 2 | Requête webhook | Lovable envoie la question au webhook Dify via une requête HTTP POST |
| 3 | Récupération RAG | L'agent interroge la base ThiakFlow_KB_v1, extrait les 3 passages les plus pertinents |
| 4 | Extraction NLU | Le nœud CHERCHEUR structure les entités (zone, tournée, gain) |
| 5 | Génération réponse | Le nœud RÉDACTEUR rédige une réponse ancrée dans les données réelles, ou renvoie un message de repli si hors-base |
| 6 | Affichage | La réponse (`data.answer`) est affichée dans la zone résultat du MVP |

## Séparation des responsabilités

- **RÉCUPÉRATION** : ancre les réponses dans des données vérifiables (élimine les hallucinations de tarifs)
- **CHERCHEUR** : extraction déterministe des entités logistiques
- **RÉDACTEUR** : mise en forme naturelle + garde-fou "Information non disponible dans ma base" pour les questions hors-périmètre

*Document établi dans le cadre du GET 409 — Swiss UMEF University, Campus de Dakar — Juin 2026*
