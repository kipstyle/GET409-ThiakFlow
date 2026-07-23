# 📓 Journal des Prompts — Séance 4 (MVP No-Code)

**Projet : ThiakFlow** — Optimisation logistique et regroupement de colis par secteur géographique à Dakar

**Master GET 409 · Transformation Numérique & IA Générative** — Swiss UMEF University, Campus de Dakar
**Enseignant responsable :** M. Malick Faye Diagne

---

## 1. Fiche d'identité du projet

| Champ | Valeur |
|---|---|
| Projet | ThiakFlow |
| Dépôt GitHub public (L2) | [https://github.com/Azizmbaye221/GET409-ThiakFlow](https://github.com/Azizmbaye221/GET409-ThiakFlow) |
| URL démo live (L1) | [https://thiakflow.lovable.app](https://thiakflow.lovable.app) |
| Outil No-Code utilisé | Lovable.dev |

**Équipe :**
- Abdou Aziz Mbaye — Chef de Produit (PM) — [@Azizmbaye221](https://github.com/Azizmbaye221)
- Ibrahima Faye — Master Prompt Engineer — [@kipstyle](https://github.com/kipstyle)
- Makhoudia Sène — Dev UI No-Code — [@Maksen](https://github.com/Maksen)
- Kalidou Baldé — Responsable Impact — [@KalidouBaLde](https://github.com/KalidouBaLde)

---

## 2. Prompt Master d'Initialisation (E1)

**Technique :** Prompt structuré en 6 blocs obligatoires (Contexte, Pages, Fonctionnalités, Design, Données, Stack)
**Outil :** Lovable.dev

```
Crée une plateforme web complète appelée ThiakFlow.

# CONTEXTE
ThiakFlow est une plateforme numérique qui optimise le regroupement de colis en temps réel et
la planification de tournées sectorielles pour les livreurs moto indépendants (Tiak-Tiak) à
Dakar afin de réduire leurs coûts de carburant et éliminer les trajets à vide.

# PAGES À CRÉER (3 pages)
1. ACCUEIL (Tableau de Bord Temps Réel)
   → Header : logo "TF" néon + nom ThiakFlow + navigation fixe.
   → Hero : titre accrocheur "Doublez vos livraisons, divisez votre carburant à Dakar" +
     sous-titre expliquant le regroupement intelligent par IA + 2 boutons CTA :
     « Commencer la tournée » et « Espace Commerçant ».
   → Section chiffres clés (3 cartes) : "30% d'économie carburant", "2x plus de courses/jour",
     "4 zones dakaroises covered".
   → Footer : mentions légales + contact (Avenue Cheikh Anta Diop, Colobane, Dakar).

2. TOURNÉES & OFFRES GROUPÉES
   → Liste de 6 cartes d'offres logistiques avec : Référence colis, Trajet
     (Ramassage → Dépôt), Zone géographique, Gain estimé en FCFA, statut.
   → Boutons de filtre interactifs : Tous | Zone A (Centre-Ville) | Zone B
     (Axe VDN/Almadies) | Zone C (Banlieue).
   → Chaque élément en carte avec pastille "Disponible" (cyan #06B6D4) ou
     "Indisponible" (rouge #EF4444).

3. SUPPORT IA & CONTACT
   → Interface de chat style Assistant IA Support : Header "ThiakFlow AI Support", zone de
     messages de démonstration de suivi de colis et 3 boutons de suggestions rapides.
   → Formulaire de contact : Nom complet, E-mail, Téléphone (format +221), Message /
     Signalement d'embouteillage.
   → Bouton d'envoi principal #1D4ED8.

# DESIGN
→ Couleur principale : #1D4ED8 (bleu électrique express)
→ Couleur d'accent : #F97316 (orange vif urgence & sécurité)
→ Fond : #0B0B14 (Dark Mode Premium)
→ Style : moderne, épuré, glassmorphism léger
→ Responsive mobile-first (breakpoint 768px)
→ Navigation fixe en haut avec les 3 pages

# DONNÉES (6 exemples réels dakarois)
1. #TF-D101 | Marché Colobane → Mermoz & Almadies | Zone B (Axe VDN) | Gain : 1 800 FCFA | Disponible
2. #TF-D102 | Marché Sandaga → Médina & Rebeuss | Zone A (Centre) | Gain : 800 FCFA | Disponible
3. #TF-D103 | Marché HLM → Pikine & Guédiawaye | Zone C (Banlieue) | Gain : 2 000 FCFA | Indisponible
4. #TF-D104 | Port de Dakar → Point E | Zone A (Centre) | Gain : 500 FCFA | Disponible
5. #TF-D105 | Ouest Foire → Ngor & Les Almadies | Zone B (Axe VDN) | Gain : 1 200 FCFA | Disponible
6. #TF-D106 | Parcelles Assainies → Keur Massar | Zone C (Banlieue) | Gain : 1 800 FCFA | Disponible

# STACK TECHNIQUE
→ React + Tailwind CSS + Vite
```

**Résultat obtenu :** ✅ Application web générée avec succès, 3 pages fonctionnelles, style Dark Mode épuré, conforme au design demandé.

---

## 3. Journal des itérations (règle : 1 prompt = 1 modification)

### 🟡 Prompt P1 — [CORRECTION DATA]

| Champ | Détail |
|---|---|
| Type | Correction de donnée |
| Consommation estimée | Faible (~5K tokens) |

```
Change le tarif estimé de la course #TF-D101 (Marché Colobane → Mermoz & Almadies) de
1 500 FCFA à 1 800 FCFA et passe son statut en "Disponible" au lieu de "En attente".
```

**Résultat obtenu :** ✅ Mis à jour instantanément sans altérer le reste du layout.

---

### 🟡 Prompt P2 — [AMÉLIORATION VISUELLE]

| Champ | Détail |
|---|---|
| Type | Amélioration visuelle |
| Consommation estimée | Moyenne (~15-25K tokens) |

```
Ajoute une bannière d'annonce en haut de toutes les pages avec le texte :
"🚦 Alerte Trafic Dakar : Embouteillages signalés sur la VDN — Privilégiez les tournées
de la Zone A (Centre-Ville)"
Style : Fond orange express #F97316, texte blanc, hauteur fine.
```

**Résultat obtenu :** ✅ Bannière d'avertissement visible en haut de l'écran sur toutes les vues.

---

### 🟡 Prompt P3 — [AMÉLIORATION FONCTIONNELLE]

| Champ | Détail |
|---|---|
| Type | Amélioration fonctionnelle |
| Consommation estimée | Élevée (~25-40K tokens) |

```
Sur la page Tournées & Offres Groupées, active les boutons de filtre : Tous | Zone A
(Centre) | Zone B (Axe VDN) | Zone C (Banlieue).
Quand l'utilisateur clique sur un bouton de zone, seules les cartes d'offres logistiques
correspondant à cette zone doivent rester affichées.
```

**Résultat obtenu :** ✅ Tri instantané des cartes sur la page sans rechargement de page.

---

### 🟡 Prompt P4 — [RESPONSIVE MOBILE]

| Champ | Détail |
|---|---|
| Type | Amélioration UX / Responsive Mobile |
| Consommation estimée | Moyenne (~15K tokens) |

```
Le menu de navigation ne s'affiche pas correctement sur écran smartphone (< 768px).
Transforme-le en menu hamburger (☰) sous 768px qui s'ouvre en overlay fluide au clic.
Ne modifie pas l'affichage desktop.
```

**Résultat obtenu :** ✅ Interface 100 % responsive, testable sur smartphone Android.

---

## 4. Tableau récapitulatif des prompts

| Code | Type | Objectif métier | Outil | Statut |
|---|---|---|---|---|
| E1 | Prompt Master Init | Générer l'application web React/Tailwind complète | Lovable.dev | ✅ Succès |
| P1 | Correction (Data) | Ajuster le tarif et le statut de la course #TF-D101 | Lovable.dev | ✅ Succès |
| P2 | Visuelle (UI) | Insérer la bannière d'alerte trafic VDN orange | Lovable.dev | ✅ Succès |
| P3 | Fonctionnelle | Activer le filtrage dynamique par zone géographique | Lovable.dev | ✅ Succès |
| P4 | Responsive | Adapter la navigation mobile en menu hamburger | Lovable.dev | ✅ Succès |

