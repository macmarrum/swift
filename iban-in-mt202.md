Unlike the MT103, which is a **customer credit transfer** and therefore prominently features IBANs for the Ordering Customer (payer) and Beneficiary Customer, the **MT202 (General Financial Institution Transfer)** is primarily for **bank-to-bank transfers**. This means the focus is on the financial institutions involved, identified by their BICs.

However, an IBAN can still appear in an MT202, specifically when an account number at one of the involved financial institutions needs to be specified. The key fields where an IBAN might be found are:

1.  **Field 52a: Ordering Institution**
    * This field identifies the financial institution that is the "ordering customer" for this specific bank-to-bank transfer. While it primarily contains the BIC (Option A) or name and address (Option D) of the ordering bank, an account number (which could be an IBAN) can be included, especially with **Option D** or potentially **Option A** if specific account details are required for identification or debiting purposes.

2.  **Field 53a: Sender's Correspondent**
    * This field specifies the bank through which the sender (Ordering Institution) will reimburse the Receiver.
    * If options **53B (Location)** or **53D (Name and Address)** are used, an account number (which could be an IBAN) can be provided to specify the Sender's Nostro account at that correspondent.

3.  **Field 54a: Receiver's Correspondent**
    * This field specifies a bank via which the Receiver of the MT202 will be reimbursed.
    * Similar to 53a, if options **54B (Location)** or **54D (Name and Address)** are used, an account number (which could be an IBAN) can be provided.

4.  **Field 56a: Intermediary Institution**
    * This field identifies an institution that acts as an intermediary in the payment chain between the Sender's Correspondent and the Account With Institution/Beneficiary Institution.
    * If options **56B (Location)** or **56D (Name and Address)** are used, an account number (which could be an IBAN) can be provided if a specific account at this intermediary is relevant for routing or processing.

5.  **Field 57a: Account with Institution**
    * This field identifies the financial institution where the beneficiary's account is held, when different from the direct receiver of the MT202.
    * While often containing a BIC (Option A), if options **57B (Location)** or **57D (Name and Address)** are used, an account number (which could be an IBAN) can be specified, particularly if a specific account at that institution needs to be identified for credit.

6.  **Field 58a: Beneficiary Institution**
    * This field identifies the ultimate financial institution that will receive the funds of this bank-to-bank transfer.
    * While typically containing a BIC (Option A), if **Option D (Name and Address)** is used, an account number (which could be an IBAN) can be provided. Some guidelines, particularly for specific currency clearings (e.g., ILS as per some search results), explicitly state that an IBAN is required for the beneficiary institution's account in Field 58A even when Option A (BIC) is used for the institution itself (e.g., by preceding the IBAN with `/` and then the BIC on a separate line or subsequent character positions).

**Key Difference from MT103:**

The MT202 does **not** have fields for "Ordering Customer" (like MT103's Field 50a) or "Beneficiary Customer" (like MT103's Field 59a) that would directly contain customer IBANs. An MT202 is about moving funds *between banks*. If it's a "cover" for a customer payment, the customer details (including their IBANs) are in the separate MT103 message, and the MT202 usually only contains references to it.

Therefore, any IBANs in an MT202 will generally relate to **internal bank accounts** (Nostro/Loro accounts) at the various financial institutions in the payment chain, rather than end-customer accounts.
