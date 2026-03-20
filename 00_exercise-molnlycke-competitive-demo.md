# Exercise: Build the Mölnlycke Competitive Intelligence POC

## Task Checklist

- [ ] **Task 1: Review Your Requirements** (5 min)
  - [ ] Step 1: Review the company background
  - [ ] Step 2: Identify key questions the data must answer

- [ ] **Task 2: Generate POC Database** (20 min)
  - [ ] Step 1: Design the data model
  - [ ] Step 2: Create the database and tables
  - [ ] Step 3: Generate product data (10 Mölnlycke + 15 competitor products)
  - [ ] Step 4: Generate wound care product categories
  - [ ] Step 5: Create product-category mappings
  - [ ] Step 6: Generate 250 clinician product reviews
  - [ ] Step 7: Validate the data

- [ ] **Task 3: Create Semantic View for Cortex Analyst** (10 min)
  - [ ] Step 1: Understand semantic views
  - [ ] Step 2: Generate the semantic view
  - [ ] Step 3: Test Cortex Analyst queries

- [ ] **Task 4: Create Cortex Search Service** (5 min)
  - [ ] Step 1: Understand Cortex Search
  - [ ] Step 2: Create the Search Service
  - [ ] Step 3: Test the Search Service

- [ ] **Task 5: Configure Snowflake Intelligence** (5 min)
  - [ ] Step 1: Understand Snowflake Intelligence
  - [ ] Step 2: Create a Cortex Agent with Multiple Tools
  - [ ] Step 3: Enable the agent in Snowflake Intelligence
  - [ ] Step 4: Test the agent

- [ ] **Task 6: Prepare Your Presentation Script** (5 min)
  - [ ] Generate talking points

---

## Objective

Build a compelling competitive analytics POC featuring **Cortex Analyst** and **Snowflake Intelligence** that you can present to your leadership team at Mölnlycke Health Care.

**Time:** 50 minutes  
**Deliverables:** 
- Working demo database with 25 MedTech products and 250 realistic clinician reviews
- Semantic view for Cortex Analyst
- Snowflake Intelligence chat experience ready for your presentation

---

## Background

You're a Market Intelligence Analyst at Mölnlycke Health Care, a world-leading MedTech company specialising in wound care and surgical solutions. After your requirements gathering meeting with leadership, you need to build a proof-of-concept that demonstrates:
1. Natural language queries for your CEO ("How do our products compare to Smith+Nephew?")
2. Self-service competitive analysis without SQL knowledge
3. Auditable, trustworthy AI-generated insights

**The approach:** Since you can't access live clinical feedback platforms for the POC, you'll create a realistic demo environment based on what you know about the European wound care market.

Your CEO, Zlatko Rihter, said:
> "We have four business areas and hundreds of products across 100 countries, but I can't tell you in 10 seconds which product lines are winning and which need intervention."

---

## Task 1: Review Your Requirements (5 min)

### Step 1: Review the company background

```
Read the company background from assets/customer-brief.md and summarize:
1. Company profile (business areas, revenue, market position)
2. Current competitive environment
3. Key pain points
4. Primary stakeholders and their concerns
```

### Step 2: Identify key questions the data must answer

The POC must answer these stakeholder questions:

**From Zlatko (CEO):**
- "How do our wound care product ratings compare to Smith+Nephew and ConvaTec?"
- "Which of our product lines is underperforming in the European market?"
- "What would it take to get Mepilex to a 4.5 average rating?"

**From Anders (EVP Wound Care):**
- "Which wound care category has the biggest gap vs competitors?"
- "What do clinicians praise about Coloplast Biatain that they don't mention about Mepilex?"

**From Eric (COO):**
- "What are the top product quality complaints across our foam dressings?"
- "Which product features should we prioritise in R&D based on clinician feedback?"

---

## Task 2: Generate POC Database (20 min)

**This is where Cortex Code shines - generating realistic demo data based on your company context.**

### Step 1: Design the data model

Ask Cortex Code to design a schema based on your company's needs:

