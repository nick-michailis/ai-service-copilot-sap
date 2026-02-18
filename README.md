# demo3-ai-service-copilot
AI Service Co-Pilot (Sales + Industrial Focus) built in n8n.  
Turns incoming industrial service cases into a structured AI analysis and generates an executive-ready HTML service ticket.

---

## 🚀 What this demo does

**Input:**  
A service case event (e.g., from SAP, MES, Shopfloor system, form or dispatcher)

**Output:**
- AI-based priority (1–5) + category
- probable root cause + recommended actions
- sales opportunity detection + upsell hint
- professional HTML email ticket with SAP-ready subject line

This demo connects service intelligence with commercial awareness in one automated flow.

---

## 🧠 Architecture

```mermaid
flowchart LR
  A[Webhook<br/>/demo3-service<br/>POST Service Case] --> B[Set<br/>Normalize Payload<br/>case_id, customer, asset, problem, impact]
  B --> C[OpenAI Chat Model<br/>Industrial Service Analysis<br/>+ Sales Opportunity]
  C --> D[Code (JS)<br/>Parse strict JSON]
  D --> E[Set<br/>Build summary + sales_note<br/>Pass-through identifiers]
  E --> F[Gmail<br/>Send HTML Ticket Email<br/>SAP-ready subject]
