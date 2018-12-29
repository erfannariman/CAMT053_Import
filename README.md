# Purpose of this project
The purpose of this project is to parse and transform a `CAMT.053` file into a dataframe.
I will not go into each and every tag, for that information you can check one of your banks CAMT implementation guidelines, for example: [ABN](https://www.abnamro.nl/nl/images/Content/022_Zakelijk_nieuwe_structuur/000_Gedeelde_documenten/pdf_sepa_betaalvereniging_ig_camt_v1-0.pdf)

# General information
* CAMT stands for _Cash Management_ and is an [ISO 20022](https://www.iso20022.org/payments_messages.page) (XML) standard globally 
* ISO defines the standards for electronic data exchanges between financial institutions
* ISO also calls it _"Universal financial industry message scheme"_
* Using these standards, it will allow banks and customers to use a standard way of reporting account information globally
* This consistency is essential so customers and system developers can rely on the fact that banks populate the information in a defined manner
* Banks can no longer store account information in their own manner
> * There are specific tags for specific information
> * Only differences can be that not all tags are mandatory, depends on the account of customer if some tags are populated
