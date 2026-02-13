# Context
This is a previous school deliverable conducted for a fictional client of their vulnerable web application, which was analyzed in a controlled white hat lab environment. The objective was to assess the security implemementation of a web application and identify exploitable vulnerabilities within the defined scope.

# Scope
The test focused exclusively on:
- Web application functionality
- Input validation mechanisms
- URL parameter handling
- Access control logic

The following were explicitily excluded:
- Host operating system
- Infrastructure configuration
- Social engineering
- CSRF, clickjacking and previously mapped vulnerabilities within the application

# Methodology
The testing process followed these phases:
- Reconnaissance
- Discovery of input vectors
- Exploitation through proof-of-concept payloads
- Documentation anc CVSS scoring

Primary tools and techniques used:
- Manual testing
- HTTP request interception and modification using Burp Suite
- Source code inspection via browser developer tools
- Payload testing for XSS and SQL injection
- CVSS v4.0 scoring for risk classification

The approach was mainly manual in order to promote the understanding of vulnerability mechanics rather than relying solely on automated scanners.

# Summary of Findings
A total of 8 vulnerabilites were identified.
They included the following categories:
- XSS, or cross-site scripting
- Reflected XSS
- SQL injection
- Logic flaws in application behaviour
- Improper access control
- Parameter manipulation vulnerabilities

All of the vulnerabilities were classified as Medium severity using CVSS v4.0 due to them sharing exploit preconditions.

# Highlighted Vulnerability - Stored XSS
The vulnerability is of the type stored cross-site scripting, and is caused by improper input validation and output encoding.

### Exploitation
A payload such as:
`<img src=x onerror=test()>`
was successfully stored in the database and executed automatically when the web page was loaded. The vulnerability existed because the "Comment" field implemented encoding of "<" and ">", while the "Name" field did not. This inconsistency created an unintended attack vector.

# Defensive Recommendations
- Implement centralized input validation and encoding.
- Adopt secure development lifecycle practices.
- Conduct periodic security testing before production release.
- Apply content security policy in order to reduce XSS impact.
- Perform internal risk assessmant beyond CVSS scoring.

# Security Lessons Learned
The test reinforced several important security principles:
- Validation of user input must be consistent across all fields.
- Blacklisting approaches do not work as intended without proper encoding.
- Business logic flaws can be as impactful as technical vulnerabilities.
- Risk classification requires contextual business understanding, and not simply technical scoring.
The project also improved my ability to communicate security vulnerabilities to both technical and non-technical recipients.
