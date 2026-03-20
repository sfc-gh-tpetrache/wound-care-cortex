# Mölnlycke Health Care: Competitive Intelligence POC
## Presentation Script (10 minutes)

---

## Opening (1 min)

**[Address Zlatko's pain point]**

> "Zlatko, you told me: *'We have four business areas and hundreds of products across 100 countries, but I can't tell you in 10 seconds which product lines are winning and which need intervention.'*"

Today I'll show you how we can answer that question in seconds, not months.

**What I built:** A competitive intelligence system using Snowflake Intelligence that lets anyone on our team ask questions in plain English and get instant, auditable answers about our product portfolio performance across European markets.

---

## Demo 1: Competitive Benchmarking (2 min)

**[Zlatko's question]**

**Ask:** "How do our wound care product ratings compare to Smith+Nephew and ConvaTec?"

**Show:**
- Mölnlycke products average vs Smith+Nephew (4.3) and ConvaTec (4.2)
- The rating gap we need to close per product line
- SQL generated for Eric's audit trail

**Talking point:**
> "We're not guessing anymore. This pulls from 250 clinician product reviews across 25 MedTech products. Every answer shows the SQL so Eric can verify the numbers."

---

## Demo 2: Product Performance (2 min)

**[Zlatko's question]**

**Ask:** "Which of our products is underperforming in the European market?"

**Show:**
- Rating breakdown by Mölnlycke product
- Market share trends for each product line
- Comparison to competitors in same category and price tier

**Talking point:**
> "Instead of waiting for quarterly market reports, you can drill into any product line instantly. The system shows both the numbers and the clinician feedback behind them."

---

## Demo 3: Clinician Review Analysis (2 min)

**[Anders's product question]**

**Ask:** "What are the top product quality complaints across our foam dressings?"

**Show:**
- Specific complaint categories (adhesion, conformability, absorbency, cost per change, sizing)
- Actual clinician review quotes as evidence
- Comparison to what Smith+Nephew ALLEVYN and Coloplast Biatain reviews praise

**Talking point:**
> "Anders, this is what you asked for - not just 'ratings are low' but WHICH product has WHICH problem. Is it adhesion, conformability, absorbency, or cost per dressing change? You can use this to prioritise R&D investments."

---

## Demo 4: Category Gap Analysis (2 min)

**[Maria's growth question]**

**Ask:** "Which wound care category has the biggest gap vs competitors?"

**Show:**
- Category-level market share for Mölnlycke products vs competitors
- Growing categories (bioactive wound care, digital wound assessment) where Mölnlycke is underrepresented
- Competitor vulnerability analysis

**Talking point:**
> "Maria, you said: *'Our Safetac technology is genuinely differentiated - clinicians who try it love it. But we're losing the messaging battle in key markets.'* This shows exactly where those messaging gaps are and which categories need attention."

---

## Closing: Auditability (1 min)

**[Address Eric's trust requirement]**

> "Eric, you said: *'We make products that go on patients' wounds. Data accuracy isn't just important - it's a patient safety issue. Any AI system must be explainable, auditable, and traceable to source data.'*"

**Show:**
- Click to reveal SQL behind any answer
- Source data is traceable to specific clinician reviews and product metrics
- No black box - full transparency

**Key point:**
> "Every insight is backed by SQL you can run yourself. Trust but verify."

---

## Summary

| Stakeholder | Question | Answer Time |
|-------------|----------|-------------|
| Zlatko (CEO) | "How do our products compare to competitors?" | < 10 seconds |
| Anders (EVP Wound Care) | "What product issues need fixing?" | < 10 seconds |
| Maria (CPO/Brand) | "Where are the category gaps?" | < 10 seconds |
| Eric (COO) | "Is the data auditable?" | SQL shown instantly |

**Success criteria met:**
- Speed: Instant answers
- Accuracy: SQL-backed, verifiable
- Simplicity: Plain English, no SQL needed
- Trust: Full audit trail
- Actionable: Specific recommendations per product line

---

## Next Steps

1. **Immediate:** Share with market intelligence team for testing
2. **Day 3:** Gather feedback on additional questions
3. **Day 5:** Decision on production implementation with real clinical feedback feeds from MedTech review platforms and hospital procurement systems

**Questions?**

---

## Appendix: Sample Questions to Demo

**CEO (Zlatko):**
- "How do our wound care product ratings compare to Smith+Nephew and ConvaTec?"
- "Which of our product lines is underperforming in the European market?"
- "What would it take to get Mepilex to a 4.5 average rating?"

**EVP Wound Care (Anders):**
- "Which wound care category has the biggest gap vs competitors?"
- "What do clinicians praise about Coloplast Biatain that they don't mention about Mepilex?"
- "Which competitor product is most vulnerable to us taking market share?"

**CPO/Brand (Maria):**
- "How is our brand perceived vs Smith+Nephew in the UK market?"
- "What messaging themes appear in positive competitor reviews but not ours?"

**COO (Eric):**
- "What are the top product quality complaints across our foam dressings?"
- "Which product features should we prioritise in R&D based on clinician feedback?"
- "How do Mepilex Border reviews compare to ConvaTec Aquacel Foam?"

**Follow-up:**
- "How is Mepilex performing compared to ALLEVYN?"
- "What should we improve on Avance Solo NPWT?"
- "Where should we invest - foam dressings or NPWT?"
