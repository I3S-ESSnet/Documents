# Overall security
The description provides a brief documentation with an overview of relevant concepts to support a security modell for establishing services in a cloud environment. The documentation is based on the description of the security model in Statistics Norway (SSB Developer Guide) and documentation of deliverables in WP1, WP2 and WP3 in I3S. 

## Zero Trust
Zero Trust, Zero Trust Network, or Zero Trust Architecture refer to security concepts and threat model that no longer assumes that actors, systems or services operating from within the security perimeter should be automatically trusted, and instead must verify anything and everything trying to connect to its systems before granting access.

Service mesh is often considered as an important infrastructure component for facilitating Zero Trust in a micro service architecture.

References:
- [What is a Zero Trust Architecture?](https://www.infradata.com/resources/what-is-a-zero-trust-architecture/)
- [BeyondProd](https://cloud.google.com/security/beyondprod)
- [BeyondCorp](https://cloud.google.com/beyondcorp)
- [BeyondTrust](https://www.beyondtrust.com/blog/entry/why-zero-trust-is-an-unrealistic-security-model)

## Service Mesh
In software architecture, a service mesh is a dedicated infrastructure layer for facilitating service-to-service communications between micro services, often using a sidecar proxy.

Having such a dedicated communication layer can provide a number of benefits, such as providing observability into communications, providing secure connections, or automating retries and backoff for failed requests.

References:
- [Service mesh](https://en.wikipedia.org/wiki/Service_mesh)
- [What is Istio?](https://istio.io/latest/docs/concepts/what-is-istio/)

## User administration and authentication
Authentication is the process of verifying a users identity.

*Azure AD is used as the identity provider for SSB users. Users and groups are managed in an on prem AD and synchronized to Azure AD. Keycloak is used for providing OAuth 2 and OIDC support to applications running in Google Kubernetes Engine (GKE). Read more about authentication in BIP in the Authentication services documentation.*

## Authorization
Role-based access control (RBAC) is a method of restricting access to data and operations a user can perform based on the users role in the Organization.

Access control in applications running in BIP should be implemented using a role based access control system. But it is possible that Attribute based access control (ABAC) is used to some extent, especially when it comes to data ownership.

## Logging and Monitoring
Logging is important in any security model for auditing and forensics.

Log scraping should be done for alle Applications. It is especially important that access related information is logged by applications to assist with auditing.

References:
- [OWASP Logging Guide](https://owasp.org/www-pdf-archive/OWASP_Logging_Guide.pdf)
- [Logging Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html)

## Automated Configuration Management
The role of automated configuration management is to maintain systems in a desired state in order to reduce cost, complexity and errors. This is especially important in a Zero Trust architecture where configuration transparency, traceability and consistency in a system is essential for security.

Terraform, Ansible and declarative manifests for describing system and application state and GIT for change management and traceability is often used.

## Managing secrets
Secrets like passwords, certificates and keys are probably the hardest assets to manage in any system, but also the most important asset. Leaked keys can lead to unauthorized access to sensitive data and have severe consequences for the organizations trust, reputation and reliability.

Examples of tools is Secret Manager, Berglas and Sealed secrets. 
