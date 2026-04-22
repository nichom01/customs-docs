# UK Import Journey: IE Messages Guide

## Overview

The UK import process involves two main systems for handling incoming goods:

1. **Safety & Security GB (S&S GB)** - Handles Entry Summary Declarations (ENS) for pre-arrival safety and security screening
2. **Customs Declaration Service (CDS)** - Handles the customs declaration for duty and tax assessment post-arrival

This document covers the complete journey from pre-arrival notification through to goods release.

## Complete Import Journey: UK Imports - IE Messages Flow

### Phase 1: Pre-Arrival Safety & Security (S&S GB)

| Sequence | Message | Name | Sender | Recipient | Purpose |
|----------|---------|------|--------|-----------|---------|
| **1** | **IE315** | Entry Summary Declaration (ENS) | Importer/Agent | HMRC (S&S GB) | Submission of pre-arrival safety and security declaration; submitted up to 200 days before goods arrive |
| **2** | **IE328** | Entry Summary Declaration Acknowledgement | HMRC (S&S GB) | Importer/Agent | Acknowledgement that ENS has been received and allocated a Movement Reference Number (MRN) |
| **3** | **IE351** | Advanced Intervention Notification (Do Not Load) | HMRC (S&S GB) | Importer/Carrier | Notification that goods must NOT be loaded onto transport due to high-risk assessment or customs intervention requirement |
| **4** | **IE313** | Entry Summary Declaration Amendment | Importer/Agent | HMRC (S&S GB) | Request to amend the ENS if errors or changes are required |
| **5a** | **IE304** | Entry Summary Declaration Amendment Acceptance | HMRC (S&S GB) | Importer/Agent | Confirmation that the ENS amendment has been accepted |
| **5b** | **IE305** | Entry Summary Declaration Amendment Rejection | HMRC (S&S GB) | Importer/Agent | Rejection notification if ENS amendment contains errors or arrival notification already received |
| **5c** | **IE316** | Entry Summary Declaration Rejection | HMRC (S&S GB) | Importer/Agent | Rejection of the original ENS (IE315) if it contains errors or fails validation |

### Phase 2: Post-Arrival Customs Declaration (CDS)

| Sequence | Message | Name | Sender | Recipient | Purpose |
|----------|---------|------|--------|-----------|---------|
| **6** | **CDS Import Declaration** | Full Customs Declaration | Importer/Agent | HMRC (CDS) | Submission of the full customs declaration for import after goods have arrived at UK port; submitted within 3 months of goods arrival |
| **7** | **DMSACC** | Declaration Accepted | HMRC (CDS) | Importer/Agent | Notification that the customs declaration has been received and validated by CDS |
| **8** | **DMSTAX** | Tax Calculation | HMRC (CDS) | Importer/Agent | Notification detailing the calculated customs duty and VAT due (indicative debt) |
| **9a** | **DMSCLE** | Declaration Cleared | HMRC (CDS) | Importer/Agent | Goods have been cleared and permission granted to release/collect goods |
| **9b** | **DMSROG** | Declaration Released or Granted | HMRC (CDS) | Importer/Agent | Alternative notification indicating goods released (may be provisional pending further processing) |
| **9c** | **DMSREJ** | Declaration Rejected | HMRC (CDS) | Importer/Agent | Rejection notification if declaration contains errors or fails validation |

### Supporting/Amendment Messages

| Message | Name | Purpose |
|---------|------|---------|
| **CDS Amendment** | Amendment to CDS Declaration | Request to amend the full customs declaration after submission |
| **CDS Cancellation** | Cancellation of CDS Declaration | Request to cancel the customs declaration |

## Timeline & Key Constraints

**Pre-arrival Filing Window:** Up to 200 days before goods arrive

**ENS Submission Requirement:** Must be submitted before goods arrive in Great Britain

**Post-Arrival Declaration:** Full customs declaration must be submitted within 3 months of goods arrival

**30 Days Before Arrival:** Import declarations can also be made up to 30 days before goods arrive (CDS)

**Amendment Deadline:** Amendments to ENS cannot be made after arrival notification has been received

**90-Day Amendment Window:** Full customs declarations can typically be amended within 90 days of submission

## Critical Dependencies