```
Based on the Mölnlycke company background and the stakeholder questions 
we need to answer, design a Snowflake database schema for our competitive 
intelligence POC. Wait for my approval before proceeding to the next step.

Consider:
- We have 10 key product brands across 4 business areas (Mepilex, Biogel, etc.)
- We track 15 competitor products (ALLEVYN, Aquacel, Biatain, Tegaderm, etc.)
- We need to analyze clinician product reviews, ratings, and sentiment
- Leadership needs competitive benchmarking and product improvement insights

Create dimension and fact tables appropriate for:
1. Product analytics (manufacturer, business area, product category, EU hospital reach)
2. Clinician review analysis (ratings, sentiment, complaints, praise)
3. Competitive benchmarking by product, category, and market

The schema must support answering all stakeholder questions listed in Task 1.

Show me the proposed schema and wait for my confirmation before creating anything.
```

### Step 2: Create the database and tables

```
Create the MOLNLYCKE_DEMO database with the schema you designed.
Use the ANALYTICS schema for the business tables. Wait for my confirmation 
before proceeding to the next step.

Execute the DDL statements to create:
1. DIM_PRODUCTS (MedTech products with attributes)
2. DIM_PRODUCT_CATEGORIES (wound care and surgical product categories)
3. BRIDGE_PRODUCT_CATEGORIES (many-to-many: which products compete in which categories)
4. FACT_PRODUCT_METRICS (quarterly product performance metrics by EU market)
5. REVIEWS (clinician product reviews with ratings and text)

Show me confirmation that each table was created.
```

### Step 3: Generate product data

```
Generate 25 MedTech products for the DIM_PRODUCTS table. Wait for my confirmation 
before proceeding to the next step.

**Our 10 Mölnlycke product brands (IS_MOLNLYCKE_PRODUCT = TRUE):**
1. Mepilex - Foam dressings, Safetac silicone technology, Premium
2. Mepitel - Wound contact layers, atraumatic dressing changes, Premium
3. Exufiber - Gelling fiber dressings, Hydrolock technology, Premium
4. Melgisorb - Silver alginate antimicrobial dressings, Premium
5. Avance Solo - Single-use NPWT, portable negative pressure, Premium
6. Granudacyn - Wound cleansing solution, hypochlorous acid, Mid-Range
7. Biogel - Surgical gloves, puncture indication system, Premium
8. BARRIER - Surgical drapes and gowns, single-use protection, Mid-Range
9. ProcedurePak - Custom procedure trays, OR efficiency, Premium
10. Hibiclens - CHG antiseptic solution, skin preparation, Mid-Range

**15 Competitor products (IS_MOLNLYCKE_PRODUCT = FALSE):**
- Smith+Nephew: ALLEVYN (foam), PICO (NPWT), ACTICOAT (antimicrobial)
- ConvaTec: Aquacel (hydrofiber), Aquacel Foam, Aquacel Ag+ (antimicrobial)
- Coloplast: Biatain (foam), Biatain Ag (antimicrobial)
- Solventum (ex-3M): Tegaderm (film dressings), V.A.C. (NPWT)
- B. Braun: Askina (foam/alginate), Prontosan (wound cleansing)
- Essity/BSN: Cutimed (foam), Jobst (compression)

Include: product_name, manufacturer, headquarters, business_area, product_type, 
price_tier, is_molnlycke_product, primary_category, eu_hospital_count
```

### Step 4: Generate product categories

```
Generate 12 wound care and surgical product categories for DIM_PRODUCT_CATEGORIES. 
Wait for my confirmation before proceeding to the next step.

Categories:
- Wound Care: Foam Dressings, Antimicrobial Dressings, Alginate/Fiber Dressings, Wound Contact Layers, NPWT, Superabsorbent Dressings, Wound Cleansing, Scar Management
- Surgical: Surgical Gloves, Surgical Drapes/Gowns
- Infection Prevention: Antiseptic Solutions, Compression Therapy

Include: category_name, segment, avg_price_eur, growth_trend
```

### Step 5: Create product-category mappings

