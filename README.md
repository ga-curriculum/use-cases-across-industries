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
| 1 | Real-World Applications Across Industries | 10 min |
| 2 | Classifying Use Cases by Autonomy and Business Value | 20 min |
| 3 | Deconstructing Agent-Process Interactions | 15 min |
| 4 | Break | 10 min |
| 5 | Lab | 60 min |
| 6 | Wrap-Up & Reflection | 5 min |
|   | **Total** | **120 min** |

---

## 1. Real-World Applications Across Industries (10 min)

### Why Industry Context Matters

Agentic AI is not a single technology applied uniformly — it is a set of architectural patterns that get instantiated differently depending on the data available, the regulatory environment, the risk tolerance, and the business process being automated. The same reasoning loop looks very different in a hospital than in a logistics warehouse.

This section surveys deployed or actively piloted agentic applications across six industries. For each, we identify the core agent components at work and the business problem being solved.

---

### Healthcare

**Use Case: Clinical Documentation and Decision Support**

In clinical settings, agents are being deployed to reduce the administrative burden on clinicians — one of the leading causes of burnout in the industry. An agent listens to patient-provider conversations via audio transcription, retrieves the patient's EHR history, drafts structured clinical notes in the provider's preferred format, and flags potential drug interactions or missing diagnostic information before the note is finalized.

| Component | Role in This Use Case |
|---|---|
| Reasoning Engine | Interprets conversation transcripts, identifies clinically relevant information, drafts notes |
| Memory | Retrieves patient history across visits from EHR integration |
| Tools | Audio transcription API, EHR read/write, drug interaction database, alert system |
| Feedback Loop | Clinician corrections to drafts are logged and used to refine future note quality |

**Business value:** Reduces documentation time per patient visit by 30–50%; increases note completeness; allows clinicians to spend more time in patient-facing care.

**Key constraint:** HIPAA compliance requires all data to remain within approved infrastructure. The agent cannot use third-party hosted LLMs unless they are covered under a Business Associate Agreement.

---

### Finance

**Use Case: Autonomous Compliance Monitoring**

Financial institutions are deploying agents to continuously monitor transactions, regulatory filings, and internal communications for compliance violations — a task previously handled by large teams of analysts. The agent ingests structured transaction data and unstructured text (emails, chat logs, filings), cross-references against current regulatory rules, flags anomalies, generates preliminary investigation reports, and routes high-confidence violations to human reviewers.

| Component | Role in This Use Case |
|---|---|
| Reasoning Engine | Classifies transactions and communications against regulatory rule sets |
| Memory | Long-term store of flagged patterns and previous case outcomes |
| Tools | Transaction database, regulatory rule engine, document parser, case management API |
| Feedback Loop | Reviewer decisions (confirmed violation vs. false positive) update the agent's classification confidence |

**Business value:** Reduces analyst time spent on low-confidence reviews by 60–70%; improves detection coverage; creates auditable decision trails required by regulators.

**Key constraint:** Every agent decision must be explainable and logged. Black-box reasoning is unacceptable in a regulated environment — this is why LangGraph's explicit state management and observability are particularly well-suited here.

---

### Customer Service

**Use Case: Intelligent Tier-1 Support Resolution**

Rather than routing every inbound query to a human agent, organizations are deploying agentic systems that can resolve a defined set of support scenarios end-to-end: order status, refund processing, account updates, subscription changes, and basic troubleshooting. The agent retrieves customer data, executes the resolution action, and escalates to a human only when the scenario falls outside its defined scope.

| Component | Role in This Use Case |
|---|---|
| Reasoning Engine | Classifies intent, selects resolution path, drafts customer-facing responses |
| Memory | Customer history, previous tickets, account preferences |
| Tools | CRM, order management system, refund API, escalation trigger, email/chat interface |
| Feedback Loop | Customer satisfaction scores and escalation rates drive prompt and routing adjustments |

**Business value:** Resolution without human involvement for 40–60% of inbound volume; faster resolution times; 24/7 availability without staffing cost.

**Key constraint:** The agent must know when not to act. A well-designed escalation path is as important as the resolution logic — agents that over-automate in customer service destroy trust rapidly.

---

### Human Resources

**Use Case: Talent Acquisition Pipeline Automation**

