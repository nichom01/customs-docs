# UK to Northern Ireland Export Journey: Customs Guide

## Overview

The UK (Great Britain) to Northern Ireland (NI) customs procedure differs significantly from both UK-to-EU exports and UK-to-rest-of-world exports due to the Northern Ireland Protocol and Windsor Framework.

**Critical Point:** GB to NI is technically an **import** procedure from NI's perspective, not an export procedure. GB is treated as a third country with respect to Northern Ireland under the protocol.

## Two-Lane System: Green Lane vs Red Lane

As of May 2025, goods moving from Great Britain to Northern Ireland operate under a two-lane system determined by whether goods are "at risk" of entering the EU:

### Green Lane (UK Internal Market Lane)
**For: "Not At Risk" Goods**

Goods that will NOT enter the EU and have zero or lower EU duty rates qualify for the simplified Green Lane. UKIMS (UK Internal Market Scheme) authorised traders can provide minimal data.

### Red Lane (Full EU Customs Controls)
**For: "At Risk" Goods**

Goods destined for the EU or Ireland, or goods with higher EU duty rates, must follow the full Red Lane with complete EU-equivalent customs controls and tariff payment.

## Complete GB to NI Journey - Import/Customs Flow

### Phase 1: Pre-Movement Safety & Security Declaration

| Sequence | Document/Message | Name | Sender | Recipient | Purpose |
|----------|------------------|------|--------|-----------|---------|
| **1** | **ENS or IE315** | Entry Summary Declaration | Importer/Agent/Carrier | ICS2 or TSS (HMRC) | Pre-arrival safety and security notification; mandatory for all GB to NI movements; submitted before goods depart GB |
| **2** | **TIMS Submission** | Trader Integration Micro Service | Importer/Software | ICS2 (HMRC) | Automated submission of ENS to ICS2; free service provided by HMRC; no registration required |

### Phase 2: Simplified or Standard Declaration (Pre-Movement)

| Sequence | Document/Message | Name | Sender | Recipient | Purpose |
|----------|------------------|------|--------|-----------|---------|
| **3a (Green Lane)** | **SFD or Simplified Data** | Simplified Frontier Declaration | Importer/Agent | CDS (HMRC) | Minimal data set submitted pre-movement for "not at risk" goods using TSS or CDS; auto-generated from ENS information; UKIMS authorisation details included |
| **3b (Red Lane)** | **Full CDS Declaration** | Full Import Declaration | Importer/Agent | CDS (HMRC) | Complete customs declaration required for "at risk" goods with full EU equivalent checks and tariff assessment |

### Phase 3: Post-Movement (For Green Lane - TSS Simplified Procedure Only)

| Sequence | Document/Message | Name | Sender | Recipient | Purpose |
|----------|------------------|------|--------|-----------|---------|
| **4** | **Supplementary Declaration** | TSS Supplementary Declaration | Importer/Agent | CDS (HMRC) | Post-movement submission of full goods information (within specified timeframe); completes the two-step TSS simplified procedure; only for Green Lane "not at risk" goods |

### Phase 4: Declaration Response Messages

| Sequence | Message | Name | Sender | Recipient | Purpose |
|----------|---------|------|--------|-----------|---------|
| **5a** | **DMSACC** | Declaration Accepted | CDS (HMRC) | Importer/Agent | Notification that declaration has been received and accepted |
| **5b** | **DMSCLE/DMSROG** | Declaration Cleared/Released | CDS (HMRC) | Importer/Agent | Notification that goods are cleared and can be released into NI |
| **5c** | **DMSREJ** | Declaration Rejected | CDS (HMRC) | Importer/Agent | Notification that declaration contains errors and must be amended |

## Key Status and Classification Codes

### "At Risk" vs "Not At Risk" Determination

**Goods are "Not At Risk" when:**
- Applicable EU rate of duty is zero, AND
- No threat of movement to the EU, AND
- UKIMS authorisation is held (if using Green Lane)

**Goods are "At Risk" when:**
- Applicable EU duty rate is higher than UK rate, OR
- Goods are destined for Ireland or EU, OR
- No UKIMS authorisation held, OR
- Goods contain restricted or prohibited items

### CDS Codes for NI Movements

