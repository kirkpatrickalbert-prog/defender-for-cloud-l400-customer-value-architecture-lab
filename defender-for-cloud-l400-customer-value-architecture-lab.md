**Microsoft Defender for Cloud | Level 400**

# Prioritize cloud risk and build a Defender for Cloud adoption roadmap

Caldova customer value architecture lab

------------------------------------------------------------------------

| Item | Detail |
|---|---|
| Level | 400 |
| Duration | 60 minutes |
| Audience | Security CSAs |
| Environment | Caldova Defender tenant |

> [!IMPORTANT]
> Replace `YOUR-TENANT-ID` in this guide and its portal URL with the authorized demo tenant ID supplied by your facilitator. The original tenant ID is omitted from this public copy. Named resources and attack paths require the matching demo dataset or the substitutions described in Troubleshooting. This Markdown conversion does not independently validate the live-tenant procedures.

## Lab outcome

Analyze cloud exposure evidence, trace a critical attack path, and convert the findings into a CNAPP architecture, a 30/60/90-day adoption roadmap, and an executive-ready value narrative.

> **Shared tenant: Complete only the read-only actions described in this document.**

## Part 1: Hands-on lab

In this exercise, you act as the Security Cloud Solution Architect (CSA) advising Caldova, an existing cloud customer with uneven Microsoft Defender for Cloud adoption. You will use evidence in the Microsoft Defender portal to identify high-impact cloud risks, analyze an attack path to a critical resource, and turn the findings into a pragmatic cloud-native application protection platform (CNAPP) architecture and adoption roadmap.

This is an advisory and architecture exercise, not a feature tour. Your final recommendation must connect cloud security posture management (CSPM), cloud workload protection platform (CWPP), and DevSecOps capabilities to measurable customer outcomes.

In this exercise, you will:

- Assess Caldova's cloud exposure and the Cloud Security initiative

- Prioritize multicloud security recommendations using business context

- Trace an attack path from an internet-exposed workload to a critical asset

- Recommend a future-state CNAPP architecture and phased adoption roadmap

- Deliver a concise, executive-ready value narrative

This exercise should take approximately **60** minutes to complete.

### Learning objectives

By the end of this exercise, you'll be able to:

1.  Use posture, recommendation, and attack-path evidence to explain cloud risk and operational value.

2.  Map Defender for Cloud capabilities across CSPM, CWPP, DevSecOps, and multicloud environments.

3.  Design an adoption roadmap with clear owners, dependencies, quick wins, and success measures.

4.  Present a customer-specific architecture recommendation in business language.

### Prerequisites

To complete this exercise, you need:

- Access to the Caldova Microsoft Defender tenant as the assigned lab user.

- Permission to view Microsoft Security Exposure Management data.

- Working knowledge of Defender for Cloud, Azure governance, workload protection, DevSecOps, and multicloud architecture.

- A copy of the Defender for Cloud customer value worksheet *(included in Part 2)*, or another place to record your findings.

> **Important: This is a shared environment. Complete only the read-only actions described in the exercise. Don't change recommendation status, assign owners, save filters, mark initiatives as favorites, or modify resources.**

### Scenario

Caldova operates Azure and AWS workloads and has Defender for Cloud capabilities available, but security leadership is concerned about uneven adoption and unclear business outcomes. The security team sees many recommendations and needs a defensible way to decide what to address first. Leadership also wants an architecture and adoption plan that improves risk reduction without creating an unrealistic remediation backlog.

Your task is to gather evidence, identify a high-value risk-reduction sequence, and prepare a recommendation for Caldova's security leadership.

Use the following timeboxes:

| **Activity**                                          | **Time**   |
|-------------------------------------------------------|------------|
| Prepare the worksheet and establish the current state | 5 minutes  |
| Assess cloud exposure and initiative health           | 10 minutes |
| Prioritize cloud recommendations                      | 15 minutes |
| Investigate a critical attack path                    | 15 minutes |
| Design the architecture and adoption roadmap          | 10 minutes |
| Prepare the customer value narrative                  | 5 minutes  |

### Prepare your evidence worksheet

The worksheet keeps your portal observations separate from your architectural judgments. Record exact portal evidence first, and then explain its significance to the customer.

1.  Open the Defender for Cloud customer value worksheet *(included in Part 2)*.

2.  Create a working copy or open a separate notes file in which you can enter your answers.

3.  Review the worksheet sections so that you know which evidence to capture.

