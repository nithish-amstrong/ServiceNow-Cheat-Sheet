# ServiceNow Development Components Cheat Sheet

> **Author: Nithish Amstrong**  
> 🛡️ *This document is copyrighted. Please do not copy or distribute without permission.*

---

## 📦 Data & Import

| Component           | Purpose                                | When to Use                                                  |
|---------------------|-----------------------------------------|---------------------------------------------------------------|
| Table               | Base container for records              | Always first—define your data model.                         |
| Column / Field      | Individual data pieces                  | Store form values like “Priority” or “Department.”           |
| Reference Field     | Links to another table                  | For look-ups (e.g., CI in incident management).              |
| Choice List         | Dropdown with options                   | Limit input options (e.g., Incident states).                 |
| Dictionary Override | Customize inherited field behavior      | When extending base tables.                                  |
| Transform Map       | Maps/transforms import data             | For Excel/CSV/API imports.                                   |
| Data Source         | Origin of import                        | Created per import channel.                                  |
| Coalesce            | Key for record matching                 | To update vs insert during import.                           |
| Import Set Table    | Temporary import staging table          | Always use before transform.                                 |
| Data Policy         | Server/client-side field behavior       | Enforce consistency in APIs or scripts.                      |

---

## 🖥 Server-side Processing

| Component         | Purpose                      | When to Use                                      |
|-------------------|-------------------------------|--------------------------------------------------|
| Business Rule     | Triggers on DB ops            | Validations, default fills, cross-table logic.   |
| Scheduled Job     | Server-side timed scripts     | Maintenance tasks, emails, cleanups.             |
| Script Include    | Reusable server-side logic    | Wrap logic for GlideAjax/client calls.           |
| GlideAjax         | Server access from client     | When client needs server data.                   |
| Script Action     | Triggered by events           | For logic after event is emitted.                |
| Event Registry    | Define/publish events         | App-specific event handling.                     |
| Inbound Email Action | Handles incoming emails    | Create/update tickets/tasks from emails.         |
| Email Script      | Logic for email templates     | Dynamic content for notifications.               |
| Notification      | Alerting via email/SMS/push   | SLAs, approvals, incidents.                      |
| Access Control (ACL) | Security restrictions      | Field/table level access control.                |

---

## 🧑‍💻 Client-side & UI

| Component            | Purpose                          | When to Use                                      |
|----------------------|-----------------------------------|--------------------------------------------------|
| Client Script         | Form logic in browser            | Field manipulation, validation.                  |
| UI Policy             | Declarative field rules          | Show/hide/require fields conditionally.          |
| Catalog Client Script | Script specific to catalog items | Modify catalog behavior.                         |
| UI Action             | Buttons or menu items            | Trigger actions client or server side.           |
| UI Macro              | Reusable HTML/Jelly component    | Consistent UI reuse.                             |
| UI Script             | Shared JS library                | Shared logic across pages/forms.                 |
| UI Page               | Custom pages/modals              | Build dashboards or advanced forms.              |
| Form Section          | Field grouping                   | Navigation-friendly layout.                      |
| Form Layout           | Visual layout tool               | Tailor by role/need.                             |
| Field Styles          | Custom CSS                       | Highlight/color-code fields.                     |
| Theme/Subtheme        | Scoped UI branding               | Scoped-app design customization.                 |
| Widget (Portal)       | AngularJS UI blocks              | Build portal UIs.                                |
| Page (Portal)         | Composite portal page            | User-facing portal interface.                    |

---

## ⚙️ Process Automation

