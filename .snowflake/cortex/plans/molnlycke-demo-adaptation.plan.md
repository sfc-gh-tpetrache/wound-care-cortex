# Plan: Adapt Demo for Molnlycke Health Care

## Context

We have an existing Pon.Bike competitive intelligence demo that uses Snowflake Cortex (Analyst, Search, Agent) to analyze bicycle brand reviews in the Dutch market. We need to adapt all assets for **Molnlycke Health Care**, a world-leading MedTech company focused on wound care and surgical solutions.

### Key Molnlycke Facts (from research)
- **Founded:** 1849, Gothenburg, Sweden
- **Owner:** Investor AB (Patricia Industries)
- **Revenue:** EUR 2,064M (2024), 7.4% growth
- **Employees:** ~9,000
- **Operations:** 100+ countries
- **CEO:** Zlatko Rihter (since 2020)

### Four Business Areas
1. **Wound Care** (EVP: Anders Andersson) -- Mepilex, Mepitel, Exufiber, Melgisorb, Avance, Granudacyn
2. **OR Solutions** (EVP: Fredrik Wallefors) -- BARRIER, ProcedurePak, Easywarm
3. **Gloves** (EVP: Katriina Oberg) -- Biogel range
4. **Antiseptics** (EVP: Lina Karlsson) -- Hibiclens, Hibiscrub

### Key Competitors
| Competitor | Strength | Focus |
|-----------|----------|-------|
| Smith+Nephew | Global wound care leader, advanced wound management | Foam dressings, NPWT |
| Solventum (ex-3M) | Scale, brand recognition, Tegaderm | Film dressings, tapes |
| ConvaTec | Strong in advanced wound care, Aquacel | Hydrofiber technology |
| Coloplast | Nordic competitor, strong in chronic wounds | Biatain foam range |
| B. Braun | German engineering, broad portfolio | Askina range |
| Essity (BSN Medical) | Compression, traditional wound care | Cutimed, Jobst |
| Paul Hartmann | German, strong in Europe | Zetuvit, Hydroclean |
| Medline | US distribution giant, private label | Value segment |

---

## Files to Change

### 1. [assets/customer-brief.md](assets/customer-brief.md) (START HERE -- review first)

**Key changes:**
- Replace Pon.Bike company profile with Molnlycke Health Care
- 4 business areas instead of 9 bicycle brands
- Key product brands within each business area (Mepilex, Biogel, etc.)
- European healthcare market context (not Dutch bicycle market)
- Revenue EUR 2,064M, ~9,000 employees, 100+ countries

**Proposed stakeholders:**

| Role | Name | Focus | Pain Point |
|------|------|-------|------------|
| CEO | Zlatko Rihter | Portfolio strategy, growth, acquisitions | "I need to see which product lines are gaining vs losing ground against competitors across Europe in real time" |
| EVP Wound Care | Anders Andersson | Product performance, market positioning | "We have 49 wound care products but I can't quickly tell which ones clinicians prefer over Smith+Nephew or ConvaTec" |
| CPO / Brand | Maria Morin | Brand perception, employer/product brand | "Our Safetac technology is differentiated but competitor messaging is winning in key European markets" |
| COO | Eric De Kesel | Quality, operations, sustainability | "Product complaints need to reach manufacturing faster -- we're losing months between feedback and action" |

**Proposed competitive environment:**
- Wound care market ~USD 25B globally, growing 5-6% annually
- Premium positioning challenged by value brands and generics
- Key battle: foam dressings (Mepilex vs Biatain vs Aquacel vs Tegaderm)
- NPWT growing fast (Avance Solo vs Smith+Nephew PICO vs KCI/3M)
- Sustainability becoming a procurement criterion

**Product categories for the demo (replacing bike categories):**
1. Foam Dressings (bordered + non-bordered)
2. Antimicrobial Dressings
3. Alginate/Fiber Dressings
4. Wound Contact Layers
5. Negative Pressure Wound Therapy (NPWT)
6. Compression Therapy
7. Superabsorbent Dressings
8. Wound Cleansing
9. Surgical Gloves
10. Antiseptic Solutions
11. Surgical Drapes/Gowns
12. Scar Management

**Reviewer personas (replacing Dutch cyclists):**
- Hospital wound care nurses (UK, Germany, France, Nordics, Benelux)
- Tissue viability specialists
- Surgical teams
- Procurement officers
- Community/home care nurses

**Geography:** European markets (UK, Germany, France, Sweden, Netherlands, Spain, Italy)

### 2. [00_exercise-pon-competitive-demo.md](00_exercise-pon-competitive-demo.md)

Rename to `00_exercise-molnlycke-competitive-demo.md`. Major updates:
- Replace all Pon.Bike context with Molnlycke
- Update stakeholder questions to wound care domain
- Update data model (DIM_PRODUCTS instead of DIM_BRANDS, product categories for MedTech)
- Update review generation prompts for healthcare professionals
- Update database name: `MOLNLYCKE_DEMO.ANALYTICS`
- Update agent name: `MOLNLYCKE_PRODUCT_ANALYST`

**Sample stakeholder questions:**
- Zlatko: "How do our wound care product ratings compare to Smith+Nephew and ConvaTec?"
- Anders: "Which product category has the biggest gap vs competitors?"
- Maria: "What do clinicians praise about Coloplast that they don't mention about us?"
- Eric: "What are the top product quality complaints across our foam dressings?"

### 3. [01-ingestion.ipynb](01-ingestion.ipynb)

Adapt all 20 cells:
- Replace bicycle brands with Molnlycke product lines + competitor products
- Replace bike categories with wound care product categories
- Replace Dutch cyclist reviewers with European healthcare professionals
- Update rating distributions (Molnlycke ~4.1, Smith+Nephew ~4.3, etc.)
- Update review content themes (clinical efficacy, ease of use, conformability, adhesion, cost-effectiveness)

### 4. [02-data-agent.ipynb](02-data-agent.ipynb)

Adapt all 19 cells:
- Update semantic view for wound care domain
- Update Cortex Search service for clinical product reviews
- Update agent instructions for MedTech context
- Update test queries

### 5. [03-presentation-script.md](03-presentation-script.md)

Rewrite with:
- Zlatko's opening pain point
- Wound care competitive benchmarking demo
- Product review analysis for Anders
- Category gap analysis for Maria
- Quality/auditability for Eric
- MedTech-specific recommendations

### 6. [README.md](README.md)

Update summary for Molnlycke context.

---

## Execution Order

We start with the customer brief (Task 1) since you want to review it before proceeding. After your approval, we update the remaining files in order.