Recruiting agents are being deployed to handle the top-of-funnel stages of hiring: screening inbound applications against job requirements, scheduling interviews, sending status updates to candidates, and generating structured summaries for hiring managers. More advanced deployments include sourcing — the agent proactively identifies potential candidates from professional networks based on the role's competency profile.

| Component | Role in This Use Case |
|---|---|
| Reasoning Engine | Matches candidate profiles to role requirements, generates assessment summaries |
| Memory | Candidate database, past hiring decisions, role-specific scoring criteria |
| Tools | ATS integration, calendar API, LinkedIn/sourcing API, email system |
| Feedback Loop | Hiring manager feedback on candidate quality refines future screening criteria |

**Business value:** Reduces time-to-first-interview by 50–70%; ensures consistent application of screening criteria; frees recruiters for relationship-intensive work.

**Key constraint:** Automated screening carries significant bias risk. Agents trained on historical hiring data may perpetuate historical biases. Human review of screening decisions is a governance requirement, not an optional enhancement.

---

### Logistics and Supply Chain

**Use Case: Dynamic Inventory and Fulfillment Optimization**

Logistics agents monitor real-time inventory levels across warehouse locations, predict stockout risk based on demand signals (sales velocity, seasonal patterns, promotional calendars), generate purchase orders, coordinate with suppliers via API, and reroute fulfillment when a warehouse is over-capacity or a shipment is delayed.

| Component | Role in This Use Case |
|---|---|
| Reasoning Engine | Forecasts demand, identifies reorder triggers, selects optimal fulfillment path |
| Memory | Historical demand data, supplier lead times, warehouse capacity records |
| Tools | Inventory management system, ERP, supplier APIs, shipping carrier APIs, alerting system |
| Feedback Loop | Actual vs. predicted demand updates the agent's forecasting model over time |

**Business value:** Reduces stockout incidents by 20–35%; decreases excess inventory carrying cost; accelerates response to supply chain disruptions.

**Key constraint:** The agent must not place orders autonomously above a defined value threshold without human approval. High-value procurement decisions require explicit human-in-the-loop checkpoints.

---

### Marketing and Growth

**Use Case: Personalized Campaign Orchestration**

Marketing agents are deployed to manage multi-channel campaign execution at a level of personalization that would be impossible to achieve manually. The agent segments audiences based on behavioral signals, selects content variants for each segment, schedules and distributes campaigns across channels (email, paid, social), monitors engagement metrics in real time, and adjusts spend allocation based on performance.

| Component | Role in This Use Case |
|---|---|
| Reasoning Engine | Interprets engagement data, selects content and channel strategies, generates copy variants |
| Memory | Customer behavioral history, campaign performance records, segment definitions |
| Tools | CRM, ad platform APIs (Meta, Google), email platform, analytics API, A/B testing framework |
| Feedback Loop | Engagement metrics (open rate, CTR, conversion) drive real-time reallocation of budget and content |

**Business value:** Increases campaign ROI by 15–40% through personalization at scale; reduces manual campaign management overhead; enables continuous experimentation without analyst bottlenecks.

**Key constraint:** Autonomous ad spend management requires strict budget guardrails and human approval for spend above defined thresholds. Unconstrained agents can exhaust budgets or make purchases that violate brand safety policies.

---

## 2. Classifying Use Cases by Autonomy and Business Value (20 min)

### Why Classification Matters

Not all agent deployments are equivalent in scope or risk. Deploying an agent that drafts emails for human review is fundamentally different from deploying one that sends them autonomously. Both have value, but they carry different risks, require different governance structures, and are appropriate for different organizational contexts.

A rigorous classification framework helps teams make informed decisions about how much autonomy to grant an agent before deployment — and when to add human checkpoints.

### The Two-Axis Classification Model

Use cases can be mapped on two axes:

**Axis 1: Autonomy Level** — how much the agent can do without human involvement

| Level | Description | Example |
|---|---|---|
| **Assisted** | Agent suggests; human decides and acts | Drafts a response for agent review |
| **Supervised** | Agent acts; human reviews before effect is permanent | Prepares a purchase order pending approval |
| **Automated** | Agent acts within defined scope; human monitors | Resolves standard support tickets autonomously |
| **Autonomous** | Agent acts across broad scope; humans review exceptions only | Manages inventory reordering end-to-end |