```
Create bridge table data linking products to the categories they compete in.
Wait for my confirmation before proceeding to the next step.

Rules:
- Broad-range manufacturers (Smith+Nephew, ConvaTec): compete in 4-6 categories
- Specialist brands (Mölnlycke Wound Care): 3-5 categories
- Single-category products (Avance Solo, PICO): 1 category
- Cross-business-area products (Biogel, BARRIER): 1-2 categories
```

### Step 6: Generate 250 clinician product reviews

```
Generate 250 realistic clinician product reviews for the REVIEWS table. 
Wait for my confirmation before proceeding to the next step.

**Distribution:** Major products (Mepilex, ALLEVYN, Aquacel) get 15-20 reviews, others get 6-12

**Rating distribution:**
- Smith+Nephew (ALLEVYN, PICO) average ~4.3 (high performer competitors)
- ConvaTec (Aquacel) / Coloplast (Biatain) average ~4.2 (strong competitors)
- Mölnlycke (Mepilex, Biogel) average ~4.0-4.1 (our key products, room for improvement)
- Other Mölnlycke products average ~3.9-4.0 (competitive but with gaps)

**Review attributes:**
- reviewer_name: Clinical professional names (NurseKathryn_UK, WundExperte_DE, InfirmiereSophie_FR)
- reviewer_country: European countries (UK, Germany, France, Sweden, Netherlands, Spain, Italy)
- reviewer_role: Wound Care Nurse (35%), Tissue Viability Specialist (20%), Surgeon (15%), Procurement Officer (15%), Community Nurse (15%)
- rating: 1-5 stars
- review_date: January 2023 - February 2026
- product_category: matching product's categories
- care_setting: Hospital Acute (40%), Hospital Chronic (25%), Community/Home Care (20%), OR/Surgical (15%)
- wound_type: Surgical wound (25%), Pressure ulcer (20%), Leg ulcer (20%), Diabetic foot ulcer (15%), Burns (10%), Trauma (10%)

**Content themes by product type:**
- Mölnlycke foam (Mepilex): Safetac adhesion comfort, absorbency, conformability, cost per use
- Mölnlycke NPWT (Avance): portability, ease of setup, canister capacity, battery life
- Mölnlycke gloves (Biogel): tactile sensitivity, puncture indication, latex concerns
- Competitors (ALLEVYN): consistent absorption, easy application, established clinical evidence
- Competitors (Aquacel): hydrofiber gelling, vertical wicking, exudate management
- Competitors (Biatain): foam structure, adhesion, cost-effectiveness

Use SNOWFLAKE.CORTEX.COMPLETE to generate review text.
```

### Step 7: Validate the data

```
Run validation queries to confirm:
1. Row counts for all tables
2. Rating distribution shows Mölnlycke products slightly below top competitors
3. All 25 products have reviews
4. Sample review text looks realistic and clinically relevant
5. Quarterly metrics show realistic growth trends

Show me a summary of what was created.
```

---

## Task 3: Create Semantic View for Cortex Analyst (10 min)

### Step 1: Understand semantic views

```
Explain what a Cortex Analyst semantic view is and why it's important 
for natural language queries. How is it different from a YAML semantic model?
Keep it brief - 3-4 sentences.
```

### Step 2: Generate the semantic view

**Note:** Use the `semantic-view-optimization` skill if available for best results.

```
Create a Cortex Analyst semantic view using SQL for the MOLNLYCKE_DEMO 
database. Wait for my confirmation before proceeding. The semantic view should:

1. Include PRODUCTS, REVIEWS, and PRODUCT_METRICS tables
2. Define relationships between tables (foreign keys via PRODUCT_ID)
3. Add business-friendly descriptions and synonyms
4. Define key metrics for competitive analysis

**Required metrics:**
- avg_rating: Average star rating
- review_count: Number of reviews
- total_units_sold: Sum of EU units sold
- total_revenue: Sum of EU revenue
- avg_market_share: Average market share percentage

**Required synonyms:**
- "our products" / "molnlycke products" = IS_MOLNLYCKE_PRODUCT = TRUE
- "competitors" / "competition" = IS_MOLNLYCKE_PRODUCT = FALSE
- "score" / "stars" = rating
- "feedback" / "comments" = reviews
- "hospitals" / "accounts" = EU_HOSPITAL_COUNT

Execute the SQL to create the semantic view.
```

