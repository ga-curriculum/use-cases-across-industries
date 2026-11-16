# Use Cases Across Industries
**Session Time:** 120 minutes  
**Format:** Instructor-Led  

---

## Prerequisites

- Completion of Sessions 1–4  
- Understanding of core agent components: reasoning engine, memory, tools, feedback loops  
- Familiarity with the agent autonomy spectrum and platform ecosystem  

---

## Learning Objectives

By the end of this session, students will be able to:

1. **Identify** real-world applications of Agentic AI across multiple industries.
2. **Classify** use cases based on autonomy levels and the business value they deliver.
3. **Analyze** how agents interact with business processes, combining reasoning, memory, and tools to deliver outcomes.

> This session bridges theory and practice. Students move from understanding what agents are to understanding what agents do — and why the architectural choices made in previous sessions directly determine business outcomes.

---

## Session Breakdown

| # | Segment | Duration |
|---|---------|----------|
| 1 | Real-World Applications Across Industries | 15 min |
| 2 | Classifying Use Cases by Autonomy and Business Value | 15 min |
| 3 | Deconstructing Agent-Process Interactions | 15 min |
| 4 | Break | 10 min |
| 5 | Lab | 60 min |
| 6 | Wrap-Up & Reflection | 5 min |
|   | **Total** | **120 min** |

---

## 1. Real-World Applications Across Industries (15 min)

### Why Industry Context Matters

Agentic AI is not a single technology applied uniformly — it is a set of architectural patterns that get instantiated differently depending on the data available, the regulatory environment, the risk tolerance, and the business process being automated. The same reasoning loop looks very different in a hospital than in a logistics warehouse.

> This section surveys deployed or actively piloted agentic applications across six industries. For each, we identify the core agent components at work and the business problem being solved.

---

### Healthcare

<img width="896" height="540" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/4f1c2497-5398-41dc-a011-98cd181a3d25" />

---

### Finance

<img width="898" height="532" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/216f9e90-bccb-4a03-9476-f9224af33709" />


---

### Customer Service

<img width="891" height="530" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/9fc3f6f6-c85b-4afc-ad08-48af66e039ef" />

---

### Human Resources

<img width="886" height="535" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/75cff03c-9d27-404f-a51e-c7df58a8176c" />


---

### Logistics and Supply Chain

<img width="889" height="536" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/6458837d-cc3d-4f6f-a9c4-b63767a28645" />


---

### Marketing and Growth

<img width="886" height="536" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/388b28ea-d7dc-4d58-a374-ba644025e729" />


---

## 2. Classifying Use Cases by Autonomy and Business Value (15 min)

### Why Classification Matters

Not all agent deployments are equivalent in scope or risk. Deploying an agent that drafts emails for human review is fundamentally different from deploying one that sends them autonomously. Both have value, but they carry different risks, require different governance structures, and are appropriate for different organizational contexts.

A rigorous classification framework helps teams make informed decisions about how much autonomy to grant an agent before deployment — and when to add human checkpoints.

### The Two-Axis Classification Model

Use cases can be mapped on two axes:

<img width="545" height="180" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/5e26c6a7-00ff-46ed-9967-72c080949fc8" />


### Applying the Classification: Industry Examples

<img width="659" height="238" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/7a9713e9-f4ab-4a1f-bd26-0dac66f70e8b" />



### The Autonomy-Risk Relationship

There is a direct relationship between autonomy level and the governance investment required:

<img width="683" height="93" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/b6218ee6-07ff-4739-90b9-1986b3ead4dc" />


This does not mean high autonomy is bad — it means the decision to grant autonomy must be made deliberately, with commensurate guardrails. An agent running at "Autonomous" level without governance infrastructure is not a more capable system — it is a liability.

A useful heuristic: **start at Supervised, earn Autonomous.** Deploy agents at a lower autonomy level, observe their behavior across a statistically significant number of interactions, measure error rates, and progressively expand their scope of action as confidence in their reliability grows.

---

## 3. Deconstructing Agent-Process Interactions (15 min)

### Agents Do Not Replace Processes — They Participate in Them

A common misconception is that deploying an agent means replacing a business process. In practice, agents are embedded within existing processes — they take over specific steps, augment others, and hand off to humans at defined points. Understanding exactly where the agent sits within the process is the most important design decision.

