# UK to EU Export Journey: IE Messages Guide

## Complete Export Journey: UK to EU - IE Messages Flow

### Main Export Process Messages

| Sequence | Message | Name | Sender | Recipient | Purpose |
|----------|---------|------|--------|-----------|---------|
| **1** | **IE515** | Export Declaration | Declarant/Exporter | HMRC (UK Office of Departure) | Declarant submits standard customs export declaration to release goods into export procedure |
| **2** | **IE528** | Export MRN Allocated | HMRC | Declarant | Confirms that a Movement Reference Number (MRN) has been allocated for the export |
| **3** | **IE529** | Export Release / Release for Export | HMRC (UK Office of Departure) | Declarant | Permission granted to release goods from the place of origin; goods cleared to proceed to exit point |
| **4** | **IE501** | Export Pre-Lodged Declaration | HMRC (UK Office of Departure) | Customs Office of Exit (EU) | Expected arrival information sent to the destination exit office |
| **5** | **IE507** | Arrival at Exit | Carrier/Trader at Exit | Customs Office of Exit (EU) | Notification that goods have physically arrived at the customs office of exit; triggers readiness for departure |
| **6** | **IE525** | Exit Release Notification | Customs Office of Exit (EU) | Declarant/Carrier | Permission granted to physically exit the customs territory |
| **7** | **IE590** | Exit Notification | Carrier | Customs Office of Exit (EU) | Confirmation that goods have physically left the customs territory of the EU |
| **8** | **IE599** | Export Notification | Customs Office of Exit (EU) | Customs systems/AES | Final notification confirming departure; confirms zero VAT treatment for export |

### Additional/Supporting Messages (If Needed)

| Message | Name | Purpose |
|---------|------|---------|
| **IE508** | Arrival at Exit Rejection | Rejection of IE507 message if data is incorrect |
| **IE509** | Export Cancellation Decision | Notification that export declaration has been cancelled |
| **IE513** | Export Declaration Amendment | Amendment/correction to export declaration (IE515) |
| **IE514** | Export Cancellation Request | Request to cancel the export declaration |
| **IE516** | Export Declaration Rejected | Notification that IE515 was rejected by customs |
| **IE551** | Export No Release | Notification that goods NOT released for export (failed customs check) |
| **IE560** | Export Control Decision Notification | Notification of customs control decision on export declaration |

## Timeline & Key Constraints

**1 hour before departure:** Declaration must be submitted (IE515)

**Release to Exit:** Once IE529 (Release for Export) received, goods can move to exit point

**90 days:** Exporters have 90 days to finalize the exit process with IE507 and IE590 after IE529 is received

**Before Physical Exit:** IE525 (Exit Release Notification) must be received before goods can physically leave the exit point

## Critical Dependencies

```
IE515 → IE529 → [Transport to Exit] → IE507 → IE525 → [Physical Exit] → IE590 → IE599
```

### Example Journey

1. Exporter submits IE515 at UK origin location
2. HMRC issues IE528 (MRN assigned)
3. HMRC issues IE529 (goods released)
4. HMRC sends IE501 to EU exit office with expected arrival details
5. Carrier physically delivers goods to EU exit point
6. Carrier submits IE507 (arrival at exit notification)
7. EU exit office issues IE525 (permission to exit)
8. Goods physically leave the EU
9. Carrier submits IE590 (exit confirmation)
10. System issues IE599 (final departure notification)

## Notes on UK-EU Trade

- UK exporters now operate under post-Brexit rules, so goods are treated as "third country" goods
- Exit procedures may vary slightly depending on the specific EU member state of exit
- Some traders may use Export Release Verification Service (ERVS) which eliminates IE507/IE590 requirement
- All messages are typically electronic and processed through national customs systems (HMRC for UK, respective member state systems for EU exit)

## Message Type Definitions

### IE501 - Export Pre-Lodged Declaration
**Sender:** HMRC (UK Office of Departure)
**Recipient:** Customs Office of Exit (EU)
**Description:** Sent by the customs office of export containing expected arrival information to the customs office of exit. This pre-notification allows the exit office to prepare for the incoming goods.

