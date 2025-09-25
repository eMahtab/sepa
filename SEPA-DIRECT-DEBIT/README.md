# SEPA Direct Debit

SEPA Direct Debit is an XML-based format that follows the ISO 20022 standard for initiating direct debit collections in the Single Euro Payments Area.


This file contains:

1. **A header section (GrpHdr) with message identification, creation timestamp, transaction count, and creditor information**

2. **Payment information section (PmtInf)** with details about the collection

3. **Two direct debit transactions (DrctDbtTxInf)** for different customers

## Key elements included:

* Creditor identification and account information

* Debtor details (customers being charged)

* Mandate references and signature dates

* Transaction amounts and remittance information

* BIC codes for the financial institutions

This is a CORE scheme file (for consumers) with RCUR sequence type (recurring payment). 

The file requests collection of €600 total (€400 from John Smith and €200 from Maria Garcia) to be collected on May 10, 2025.



```xml
<?xml version="1.0" encoding="UTF-8"?>
<Document xmlns="urn:iso:std:iso:20022:tech:xsd:pain.008.001.02" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <CstmrDrctDbtInitn>
    <GrpHdr>
      <MsgId>MSGID-2025-04-26T12345</MsgId>
      <CreDtTm>2025-04-26T10:30:00</CreDtTm>
      <NbOfTxs>2</NbOfTxs>
      <CtrlSum>600.00</CtrlSum>
      <InitgPty>
        <Nm>ACME Corporation</Nm>
        <Id>
          <OrgId>
            <Othr>
              <Id>DE98ZZZ09999999999</Id>
              <SchmeNm>
                <Cd>SEPA</Cd>
              </SchmeNm>
            </Othr>
          </OrgId>
        </Id>
      </InitgPty>
    </GrpHdr>
    <PmtInf>
      <PmtInfId>PMTINFID-2025-04-26-1</PmtInfId>
      <PmtMtd>DD</PmtMtd>
      <BtchBookg>true</BtchBookg>
      <NbOfTxs>2</NbOfTxs>
      <CtrlSum>600.00</CtrlSum>
      <PmtTpInf>
        <SvcLvl>
          <Cd>SEPA</Cd>
        </SvcLvl>
        <LclInstrm>
          <Cd>CORE</Cd>
        </LclInstrm>
        <SeqTp>RCUR</SeqTp>
      </PmtTpInf>
      <ReqdColltnDt>2025-05-10</ReqdColltnDt>
      <Cdtr>
        <Nm>ACME Corporation</Nm>
      </Cdtr>
      <CdtrAcct>
        <Id>
          <IBAN>DE89370400440532013000</IBAN>
        </Id>
      </CdtrAcct>
      <CdtrAgt>
        <FinInstnId>
          <BIC>DEUTDEFFXXX</BIC>
        </FinInstnId>
      </CdtrAgt>
      <CdtrSchmeId>
        <Id>
          <PrvtId>
            <Othr>
              <Id>DE98ZZZ09999999999</Id>
              <SchmeNm>
                <Prtry>SEPA</Prtry>
              </SchmeNm>
            </Othr>
          </PrvtId>
        </Id>
      </CdtrSchmeId>
      <!-- First Transaction -->
      <DrctDbtTxInf>
        <PmtId>
          <EndToEndId>ENDTOEND-2025-04-26-1</EndToEndId>
        </PmtId>
        <InstdAmt Ccy="EUR">400.00</InstdAmt>
        <DrctDbtTx>
          <MndtRltdInf>
            <MndtId>MANDATE-2023-01-15-1</MndtId>
            <DtOfSgntr>2023-01-15</DtOfSgntr>
          </MndtRltdInf>
        </DrctDbtTx>
        <DbtrAgt>
          <FinInstnId>
            <BIC>COBADEFFXXX</BIC>
          </FinInstnId>
        </DbtrAgt>
        <Dbtr>
          <Nm>John Smith</Nm>
        </Dbtr>
        <DbtrAcct>
          <Id>
            <IBAN>DE12500105170648489890</IBAN>
          </Id>
        </DbtrAcct>
        <RmtInf>
          <Ustrd>Invoice 2025-123 Monthly Subscription</Ustrd>
        </RmtInf>
      </DrctDbtTxInf>
      <!-- Second Transaction -->
      <DrctDbtTxInf>
        <PmtId>
          <EndToEndId>ENDTOEND-2025-04-26-2</EndToEndId>
        </PmtId>
        <InstdAmt Ccy="EUR">200.00</InstdAmt>
        <DrctDbtTx>
          <MndtRltdInf>
            <MndtId>MANDATE-2024-03-20-2</MndtId>
            <DtOfSgntr>2024-03-20</DtOfSgntr>
          </MndtRltdInf>
        </DrctDbtTx>
        <DbtrAgt>
          <FinInstnId>
            <BIC>BYLADEM1001</BIC>
          </FinInstnId>
        </DbtrAgt>
        <Dbtr>
          <Nm>Maria Garcia</Nm>
        </Dbtr>
        <DbtrAcct>
          <Id>
            <IBAN>DE02100500000054540402</IBAN>
          </Id>
        </DbtrAcct>
        <RmtInf>
          <Ustrd>Invoice 2025-124 Annual Service</Ustrd>
        </RmtInf>
      </DrctDbtTxInf>
    </PmtInf>
  </CstmrDrctDbtInitn>
</Document>
```


# References :

SEPA Direct Debit XML fields details :
https://docs.oracle.com/en/applications/jd-edwards/localizations/9.2/eoael/group-header-elements.html