### Safety & Security Phase
```
IE315 (ENS Submission) 
    ↓
    → IE328 (MRN Allocated) [Normal path]
    → IE316 (ENS Rejected) [Error path - requires correction and resubmission]
    ↓
    ├→ IE351 (Do Not Load) [High-risk intervention]
    │
    ├→ IE313 (Amendment) [If changes needed]
    │   ├→ IE304 (Amendment Accepted)
    │   └→ IE305 (Amendment Rejected)
    │
    └→ [Goods proceed to arrival]
```

### Customs Declaration Phase
```
CDS Declaration (Post-Arrival)
    ↓
    → DMSACC (Accepted)
    ├→ DMSTAX (Tax Calculated)
    ├→ DMSCLE/DMSROG (Cleared/Released)
    └→ DMSREJ (Rejected - requires amendment)
```

### Complete Journey
```
IE315 → IE328 → [Goods Arrive] → CDS Declaration → DMSACC → DMSTAX → DMSCLE → [Goods Released]
```

## Example Journey

1. Importer/agent submits IE315 (ENS) up to 200 days before goods arrive
2. HMRC S&S GB issues IE328 (MRN allocated) - goods proceed to export
3. Goods arrive at UK port
4. Importer/agent submits full customs declaration via CDS
5. HMRC CDS issues DMSACC (declaration accepted)
6. HMRC CDS issues DMSTAX (tax and duty calculated)
7. HMRC CDS issues DMSCLE (cleared) or DMSROG (released)
8. Importer collects/releases goods

**If High-Risk Issues Detected:**
- HMRC S&S GB may issue IE351 (Do Not Load) before goods depart origin
- Goods are prevented from loading onto transport
- Importer/agent must resolve the issue with customs

**If Errors in ENS:**
- IE316 is issued instead of IE328
- Importer/agent must resubmit corrected IE315
- Process restarts

## Message Type Definitions

### Phase 1: Safety & Security (S&S GB) Messages

#### IE315 - Entry Summary Declaration (ENS)
**Sender:** Importer/Agent
**Recipient:** HMRC (S&S GB)
**Description:** The pre-arrival safety and security declaration submitted for goods entering Great Britain. Contains information about the consignment, parties involved, and goods description. Must be submitted before goods arrive (up to 200 days in advance). From January 31, 2025, consists of 20 mandatory fields and 8 conditional fields.

#### IE316 - Entry Summary Declaration Rejection
**Sender:** HMRC (S&S GB)
**Recipient:** Importer/Agent
**Description:** Rejection notification issued when the submitted ENS (IE315) contains errors or fails validation. The declaration must be corrected and resubmitted as a new IE315.

#### IE328 - Entry Summary Declaration Acknowledgement
**Sender:** HMRC (S&S GB)
**Recipient:** Importer/Agent
**Description:** Acknowledgement that the ENS has been successfully received and accepted. Includes the allocated Movement Reference Number (MRN) which is essential for tracking the import through all subsequent stages.

#### IE313 - Entry Summary Declaration Amendment
**Sender:** Importer/Agent
**Recipient:** HMRC (S&S GB)
**Description:** Request to amend or correct information in a previously submitted ENS (IE315). Can only be submitted before the goods have arrived. Cannot be submitted after an arrival notification has been received.

#### IE304 - Entry Summary Declaration Amendment Acceptance
**Sender:** HMRC (S&S GB)
**Recipient:** Importer/Agent
**Description:** Confirmation that the ENS amendment (IE313) has been accepted and the record has been updated accordingly.

#### IE305 - Entry Summary Declaration Amendment Rejection
**Sender:** HMRC (S&S GB)
**Recipient:** Importer/Agent
**Description:** Rejection notification for an ENS amendment (IE313). May occur if the amendment request contains errors or if an arrival notification for that MRN has already been received, preventing further amendments.

#### IE351 - Advanced Intervention Notification (Do Not Load)
**Sender:** HMRC (S&S GB)
**Recipient:** Importer/Carrier
**Description:** High-risk intervention notification instructing that goods must NOT be loaded onto the means of transport. Issued when customs has identified a need for intervention or high-risk assessment. Goods cannot proceed until the issue is resolved with HMRC. Prevents goods from leaving the origin country.

### Phase 2: Customs Declaration (CDS) Messages

#### CDS Import Declaration
**Sender:** Importer/Agent
**Recipient:** HMRC (CDS)
**Description:** The full customs declaration for import submitted after goods have arrived at a UK port. Contains detailed information about goods, values, tariff classifications, licenses, and origin. Can be submitted up to 30 days before or within 3 months after goods arrival. Used to calculate and assess customs duty and VAT.

