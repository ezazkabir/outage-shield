# Outage Shield

**ServiceNow | ITSM Automation | REST APIs | CMDB/CSDM | JavaScript**

A ServiceNow application I designed and built to monitor SaaS vendor outages, assess potential business impact and automate an appropriate ITSM response.

**[Full Case Study & Test Evidence](https://ezazkabir.com/projects/outage-shield/)**

## Why I Built It

When a SaaS provider reports an outage, that doesn't necessarily mean every organisation using the service is affected.

I wanted to explore how ServiceNow could connect external vendor status information with an organisation's own service model to make better Incident management decisions.

The challenge wasn't simply creating Incidents from API responses. It was determining which services might be affected, avoiding duplicate tickets, handling unreliable information and escalating appropriately without removing human oversight.

## What Outage Shield Does

The application monitors GitHub and Cloudflare status APIs and processes reported incidents through a configurable, risk-based workflow.

- **Vendor monitoring:** Retrieves and processes vendor status information using REST APIs, JSON and scheduled polling.
- **Service impact:** Maps affected vendor components to CSDM Service Offerings and considers their business criticality.
- **Risk classification:** Determines preliminary business risk using vendor severity and service criticality.
- **Incident automation:** Creates investigative Incidents for Medium and High risk, targeting P3 and P2 through ServiceNow's standard Impact/Urgency matrix.
- **Duplicate prevention:** Reuses existing Incidents and escalates priority when warranted rather than creating additional tickets.
- **Major Incident governance:** Submits native Major Incident proposals for Very High risk, leaving declaration to an authorised person.
- **Safeguards:** Handles missing service mappings, conflicting status information, insufficient evidence and invalid API responses.
- **Notifications:** Includes event-driven subscriber-notification logic for outage and recovery updates.
- **Recovery handling:** Tracks status changes and reconciles outages when vendors report recovery.

## Technical Implementation

Built in a ServiceNow Personal Developer Instance using:

| Area | Implementation |
|---|---|
| Application | Scoped ServiceNow application |
| Integrations | REST APIs, JSON processing |
| Scripting | JavaScript, Script Includes, GlideRecord |
| Automation | Scheduled polling, Incident creation and escalation |
| Service modelling | CMDB/CSDM, Service Offerings and component mappings |
| ITSM | Incident Management, Major Incident proposals, Impact/Urgency matrix |
| Security | Application roles, ACLs and cross-scope permissions |
| Notifications | ServiceNow events and subscriber-notification logic |
| Delivery | Requirements, user stories, acceptance criteria, testing and GitHub source control |

### Key Design Decisions

I deliberately used ServiceNow's native capabilities wherever practical.

**Standard priority calculation:** Incident priority is determined through the configured Impact/Urgency matrix rather than custom priority values.

**One primary Incident per outage:** Repeated polling updates an existing Incident instead of creating duplicates.

**Human control over Major Incidents:** A high-risk vendor event can trigger a Major Incident proposal, but not automatic declaration.

**Fail safely when evidence is unclear:** Missing mappings, conflicting information or invalid API responses are handled without automatically creating an unjustified Incident.

These decisions helped me explore the balance between useful automation and operational control.

## Testing and Validation

I tested the application using live vendor API polling in monitoring-only mode and controlled scenarios for Incident automation.


The validation covered:

- Live GitHub and Cloudflare API polling and processing.
- Vendor component mapping to Service Offerings and business-risk assessment.
- Controlled Incident creation, primary-Incident reuse and P3-to-P2 escalation.
- Native Major Incident proposals for human review.
- Four safeguard tests covering unmapped, conflicting, missing and invalid data.
- Subscriber event generation and queued outbound email records.


**Results:** The controlled Incident and Major Incident scenarios passed, including all 4 safeguard tests.

The published case study includes screenshots, test results and a detailed validation report.

**[View Test Evidence](https://ezazkabir.com/projects/outage-shield/#evidence)**

## Repository Structure

This repository contains the application files exported through ServiceNow source control.

Within the generated application folder:

- `update/` — ServiceNow application records, scripts and configuration.
- `dictionary/` — Table and field definitions.
- `author_elective_update/` — Additional tracked application changes.
- Application XML and checksum files — Generated source-control metadata.

The application uses ServiceNow's generated XML format rather than a conventional standalone JavaScript project structure.

## Scope and Limitations

This is an independently developed portfolio project built and tested in a ServiceNow Personal Developer Instance, not a production deployment.

Live vendor polling and controlled Incident automation have been tested separately. The published validation evidence identifies the scenarios and boundaries of testing.

The project demonstrates the application design and tested functionality, but does not claim production readiness, enterprise deployment or completed end-to-end email-delivery validation.

## About Me

I'm transitioning into ServiceNow consulting after more than 20 years running technology-led businesses, including product ownership, systems integration and process improvement.

Outage Shield allowed me to apply that experience to ServiceNow while developing my hands-on skills in ITSM, CSDM, scripting, integrations and platform configuration.

**Certifications:** CSA | CIS-ITSM | CIS-Data Foundations

**Portfolio:** https://ezazkabir.com

**LinkedIn:** https://linkedin.com/in/ezazkabir