| Code | Description | Usage |
|------|-------------|-------|
| **NIREM** | Not at Risk - UKIMS Exemption | Declared at goods item level in DE 2/2 to indicate "not at risk" status with valid UKIMS authorisation |
| **NIPRO** | Not at Risk - Preferential Origin | Indicates preferential origin status for non-at-risk goods |
| **NIQUO** | Not at Risk - Quota Relief | Indicates goods qualify for quota relief as "not at risk" |
| **VAT Z** | VAT Zero-Rated | Used in CDS for zero-rated supplies (where applicable) |

## Timeline & Key Deadlines

**Pre-Movement Requirements:**
- ENS must be submitted before goods depart GB (mandatory)
- SFD (for Green Lane) submitted before or at time of movement
- Full declaration (for Red Lane) submitted before goods arrive in NI

**Post-Movement Deadlines:**
- Supplementary Declaration (Green Lane TSS): Must be submitted within specified timeframe after goods arrival
- Amendment deadline: Typically within 90 days of original declaration submission

**Note:** ICS2 is now live and will replace ICS NI. ICS2 became mandatory from 31 December 2025.

## Declaration Flow

### Green Lane ("Not At Risk") Flow
```
ENS (IE315) → TIMS Automatic Submission to ICS2 → Simplified Frontier Declaration (SFD)
→ CDS Acceptance (DMSACC) → CDS Clearance (DMSCLE) → Goods Released into NI
→ Post-Movement: Supplementary Declaration → Final Clearance
```

### Red Lane ("At Risk") Flow
```
ENS (IE315) → TIMS Automatic Submission to ICS2 → Full CDS Import Declaration
→ CDS Acceptance (DMSACC) → [Full EU Customs Checks] → CDS Clearance (DMSCLE)
→ Customs Duty/Tariff Payment → Goods Released into NI
```

## Example Journeys

### Scenario 1: Green Lane - "Not At Risk" Goods (UKIMS Authorised Trader)

1. Importer holds valid UKIMS authorisation
2. Goods sourced in GB with zero EU tariff rate
3. Destination: Northern Ireland only (no onward movement to EU/Ireland)
4. Importer/agent submits ENS to ICS2 (before goods depart GB)
5. TIMS automatically routes ENS to ICS2
6. TSS generates Simplified Frontier Declaration with reduced data set
7. Goods depart GB and travel to NI
8. Goods arrive in NI, declaration status checked in CDS
9. CDS issues DMSACC (accepted)
10. CDS issues DMSCLE (cleared)
11. Goods released immediately into NI
12. Within 14 days (typical): Supplementary Declaration submitted with full details
13. Final clearance confirmed
14. Zero customs duty payable

### Scenario 2: Red Lane - "At Risk" Goods (Full Customs Controls)

1. Importer holds no UKIMS authorisation, OR goods destined for Ireland, OR EU tariff rate applies
2. Goods classified as "at risk"
3. Importer/agent submits ENS to ICS2 (before goods depart GB)
4. Importer/agent submits full CDS Import Declaration with all EU equivalent details
5. Goods depart GB and travel to NI
6. Goods arrive in NI
7. CDS validates declaration
8. CDS issues DMSACC (accepted)
9. Full EU-equivalent customs checks initiated (documentary, physical, risk-based)
10. Customs duty calculated and assessed (per NI Online Tariff)
11. If duty owed: must be paid before goods released
12. CDS issues DMSCLE (cleared) after checks and duty paid
13. Goods released into NI
14. No supplementary declaration needed (full declaration submitted pre-movement)

## Important Distinctions

### GB to NI vs GB to EU

| Aspect | GB to NI | GB to EU |
|--------|----------|----------|
| **Declaration Type** | Import declaration (NI treats GB as 3rd country) | Export declaration |
| **IE Messages** | IE315 (ENS), CDS notifications (DMSXXX) | IE515, IE501, IE507, IE525, IE590, IE599 |
| **Safety & Security** | ENS mandatory via ICS2 | Exit Summary Declaration |
| **Tariff Applied** | NI Online Tariff / EU Tariff | UK Trade Tariff |
| **Duty Assessment** | EU duty rates apply | No UK duty (export) |
| **Proof of Supply** | DMSACC/DMSCLE | DMSEOG (IE599) |
| **Green/Red Lane** | Two-lane system applies | Not applicable |
| **UKIMS** | May qualify for Green Lane | Not applicable |