**Axis 2: Business Value Tier** — the magnitude of impact delivered

| Tier | Description | Example |
|---|---|---|
| **Efficiency** | Reduces time or cost of existing tasks | Automated email triage |
| **Quality** | Improves accuracy, consistency, or coverage | Compliance monitoring at scale |
| **Capability** | Enables tasks previously impossible at this scale | Personalized 1:1 marketing for millions of users |
| **Transformation** | Restructures how a business process fundamentally works | Autonomous supply chain management |

### Applying the Classification: Industry Examples

| Use Case | Autonomy Level | Business Value Tier | Governance Implication |
|---|---|---|---|
| Clinical note drafting | Supervised | Quality | Clinician must review all notes before submission |
| Compliance monitoring | Automated | Quality + Capability | Human reviews flagged cases; agent monitors continuously |
| Tier-1 support resolution | Automated | Efficiency + Capability | Escalation path required for out-of-scope scenarios |
| Talent screening | Supervised | Efficiency | Human review required; bias audit recommended |
| Inventory reordering (low value) | Autonomous | Efficiency + Capability | Budget cap enforced; exception alerts to humans |
| Campaign orchestration | Automated | Capability + Transformation | Spend guardrails; brand safety checks |

### The Autonomy-Risk Relationship

There is a direct relationship between autonomy level and the governance investment required:

```
Higher Autonomy → Higher Risk of Unintended Action → Higher Governance Investment Required
```

This does not mean high autonomy is bad — it means the decision to grant autonomy must be made deliberately, with commensurate guardrails. An agent running at "Autonomous" level without governance infrastructure is not a more capable system — it is a liability.

A useful heuristic: **start at Supervised, earn Autonomous.** Deploy agents at a lower autonomy level, observe their behavior across a statistically significant number of interactions, measure error rates, and progressively expand their scope of action as confidence in their reliability grows.

---

## 3. Deconstructing Agent-Process Interactions (15 min)

### Agents Do Not Replace Processes — They Participate in Them

A common misconception is that deploying an agent means replacing a business process. In practice, agents are embedded within existing processes — they take over specific steps, augment others, and hand off to humans at defined points. Understanding exactly where the agent sits within the process is the most important design decision.

### The Process Integration Map

For any use case, the agent's role can be mapped across five process stages:

| Stage | Agent Role | Human Role |
|---|---|---|
| **Trigger** | Detects event and initiates workflow | Defines the trigger conditions |
| **Data Gathering** | Retrieves and assembles relevant context | Reviews data sources and access permissions |
| **Reasoning and Decision** | Analyzes situation and selects action | Sets decision boundaries and escalation rules |
| **Execution** | Calls tools, updates systems, sends communications | Approves high-risk actions; handles exceptions |
| **Logging and Review** | Records reasoning trace and outcome | Audits performance; adjusts configuration |

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

*Lab details in the Lab Guide document.*

---

## 6. Wrap-Up & Reflection (5 min)

1. Name two industries not covered in this session and describe one plausible agentic application in each. Which agent components would be most critical?
2. Using the two-axis model, classify the following: an agent that automatically posts to a company's social media accounts based on trending topics. What autonomy level is appropriate at initial deployment? What would need to be true before expanding it?
3. In the customer service deconstruction, what would happen if the `shipping_escalation` tool returned an error? Trace the agent's likely behavior and identify where a human checkpoint should be added.

> Next session: **Prompts, Intents, and Context**

---

## Resources

- McKinsey Global Institute — *The Economic Potential of Generative AI* (2023)
- [Salesforce — State of Service Report: AI in Customer Service](https://www.salesforce.com/resources/research-reports/state-of-service/)
- [Google DeepMind — Agents in Healthcare: Opportunities and Challenges](https://deepmind.google/research/)
- Lilian Weng — *LLM-powered Autonomous Agents* (2023) — [lilianweng.github.io](https://lilianweng.github.io/posts/2023-06-23-agent/)
- [a16z — The Enterprise AI Adoption Playbook](https://a16z.com/ai/)
- [MIT Sloan — AI in Supply Chain Management](https://mitsloan.mit.edu/ideas-made-to-matter/ai-supply-chain)
