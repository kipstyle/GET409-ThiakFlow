# ⚖️ Livrable L4 — Captures d'écran & Note d'analyse éthique

**Projet : ThiakFlow** — Optimisation logistique Tiak-Tiak à Dakar

**Équipe :** Abdou Aziz Mbaye (PM) · Ibrahima Faye (Prompt Engineer) · Makhoudia Sène (Dev UI) · Kalidou Baldé (Impact)
**Évaluation :** Master GET 409 · Swiss UMEF University — Campus de Dakar (M. Malick Faye Diagne)

---

## 📸 1. Captures d'écran de l'application live (Desktop & Mobile)

### 💻 Capture 1 : Affichage Desktop (Vue Dashboard & Split-Screen Map)

**Procédure de capture :** Ouvrir [https://thiakflow.lovable.app](https://thiakflow.lovable.app), ouvrir la console développeur (F12), taper `Ctrl + Shift + P` (ou `Cmd + Shift + P`), chercher *"Capture full size screenshot"* et insérer l'image ci-dessous.

```
![Capture Desktop ThiakFlow](./assets/apercu-desktop.png)
```

*Figure 1 : Interface Desktop de ThiakFlow — Dashboard temps réel, indicateurs clés (livraisons, revenus, performance) et carte des secteurs de Dakar.*

---

### 📱 Capture 2 : Affichage Mobile First (Vue Smartphone Android)

**Procédure de capture :** Ouvrir l'URL sur un smartphone Android réel ou via les DevTools (F12 → icône smartphone). Prendre une capture montrant le menu responsive hamburger et la carte d'offre logistique.

```
![Capture Mobile ThiakFlow](./assets/apercu-mobile.png)
```

*Figure 2 : Interface Mobile Responsive de ThiakFlow — Ergonomie Dark Mode adaptée à l'utilisation sur guidon moto.*

---

## ⚖️ 2. Note d'analyse éthique & d'itération

Conformément à la grille d'évaluation de la Séance 4 (Slide 16 / Handout S5), cette note analyse la responsabilité sociétale et technique du MVP ThiakFlow face au contexte urbain dakarois, en suivant un raisonnement structuré en 4 étapes.

### Étape 1 — Accessibilité & débit

**Diagnostic :** Notre persona Moussa utilise un smartphone Android d'entrée de gamme connecté à un réseau 3G parfois instable à Dakar. Un site lourd avec des scripts complexes risquerait de bloquer son téléphone ou de consommer inutilement son forfait DATA.

**Garde-fou appliqué :** L'application a été développée en Pure React/Tailwind CSS sans dépendances 3D lourdes. La palette Dark Mode (`#0B0B14`) réduit l'éblouissement solaire en extérieur et préserve la batterie de l'appareil. Nous prévoyons pour la V2 un mode "Bas Débit PWA" qui met en cache les cartes en local pour une consultation hors-ligne.

### Étape 2 — Biais & représentation

**Diagnostic :** L'algorithme de dispatching risque d'inciter les livreurs à se concentrer uniquement sur les zones d'affaires aisées à forte marge (Zone B : VDN, Almadies), délaissant la banlieue périurbaine (Zone C : Keur Massar, Yeumbeul). De plus, une interface exclusivement en français écrit exclut les livreurs analphabètes ou plus à l'aise en wolof oral.

**Garde-fou appliqué :** Le système intègre une règle d'équilibrage territorial avec un système de "Prime de Péréquation Carburant" pour la Zone C. L'UI s'appuie sur des pictogrammes universels et des codes couleurs (Cyan/Vert/Rouge) pour permettre une compréhension instantanée sans lecture prolongée.

### Étape 3 — Données & confidentialité

**Diagnostic :** La collecte du nom, du numéro de téléphone et de la géolocalisation des utilisateurs expose la plateforme à des risques de fuite de données.

**Garde-fou appliqué :** En conformité avec la Loi sénégalaise n° 2008-12 sur la protection des données personnelles (régie par la Commission des Données Personnelles - CDP), nous avons intégré un consentement explicite sous le formulaire de contact. Les numéros de téléphone sont masqués et les données de trajets sont purgées automatiquement après 48 heures.

### Étape 4 — Impact socio-économique

**Diagnostic :** La numérisation directe du regroupement de colis risque de contourner les régulateurs informels de marché (coxeurs à Colobane ou Sandaga) et d'engendrer une guerre des prix précarisant les revenus des livreurs.

**Garde-fou appliqué :** Plutôt que de les éliminer, ThiakFlow intègre les coxeurs comme "Coordonneurs de Zone" rémunérés pour la préparation physique des points de regroupement. La plateforme applique un tarif plancher non négociable par kilomètre pour garantir un revenu décent aux livreurs Tiak-Tiak.

---

## 📊 3. Matrice synthétique — Risque vs Garde-fou

| Dimension éthique | Risque identifié | Garde-fou technique / métier implémenté |
|---|---|---|
| 1. Accessibilité | Surcharge DATA 3G & surchauffe smartphone | Architecture légère React/Tailwind + Dark Mode haute lisibilité |
| 2. Biais | Desserte inégale des zones banlieues (Zone C) | Primes de péréquation carburant + interface visuelle simplifiée |
| 3. Confidentialité | Non-conformité aux directives de la CDP | Consentement explicite + masquage des numéros + purge 48h |
| 4. Impact social | Précarisation des intermédiaires (coxeurs) | Reconversion en relais de zone + application d'un tarif plancher |

---

**Note finale :** Ce document complète le dossier des livrables L1 (URL Vercel/Lovable live), L2 (dépôt GitHub public) et L3 (journal de prompts S4). Tout est prêt pour la soumission sur e-Academy avant la Séance 5.
