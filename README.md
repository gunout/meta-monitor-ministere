<div align="center">

# 🇫🇷 Meta Monitor — Expertise Data.gouv.fr

**Dashboard d'expertise automatique multi-secteurs pour l'analyse de jeux de données publiques français**

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/fr/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/fr/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/fr/docs/Web/JavaScript)
[![DSFR](https://img.shields.io/badge/DSFR-1.11.2-000091?style=for-the-badge)](https://www.systeme-de-design.gouv.fr/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=for-the-badge)](http://makeapullrequest.com)

[![Chart.js](https://img.shields.io/badge/Chart.js-4.4.0-FF6384?style=flat-square&logo=chart.js&logoColor=white)](https://www.chartjs.org/)
[![SheetJS](https://img.shields.io/badge/SheetJS-0.18.5-217346?style=flat-square)](https://sheetjs.com/)
[![jsPDF](https://img.shields.io/badge/jsPDF-2.5.1-EC1C24?style=flat-square)](https://github.com/parallax/jsPDF)
[![Made in France](https://img.shields.io/badge/Made%20in-France-000091?style=flat-square)](https://www.gouvernement.fr/)

---

**🔬 Expertisez, analysez et surveillez automatiquement des dizaines de jeux de données publiques en un clic.**

[Fonctionnalités](#-fonctionnalités) · [Installation](#-installation) · [Utilisation](#-utilisation) · [Architecture](#️-architecture) · [Contribuer](#-contribuer)

</div>

---

## 📖 Table des matières

- [✨ Aperçu](#-aperçu)
- [🎯 Fonctionnalités](#-fonctionnalités)
- [🚀 Installation](#-installation)
- [💻 Utilisation](#-utilisation)
- [📂 Structure du projet](#-structure-du-projet)
- [🏗️ Architecture](#️-architecture)
- [🧠 Capacités d'analyse](#-capacités-danalyse)
- [🎨 Thèmes & Design](#-thèmes--design)
- [📊 Formats supportés](#-formats-supportés)
- [🔒 Détection PII](#-détection-pii)
- [📄 Export PDF](#-export-pdf)
- [⚙️ Configuration](#️-configuration)
- [🐛 Dépannage](#-dépannage)
- [🤝 Contribuer](#-contribuer)
- [📜 Licence](#-licence)

---

## ✨ Aperçu

**Meta Monitor** est un dashboard web autonome (single-page HTML) qui :

1. 📥 **Charge automatiquement** 15+ fichiers JSON de jeux de données publiques (Agriculture, Armée, Culture, Écologie, Éducation, Europe, Finances, Industrie, Intérieur, Justice, Logements, Santé, Sport, Travail…)
2. 🔬 **Expertise chaque ressource** : CSV, JSON, XLSX — détection de types, statistiques, doublons, aberrations, corrélations
3. 🚨 **Surveille la conformité** : alertes automatiques sur les métadonnées manquantes ou obsolètes
4. 🔒 **Détecte les PII** : emails, téléphones, IBAN, NIR, SIRET…
5. 📄 **Génère des rapports PDF** d'expertise complets
6. 🌍 **Filtre multi-thèmes** avec catégorisation intelligente par mots-clés

> ⚡ Aucune installation, aucune dépendance backend — un simple serveur HTTP suffit.

---

## 🎯 Fonctionnalités

### 📊 Analyse de données
- ✅ Détection automatique du type (number, date, boolean, string)
- ✅ Statistiques par colonne (min, max, moyenne, médiane, Q1, Q3, écart-type)
- ✅ Détection de doublons
- ✅ Détection de valeurs aberrantes (IQR)
- ✅ Matrice de corrélations (Pearson)
- ✅ Taux de remplissage par colonne

### 🎨 Visualisations
- 📈 Graphique en donut des types
- 📊 Barres de remplissage
- 📉 Cardinalité par colonne
- 📦 Distribution (boxplot-like)
- 🏷️ Top catégories (camembert)
- 🎯 Palette de 12 couleurs

### 🚨 Surveillance
- Alertes critiques vs avertissements
- Données obsolètes (>5 ans, >10 ans)
- Description manquante ou courte
- Tags absents
- Ressources manquantes
- URL non HTTPS

### 🔒 Sécurité & Conformité
- Détection d'emails, téléphones, IBAN
- NIR (numéro de sécurité sociale)
- SIRET / SIREN
- Codes postaux, dates de naissance
- Adresses IP, URLs
- Score de conformité 0–100

### 📤 Export & Interop
- 📄 Rapport PDF multi-pages
- 📊 Export XLSX-ready
- 🔀 Comparaison de deux jeux
- 📋 Historique des actions
- 🖨️ Impression navigateur

### 🌍 Multi-thèmes
- 15 ministères/secteurs préchargés
- Filtre par thème
- Catégorisation auto par mots-clés
- 10 catégories transverses
- Recherche full-text

---

## 🚀 Installation

### Prérequis

- Un navigateur moderne (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- **Python 3** ou **Node.js** (pour servir les fichiers localement)
- Les fichiers JSON dans un dossier `json/`

### Étapes

```bash
# 1. Cloner le dépôt
git clone https://github.com/votre-compte/meta-monitor.git
cd meta-monitor

# 2. Vérifier la structure
ls -la
# → index.html
# → json/
#    ├── agriculture.json
#    ├── army.json
#    ├── culture.json
#    └── ...

# 3. Lancer un serveur local
python -m http.server 8000
# OU
npx serve .
# OU
php -S localhost:8000
```

### Accès

Ouvrez votre navigateur sur :

```
http://localhost:8000/
```

> ⚠️ **Important** : `fetch()` sur `file://` est bloqué par CORS. Vous **devez** utiliser un serveur HTTP local.

---

## 💻 Utilisation

### 1️⃣ Navigation

| Action | Résultat |
|--------|----------|
| **🔍 Barre de recherche** | Recherche full-text dans titres, descriptions, tags, organisations |
| **🌍 Sélecteur de thème** | Filtre par ministère/secteur |
| **📎 Tri** | Par ressources, popularité, récence, titre |
| **🏷️ Catégories (sidebar)** | Filtre par catégorie transverse |
| **📋 Pagination** | 10 / 25 / 50 résultats par page |

### 2️⃣ Analyse d'un jeu de données

1. Cliquez sur une **carte résultat** → passage en mode Expertise
2. Consultez le **score de conformité** et les insights
3. Cliquez sur **🔬 Expertiser** sur chaque ressource pour analyser son contenu
4. Visualisez les **graphiques** générés automatiquement

### 3️⃣ Actions rapides

| Bouton | Fonction |
|--------|----------|
| 🔬 **Tout expertiser** | Analyse toutes les ressources de la page courante |
| 🚨 **Lancer la surveillance** | Scanne les 15 fichiers et remonte les alertes |
| 🔒 **Scanner les PII** | Agrège toutes les PII détectées dans les analyses en cache |
| 📄 **Export PDF** | Génère un rapport PDF du jeu sélectionné |
| 🔀 **Comparer** | Compare les métadonnées avec un autre jeu |

---

## 📂 Structure du projet

```
meta-monitor/
├── index.html              # 🎯 Dashboard complet (fichier unique)
├── README.md               # 📖 Ce fichier
├── json/                   # 📦 Vos fichiers de données
│   ├── agriculture.json
│   ├── army.json
│   ├── culture.json
│   ├── ecologie.json
│   ├── education.json
│   ├── enseignement.json
│   ├── europe.json
│   ├── finances.json
│   ├── industrie.json
│   ├── interieur.json
│   ├── justice.json
│   ├── logements.json
│   ├── santé.json
│   ├── sport.json
│   └── travail.json
└── fetch.py                # 🐍 Script de collecte (optionnel)
```

### Format JSON attendu

```json
{
  "results": [
    {
      "id": "dataset-001",
      "titre": "Nom du jeu de données",
      "description": "Description détaillée…",
      "organisation": "Ministère X",
      "url": "https://…",
      "last_update": "2025-01-15T00:00:00Z",
      "tags": ["tag1", "tag2", "tag3"],
      "popularity": 1234,
      "resources": [
        {
          "title": "Fichier CSV principal",
          "url": "https://exemple.fr/data.csv",
          "format": "csv"
        }
      ]
    }
  ]
}
```

> 💡 **Flexibilité** : le dashboard accepte aussi un tableau racine `[…]` ou une clé `data: […]`.

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    index.html (SPA)                         │
├──────────────┬──────────────────────┬───────────────────────┤
│   SIDEBAR    │       CENTRE         │        DROITE         │
│              │                      │                       │
│  Catégories  │  Recherche + Tri     │  État global          │
│  (10)        │  Onglets             │  Actions rapides      │
│              │  ┌────────────────┐  │  Historique           │
│  Filtres     │  │  Résultats     │  │                       │
│              │  │  Expertise     │  │                       │
│              │  │  Surveillance  │  │                       │
│              │  │  PII           │  │                       │
│              │  └────────────────┘  │                       │
│              │  Pagination          │                       │
└──────────────┴──────────────────────┴───────────────────────┘
                            │
                            ▼
        ┌───────────────────────────────────────┐
        │         Moteur d'analyse              │
        ├───────────────────────────────────────┤
        │  • Parsers : CSV / JSON / XLSX        │
        │  • Stats : types, doublons, outliers  │
        │  • Corrélations (Pearson)             │
        │  • Détection PII (regex)              │
        │  • Score de conformité                │
        └───────────────────────────────────────┘
```

### Technologies

| Couche | Technologie | Rôle |
|--------|-------------|------|
| **UI** | DSFR 1.11.2 | Système de design de l'État |
| **Graphiques** | Chart.js 4.4.0 | Visualisations interactives |
| **XLSX** | SheetJS 0.18.5 | Parsing Excel |
| **PDF** | jsPDF 2.5.1 + AutoTable | Génération de rapports |
| **HTTP** | Fetch API | Chargement des JSON |
| **Stockage** | Map (mémoire) | Cache des analyses |

---

## 🧠 Capacités d'analyse

### 📐 Score de conformité (0–100)

| Critère | Points |
|---------|--------|
| Titre ≥ 10 caractères | +20 |
| Description ≥ 100 car. | +25 |
| Description 30–99 car. | +12 |
| Organisation renseignée | +10 |
| URL HTTPS | +5 |
| ≥ 3 tags | +15 |
| 1–2 tags | +7 |
| Mise à jour < 1 an | +15 |
| Mise à jour < 5 ans | +7 |
| ≥ 1 ressource | +10 |

**Interprétation** :
- 🟢 **70–100** : Conforme
- 🟡 **40–69** : Partiel
- 🔴 **0–39** : Non conforme

### 📊 Statistiques calculées

- **Centralité** : moyenne, médiane, min, max
- **Dispersion** : écart-type, Q1, Q3, IQR
- **Unicité** : nombre de valeurs distinctes, ratio
- **Complétude** : taux de remplissage, cellules vides
- **Aberrations** : méthode IQR (1.5 × IQR)
- **Corrélations** : coefficient de Pearson (|r| > 0.5)

---

## 🎨 Thèmes & Design

Le dashboard reprend la **charte de l'État français** (DSFR) :

| Couleur | Hex | Usage |
|---------|-----|-------|
| 🔵 Bleu France | `#000091` | Primaire, titres |
| 🔴 Rouge Marianne | `#E1000F` | Alertes, accents |
| 🟢 Vert Émeraude | `#00a95f` | Succès |
| 🟡 Jaune Tournesol | `#ffb800` | Avertissements |
| ⚪ Gris 50 | `#f6f6f6` | Fonds |

**Bande Marianne** en haut de page, typographie Marianne, style épuré.

---

## 📊 Formats supportés

| Format | Parseur | Support |
|--------|---------|---------|
| **CSV** | Native | ✅ Auto-détection `,` / `;` |
| **JSON** | Native | ✅ `results[]`, `data[]`, tableau racine |
| **XLSX** | SheetJS | ✅ Première feuille |
| **XLS** | SheetJS | ✅ (legacy) |
| **Autres** | Sniffing | ⚠️ Tentative CSV/JSON |

---

## 🔒 Détection PII

| Type | Criticité | Regex |
|------|-----------|-------|
| Email | 🚨 Critique | RFC 5322 simplifié |
| Téléphone FR | 🚨 Critique | `+33` / `0X XX XX XX XX` |
| IBAN | 🚨 Critique | Format international |
| NIR (sécu) | 🚨 Critique | 15 chiffres |
| SIRET | ⚠️ Info | 14 chiffres |
| SIREN | ⚠️ Info | 9 chiffres |
| Code postal | ⚠️ Info | 5 chiffres |
| Date de naissance | ⚠️ Info | JJ/MM/AAAA |
| IP | ⚠️ Info | IPv4 |
| URL | ⚠️ Info | HTTP(S) |

> ⚠️ **Avertissement** : la détection est basée sur des **regex heuristiques**. Elle peut produire des faux positifs (ex : SIRET vs numéro quelconque). À utiliser comme **premier filtre**, pas comme preuve.

---

## 📄 Export PDF

Le rapport PDF généré contient :

1. **En-tête** : bandeau bleu France + date
2. **Métadonnées** : titre, organisation, ID, dates, score
3. **Description** complète
4. **Tags**
5. **Liste des ressources** (20 premières)
6. **Rapports d'analyse** : pour chaque ressource expertisée
   - Format, taille, lignes, colonnes
   - Doublons, aberrations, PII
7. **Pied de page** : pagination

---

## ⚙️ Configuration

### Ajouter un nouveau fichier JSON

Éditez le tableau `JSON_FILES` dans `index.html` :

```javascript
const JSON_FILES = [
  { file: 'json/agriculture.json',  label: 'Agriculture',   icon: '🌾' },
  { file: 'json/army.json',         label: 'Armée',         icon: '⚔️' },
  // ➕ Ajoutez ici
  { file: 'json/nouveau.json',      label: 'Nouveau',       icon: '🆕' }
];
```

### Personnaliser les catégories

Éditez `CATEGORIES` :

```javascript
const CATEGORIES = [
  { id: 'effectifs', nom: 'Effectifs & RH', icon: '👥',
    keywords: ['effectif', 'recrutement', 'personnel'] },
  // ➕ Ajoutez ici
];
```

### Ajuster la pagination

Dans le `<select id="pageSizeSelect">` :

```html
<option value="25" selected>25 / page</option>
```

---

## 🐛 Dépannage

<details>
<summary><strong>❌ Aucun fichier JSON n'a pu être chargé</strong></summary>

1. Vérifiez que le dossier `json/` existe à la racine
2. Vérifiez que les fichiers contiennent une clé `results` (tableau)
3. Servez via `python -m http.server` (pas `file://`)
4. Ouvrez la console (F12) pour voir les erreurs réseau
</details>

<details>
<summary><strong>⚠️ Erreur CORS</strong></summary>

Le dashboard doit être servi par un **serveur HTTP**. Solutions :
```bash
python -m http.server 8000
npx serve .
php -S localhost:8000
```
</details>

<details>
<summary><strong>🔤 Problème avec santé.json (accent)</strong></summary>

Certains systèmes gèrent mal les accents dans les noms de fichiers. Renommez :
```bash
mv json/santé.json json/sante.json
```
Puis mettez à jour `JSON_FILES` dans `index.html`.
</details>

<details>
<summary><strong>📉 Graphiques vides</strong></summary>

Les graphiques ne s'affichent que pour les ressources **expertisées**. Cliquez sur **🔬 Expertiser** sur au moins une ressource.
</details>

<details>
<summary><strong>🚨 Trop d'alertes</strong></summary>

C'est normal sur des jeux mal renseignés. Utilisez le filtre par thème pour cibler un ministère, ou triez par score de conformité.
</details>

---

## 🤝 Contribuer

Les contributions sont **les bienvenues** !

```bash
# 1. Fork le projet
# 2. Créer une branche
git checkout -b feature/ma-fonctionnalite

# 3. Commit
git commit -m "feat: ajout de ma fonctionnalité"

# 4. Push
git push origin feature/ma-fonctionnalite

# 5. Ouvrir une Pull Request
```

### Idées d'amélioration

- [ ] 🌙 Mode sombre
- [ ] 📱 PWA (offline + install)
- [ ] 💾 Persistance IndexedDB des analyses
- [ ] 🔍 Filtres avancés (score, date, taille)
- [ ] 📤 Export CSV/XLSX des résultats
- [ ] 🌐 Internationalisation (EN, DE, ES)
- [ ] 🤖 Détection auto du schéma (ML)
- [ ] 📊 Comparaison de N jeux simultanés

---

## 📜 Licence

Distribué sous licence **MIT**. Voir [`LICENSE`](LICENSE) pour plus d'informations.

```
MIT License

Copyright (c) 2025 Meta Monitor

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

<div align="center">

## 🙏 Remerciements

**[data.gouv.fr](https://www.data.gouv.fr/)** · **[DSFR](https://www.systeme-de-design.gouv.fr/)** · **[Chart.js](https://www.chartjs.org/)** · **[SheetJS](https://sheetjs.com/)** · **[jsPDF](https://github.com/parallax/jsPDF)**

---

**⭐ Si ce projet vous plaît, n'hésitez pas à lui mettre une étoile ! ⭐**

[![Stars](https://img.shields.io/github/stars/votre-compte/meta-monitor?style=social)](https://github.com/votre-compte/meta-monitor)
[![Forks](https://img.shields.io/github/forks/votre-compte/meta-monitor?style=social)](https://github.com/votre-compte/meta-monitor/fork)

---

**🇫🇷 Liberté · Égalité · Fraternité**

<sub>Fait avec ❤️ en France</sub>

</div>