### Step 3: Test Cortex Analyst queries

Test the semantic view with questions leadership will ask:

```
Using the semantic view we just created, test these questions:

1. "How do our product ratings compare to Smith+Nephew and ConvaTec?" (Zlatko's question)
2. "Which of our products is underperforming?" (Zlatko's question)
3. "Which product category has the highest revenue?" (Anders's question)
4. "What is Mepilex's market share trend?" (Anders's question)
5. "Which products have the most reviews?" (general)

For each question, show me:
- The natural language question
- The SQL that Cortex Analyst generated
- The results
```

---

## Task 4: Create Cortex Search Service (5 min)

### Step 1: Understand Cortex Search

```
Explain what Cortex Search is and why it's useful for semantic search over reviews.
How is it different from SQL queries on review text? Keep it to 3-4 sentences.
```

### Step 2: Create the Search Service

```
Create a Cortex Search Service for semantic search over our clinician reviews. 
Wait for my confirmation before executing.

The search service should:
1. Be named PRODUCT_REVIEWS_SEARCH
2. Index the REVIEW_TEXT column for semantic search
3. Include PRODUCT_ID, PRODUCT_CATEGORY, and CARE_SETTING as filterable attributes
4. Include additional columns: REVIEW_ID, REVIEWER_NAME, REVIEWER_COUNTRY, RATING, REVIEW_DATE, REVIEWER_ROLE
5. Use the snowflake-arctic-embed-l-v2.0 embedding model
6. Set TARGET_LAG to '1 day'

Execute the DDL to create the search service.
```

### Step 3: Test the Search Service

```
Test the Cortex Search Service by searching for clinical feedback about our products:

1. First, get the PRODUCT_IDs for our Mölnlycke products (IS_MOLNLYCKE_PRODUCT = TRUE)
2. Search for "complaints about adhesion and conformability on foam dressings" filtered to only our products
3. Show the top 5 results with rating, role, country, and review text

This demonstrates semantic search - finding relevant clinical feedback even when reviews don't contain exact keywords.
```

---

## Task 5: Configure Snowflake Intelligence (5 min)

### Step 1: Understand Snowflake Intelligence

```
What is Snowflake Intelligence and how does it differ from Cortex Analyst? 
How do they work together? Keep it to 3-4 sentences.
```

### Step 2: Create a Cortex Agent with Multiple Tools

**Note:** Use the `agent-optimization` skill if available for best results.

```
Create a Cortex Agent for our Mölnlycke POC with TWO tools:
1. Cortex Analyst (product_analyst) - for structured data queries
2. Cortex Search (review_search) - for semantic search over clinician reviews

Wait for my confirmation before executing SQL. The agent should:

1. Be named "MOLNLYCKE_PRODUCT_ANALYST"
2. Use claude-sonnet-4-5 as the orchestration model
3. Configure product_analyst tool with our semantic view
4. Configure review_search tool with our Cortex Search Service
5. Set max_results to 10 for the search tool

**Agent instructions:**
"You help analyze MedTech product competitive intelligence for Mölnlycke 
Health Care across European markets. Use the analyst tool for data queries 
(ratings, metrics, market share comparisons). Use the search tool to find 
specific clinician reviews or product feedback. Our products have 
IS_MOLNLYCKE_PRODUCT=TRUE, competitors have IS_MOLNLYCKE_PRODUCT=FALSE."

**Response instructions:**
"Be concise and data-driven. When discussing reviews, include relevant clinician 
quotes. Always specify product names and manufacturers rather than just IDs."

Execute the CREATE AGENT DDL.
```

### Step 3: Enable the agent in Snowflake Intelligence

```
Make the Mölnlycke Product Analyst agent available in Snowflake Intelligence.
Wait for my confirmation before executing grants.

1. Grant USAGE on the agent to PUBLIC (or a specific role)
2. Add the agent to the Snowflake Intelligence object
3. Verify it was added successfully

Execute all SQL.
```