| Component         | Purpose                         | When to Use                                      |
|-------------------|----------------------------------|--------------------------------------------------|
| Workflow          | Legacy automation engine         | Older processes or cross-table approvals.        |
| Flow Designer     | Modern low-code automation       | New approvals, tasks, integrations.              |
| Trigger (Flow)    | Flow start condition             | On record create/update/schedule.                |
| Action (Flow)     | Step in flow                     | Notify, script, lookup, approve.                 |
| Subflow           | Reusable logic segment           | Shared across flows.                             |
| IntegrationHub    | Connect to external platforms    | REST/SOAP/Slack/Teams integrations.              |
| Service Catalog   | Service ordering framework       | Build requestable items.                         |
| Catalog Item      | Requestable UI item              | Single service item.                             |
| Order Guide       | Bundle of items                  | When multiple items ordered together.            |
| Item Variables    | Input fields                     | User input, variable sets.                       |
| Cart & Order      | Ordering UI                      | End-user interaction.                            |
| Fulfillment Workflow | Task automation                | Multi-step fulfillment by teams.                 |

---

## 🔗 Integration

| Component           | Purpose                     | When to Use                                      |
|---------------------|------------------------------|--------------------------------------------------|
| REST/SOAP Message    | Outbound service call config | For calling external APIs.                       |
| Inbound REST         | Accept external data         | Let others send records to SNOW.                 |
| Scripted REST API    | Custom REST logic            | Custom endpoints with JS logic.                  |
| SOAP Message         | Legacy XML integrations      | For older systems using SOAP.                    |
| Web Service Vue/API  | SIMO orchestration           | System-level integration.                        |
| ECC Queue            | Async/sync comms             | Used by MID Servers.                             |
| MID Server           | Connect on-prem systems      | Discovery, Orchestration.                        |
| Discovery Pattern    | Identify CIs                 | Scan infra automatically.                        |
| Service Mapping      | Map apps/dependencies        | Visual CI relationships.                         |

---

## 🚀 Governance & Release

| Component             | Purpose                       | When to Use                                      |
|------------------------|-------------------------------|--------------------------------------------------|
| Update Set             | Track changes                 | Promote Dev → Test → Prod.                       |
| Application Repository | Git-based app source control  | CI/CD for scoped apps.                           |
| Scoped App             | Isolated environment          | Encapsulate multi-tenant logic.                  |
| Application File       | Individual app element        | Scripts, tables, actions, etc.                   |
| Automated Test Framework | Scripted tests              | For CI/CD test automation.                       |

---

## 📊 Performance & Monitoring

| Component            | Purpose                       | When to Use                                      |
|-----------------------|-------------------------------|--------------------------------------------------|
| Performance Analytics | Scorecards & OLAP views       | Track incident resolution trends.                |
| Metric Definition     | KPI/time trackers             | Duration-based metrics.                          |
| Dashboard             | Visual display of metrics     | Executive reporting.                             |
| Benchmarking          | Goal and SLA targets          | Compare against SLAs.                            |
| Event Management      | Aggregates alerts/incidents   | Proactive alerting.                              |

---

## 🔐 Security & Access

| Component              | Purpose                    | When to Use                                      |
|-------------------------|----------------------------|--------------------------------------------------|
| Access Control (ACL)    | Role-based security        | Field/table-level CRUD control.                  |
| Role                    | User permission sets       | Define what users can do.                        |
| Groups & Membership     | Organize users             | Assign roles/team permissions.                   |
| User Criteria           | Catalog item visibility    | Control visibility per user/group.               |
| Scoped App ACLs         | Access control in scoped apps | Protect app-specific data.                    |
| Encryption Support      | Secure fields/tables       | For compliance/sensitive data.                   |
| OAuth Provider/Config   | Token-based auth           | When integrating with OAuth systems.             |
| Password Reset Flows    | Reset UI and logic         | For ITSM or user self-service.                   |

---

## 🧠 Best Practices

- **Client vs Server**: Use Client Scripts for UI, Business Rules for backend logic.
- **Declarative First**: Prefer no-code tools like UI Policy and Flow Designer before scripting.
- **Modern Tools**: Use Flow Designer and IntegrationHub instead of legacy Workflows/SOAP.
- **Scoped Apps**: Avoid conflicts by using scoped app containers.
- **Security First**: Plan ACLs, roles, and user groups up front.

---

### 📌 Author Info

> Created by **Nithish Amstrong**  
> © All rights reserved. If you reuse this, credit is mandatory.