### The Process Integration Map

For any use case, the agent's role can be mapped across five process stages:

<img width="553" height="201" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/00eca675-6584-40b1-8571-37db09f23839" />

The boundary between "Agent Role" and "Human Role" at each stage is not fixed — it is a design decision that reflects the organization's risk tolerance, regulatory environment, and confidence in the agent's reliability.

### Deep Deconstruction: Customer Service Resolution Agent

Let us walk through a complete agent-process interaction for the customer service use case introduced in Segment 1.

**Trigger:**  
A customer submits a support ticket via chat: *"My order #48291 hasn't shipped after 5 days. I need it by Friday."*

```
TRIGGER → Agent receives message via chat interface webhook
```

**Data Gathering:**  
The agent assembles context before reasoning:

```
Memory retrieval:
  → Customer profile (account since 2021, 3 previous tickets, no prior complaints)
  → Order #48291: placed 5 days ago, current status "processing"
  → Company policy: standard shipping 3–5 business days; expedited available

Tool calls:
  → order_lookup(order_id="48291") → returns status: "processing – warehouse delay"
  → shipping_options(order_id="48291") → returns: "expedited available, +$12"
```

**Reasoning and Decision:**  
The LLM interprets the assembled context:

```
THINK: "The order is delayed due to a warehouse issue, not the customer's fault.
        The customer has a hard deadline (Friday). Standard shipping may not arrive in time.
        Company policy allows waiving expedited fees for warehouse-caused delays.
        Action: offer expedited shipping at no charge, escalate if customer declines."
```

**Execution:**  
The agent calls tools to act on its decision:

```
ACT:
  → shipping_escalation(order_id="48291", type="expedited", fee_waived=true)
  → send_message(channel="chat", content="We've upgraded your shipment to expedited 
     delivery at no charge. Your order will arrive by Thursday. Apologies for the delay.")
  → crm_note(customer_id="C10482", note="Warehouse delay – expedited fee waived per policy")
```

**Logging and Review:**  
```
STORE:
  → Interaction log: full reasoning trace + tool calls + outcome
  → Customer satisfaction survey triggered 24 hours after resolution
  → Escalation rate metric updated: ticket resolved without human intervention
```

### What This Deconstruction Reveals

Walking through this interaction step by step exposes decisions that are invisible in a high-level description:

- The agent needs access to **three separate data sources** (order system, shipping API, CRM) — each requires a configured tool with appropriate permissions
- The fee-waiver decision requires the agent to know company policy — this must be in the **system prompt or a retrievable knowledge base**
- If the warehouse escalation API returns an error, the agent needs a **fallback path** — escalate to human, or inform the customer of the delay without committing to expedited shipping
- Every action is logged — not just the final response, but the **full reasoning trace**, enabling human review and performance improvement

This is the level of specificity required to design a production agent. High-level descriptions obscure the decisions that determine whether the system works.

---

## 4. Break (10 min)

---

## 5. Lab (60 min)

https://ga-curriculum.github.io/use-cases-across-industries/

---

## 6. Wrap-Up & Reflection (5 min)

### Key Takeaways

- Agents Create Outcomes, Not Just Answers
- Autonomy Is a Design Choice, Not a Feature
- Agents Don’t Replace Processes. They Integrate Into Them.

---

> Next session: **Prompts, Intents, and Context**

---

## Resources

- McKinsey Global Institute — *The Economic Potential of Generative AI* (2023)
- [Salesforce — State of Service Report: AI in Customer Service](https://www.salesforce.com/resources/research-reports/state-of-service/)
- [Google DeepMind — Agents in Healthcare: Opportunities and Challenges](https://deepmind.google/research/)
- Lilian Weng — *LLM-powered Autonomous Agents* (2023) — [lilianweng.github.io](https://lilianweng.github.io/posts/2023-06-23-agent/)
- [a16z — The Enterprise AI Adoption Playbook](https://a16z.com/ai/)
- [MIT Sloan — AI in Supply Chain Management](https://mitsloan.mit.edu/ideas-made-to-matter/ai-supply-chain)


---

*General Assembly · Build AI Agents · BAA 5.0 · © 2026*
