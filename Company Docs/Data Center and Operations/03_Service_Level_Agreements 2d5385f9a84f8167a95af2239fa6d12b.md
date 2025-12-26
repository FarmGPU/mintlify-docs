# 03_Service_Level_Agreements

# Service Level Agreement

## 15.1 Applicability of SLA

The service level commitments, performance metrics, and remedies set forth in this Article 15 (collectively, the “SLA”) apply to:

- **Reserved Instance Services**
- **Bare Metal Services**

**On-Demand Services** and **Spot Instance Services** are provided without service level guarantees or commitments and are not subject to this SLA. **Beta Services** are expressly excluded from SLA coverage.

## 15.2 Service Availability Commitment

### Monthly Uptime Percentage

FarmGPU commits to providing the following **Monthly Uptime Percentage** for Customer’s Reserved Capacity and Bare Metal Services, measured on a monthly basis:

| SERVICE TIER | COMMITTED MONTHLY UPTIME % | TARGET MONTHLY UPTIME % |
| --- | --- | --- |
| Standard | 99.0% | 99.5% |
| Premium | 99.7% | 99.9% |
| Enterprise | 99.9% | 99.95% |

**Bare Metal Services Default SLA Tier:** Unless otherwise specified in the Order Form, Bare Metal Services are provided with **Premium** SLA tier (99.7% committed uptime). Customer may upgrade to Enterprise tier for additional monthly fees as specified in the applicable Order Form.

### Calculation of Monthly Uptime Percentage

Monthly Uptime Percentage = [(Total Minutes in Month – Downtime Minutes) / Total Minutes in Month] × 100

## 15.3 Definition of Downtime

“Downtime” means any period of time (measured in minutes) during which Customer’s Reserved Capacity or Bare Metal Services are unavailable for use due to a failure **within FarmGPU’s control**, as demonstrated by Customer’s inability to:

(a) Submit new jobs or workloads to Reserved Capacity or Bare Metal GPU instances through normal access methods; OR

(b) Execute running jobs due to GPU hardware failure, system failure, or infrastructure failure affecting Reserved Capacity or Bare Metal Services; OR

(c) Access Reserved Capacity or Bare Metal Services due to network connectivity failures within FarmGPU’s control; OR

(d) Access Reserved Capacity or Bare Metal Services through normal authentication and access control mechanisms due to failures in FarmGPU’s systems; OR

(e) For Bare Metal Services specifically: inability to access server management interfaces (IPMI/BMC) for remote administration.

For avoidance of doubt, **performance degradation that does not materially prevent job submission or execution** does not constitute Downtime.

## 15.4 Downtime Exclusions

Downtime shall not include, and the Monthly Uptime Percentage calculation shall exclude, any periods of unavailability resulting from or caused by:

(a) **Scheduled Maintenance:** Planned maintenance activities conducted during pre-announced maintenance windows, provided that such scheduled maintenance does not exceed four (4) hours in any calendar month;

(b) **Customer-Caused Issues:** Customer’s or Authorized Users’ misconfigurations, software errors or bugs in Customer Content, credential management failures, or misuse of the GPU Services;

(c) **Force Majeure Events:** Events beyond FarmGPU’s reasonable control including but not limited to acts of God, natural disasters, wars, terrorist attacks, riots, labor disputes, pandemics, government orders, failures of upstream internet service providers or network carriers, public utility failures, and distributed denial-of-service (DDoS) attacks;

(d) **Spot Instance Interruptions:** Reclamation or unavailability of Spot Instance capacity (Spot Instances are explicitly excluded from SLA coverage);

(e) **Policy Violations:** Service suspensions or terminations resulting from Customer’s violation of the Acceptable Use Policy or other material breaches of this Agreement;

(f) **Non-Payment Suspensions:** Service suspensions due to Customer’s failure to pay undisputed amounts when due;

(g) **Partial Degradation:** Performance degradation, reduced throughput, or increased latency that does not materially prevent job submission or execution;

