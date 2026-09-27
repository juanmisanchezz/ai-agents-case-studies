# AI agents & automation — case studies

Real systems I designed and built for small businesses in Spain (2026): WhatsApp booking agents powered by LLMs, and a custom CRM. Each case explains the problem, the architecture, and the engineering decisions — most of them triggered by real bugs found with real users.

| # | Case | What it is | Stack |
|---|------|-----------|-------|
| 01 | [Beauty salon WhatsApp agent](01-beauty-salon-whatsapp-agent/) | Multi-agent LLM system (router + 2 sub-agents), 215 services, 8 professionals | n8n · Claude Haiku · Supabase · Google Calendar · Evolution API |
| 02 | [Fitness studio booking agent](02-fitness-studio-booking-agent/) | Single LLM agent with tools, waiting list, auto-generated weekly schedules for ~95 clients | n8n · NocoDB/Postgres · Google Calendar · Whapi.Cloud |
| 03 | [Nail salon CRM](03-nail-salon-crm/) | Internal web app with roles, stats and automatic email reminders for ~10 €/year | Lovable · Supabase · Resend |

## Recurring lessons

- **Deterministic first, LLM second.** Anything that can be computed (classification, grouping, dates, prices) is computed in code and handed to the model ready to use. The model writes the reply.
- **Write tools are dangerous.** No blind retries, verify real state before confirming, one execution per conversation at a time.
- **State lives in the database**, not in the model's memory.
- **Test on real channels, but never with real customers' data.**
- **Business constraints are architecture.** Budget, monthly fees and account-ban risk shaped these systems as much as any technical choice.

## About the code

The workflows are n8n JSON files that contain credential references, IDs and customer data, so they are not published. The case studies describe the architecture and the decisions instead.

---

*All client names and personal data have been anonymised.*