### Step 4: Test the agent

```
Test the agent with executive-style questions that Zlatko, Anders, and Eric 
might ask:

1. "How do our product ratings compare to Smith+Nephew and ConvaTec?" (uses: analyst tool)
2. "What are the top complaints about Mepilex foam dressings?" (uses: search tool)
3. "Which wound care category has the biggest gap vs competitors?" (uses: analyst tool)

Show me the SQL for each response (Eric needs auditability).
```

---

## Task 6: Prepare Your Presentation Script (5 min)

### Generate talking points

```
Based on my customer brief and stakeholder questions, create a 10-minute 
presentation script that:

1. Opens with Zlatko's pain point (can't tell which products are winning)
2. Shows competitive benchmarking answering his question in seconds
3. Demonstrates clinician review analysis for Anders's question
4. Shows category gap analysis for Maria
5. Addresses Eric's concern about auditability (show the SQL)
6. Ends with specific recommendations for Mölnlycke

Format as brief talking points with the exact queries to run.
Reference specific quotes from the customer brief.
```

---

## Validation Checklist

Before proceeding, verify:

- [ ] MOLNLYCKE_DEMO database created with all tables
- [ ] 25 products loaded (10 Mölnlycke + 15 competitors with IS_MOLNLYCKE_PRODUCT flag)
- [ ] 250 reviews with clinically relevant product review content
- [ ] Rating distribution: Smith+Nephew ~4.3, Mölnlycke ~4.0-4.1
- [ ] Quarterly metrics show realistic market growth trends
- [ ] Semantic view created and responding to natural language
- [ ] Generated SQL is correct and auditable
- [ ] Cortex Search Service created (PRODUCT_REVIEWS_SEARCH)
- [ ] Cortex Agent created with TWO tools (analyst + search)
- [ ] Agent enabled in Snowflake Intelligence
- [ ] Can answer all stakeholder questions from Task 1

---

## Key Stakeholder Questions - Data Requirements

| Question | Required Data | Agent Tool Used |
|----------|---------------|------------------|
| "How do our product ratings compare to Smith+Nephew?" | avg_rating by product, IS_MOLNLYCKE_PRODUCT flag | **Analyst** (structured query) |
| "Which of our products is underperforming?" | avg_rating by Mölnlycke product | **Analyst** (structured query) |
| "Which wound care category has the biggest gap?" | category, product, market share | **Analyst** (structured query) |
| "What are the top complaints about our foam dressings?" | review_text semantic search | **Search** (semantic search) |
| "Which features should we prioritise in R&D?" | review_text sentiment analysis | **Search** (semantic search) |
| "What is Mepilex's market share trend?" | quarterly metrics time series | **Analyst** (structured query) |
| "How do Mepilex reviews compare to ALLEVYN?" | review_text, rating by product | **Both** (analyst + search) |
| "What do clinicians praise about competitors?" | review_text semantic search | **Search** (semantic search) |

---

## Key Takeaways

1. **Context is everything** - Your company knowledge drives realistic demos
2. **Cortex Code generates data** - No need to manually create sample datasets
3. **Semantic views are the foundation** - They teach AI how to query your data correctly
4. **Test with real questions** - Use actual questions from your stakeholders
5. **Show the SQL** - Builds trust with skeptical stakeholders like Eric

---

## Pro Tips

1. **Make it personal** - Use "our products" vs "competitors" throughout
2. **Include realistic weaknesses** - Mölnlycke products should have fixable gaps vs market leaders
3. **Show the opportunity** - Data should reveal clear category and product improvement areas
4. **Match product names** - Use real product and manufacturer names for credibility
5. **Test edge cases** - What if a category has no Mölnlycke product? Empty results?

---

## Next Steps

After completing this exercise, you can:
1. Present to Zlatko, Anders, Maria, and Eric
2. Iterate based on their feedback
3. Plan production implementation with real clinical feedback feeds from MedTech review platforms and hospital procurement systems