### GB to NI vs GB to Rest of World

| Aspect | GB to NI | GB to Rest of World |
|--------|----------|-------------------|
| **Customs Regime** | Import procedure (3rd country status) | Export procedure |
| **Tariff** | NI/EU tariff rates | UK Trade Tariff (export) |
| **Duty Payable** | Yes (EU rates) | No (export) |
| **Declarations** | Import + ENS | Export declaration |
| **Lane System** | Green/Red lanes | Not applicable |
| **Final Proof** | DMSACC/DMSCLE | DMSEOG |

## Critical Requirements

### Mandatory for All GB to NI Movements

1. **Entry Summary Declaration (ENS/IE315)** - MUST be submitted before goods depart GB
2. **Declaration to CDS** - Either SFD (Green Lane) or full declaration (Red Lane)
3. **Risk Assessment** - Determine "at risk" or "not at risk" status
4. **EORI Number** - Importer/declarant must have valid EORI

### Green Lane ("Not At Risk") Requirements

- UKIMS authorisation must be held
- Goods classified as zero-tariff with no onward movement to EU
- Two-step procedure: pre-movement SFD + post-movement supplementary declaration
- Reduced data submission via TSS

### Red Lane ("At Risk") Requirements

- Full customs declaration with all commercial and tariff details
- Customs duty must be assessed and paid (if applicable)
- Full EU-equivalent customs controls apply
- May include physical inspections, document checks, risk assessment

## Windsor Framework Updates (May 2025)

The Windsor Framework introduced significant simplifications:

- **UK Internal Market Lane** allows simplified data submission for qualifying goods
- **UKIMS Authorisation** provides pathway to Green Lane
- Reduces administrative burden for compliant traders
- Maintains full EU customs controls for "at risk" goods

## Important Notes

- **No Export Declaration Required in GB** - GB to NI is import-based, not export-based
- **ICS2 Now Mandatory** - Replaced ICS NI; became mandatory 31 December 2025
- **TIMS Integration** - Free automatic ENS submission service
- **TSS Alternative** - TSS can be used by hauliers for ENS submission (submits to ICS2)
- **NI/Ireland Trade** - Goods moving NI to Ireland/Ireland to NI have NO customs requirements
- **Tariff Determination** - CDS checks both GB and NI tariffs to determine duty
- **Supplementary Declarations** - Only required for Green Lane TSS simplified procedure

## References

- [Moving Goods from Great Britain to Northern Ireland - GOV.UK](https://assets.publishing.service.gov.uk/media/605b26dae90e0724cad2c980/Northern_Ireland_Trade_Explainer_V7.pdf)
- [Guidance for the Import Control System Northern Ireland (ICS NI) - GOV.UK](https://www.gov.uk/government/publications/import-control-system-guidance-for-the-uk/guidance-for-the-import-control-system-northern-ireland-ics-ni)
- [Simplifying Entry Summary Declaration & TSS for GB-NI Movement - iCustoms](https://www.icustoms.ai/blogs/importing-gb-to-ni-guide-tss-entry-summary-declarations/)
- [A Beginner's Guide for Moving Goods to Northern Ireland - NI Customs & Trade Academy](https://www.nicustomstradeacademy.co.uk/guides/beginners-guide/)
- [Moving Goods to or from Northern Ireland - Logistics UK](https://logistics.org.uk/international-trade/logisticsuk-brexit-advice/industry-and-government-advice-1/moving-goods-to-or-from-northern-ireland)
- [Introduction of the Windsor Framework - AEB Help Center](https://service.aeb.com/hc/en-us/articles/28927857161617-Introduction-of-the-Windsor-Framework)
- [CDS Declaration Completion Instructions for Imports - GOV.UK](https://www.gov.uk/government/publications/cds-uk-trade-tariff-volume-3-import-declaration-completion-guide)
- [A Guide to Trading in Northern Ireland and the Windsor Framework - InterTrade Ireland](https://crossbordertradehub.intertradeireland.com/trading-in-ni-and-windsor-framework)
