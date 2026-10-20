# Project 4 - Identity Governance & Access Reviews

## Project Overview

This project explores identity governance and access reviews using a fictional company, Southstars Retail. The goal is to establish a repeatable process for ensuring that employees retain only the access and permissions required for their current responsibilities.

The project focuses on reviewing group membership, managing employee transfers and departures, evaluating privileged access, and documenting access review decisions. It also outlines how Microsoft Entra ID Access Reviews could support a recurring governance process.

**Platform:** Microsoft Entra ID  
**Environment:** Microsoft Entra ID Free tenant and documented governance scenarios  
**Project Type:** IAM portfolio project: hands-on identity review scenarios and access review workflow design

## Business Scenario

Southstars Retail has 40 employees across five departments:

- IT
- Human Resources (HR)
- Finance
- Sales
- Operations

As employees change positions, transfer between departments, or leave the organization, their access must be updated accordingly. Without a consistent review process, employees may retain unnecessary group memberships or administrative permissions.

This project establishes an access governance process to identify outdated permissions, determine whether access remains appropriate, and document the actions required to reduce access-related risks.

## Project Objectives

- Apply the Joiner-Mover-Leaver (JML) lifecycle to identity governance scenarios.
- Identify and address outdated group memberships.
- Design a quarterly access review for the Sales security group.
- Define reviewer responsibilities and escalation procedures.
- Evaluate privileged access using least-privilege principles.
- Document governance decisions and remediation actions.
- Explore how Microsoft Entra ID can support access governance.

## Part 1 - Identify Access Governance Risks

### Scenario

Rex Anderson transfers from the Sales department to Human Resources but remains a member of the SG-Sales security group.

### Risk Assessment

Rex may retain access to Sales resources that are no longer necessary for his new responsibilities. This creates unnecessary access and increases the risk of unauthorized or inappropriate use of resources.

### Recommended Actions

1. Verify Rex's new department, responsibilities, and approved access requirements.
2. Remove his membership in SG-Sales once the change is authorized.
3. Grant the appropriate HR group membership and resource access based on his new role.
4. Verify that the outdated Sales access has been removed.
5. Document the transfer and access changes.

### Least Privilege

Employees should have only the permissions required to perform their current job responsibilities. A department transfer should trigger an access review and timely permission changes rather than leaving previous access in place.

## Part 2 - Review User Accounts and Access

Three identity governance scenarios were evaluated.

### Case 1: Rex Anderson - Department Transfer

**Finding:** Rex moved from Sales to HR but remains in SG-Sales.

**Decision:** Remove outdated Sales group membership and grant appropriate HR access after verifying the business need and authorization.

**Lifecycle Category:** Mover

**Reasoning:** Access must reflect the employee's current responsibilities rather than their previous position.

### Case 2: Jordan Leigh - Privileged Access

**Finding:** Jordan is assigned the Helpdesk Administrator role and continues to work in IT support.

**Decision:** Retain the role only if current responsibilities, authorization, and business need justify the privilege.

**Lifecycle Category:** Periodic access and privileged role review

**Reasoning:** An employee's continued employment does not automatically justify retaining administrative permissions. The organization should verify that the role is still necessary and that a less privileged role would not be sufficient.

### Case 3: Emmanuel David - Employee Departure

**Finding:** Emmanuel has left Southstars Retail, but his account remains enabled.

**Decision:** Disable the account promptly through the organization's approved offboarding process, revoke active sessions where appropriate, and review associated group memberships, application access, and other permissions.

**Lifecycle Category:** Leaver

**Reasoning:** Former employees should not retain active access to organizational resources. Offboarding should be handled promptly rather than waiting for the next scheduled access review.

## Part 3 - Quarterly Access Review Design

### Objective

Design a quarterly review of membership in the SG-Sales security group to confirm that each member still requires access to Sales resources.

### Proposed Configuration

| Setting | Proposed Design |
|---|---|
| Review name | Quarterly Sales Group Access Review |
| Resource  | SG-Sales |
| Frequency | Quarterly |
| Reviewers | Designated group owner or appropriate employee managers |
| Review decisions | Retain access or remove access |
| Unclear decisions | Escalate for clarification |
| Documentation | Reviewer, review date, decision, justification, and remediation status |

This is a proposed configuration. It was not deployed as a recurring Microsoft Entra ID Access Reviews configuration in the free tenant.

### Review Workflow

1. **Initiate the review:** Obtain the current membership list for SG-Sales.
2. **Assign reviewers:** Identify an accountable group owner or managers who can evaluate each employee's business need.
3. **Evaluate membership:** Verify each member's current department, job responsibilities, authorization, and need for Sales resources.
4. **Record decisions:** Document whether access should be retained or removed, including the justification.
5. **Escalate uncertainty:** Request clarification from the appropriate manager or group owner if the reviewer's information is insufficient.
6. **Apply approved changes:** Remove memberships that are no longer justified through the appropriate administrative process.
7. **Verify remediation:** Confirm that the approved access changes were completed.
8. **Retain review records:** Document outstanding decisions, completed actions, reviewer details, and the review date.

### Handling Decisions

