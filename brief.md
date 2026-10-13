Skeleton: NAFATH-V1

My track: Networking

## Overview:

NAFATH will give citizens one identity account for many government services through a mobile app and website. The authority must separate authentication, which confirms who signed in, from authorization, which defines what each connected service may access. It must secure network lookups, limit mobile permissions, and apply phishing-resistant sign-in. AI can help detect suspicious access, but only if risks such as bias, false alarms, privacy loss, and model drift are measured and managed. Data rules influence every layer: identity attributes, login telemetry, risk scores, retention, and sharing with service agencies. The project should therefore agree on standards, minimal data flows, user recovery, incident response, and legal responsibilities before launch, then test these controls in a pilot and monitor them continuously.

## Software:

OAuth 2.0 is an authorization framework: it issues scoped access tokens so an app or service can call protected APIs without receiving a citizen’s password. OpenID Connect (OIDC) adds an identity layer over OAuth 2.0 and returns an ID Token that the client validates to confirm the signed-in user. Use OIDC for citizens’ login and OAuth 2.0 access tokens to limit each government service’s API permissions.

Resource: OpenID Connect Core 1.0 incorporating errata set 2 - https://openid.net/specs/openid-connect-core-1_0.html

## AI:

Use NIST’s AI Risk Management Framework (AI RMF 1.0): Govern, Map, Measure, and Manage. Before deployment, define accountable owners and intended use; assess false positives and missed attacks; test bias across relevant users and devices; examine privacy, security, data quality, and adversarial manipulation; validate performance on realistic login traffic; and monitor drift after launch. A risk score should trigger proportionate checks, not automatically deny essential public services without appeal or human review.

Resource: NIST AI Risk Management Framework (AI RMF 1.0) - https://doi.org/10.6028/NIST.AI.100-1

## Mobile:

Android requires sensitive permissions to be declared in the manifest and, for runtime permissions, requested in context when a user invokes a feature that needs protected data. The app must check permission status, explain why access is needed when appropriate, handle denial, and degrade gracefully. Routine sign-in should not need contacts, microphone, or location. Ask for camera access only for an optional feature such as scanning an identity document.

Resource: Request runtime permissions | Android Developers - https://developer.android.com/training/permissions/requesting
