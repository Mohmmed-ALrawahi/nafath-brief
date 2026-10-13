Skeleton: NAFATH-V1

My track: Networking

## Overview:

Your single sign-on platform connects citizens to multiple government services through a mobile app and website using one identity account. To build a secure and lawful infrastructure, six key technical domains must work together. Software engineering and cybersecurity separate user authentication from service authorization while applying phishing-resistant multi-factor sign-in. Mobile development limits app permissions, while secure networking protects domain lookups. Artificial intelligence automatically monitors traffic patterns to detect suspicious access, provided risks like false alarms, bias, and privacy loss are properly managed. Finally, strict data management ensures full compliance with Oman privacy regulations across all personal record storage and sharing. The project must agree on standards, recovery plans, and legal responsibilities before testing these controls in a pilot and monitoring them continuously.


## Software:

OAuth 2.0 is an authorization framework designed for delegated access, allowing third-party applications to access server resources without sharing credentials. OpenID Connect builds on OAuth 2.0 by adding an identity layer, specifically providing an ID token for user authentication and login verification. For your single sign-on service, OpenID Connect authenticates citizen identities during login, while OAuth 2.0 manages authorized access to specific government backend APIs and user data resources securely.

Resource: RFC 6749 - The OAuth 2.0 Authorization Framework - https://www.rfc-editor.org/rfc/rfc6749

## AI:

Use NIST’s AI Risk Management Framework (AI RMF 1.0): Govern, Map, Measure, and Manage. Before deployment, define accountable owners and intended use; assess false positives and missed attacks; test bias across relevant users and devices; examine privacy, security, data quality, and adversarial manipulation; validate performance on realistic login traffic; and monitor drift after launch. A risk score should trigger proportionate checks, not automatically deny essential public services without appeal or human review.

Resource: NIST AI Risk Management Framework (AI RMF 1.0) - https://doi.org/10.6028/NIST.AI.100-1

## Mobile:

Android requires sensitive permissions to be declared in the manifest and, for runtime permissions, requested in context when a user invokes a feature that needs protected data. The app must check permission status, explain why access is needed when appropriate, handle denial, and degrade gracefully. Routine sign-in should not need contacts, microphone, or location. Ask for camera access only for an optional feature such as scanning an identity document.

Resource: Request runtime permissions | Android Developers - https://developer.android.com/training/permissions/requesting

## Networking:

DNS over HTTPS (DoH) sends DNS queries and responses through HTTPS, protecting them in transit from many local or on-path observers and making tampering harder. It does not make citizens anonymous: the chosen resolver can still observe queries, and DoH does not encrypt unrelated app traffic or hide all destination information. DoH also does not replace DNSSEC, which supports DNS-data authenticity and integrity. Choose a trusted resolver and assess its logging policy.

Resource: RFC 8484 - DNS Queries over HTTPS (DoH) - https://www.rfc-editor.org/rfc/rfc8484.html

## Cybersecurity:

Phishing resistance means the authentication protocol binds proof cryptographically to the genuine service, preventing attackers from simply relaying stolen codes. NIST identifies WebAuthn/FIDO2 authenticators and client-authenticated certificates as examples. Passwords, SMS/email codes, and manually entered one-time passcodes are not phishing-resistant, even when used as a second factor. For citizens, prioritize passkeys/WebAuthn, protect recovery flows, and require stronger checks for sensitive account changes.

Resource: NIST SP 800-63B: Authentication and Authenticator Management, Section 3.2.5 - https://pages.nist.gov/800-63-4/sp800-63b/authenticators/

## Data:

Oman’s Personal Data Protection Law (Royal Decree 6/2022) was amended by Royal Decree 68/2026. Before launch, obtain legal advice on Article 3 exclusions, which may cover state-body processing within legally assigned powers. Where the law applies, document a lawful basis, explain processing purposes and contact details, minimise collection, secure records, set retention and disclosure controls, support data-subject rights, and follow rules for sensitive data and cross-border transfers. Review the 2024 Executive Regulation too.

Resource: Royal Decree 6/2022 Issuing the Personal Data Protection Law (Consolidated through Royal Decree 68/2026) - https://decree.om/2022/l20220006/

## Misconception in My Track:

A common misconception is that turning on DNS over HTTPS makes a user anonymous. RFC 8484 only protects the DNS exchange between the client and the selected resolver using HTTPS; it does not hide DNS queries from that resolver or prevent all other methods of tracking. Its Section 8, “Privacy Considerations,” discusses information observable on the wire and by the server, while Section 9, “Security Considerations,” explains that DoH transport security does not provide DNS-data integrity by itself. The correct design combines DoH with trusted resolver selection, sensible logging limits, HTTPS, and DNSSEC where appropriate.

## Open Question:

Which resolver can the authority approve for both mobile and web clients, and what logging, retention, DNSSEC-validation, and availability requirements will apply to it?
