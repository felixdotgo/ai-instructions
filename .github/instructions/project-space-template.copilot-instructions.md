---
applyTo: "{{PROJECT_FILE_GLOB}}"
description: "Project-Specific Custom Space Template - Fill placeholders for each project"
---

# Project Custom Space Template

## 1) Project Identity
- Project Name: {{PROJECT_NAME}}
- Domain: {{DOMAIN_NAME}}
- Primary Runtime/Stack: {{STACK}}
- Deployment Environment: {{ENVIRONMENTS}}
- Criticality Level: {{CRITICALITY_LEVEL}}

## 2) Product and Delivery Goals
- Business Goal: {{BUSINESS_GOAL}}
- User Outcomes: {{USER_OUTCOMES}}
- Non-Goals: {{NON_GOALS}}
- Definition of Done: {{DEFINITION_OF_DONE}}

## 3) Architecture and Constraints
- Architectural Style: {{ARCH_STYLE}}
- Hard Constraints: {{HARD_CONSTRAINTS}}
- Performance Targets: {{PERFORMANCE_TARGETS}}
- Availability Targets: {{AVAILABILITY_TARGETS}}
- Data Residency/Compliance: {{DATA_COMPLIANCE}}

## 4) Coding and Clean Code Rules
- Naming Rules: {{NAMING_RULES}}
- Module Boundaries: {{MODULE_BOUNDARIES}}
- Complexity Thresholds: {{COMPLEXITY_LIMITS}}
- Allowed Dependencies: {{ALLOWED_DEPENDENCIES}}
- Forbidden Patterns: {{FORBIDDEN_PATTERNS}}

## 5) Programming Principles Priority
Apply these principles in this order for this project:
1. {{PRINCIPLE_1}}
2. {{PRINCIPLE_2}}
3. {{PRINCIPLE_3}}
4. {{PRINCIPLE_4}}
5. {{PRINCIPLE_5}}

Example principles you can choose from:
- Single Responsibility
- Open/Closed
- Dependency Inversion
- KISS
- DRY
- YAGNI
- Composition over inheritance
- Fail fast at boundaries

## 6) SDLC Requirements (Project-Specific)

### Requirements Stage
- Mandatory artifacts: {{REQ_ARTIFACTS}}
- Acceptance criteria policy: {{REQ_ACCEPTANCE_POLICY}}

### Design Stage
- Required design docs: {{DESIGN_ARTIFACTS}}
- ADR trigger threshold: {{ADR_THRESHOLD}}

### Implementation Stage
- Branching strategy: {{BRANCHING_STRATEGY}}
- Change size policy: {{CHANGE_SIZE_POLICY}}

### Verification Stage
- Mandatory checks: {{MANDATORY_CHECKS}}
- Test depth by risk tier: {{TEST_POLICY_BY_RISK}}

### Release Stage
- Rollout strategy: {{ROLLOUT_STRATEGY}}
- Rollback criteria: {{ROLLBACK_CRITERIA}}

### Operations Stage
- Required observability: {{OBSERVABILITY_REQUIREMENTS}}
- Runbook ownership: {{RUNBOOK_OWNERSHIP}}

### Maintenance Stage
- Versioning/deprecation policy: {{DEPRECATION_POLICY}}
- Documentation update rules: {{DOC_UPDATE_POLICY}}

### Incident Stage
- Severity model: {{SEVERITY_MODEL}}
- Postmortem SLA: {{POSTMORTEM_SLA}}

## 7) Security and Compliance Rules
- Threat model baseline: {{THREAT_MODEL_BASELINE}}
- AuthN/AuthZ requirements: {{AUTH_REQUIREMENTS}}
- Data classification policy: {{DATA_CLASSIFICATION_POLICY}}
- Secrets policy: {{SECRETS_POLICY}}
- Audit/logging policy: {{AUDIT_POLICY}}

## 8) Repository Conventions
- Directory ownership map: {{OWNERSHIP_MAP}}
- Public API contract locations: {{API_CONTRACT_LOCATIONS}}
- Migration policy: {{MIGRATION_POLICY}}
- Feature flag policy: {{FEATURE_FLAG_POLICY}}

## 9) Agent Behavior Overrides
- Response language override: {{RESPONSE_LANGUAGE_OVERRIDE}}
- Explanation verbosity: {{VERBOSITY_LEVEL}}
- Clarification threshold: {{CLARIFICATION_THRESHOLD}}
- Mandatory final report format: {{FINAL_REPORT_FORMAT}}

## 10) Project Placeholders Checklist
Replace every placeholder before using this file:
- {{PROJECT_NAME}}, {{STACK}}, {{PROJECT_FILE_GLOB}}, {{DEFINITION_OF_DONE}}
- {{MANDATORY_CHECKS}}, {{ROLLOUT_STRATEGY}}, {{ROLLBACK_CRITERIA}}
- {{THREAT_MODEL_BASELINE}}, {{SECRETS_POLICY}}, {{POSTMORTEM_SLA}}
