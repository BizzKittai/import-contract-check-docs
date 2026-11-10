# Data handling — local plugin

Product data-handling notice, 10 November 2026. Controller and product contact: BizzKitt BV, Frederikstraat 67, 3034 LD Rotterdam, Netherlands; hello@bizzkitt.ai.

Import Contract Check reads only the local CSV and contract the user selects.
Their bytes are held in memory for parsing, validation and SHA-256 hashing.
The plugin does not upload these files, call an AI model, use analytics, or send
validation events to BizzKitt BV. It has no validation backend or user account.
It does not edit either input. It writes a report only when the user chooses
Export and a destination, with explicit confirmation before replacement.

Reports omit data-cell values and input paths. They include header/field names,
rule names, record and source positions, counts and hashes of the input files.
These are not guaranteed anonymous: a header may contain personal information
and a hash can identify a known file. Review a report before sending it elsewhere.
Error text shown in the IDE can include a local filesystem path or invalid
contract property; no such text is uploaded by this plugin.

JetBrains' IDE, Marketplace and licensing services have their own data handling.
The paid build reads the IDE's license confirmation and verifies the
JetBrains signature locally; activation, account and payment flows are handled
by JetBrains. "No file uploads" is not a claim that the entire IDE is offline.

## Support and Marketplace information

If you choose to contact hello@bizzkitt.ai, BizzKitt BV receives the message and contact information you provide through its business email service. Send the plugin/IDE versions, rule name and a minimal fictional reproducer. Do not send production files, license tokens, passwords, personal records or payment details.

We use support correspondence to answer the request, investigate defects and provide the requested service. Information necessary to perform a customer's contract is processed for that purpose; ordinary business-contact correspondence is used for the legitimate interest of responding to that contact. We retain correspondence only as long as needed for the request, relevant follow-up or applicable legal obligations. This notice does not imply an automatic deletion system or that correspondence is anonymous.

You can contact the above address about access, correction, deletion, restriction, objection or portability where applicable. You may also contact the Dutch Autoriteit Persoonsgegevens or your competent supervisory authority. The scope of these rights depends on applicable law and the circumstances. See the [European Data Protection Board’s explanation of these rights](https://www.edpb.europa.eu/sme/be-compliant/respect-individuals-rights_en).

JetBrains operates the Marketplace and account/licensing services separately. Consult its [Privacy Notice](https://www.jetbrains.com/legal/docs/privacy/privacy/) for those services. BizzKitt BV may receive order/license information made available to the vendor by Marketplace to administer sales and support. The plugin itself does not collect payment details.
