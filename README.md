# TCM Knowledge Base — Obsidian Vault for RAG & AI

A structured knowledge base built in [Obsidian](https://obsidian.md/) covering Traditional Chinese Medicine (TCM): acupuncture, herbal medicine, diagnostics, dietary therapy, and aromatherapy. Designed from the ground up to be **RAG-ready** — every note uses consistent YAML frontmatter, wiki-link graphs, and semantic tagging so the vault can be embedded and queried by AI systems.

> **This repository shows the project structure and sample formats only.** The full vault (4,400+ notes) is private.

---

## Vault at a Glance

| Metric | Value |
|---|---|
| Total notes | 4,400+ |
| Expert sources integrated | 25 |
| Acupuncture points mapped | 1,280+ (across 2 independent atlases) |
| Treatment protocols | 245 |
| Herbal monographs (TCMwiki) | 303 |
| Food-as-medicine entries | 99 |
| Aromatherapy monographs | 25 |
| Molecular cross-references | LOTUS, PharmGKB, CPIC, M2OR |

## What Makes It RAG-Ready

- **Consistent YAML frontmatter** on every note — structured fields for temperature, taste, meridians, effects, cross-references
- **Wiki-link graph** — `[[note-name]]` links create a navigable knowledge graph between herbs, acupoints, diseases, and treatment schemes
- **Semantic chunking** — each note is one concept (one herb, one acupoint, one disease protocol) at an optimal size for embedding
- **Standardized taxonomies** — meridian codes (P, GI, E, RP, C, IG, V, R, MC, TR, VB, F, VG, VC), effect tags, body-region tags
- **Multi-source cross-referencing** — the same acupoint or herb is linked across different expert sources, enabling consensus queries

## Source Material & Processing Pipeline

```
Raw Sources                    Processing                    Vault Notes
─────────────                  ──────────                    ───────────
PDF books (OCR) ──────────►    PDFgear / pdftotext ──►       Structured .md
Video lectures ──────────►     Whisper transcription ──►     with YAML frontmatter
Web databases  ──────────►     Custom Python parsers ──►     + wiki-links
Clinical courses ────────►     Claude AI extraction ──►      + tag taxonomy
Molecular DBs  ──────────►     TSV/JSON normalization ──►    + molecular layer
```

## Repository Structure

```
.
├── 01-Glikman/              # 669 notes — Acupuncture courses (2 courses, 20 sessions)
│   ├── Course-1/            #   10 sessions, lecture notes + clinical protocols
│   ├── Course-2/            #   10 sessions, disease treatment algorithms
│   └── Atlas/               #   Acupuncture zone atlas
│
├── 02-Dubrovin/             # 57 notes — Classical TCM texts & diagnostics
│   └── Knowledge-Base/
│       ├── 00-Indexes/
│       ├── 01-Theory/       #   Fundamental TCM theory
│       ├── 02-Classical-Texts/  # Nan Jing, classical references
│       ├── 03-Diagnostics/  #   Pulse, tongue, face diagnostics
│       ├── 04-Pathology/    #   Zang-Fu pathology patterns
│       └── 05-Treatment/    #   Treatment principles
│
├── 03-Alanov/               # 63 notes — Jing-Luo channel theory
│   ├── Theory-TCM/          #   Transport points, Luo channels, Jin-Jin
│   └── Slipbox-Cards/       #   Zettelkasten-style atomic notes
│
├── 04-Fedorov/              # 58 notes — Pulse, tongue & face diagnostics (4 volumes)
├── 05-Osipov/               # Wu-Xing (Five Elements) system
├── 06-Upur-Nachatoy/        # Syndrome differentiation
├── 07-Maciocia/             # Western TCM textbook reference
│
├── 08-Belousov/             # 773 notes — Largest single source
│   ├── Theory-Foundations/  #   9 chapters: Yin-Yang, Wu-Xing, Qi, Zang-Fu, 8 Principles
│   ├── Disease-Treatment/   #   42 disease protocols
│   ├── Zhen-Jiu-Vol1/       #   14 meridians + extra points
│   ├── Methods-Techniques/  #   9 needles, stimulation, moxibustion, cupping
│   ├── Cultivated-Plants-Vol1/  # Grains, legumes, sesame
│   ├── Cultivated-Plants-Vol2/  # Vegetables (12 chapters)
│   └── Cultivated-Plants-Vol3/  # Fruits & mushrooms (10 chapters)
│
├── 09-Nachatoy-Dif/         # Differential diagnosis
├── 10-Muzhikov/             # Akabane diagnostics + IR treatment
├── 12-Simonov/              # Quantitative pulse (Nan Jing), Yi Jing hexagrams
│
├── 14-TCMwiki/              # 303 herbal monographs
│   ├── 01_exterior-releasing/   # Wind-cold & wind-heat herbs
│   ├── 02_heat-clearing/        # Fire-purging, damp-heat, toxic-heat
│   ├── ...                      # 20 functional categories
│   └── 20_external-use/
│
├── 15-FoodWiki/             # 99 food-as-medicine entries
│   ├── 01_grains/
│   ├── 02_vegetables/
│   ├── ...                  # 11 food categories
│   └── 11_beverages/
│
├── 16-Kirschbaum/           # Tongue diagnosis (13 chapters)
├── 17-Lednev/               # Electropuncture + disease index
├── 18-Vasilenko/            # TCM methodology (Qi, channels, standard points)
├── 19-Khudovekov/           # Pediatric TCM (complete)
├── 20-Glikman-Atlas/        # Acupuncture zone atlas (12 zones)
│
├── 21-Eledia/               # 888 notes — Acupoint atlas + treatment schemes
│   ├── Acupoint-Atlas/      #   642 points across 16 meridians + extra points
│   │   ├── P-Lungs/
│   │   ├── GI-Large-Intestine/
│   │   ├── ...              #   14 regular + 2 extraordinary meridians
│   │   ├── PC-Extra-Points/
│   │   └── NT-New-Points/
│   └── Treatment-Schemes/   #   245 disease protocols
│       ├── Respiratory/     #     Cough, asthma, bronchitis, pneumonia
│       ├── Cardiovascular/  #     Hypertension, arrhythmia
│       ├── Digestive/       #     Gastritis, constipation, liver disorders
│       ├── Neurological/    #     Headache, neuralgia, paralysis
│       ├── Musculoskeletal/ #     Arthritis, back pain, cervical spondylosis
│       ├── Gynecology/      #     Menstrual disorders, infertility
│       ├── Dermatology/     #     Eczema, psoriasis, acne
│       ├── ENT/             #     Tinnitus, rhinitis, sinusitis
│       ├── Ophthalmology/   #     Myopia, conjunctivitis
│       └── Pediatric/       #     Childhood conditions
│
├── 22-Kiberis/              # 642 points — Second independent acupoint atlas
├── 23-AromaEmotions/        # 26 notes — Essential oils (3 books, 160+ oils)
│
├── 24-MedDatabases/         # Molecular & pharmacogenomic cross-references
│   ├── HERB/                #   Herb–compound–target database
│   ├── LOTUS/               #   659K natural product–organism pairs
│   ├── PharmGKB/            #   Pharmacogenomics annotations
│   ├── CPIC/                #   Clinical pharmacogenetics guidelines
│   ├── M2OR/                #   79K molecule–olfactory receptor pairs
│   └── BATMAN-TCM/          #   TCM ingredient–target–disease network
│
├── 25-Electropuncture/      # 22 notes — Electroacupuncture theory & devices
│
├── _templates/              # 9 note templates
├── _workflow/               # Processing pipeline documentation
│
└── samples/                 # ← Sample notes demonstrating data formats
    ├── sample-herb.md       #   Herbal monograph with molecular layer
    ├── sample-acupoint.md   #   Acupuncture point card
    ├── sample-treatment-scheme.md  # Disease treatment protocol
    └── sample-food.md       #   Food-as-medicine entry
```

## Note Formats

The vault uses four primary note types, each with structured YAML frontmatter. See the [`samples/`](samples/) directory for full examples.

### Herbal Monograph
```yaml
name_zh: "白芷"
name_pinyin: "Bái Zhǐ"
temperature: "warm"
taste: ["acrid"]
meridians: ["Lungs", "Stomach"]
effects: ["disperses-wind-cold", "opens-nasal-passages"]
molecular_layer:
  lotus_compounds: ["imperatorin", "isoimperatorin"]
  target_genes: ["CYP1A2", "CYP2C9"]
```

### Acupuncture Point
```yaml
point_id: "P10"
name_pinyin: "Yú Jì"
international_code: "LU-10"
meridian: "P — Lungs"
classification: "Ying-Spring point (Fire)"
```

### Treatment Scheme
```yaml
disease: "Cough"
category: "Respiratory"
point_count: 18
body_regions: ["chest", "back", "upper-limb", "lower-limb"]
```

### Food-as-Medicine
```yaml
name_zh: "粳米"
temperature: "neutral"
taste: ["sweet"]
meridians: ["Spleen", "Stomach"]
effects: ["tonifies-qi", "strengthens-spleen"]
```

## Technology Stack

| Tool | Purpose |
|---|---|
| **Obsidian** | Primary editor, graph visualization, daily workflow |
| **Claude AI** | Content extraction, structuring, YAML generation |
| **Python** | Custom parsers for web databases and PDF processing |
| **PDFgear / pdftotext** | OCR and text extraction from scanned books |
| **Whisper (pywhispercpp)** | Speech-to-text for video lecture transcription |
| **LOTUS / PharmGKB / CPIC** | Molecular and pharmacogenomic enrichment |

## Use Cases

- **RAG-powered clinical assistant** — embed the vault, query by symptom pattern or herb name, get structured treatment recommendations with source citations
- **Cross-reference engine** — "Which herbs targeting CYP2C9 are used for Wind-Cold patterns?" combines molecular data with TCM classification
- **Treatment protocol lookup** — structured acupoint prescriptions organized by disease category and body region
- **Educational resource** — 25 expert sources cross-linked into a unified graph

## Building a Vault Like This

I offer this as a professional service — transforming your raw texts, PDFs, lectures, and notes into a structured, RAG-ready Obsidian vault. See my [Fiverr gig](https://www.fiverr.com/olegokeev) for details.

## License

This repository contains the project structure and sample data formats only. The full knowledge base content is proprietary and not included.

Structure and samples: MIT License.