### IE507 - Arrival at Exit
**Sender:** Carrier/Trader at Exit
**Recipient:** Customs Office of Exit (EU)
**Description:** Submitted when goods physically arrive at the customs office of exit. Indicates goods are ready for export and triggers the next stage of the process. Only one IE507 per MRN can be lodged; subsequent ones are rejected.

### IE508 - Arrival at Exit Rejection
**Sender:** Customs Office of Exit (EU)
**Recipient:** Carrier/Trader
**Description:** Rejection notification sent when an IE507 message contains incorrect or problematic data.

### IE509 - Export Cancellation Decision
**Sender:** HMRC
**Recipient:** Declarant/Customs systems
**Description:** Notification that an export declaration has been cancelled by customs authorities.

### IE513 - Export Declaration Amendment
**Sender:** Declarant/Exporter
**Recipient:** HMRC
**Description:** Used to amend or correct an export declaration (IE515) after it has been submitted.

### IE514 - Export Cancellation Request
**Sender:** Declarant/Exporter
**Recipient:** HMRC
**Description:** Request submitted by the declarant to cancel an export declaration.

### IE515 - Export Declaration
**Sender:** Declarant/Exporter
**Recipient:** HMRC (UK Office of Departure)
**Description:** The standard customs export declaration submitted by the declarant to release goods into the export customs procedure. Must be submitted at least 1 hour before departure.

### IE516 - Export Declaration Rejected
**Sender:** HMRC
**Recipient:** Declarant/Exporter
**Description:** Notification that an export declaration (IE515) has been rejected by HMRC customs due to validation errors or other issues.

### IE525 - Exit Release Notification
**Sender:** Customs Office of Exit (EU)
**Recipient:** Declarant/Carrier
**Description:** Permission granted to physically exit the customs territory. Must be received before goods can physically leave the exit point.

### IE528 - Export MRN Allocated
**Sender:** HMRC
**Recipient:** Declarant/Exporter
**Description:** Notification that a Movement Reference Number (MRN) has been successfully allocated for the export declaration.

### IE529 - Export Release / Release for Export
**Sender:** HMRC (UK Office of Departure)
**Recipient:** Declarant/Exporter
**Description:** Permission granted to release goods from the place of origin. Goods are cleared to proceed to the exit point. This must be received before IE507 can be submitted.

### IE551 - Export No Release
**Sender:** HMRC
**Recipient:** Declarant/Exporter
**Description:** Notification that goods have NOT been released for export. Typically indicates that customs checks have failed or other compliance issues exist.

### IE560 - Export Control Decision Notification
**Sender:** HMRC or Customs Office of Exit
**Recipient:** Declarant/Customs systems
**Description:** Notification of the customs control decision made on the export declaration. May indicate whether goods require physical inspection or have been cleared.

### IE590 - Exit Notification
**Sender:** Carrier
**Recipient:** Customs Office of Exit (EU)
**Description:** Confirmation submitted by the carrier that goods have physically left the customs territory of the EU. This finalizes the exit process.

### IE599 - Export Notification
**Sender:** Customs Office of Exit (EU)
**Recipient:** Customs systems/Automated Export System (AES)
**Description:** Final notification confirming departure of goods from the customs territory. Confirms zero VAT treatment for the export and closes out the export movement.

## References

- [Procedure for standard customs declaration for exports - Tullverket](https://www.tullverket.se/en/startpage/business/internationalbusiness/exportinggoods/declaringgoodsforexport/typesofcustomsdeclarationsforexport/standardcustomsdeclarationforexports/procedureforstandardcustomsdeclarationforexports.4.3e6caad21870dc6781c36db.html)
- [IE507 and IE590 Automated Export System (AES) messages](https://www.thyme-it.com/2023/07/ie507-and-ie590-in-aes/)
- [Making a full export declaration - GOV.UK](https://www.gov.uk/guidance/making-a-full-export-declaration)
- [HMRC Customs Declarations End-to-End Service Guide](https://developer.service.hmrc.gov.uk/guides/customs-declarations-end-to-end-service-guide/documentation/submitting-import-and-export-customs-declarations.html)