(h) **De Minimis Outages:** Individual hardware failures or component failures that are fully remediated within **sixty (60) minutes**;

(i) **Beta and Pre-Release Services:** Any Beta Services as defined in Section 2.5;

(j) **Bare Metal Specific Exclusions:**

- Operating system failures, kernel panics, or software crashes in Customer-managed software layers
- Issues related to Customer-installed applications or middleware
- Network issues originating from Customer-configured network settings, firewall rules, VLAN/private segment settings, or routing policies
- Self-induced hardware issues resulting from Customer exceeding published thermal, power, or operating specifications

## 15.5 Capacity Availability Guarantee

### Minimum Available Capacity

For Reserved Instance and Bare Metal Services, FarmGPU guarantees that at least **ninety-five percent (95%)** of Customer’s committed GPU capacity shall be available for Customer’s use during each calendar month, excluding scheduled maintenance windows and Force Majeure events.

This guarantee applies only to unavailability caused by conditions within FarmGPU’s control and excludes partial degradation that does not fully prevent use of affected GPU resources.

### Calculation of Capacity Availability

Capacity Availability Percentage = (Available GPU-Hours / Total Reserved GPU-Hours) × 100

Measured on a monthly basis, where:

- Available GPU-Hours = GPU-hours of reserved/committed capacity available for Customer use during the month
- Total Reserved GPU-Hours = total GPU-hours of reserved/committed capacity under the Order Form for that month

### Bare Metal Hardware Availability

For Bare Metal Services, availability is measured on a per-server basis. If a Bare Metal server is completely unavailable, it counts as 100% unavailable for that time period. Partial loss (e.g., one GPU failed in an 8-GPU server) may be calculated proportionally **only if** the remaining system cannot support workload execution for the contracted configuration.

## 15.6 Hardware Replacement Service Level (Targets)

FarmGPU will use commercially reasonable efforts to meet the following **target** response and resolution times for hardware failures affecting Customer’s Reserved Capacity and Bare Metal Services:

| ISSUE TYPE | TARGET RESOLUTION TIME – BARE METAL |
| --- | --- |
| Individual GPU failure | 24 hours |
| Complete node failure | 1 week |
| Network infrastructure failure | 12 hours |
| Storage device failure | 12 hours |
| Memory failure | 24 hours |
| Power supply failure | 12 hours |

**Initial Response Time** means the time from FarmGPU’s detection of the failure or receipt of Customer notice (whichever is earlier) until technical personnel begin active diagnosis.

**Target Resolution Time** means the time from detection/notice (whichever is earlier) until service is restored or equivalent replacement capacity is provisioned.

Target resolution times are subject to site access, safety constraints, and hardware availability.

## 15.7 Service Credits

### Service Availability Service Credits

If FarmGPU fails to achieve the committed Monthly Uptime Percentage for any calendar month, Customer shall be eligible for Service Credits as follows:

**Standard Tier (99.0% commitment):**

| ACHIEVED MONTHLY UPTIME % | SERVICE CREDIT (% OF MONTHLY FEES) |
| --- | --- |
| 99.0% to < 99.5% | 10% |
| < 99.0% | 25% |

**Premium Tier (99.7% commitment):**

| ACHIEVED MONTHLY UPTIME % | SERVICE CREDIT (% OF MONTHLY FEES) |
| --- | --- |
| 99.5% to < 99.7% | 15% |
| 99.0% to < 99.5% | 30% |
| < 99.0% | 50% |

**Enterprise Tier (99.9% commitment):**

| ACHIEVED MONTHLY UPTIME % | SERVICE CREDIT (% OF MONTHLY FEES) |
| --- | --- |
| 99.7% to < 99.9% | 15% |
| 99.5% to < 99.7% | 30% |
| < 99.5% | 50% |

### Capacity Availability Service Credits

If Capacity Availability Percentage falls below 95% in any calendar month:

| ACHIEVED CAPACITY AVAILABILITY % | SERVICE CREDIT (% OF MONTHLY FEES) |
| --- | --- |
| 90% to < 95% | 10% |
| 85% to < 90% | 25% |
| < 85% | 35% |

