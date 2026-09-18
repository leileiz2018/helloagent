# Daily Multilingual Morning Greeting based on weather

Automated scheduled workflow that sends a "Hello" greeting every morning at 8:00 AM, rotating through different languages each day.

## Business challenge

Send a daily morning greeting at 8:00 AM using a different language each time to create a fun, inclusive, and engaging experience for employees or users.

## Business Architecture (RBA)

### End-to-End Process

Recruit to Retire (Manage Workforce Experience)

### Process Hierarchy

```
Recruit to Retire (E2E)
└── Manage Workforce (generic)
    └── Manage workforce experience (BPS-392)
        └── Enrich workforce experience
```

### Summary

Daily multilingual greetings map to workforce experience enrichment within the Recruit to Retire E2E, supporting employee engagement and inclusion.

## Fit Gap Analysis

| Requirement (business) | Standard asset(s) found | API ORD ID | MCP Server ORD ID | MCP Server Version | Gap? | Notes / assumptions |
| ---------------------- | ----------------------- | ---------- | ----------------- | ------------------ | ---- | ------------------- |
| Scheduled daily trigger at 8:00 AM | n8n Schedule Trigger | — | — | — | No | Native n8n capability |
| Rotate greeting through multiple languages | Custom logic in n8n | — | — | — | No | Language list maintained in workflow |
| Deliver greeting message | n8n notification node (email/Slack/Teams) | — | — | — | No | Channel to be configured |

### Key findings
- No SAP product covers this use case out of the box — a lightweight custom workflow is the right fit.
- n8n provides native scheduling, logic branching, and messaging capabilities sufficient for this solution.
- Language rotation can be implemented with a simple counter or randomizer in the workflow.
- Delivery channel (email, Slack, Teams, etc.) can be configured as a workflow parameter.
- No SAP backend integration is required for this use case.

## Recommendations

### Daily Multilingual Greeting Workflow

#### Executive Summary

Scheduled n8n workflow sends a daily 8 AM greeting in a rotating language.

#### Recommended Solution

An n8n workflow triggered daily at 8:00 AM that selects a language from a predefined list (rotating or random), composes the "Hello" greeting in that language, and delivers it via a configured channel (e.g., email, Slack, or Microsoft Teams).

#### Recommended solution category

n8n Workflow

#### Intent fit
95%