4.  Open [Microsoft Defender](https://security.microsoft.com/homepage?tid=YOUR-TENANT-ID).

5.  Confirm that the tenant context in the URL contains YOUR-TENANT-ID.

> **Verification**: You should see the Microsoft Defender home page and your assigned lab account in the account manager.

### Assess cloud exposure and initiative health

Start with cross-domain exposure evidence. This helps you frame the customer conversation around risk and outcomes before discussing individual product plans.

1. In the Microsoft Defender portal, select **Show navigation**.

2. Expand **Exposure management**, and then select **Overview**.

3. Review **Resolve now** and record the following cloud evidence in the worksheet:

    - Total recommendations for exploitable, internet-exposed cloud assets

    - Recommendations associated with critical assets

    - Known exploited vulnerabilities on cloud assets

    - Critical recommendations for internet-exposed cloud assets

4. Review **Monitor exposure**, and record the number of internet-exposed **Cloud assets**.

5. Review **Domain initiatives**, and record the current **Cloud** score and target score.

> Note: Exposure data is refreshed over time. Record the values you see rather than treating values in screenshots or instructor demonstrations as fixed.

6. Expand **Exposure management**, and then select **Initiatives**.

7. In **Domain initiatives**, locate **Cloud Security**.

8. Record its current score, 14-day change, workload, and last-updated time.

9. Locate **Critical Asset Protection** and record the same fields.

10. Compare the two initiatives and answer these questions in the worksheet:

    - Which initiative should Caldova discuss first with leadership?

    - What additional evidence would you request before recommending a licensing or deployment change?

> **Verification**: The **Cloud Security** initiative should identify **Defender for Cloud** as its workload. The **Critical Asset Protection** initiative should include Defender for Cloud and Defender for Endpoint. Both initiatives should display a current score.

### Prioritize cloud recommendations

Recommendations become actionable when you combine technical severity with asset context. In this section, compare an AWS data-exposure finding with an Azure storage-control finding.

1.  Expand **Exposure management**, and then select **Recommendations**.

2.  Select the **Cloud** tab.

3.  Review the **Recommendations summary**, and record:

    - **Cloud secure score**

    - The number of **Critical** recommendations

4.  Confirm that the recommendation table includes the following columns:

    - **Risk level**

    - **Recommendation title**

    - **Exposed asset**

    - **Asset risk factors**

    - **Asset attack paths**

    - **Recommendation owner**

    - **Status**

5.  Locate the critical recommendation **S3 buckets public read access should be removed** for the aws-sensitive-data AWS S3 bucket.

6.  Record its risk factors and number of related attack paths.

7.  Locate **S3 Block Public Access setting should be enabled at the bucket level** for the same asset.

8.  Record how its risk factors and attack-path count compare with the public-read-access recommendation.

9.  Locate **Storage accounts should prevent shared key access** for blobpurviewdemoed70ec92, or for another Azure Storage account if the named asset is no longer listed.

10. Compare the Azure and AWS findings by using these decision criteria:

    - Internet exposure and anonymous access

    - Sensitive-data context

    - Critical-resource context

    - Contribution to an attack path

    - Likely remediation dependency

11. Rank the three recommendations in the worksheet. Explain why your order might differ from a simple severity-only sort.

> **Verification**: The aws-sensitive-data recommendations should be **Critical** and show the risk factors **Exposure to the Internet**, **Anonymous Access**, **Sensitive Data**, and **Critical Resource**. At least one should show a related attack path.

### Investigate a critical attack path

Attack-path analysis connects separate findings into an end-to-end risk story. Use it to explain how a workload weakness can lead to compromise of a critical cloud resource.

1.  Expand **Exposure management**, and then select **Attack paths**.

2.  On the **Overview** tab, review:

    - **Top 5 attack paths**

    - **Top 5 choke points**

    - **Top targets**

    - **Top entry points**

3.  Record one observation about the concentration of risk. For example, note whether several attack paths converge on one target type or originate from one entry-point type.

4.  Under **Top 5 attack paths**, select **Show more**.

5.  In the attack-path list, locate:

    **Internet exposed Azure VM with high severity vulnerabilities allows lateral movement to Critical Azure storage account with sensitive data**

6.  Select the row with:

    - Entry point: alpine-srv1

    - Target: c5uj5lrp6r3dm

7.  In the details pane, record:

    - Risk level

    - Entry point and target

    - Number of layers

    - Description

    - The six stages in the **Attack Story**

    - MITRE ATT&CK tactics

    - Risk factors

8.  Explain the attack path in customer language. Avoid repeating only the technical labels; describe the plausible business impact if sensitive data is read or exfiltrated from the storage account.

9.  Identify the minimum set of control outcomes needed to break the path. Include at least:

    - One exposure-reduction outcome

    - One vulnerability-management or workload-protection outcome

    - One identity or privilege outcome

    - One critical-asset protection outcome

> **Verification**: The details pane should explain that an attacker can exploit an internet-reachable VM, use managed identities to move through an Azure Function App, and read sensitive data from an Azure Storage account. It should list **Initial Access**, **Execution**, **Credential Access**, **Lateral Movement**, and **Exfiltration** as MITRE ATT&CK tactics.

### Design a future-state CNAPP architecture and adoption roadmap

Use the evidence you collected to recommend a coherent Defender for Cloud architecture. Separate confirmed findings from assumptions that require discovery with the customer.

1.  Complete the **Future-state CNAPP architecture** section of the worksheet.

2.  Map each observed risk to one or more of these capability areas:

    - **CSPM**: posture visibility, risk prioritization, secure score, recommendations, attack paths, and governance

    - **CWPP**: protection for servers, storage, databases, containers, APIs, or other relevant workloads

    - **DevSecOps**: code-to-cloud context, source control integration, infrastructure-as-code scanning, and developer remediation

    - **Security operations**: Defender portal investigation, exposure management, alert operations, and ownership workflows

3.  Include Azure and AWS in the architecture. Mark hybrid, GCP, or DevOps components as **Discovery required** unless you observed evidence that confirms them.

4.  Define three adoption phases:

    - **0-30 days**: immediate risk reduction and ownership

    - **31-60 days**: workload coverage and governance

    - **61-90 days**: DevSecOps integration, optimization, and measurement

5.  Add an owner, dependency, and success measure to every roadmap action.

6.  Include at least four measurable outcomes. Examples include:

    - Reduction in critical internet-exposed recommendations

    - Reduction in active attack paths to critical assets

    - Percentage of priority workloads covered by the intended Defender plan

    - Percentage of critical recommendations with an accountable owner

    - Improvement in the Cloud Security initiative score

7.  Identify one licensing or plan assumption that must be validated before implementation.

> **Verification**: Your architecture should cover CSPM, CWPP, DevSecOps, and security operations. Your roadmap should contain actions in all three phases, and every action should have an owner and measure.

### Prepare an executive-ready customer value narrative

Close the exercise by converting technical findings into a concise customer conversation. Your pitch should lead with Caldova's business risk, not a list of product features.

1.  Complete the **3-minute customer value narrative** section of the worksheet.

2.  Use this sequence:

    - **Current state**: State the customer problem and cite two portal observations.

    - **Risk**: Explain one credible attack path and its potential business impact.

    - **Recommendation**: Describe the future-state CNAPP architecture and the first adoption phase.

    - **Value**: Name measurable risk-reduction and operational outcomes.

    - **Next action**: Propose a specific customer working session or validation activity.

3.  Rehearse the narrative with a partner or deliver it to the instructor.

4.  Ask your reviewer to challenge one assumption about licensing, workload coverage, ownership, or implementation dependencies.

5.  Revise the roadmap or pitch to address that challenge.

> **Verification**: Your narrative should mention Defender for Cloud capabilities only in the context of Caldova's risk, adoption plan, and measurable outcomes. It should be deliverable in three minutes or less.

### Summary

In this exercise, you used Microsoft Defender exposure evidence to assess Caldova's cloud security posture, prioritize Azure and AWS recommendations, and investigate an attack path from an internet-exposed VM to a critical Azure Storage account containing sensitive data. You translated the evidence into a future-state CNAPP architecture, a phased adoption roadmap, measurable success criteria, and an executive-ready customer value narrative.

You have successfully completed this exercise.

### Clean up

This exercise uses read-only investigation steps and doesn't create cloud resources.

1.  Close any open recommendation or attack-path details pane.

2.  Select **Reset all** if you changed any local filters.

3.  Confirm that you didn't save a filter, change a recommendation status, assign an owner, or mark an initiative as a favorite.

4.  Sign out of the lab account if instructed by your facilitator.

### Troubleshooting

| **Issue** | **Likely cause** | **Resolution** |
|----|----|----|
| **Cloud security** overview shows N/A or zero assets | That dashboard isn't populated for the assigned lab user or current experience | Continue through **Exposure management**, which is the validated data source for this exercise. |
| **Initiatives** initially shows only column headings | The initiative data is still loading | Wait up to 30 seconds, and then refresh the page once. |
| **Recommendations** opens on **Devices** | **Devices** is the default tab | Select the **Cloud** tab before looking for the named cloud assets. |
| A named recommendation or asset is no longer listed | Tenant data changed after the lab was validated | Select another **Critical** cloud recommendation with comparable risk factors and record the substitution in the worksheet. |
| The named attack path isn't listed | Exposure data was recalculated | Select another **Critical**, **Cloud** attack path that starts with an internet-exposed VM and ends at a critical target. Capture the selected entry point, target, attack story, tactics, and risk factors. |
| The page remains on **Loading** | Defender portal data is still being retrieved | Wait up to 30 seconds. Refresh once, and then reopen the page from **Exposure management**. |

### Additional resources

- [Overview of Defender for Cloud in the Defender portal](https://learn.microsoft.com/azure/defender-for-cloud/defender-portal/defender-for-cloud-defender-portal)

- [Security recommendations in Microsoft Defender for Cloud](https://learn.microsoft.com/azure/defender-for-cloud/security-recommendations)

- [Identify and remediate attack paths](https://learn.microsoft.com/azure/defender-for-cloud/how-to-manage-attack-path)

- [Start using Microsoft Security Exposure Management](https://learn.microsoft.com/security-exposure-management/get-started-exposure-management)

## Part 2: Learner worksheet

> **Complete this worksheet as you move through Part 1. Record portal evidence before adding interpretation or recommendations.**

Use this worksheet to separate portal evidence from assumptions and recommendations. Record the values currently displayed in the tenant because exposure data can change over time.

### Current-state evidence

| **Evidence** | **Observed value** | **Why it matters to Caldova** |
|----|----|----|
| Exploitable, internet-exposed cloud asset recommendations |  |  |
| Recommendations associated with critical assets |  |  |
| Known exploited vulnerabilities on cloud assets |  |  |
| Critical recommendations for internet-exposed cloud assets |  |  |
| Internet-exposed cloud assets |  |  |
| Cloud initiative current score and target |  |  |

### Initiative comparison

| **Initiative** | **Current score** | **14-day change** | **Workloads** | **Last updated** | **Advisory interpretation** |
|----|----|----|----|----|----|
| Cloud Security |  |  |  |  |  |
| Critical Asset Protection |  |  |  |  |  |

**Initiative to discuss first with leadership:**

**Reason:**

**Evidence or licensing information still required:**

### Recommendation prioritization

| **Priority** | **Recommendation** | **Asset** | **Cloud** | **Risk factors** | **Attack paths** | **Dependency or constraint** | **Rationale** |
|----|----|----|----|----|----|----|----|
| 1 |  |  |  |  |  |  |  |
| 2 |  |  |  |  |  |  |  |
| 3 |  |  |  |  |  |  |  |

**Why this order differs from severity-only prioritization:**

### Attack-path analysis

| **Field**            | **Observation** |
|----------------------|-----------------|
| Attack-path name     |                 |
| Risk level           |                 |
| Entry point          |                 |
| Target               |                 |
| Layers               |                 |
| Description          |                 |
| MITRE ATT&CK tactics |                 |
| Risk factors         |                 |

#### Attack story

1. &nbsp;
2. &nbsp;
3. &nbsp;
4. &nbsp;

#### Business impact

Describe the likely operational, financial, regulatory, or trust impact if the attacker reaches the target.

#### Control outcomes that break the path

| **Control outcome** | **Capability area** | **Expected risk reduction** |
|----|----|----|
| Reduce external exposure |  |  |
| Remediate workload vulnerabilities |  |  |
| Reduce managed identity privilege |  |  |
| Protect and monitor the critical target |  |  |

### Future-state CNAPP architecture

Complete the architecture using confirmed evidence. Label unverified components **Discovery required**.

| **Architecture layer** | **Current-state evidence or gap** | **Future-state Defender capability** | **Azure scope** | **AWS scope** | **Other scope or discovery** |
|----|----|----|----|----|----|
| CSPM |  |  |  |  |  |
| CWPP |  |  |  |  |  |
| DevSecOps |  |  |  |  |  |
| Security operations |  |  |  |  |  |
| Governance and ownership |  |  |  |  |  |

### Phased adoption roadmap

| **Phase** | **Action** | **Owner** | **Dependency** | **Success measure** | **Business outcome** |
|----|----|----|----|----|----|
| 0-30 days |  |  |  |  |  |
| 0-30 days |  |  |  |  |  |
| 31-60 days |  |  |  |  |  |
| 31-60 days |  |  |  |  |  |
| 61-90 days |  |  |  |  |  |
| 61-90 days |  |  |  |  |  |

**Licensing or plan assumption to validate:**

**Primary technical blocker and proposed resolution:**

### 3-minute customer value narrative

#### Current state

State Caldova's business problem and cite two portal observations.

#### Risk

Explain one credible attack path and the potential business impact.

#### Recommendation

Summarize the future-state CNAPP architecture and first adoption phase.

#### Value

Name the measurable risk-reduction and operational outcomes.

#### Next action

Propose one specific customer working session or validation activity.

#### Peer or instructor challenge

**Assumption challenged:**

**Revision made to the architecture, roadmap, or pitch:**
