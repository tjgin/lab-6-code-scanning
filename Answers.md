# Answers to Part 3

Add your answers to the questions in Part 3, Step 2 below. 

## Vulernability Remediation:
### Vulnerability 1: LanguageSpecificPackageVulnerability
1. Which package or library are you addressing?
trivy-results.sarif

2. Which CVE is linked to this vulnerability?
CVE-2020-14343

3. What remediation steps do you suggest?
Upgrade PyYAML to version 5.4 or later immediately across all affected systems. Audit all applications to identify usage of full_load() or FullLoader and replace with safe_load() where possible. Implement input validation to reject YAML documents containing Python object tags before parsing. Consider using yaml.safe_load() as the default loader, which restricts parsing to basic YAML types only.


### Vulnerability 2: OsPackageVulnerability
1. Which vulnerability are you addressing?
docker-scout-findings

2. Which CVE is linked to this vulnerability?
CVE-2026-102268

3. What remediation steps do you suggest? 
Upgrade PyJWT to version 2.14.0 or later. Ensure applications do not mix HMAC and asymmetric algorithms in token handling. Review and validate PEM key format handling in token validation logic.
