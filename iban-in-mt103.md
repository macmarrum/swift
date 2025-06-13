In an MT103 message, an IBAN can appear in the "account number" component of several fields, particularly those identifying parties or accounts involved in the transaction.

The most common and critical fields that can contain an IBAN are:

1.  **Field 50a: Ordering Customer (Payer)**
    * This field identifies the customer (payer) who initiated the payment.
    * For options 50A, 50F, and 50K, the account number line can contain an IBAN, especially for payments originating from an IBAN-country. It is often the first line of this field.

2.  **Field 59a: Beneficiary Customer**
    * This field identifies the ultimate recipient of the funds.
    * For options 59 (no letter suffix implies a specific format, often including the account) and 59A, the account number line is where the IBAN for the beneficiary is typically placed.
    * **Crucially:** If Field 57A (Account with Institution) is not present, the IBAN in Field 59a is often **mandatory** (especially if the country code of the beneficiary's bank is within the SEPA/IBAN area). Even if 57A is present, if the country code of the BIC in 57A is an IBAN country, the IBAN in 59a is mandatory.

Beyond the direct customer fields, IBANs can also appear in fields related to the correspondent banks if a specific account number at that correspondent is being identified:

3.  **Field 53a: Sender's Correspondent**
    * This field specifies the bank through which the sender will reimburse the receiver.
    * If options **53B (Location)** or **53D (Name and Address)** are used, an account number (which could be an IBAN) can be provided on the first line to specify the Sender's Nostro account at that correspondent.

4.  **Field 54a: Receiver's Correspondent**
    * This field specifies a bank via which the receiver will be reimbursed.
    * Similar to 53a, if options **54B (Location)** or **54D (Name and Address)** are used, an account number (which could be an IBAN) can be provided.

5.  **Field 57a: Account with Institution (Beneficiary's Bank)**
    * This field identifies the financial institution where the beneficiary's account is held, when different from the direct receiver of the message.
    * While primarily intended for the BIC of the beneficiary's bank, options **57B (Location)** or **57D (Name and Address)** can contain an account number (which could be an IBAN) if it's relevant to identify a specific account at that institution.

**In summary, the most common and definitive places for an IBAN in an MT103 are the account lines within Field 50a (Ordering Customer) and Field 59a (Beneficiary Customer). It can also appear in the correspondent bank fields (53a, 54a) and the beneficiary's bank field (57a) if a specific account number at those institutions needs to be indicated using the relevant options.**
