# Mölnlycke Health Care Competitive Intelligence POC

Build a competitive analytics proof-of-concept for **Mölnlycke Health Care** using Snowflake Cortex.

## What We're Building
A demo environment with 25 MedTech products (10 Mölnlycke + 15 competitors) and 250 clinician reviews, enabling natural language queries for executive decision-making in the European wound care and surgical products market.

## Key Components
1. **POC Database** - Dimension tables (products, categories) + fact tables (product metrics, reviews)
2. **Semantic View** - Cortex Analyst integration for natural language queries
3. **Cortex Search** - Semantic search over clinician product reviews
4. **Cortex Agent** - Combined analyst + search in Snowflake Intelligence

## Business Context
- **Company**: Mölnlycke Health Care (4 business areas, EUR 2,064M revenue)
- **Challenge**: Mölnlycke products average ~4.1 rating vs Smith+Nephew at ~4.3
- **Goal**: Identify product gaps, category opportunities, and R&D priorities

## Time: ~50 minutes
See `00_exercise-molnlycke-competitive-demo.md` for detailed step-by-step instructions.