### Bare Metal Enhanced Credits (Optional; Keep or Remove)

For Bare Metal Services only, if a critical hardware replacement exceeds the applicable **Target Resolution Time** by more than 50% due to conditions within FarmGPU’s control, Customer receives additional Service Credits:

| RESOLUTION TIME OVERAGE | ADDITIONAL SERVICE CREDIT |
| --- | --- |
| 50% to < 100% over target | 5% |
| 100% to < 200% over target | 10% |
| 200%+ over target | 15% |

Enhanced credits are cumulative with availability credits, subject to the caps in Section 15.10.

## 158 Service Credit Calculation; Caps

Service Credits are calculated as a percentage of the monthly recurring fees paid or payable for the affected Reserved Capacity or Bare Metal Services that experienced the SLA failure.

**Service Credit Caps:**

- Maximum Service Credits in any single calendar month: **30%** of the total monthly fees for the affected Order Form
- Maximum aggregate Service Credits over any twelve (12) month period: **30%** of the total contract value under the affected Order Form

## 15.9 Chronic Failure Termination Right

If:

(a) Monthly Uptime Percentage falls below **99.5%** for two (2) consecutive calendar months; OR

(b) Monthly Uptime Percentage falls below **99.0%** for any single calendar month;

Customer may, upon forty-five (45) days’ prior written notice, terminate the affected Order Form without early termination fees. FarmGPU shall refund any prepaid fees allocable to services not yet rendered, pro-rated as of the effective termination date.

This right does not apply where the failure is caused by events constituting Downtime Exclusions under Section 15.4.

During the notice period, FarmGPU may demonstrate that the root cause has been remediated through structural improvements. If FarmGPU demonstrates remediation to Customer’s reasonable satisfaction, Customer may withdraw the termination notice.

## 15.10 Service Credit Request Procedure

To receive Service Credits, Customer must:

(a) Submit a claim within thirty (30) days after the end of the month of the alleged violation;

(b) Include affected resources, description of issue, supporting evidence, and Customer’s downtime calculation;

(c) Failure to submit within this period waives the claim.

FarmGPU will review claims within fifteen (15) business days and, if validated, apply credits within thirty (30) days.

**SERVICE CREDITS ARE CUSTOMER’S SOLE AND EXCLUSIVE REMEDY** for any failure to meet this SLA.

## 15.11 Application of Service Credits

Service Credits:

- Are applied against future invoices for the same Order Form
- Have no cash value and are not refundable
- Expire upon termination or expiration of the Order Form
- Are not transferable

## 15.12 Monitoring, Reporting, and Transparency

FarmGPU will provide:

- A real-time status dashboard
- Monthly SLA reports (within five (5) business days after month-end)
- RCA within forty-eight (48) hours for Downtime events lasting > 30 minutes
- API access to metrics where available
- Bare Metal monitoring access including BMC/IPMI where applicable

## 15.13 Scheduled Maintenance

(a) At least seven (7) days’ advance notice for scheduled maintenance impacting applicable services

(b) Scheduled maintenance not to exceed four (4) hours in any calendar month per affected cluster/zone/server

(c) FarmGPU will use commercially reasonable efforts to perform non-disruptive maintenance when feasible

(d) Emergency maintenance permitted when necessary for security, integrity, or stability, with notice as practicable

## 15.14 SLA Exclusions and Limitations

This SLA does not apply to:

- Beta/free trial services
- On-Demand and Spot services
- Suspended services due to Customer breach or non-payment
- Unsupported or non-recommended configurations
- Bare Metal issues arising from Customer-managed OS/software or Customer-induced hardware stress beyond published specifications

## 15.15 SLA Modifications

FarmGPU may modify this SLA upon ninety (90) days’ prior notice, provided:

- Changes do not apply to existing Order Forms during their term without Customer consent
- Changes apply to new Order Forms and renewals
- Changes do not materially diminish commitments for active reserved/bare metal terms