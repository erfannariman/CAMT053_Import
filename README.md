### note
This project is still under development.

# Purpose of this project
The purpose of this project is to parse and transform a `CAMT.053` file into a dataframe.
I will not go into each and every tag, for that information you can check one of your banks CAMT implementation guidelines, for example: [ABN](https://www.abnamro.nl/nl/images/Content/022_Zakelijk_nieuwe_structuur/000_Gedeelde_documenten/pdf_sepa_betaalvereniging_ig_camt_v1-0.pdf)

# General information and benefits of CAMT reporting
* CAMT stands for _Cash Management_ and is an [ISO 20022](https://www.iso20022.org/payments_messages.page) (XML) standard globally 
* ISO defines the standards for electronic data exchanges between financial institutions
* ISO also calls it _"Universal financial industry message scheme"_
* Using these standards, it will allow banks and customers to use a standard way of reporting account information globally
* This consistency is essential so customers and system developers can rely on the fact that banks populate the information in a defined manner
* Banks can no longer store account information in their own manner
> * There are specific tags for specific information
> * Only differences can be that not all tags are always present, it depends on the type of transaction if certain tags are populated

--> The end goal is to improve the end to end business process from payments to reconciliation

# File specific information
CAMT.053 files are `.XML` files. Which means the data is stored in layers (or tree structure).
This means it is not as easy to read as tabular data (for example Excel)

To be able to parse this file, first we need to understand its structure.  
The XML tree of each CAMT.053 has the following format:
> Document
>> BkToCstmrStmt
>>> GrpHdr
>>>> Stmt
>>>>> Bal
>>>>> Ntry
>>>>>> NtryDtls
>>>>>>> Btch  
>>>>>>> TxDtls

## CrdtDbtInd
The specifications Balance (Bal), Entry (Ntry) and Batch (Btch) have the tag `CrdtDbtInd`.
This tag has two valid values: `DBIT` (Debit) and `CRDT` (Credit). These tags must be seen from the perspective of the receiving party. So the owner of the file must see a DBIT value as negative and CRDT as positive amount on the balance