If a reviewer cannot determine whether an employee still requires access, the decision should be escalated to someone with sufficient knowledge of the employee's responsibilities.

The review should record the unresolved decision and follow an established response deadline and escalation process. Uncertainty should not result in indefinite access retention without accountability. For sensitive resources, the organization should define stricter rules based on risk and business requirements.

### Quarterly Reviews Matter

Access reviews help identify outdated permissions that may not be discovered through routine administration alone. They provide a repeatable way to verify access, assign accountability, and document governance decisions.

However, quarterly reviews are not a replacement for timely access changes triggered by transfers, terminations, or changes in job responsibilities.

## Part 4 - Microsoft Entra ID Implementation Approach

Microsoft Entra ID provides identity administration capabilities and, where appropriately licensed, Access Reviews functionality to help organizations evaluate group memberships and other access.

### Proposed Access Review

The planned review would evaluate SG-Sales membership on a quarterly schedule, assign appropriate reviewers, collect retain-or-remove decisions, and track the resulting actions.

### Implementation Considerations

- Confirm that the organization's Microsoft Entra licensing supports the required Access Reviews functionality.
- Identify accountable reviewers who understand employees' business responsibilities.
- Establish decision deadlines and escalation procedures.
- Document justifications for retaining or removing access.
- Verify that approved changes are completed.
- Retain evidence of review completion and remediation.

### Environment Limitations

This project used a Microsoft Entra ID Free tenant for identity administration and learning. The full recurring Access Reviews workflow described here was designed and documented but was not created or deployed in the tenant.

The project therefore demonstrates access governance planning and scenario-based decision-making, rather than a completed production Access Reviews implementation.

## Part 5 - Privileged Access Review

### Scenario

Jordan Leigh is assigned the Helpdesk Administrator role. Because this is a privileged directory role, the organization must verify that the permissions remain necessary and authorized.

### Review Checklist

Before retaining the role, the reviewer should verify:

- **Current responsibilities:** Does Jordan still perform duties requiring this administrative access?
- **Authorization:** Is the assignment approved under the organization's access management process?
- **Least privilege:** Could a less privileged role provide the permissions needed for the job?
- **Ongoing business need:** Is the role still required for Jordan's current duties?
- **Review accountability:** Has the decision been documented, and is the role subject to future review?

### Decision Process

- **Retain:** Keep the role when the business need and authorization are confirmed.
- **Remove:** If the role is no longer necessary or authorized, remove it through the approved process and verify that the privilege has been revoked.
- **Escalate:** If the reviewer's information is insufficient, request clarification from the appropriate manager or role owner and document the unresolved decision.

### Privileged Access Requires Special Attention

Administrative roles can allow users to manage other accounts, change permissions, or access sensitive organizational resources. Unnecessary privileged access can therefore create a greater security risk than ordinary group membership.

Periodic privileged access reviews help ensure that administrative permissions remain justified and appropriately limited.

## Part 6 - Joiner-Mover-Leaver Governance

The project applies the Joiner-Mover-Leaver lifecycle to ensure that access changes follow employee lifecycle events.

| Lifecycle Event | Governance Action | Example |
|---|---|---|
| Joiner | Grant approved access required for the employee's role. | Assign a new Sales employee to the appropriate group. |
| Mover | Review existing access, remove permissions no longer needed, and grant approved new access. | Remove Rex from SG-Sales and grant appropriate HR access. |
| Leaver | Disable the account promptly and remove or revoke associated access according to offboarding procedures. | Disable Emmanuel's account and review his remaining access. |

### Relationship Between Access Reviews and JML

JML processes respond to changes in employment status or responsibilities. Access reviews provide an additional periodic check to identify permissions that may have become inappropriate or were missed during routine changes.

Both processes are necessary: an organization should not wait for a quarterly review to address a known employee departure or department transfer.

## Part 7 - Documentation and Success Criteria

### Required Review Records

A completed access review should capture:

- Review name and scope
- Review period and completion date
- Reviewer or decision-maker
- Employee and group or role being reviewed
- Retain, remove, or escalate decision
- Business justification
- Approved remediation actions
- Remediation completion and verification status
- Outstanding decisions and escalation history

### Success Criteria

The governance process is successful when:

- Group memberships reflect current business responsibilities.
- Employee transfers trigger appropriate access changes.
- Former employees do not retain unnecessary active access.
- Privileged role assignments are justified and periodically reviewed.
- Uncertain decisions are escalated and tracked.
- Approved changes are completed and verified.
- Review decisions and remediation actions are documented for accountability.

## Key Skills Demonstrated

- Microsoft Entra ID identity governance concepts
- Access review planning and workflow design
- Joiner-Mover-Leaver lifecycle management
- Least-privilege access decisions
- Security group membership review
- Privileged access evaluation
- Access remediation and verification
- Reviewer accountability and escalation
- IAM documentation and risk analysis

## Conclusion

This project demonstrates how identity governance can help an organization maintain appropriate access as employees join, change roles, or leave. By combining periodic access reviews with timely lifecycle changes and privileged access evaluations, Southstars Retail can reduce unnecessary permissions and improve accountability.
