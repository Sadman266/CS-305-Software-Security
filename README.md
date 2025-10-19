# CS-305-Software-Security

**Overview **This repository contains the completed Artemis Financial Practices for Secure Software Report (Project Two) and the refactored Artemis Financial code base used to implement HTTPS, a /hash checksum endpoint, and OWASP dependency-check integration. The included artifacts demonstrate a vulnerability assessment, secure coding practices, certificate generation, and static dependency testing.

**Brief summary of the client and software requirements** Artemis Financial is a small financial services application owner that required hardening of an existing web application to protect client data in transit and to improve supply‑chain hygiene. The client asked that the application be refactored to use HTTPS, provide demonstrable data‑integrity verification, and integrate static dependency scanning so that known library vulnerabilities would be identified and either remediated or documented as accepted risk.

**What I did well and why secure coding matters** I clearly documented and implemented transport‑layer security (HTTPS), generated and installed a development keystore and certificate, and added a deterministic SHA‑256 checksum endpoint that includes a unique identifier for verification screenshots. I integrated OWASP Dependency‑Check to detect third‑party vulnerabilities and created targeted suppressions for verified false positives. Secure coding prevents data breaches, maintains customer trust, and reduces legal and financial exposure for companies; investing in these practices increases operational resilience and the company’s long‑term value.

**Most challenging or most helpful part of the assessment** The most challenging part was reconciling keystore formats, aliases, and passwords so the embedded Tomcat connector could load the keystore without errors. The most helpful part was running dependency scanning and learning how to craft precise suppression entries that avoid masking real vulnerabilities while removing known false positives from the report.

**How I increased layers of security and future assessment tools** I increased defense-in-depth by adding transport encryption (HTTPS), integrity verification (SHA‑256 checksum), and supply‑chain scanning (dependency-check). For future work I would add automated CI/CD gates for dependency scanning, SAST/DAST tools (e.g., SpotBugs, SonarQube, OWASP ZAP), and runtime protections (WAF, secret scanning). I would prioritize fixes based on CVSS, exploitability, and exposure, and consult vendor advisories and backport information when choosing mitigation strategies.

**How I verified code functionality and checked for new vulnerabilities** I validated functionality by building and running the application locally, exercising the /hash endpoint in a browser (and curl) to capture the input and SHA‑256 output, and confirming Tomcat started on port 8443. I re-ran mvn clean verify (including dependency-check) after refactoring to ensure no new high‑risk vulnerabilities were introduced. Any scanner findings were triaged, documented, and either remediated or suppressed with justification.

**Resources, tools, and practices used that will help in the future**

Java Keytool for keystore and certificate management.

Spring Boot properties for SSL configuration and local HTTPS testing.

Java MessageDigest (SHA‑256) for integrity checks.

OWASP Dependency-Check integrated into Maven for supply‑chain scanning.

**Key practices:** never store plaintext secrets in source, use AEAD ciphers for confidentiality in production, externalize secrets to KMS/secret manager, and document suppression decisions with review dates.

**Artifacts to show future employers** I would show the completed Practices for Secure Software Report, the refactored project demonstrating HTTPS and checksum functionality, the keytool commands used to create the keystore, and the dependency-check reports (before and after targeted suppressions). These artifacts demonstrate practical secure coding, dependency management, and the ability to document and justify security decisions.

**How to view the artifact in this repository**

Open the ProjectTwo folder for the Practices for Secure Software Report (Word/PDF) and the zipped refactored code.

Read the README sections above, then run the included build instructions to reproduce the keystore, start the application, and visit https://localhost:8443/hash to confirm the checksum output.

Notes and next steps This repository is intended for portfolio presentation. For production deployment, keystores should be generated and stored in a managed KMS/HSM, certificates must be obtained from trusted CAs, and automated CI/CD security checks should be enabled to enforce dependency and code‑quality gates.

-- End of README content --