#### DMSACC - Declaration Accepted
**Sender:** HMRC (CDS)
**Recipient:** Importer/Agent
**Description:** Notification that the customs declaration has been received and successfully validated by the CDS system. Indicates no immediate errors were found in the submission.

#### DMSTAX - Tax Calculation
**Sender:** HMRC (CDS)
**Recipient:** Importer/Agent
**Description:** Detailed notification showing the calculated customs duty, VAT, and any other charges due on the imported goods. Represents the "indicative customs debt" that must be paid before or upon release of goods.

#### DMSCLE - Declaration Cleared
**Sender:** HMRC (CDS)
**Recipient:** Importer/Agent
**Description:** Notification that goods have been cleared by customs and permission is granted to release/collect the goods. Indicates all customs procedures are complete and debt has been satisfied.

#### DMSROG - Declaration Released or Granted
**Sender:** HMRC (CDS)
**Recipient:** Importer/Agent
**Description:** Alternative notification indicating goods have been released. May be issued when debt is calculated as provisional, meaning some finalisation activities may still be required post-release.

#### DMSREJ - Declaration Rejected
**Sender:** HMRC (CDS)
**Recipient:** Importer/Agent
**Description:** Rejection notification indicating the customs declaration contains errors or fails validation. The declaration must be amended and resubmitted before goods can be cleared.

#### CDS Amendment
**Sender:** Importer/Agent
**Recipient:** HMRC (CDS)
**Description:** Request to amend or correct information in a previously submitted customs declaration. Can typically be submitted within 90 days of the original declaration.

#### CDS Cancellation
**Sender:** Importer/Agent
**Recipient:** HMRC (CDS)
**Description:** Request to cancel a submitted customs declaration. May be used if goods are not proceeding as planned or if a declaration was submitted in error.

## Key Differences Between Systems

### S&S GB (Safety & Security)
- **Mandatory:** Yes, for all goods entering Great Britain
- **Timing:** Pre-arrival (up to 200 days before)
- **Purpose:** Safety, security, and risk assessment
- **Messages:** IE315, IE316, IE328, IE313, IE304, IE305, IE351
- **Data Fields:** 20 mandatory + 8 conditional fields (as of Jan 31, 2025)

### CDS (Customs Declaration Service)
- **Timing:** Up to 30 days before or within 3 months after arrival
- **Purpose:** Customs duty and tax assessment
- **Messages:** CDS Declaration, DMSACC, DMSTAX, DMSCLE, DMSROG, DMSREJ
- **Full Detail:** Requires complete commercial and tariff information

## Important Considerations

- Both systems are required for most imports into Great Britain
- IE351 (Do Not Load) can completely prevent goods from departing the origin country
- ENS amendments cannot be made after goods arrive
- CDS declarations can be amended within 90 days
- Failure to submit ENS before goods arrive may result in goods being held
- Customs duty must be paid before or upon release under DMSCLE
- Different rules may apply for Northern Ireland (ICS NI)
- Software must be XML-compatible to submit S&S GB declarations

## References

- [Safety and Security Import Declarations Service Guide - HMRC](https://developer.service.hmrc.gov.uk/guides/safety-and-security-import-declarations-end-to-end-service-guide/)
- [Making an Entry Summary Declaration - GOV.UK](https://www.gov.uk/guidance/making-an-entry-summary-declaration)
- [HMRC CDS Declaration Submission - Import](https://www.basda.org/wp-content/uploads/2022/05/CDS-03-Declaration-Submission-Service-Design-Imports-v2.0-180424-BW-min-Accessible.pdf)
- [Receiving Notifications - HMRC Customs Declarations End-to-End Service Guide](https://developer.service.hmrc.gov.uk/guides/customs-declarations-end-to-end-service-guide/documentation/notifications.html)
- [Entry Summary Declaration (ENS): A Comprehensive Guide - iCustoms](https://www.icustoms.ai/blogs/entry-summary-declaration-ens-guide/)
- [Submitting Import and Export Customs Declarations - HMRC CDS Guide](https://developer.service.hmrc.gov.uk/guides/customs-declarations-end-to-end-service-guide/documentation/submitting-import-and-export-customs-declarations.html)