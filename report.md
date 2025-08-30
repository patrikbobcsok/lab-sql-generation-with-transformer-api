
# Report: SQL Generation with Transformer API

## Overview
This exercise explored how a transformer model (SQLCoder) generates SQL queries from natural language prompts using a fixed database schema. I tested multiple prompt variations, compared outputs, and evaluated accuracy, hallucinations, and reliability.

---

## Prompt Variations & Results
1) Revenue by Product (NY, last month): ✅ Mostly correct (formula ok; date window ambiguous).

2) Top Customers by Revenue (last quarter): ❌ Wrong (used s.price; missing join to products; quarter logic off).

3) Top Salespeople by Revenue (this year): ✅ Correct joins and formula; better to group by salesperson_id too.

4) Invalid Column Test (delivery_time): ❌ Hallucination — referenced non-existent column instead of 'I do not know'.

---

## Key Learnings
- Clear, schema-anchored prompts work better.
- Model can hallucinate if asked about missing columns.
- Time periods like “last month/quarter” need explicit bounds.
- Always validate generated SQL against schema.

---

## Conclusion
The model is useful, but only with strict prompts and validation.
