# Answers to Part 3

Add your answers to the questions in Part 3, Step 2 below. 

## Vulernability Remediation:
### Vulnerability 1: LanguageSpecificPackageVulnerability
1. Which package or library are you addressing?<br>
trivy-results.sarif<br>

2. Which CVE is linked to this vulnerability?<br>
CVE-2020-14343 - The PyYAML library in versions before 5.4 is susceptible to arbitrary code execution when it processes untrusted YAML files through the full_load method or with the FullLoader loader. This flaw allows an attacker to execute arbitrary code on the system by abusing the python/object/new constructor.<br>

3. What remediation steps do you suggest?<br>
Upgrade PyYAML to version 5.4 or later immediately across all affected systems. Audit all applications to identify usage of full_load() or FullLoader and replace with safe_load() where possible. Implement input validation to reject YAML documents containing Python object tags before parsing. Consider using yaml.safe_load() as the default loader, which restricts parsing to basic YAML types only.
<br>

### Vulnerability 2: OsPackageVulnerability
1. Which vulnerability are you addressing?<br>
docker-scout-findings<br>

2. Which CVE is linked to this vulnerability?<br>
CVE-2026-102268 - PyJWT is a Python implementation of JSON Web Token standards. Prior to 2.14.0, is_pem_format in jwt/utils.py is affected because is_pem_format does not recognize every PEM representation accepted by the cryptography loader. This occurs when an application mixes HMAC and asymmetric algorithms and supplies a mutated public-key PEM as raw key bytes. As a result, HMACAlgorithm.prepare_key treats the unrecognized asymmetric public key as an HMAC secret. Consequently, an attacker who knows the public key can forge authenticated HMAC tokens.<br>

3. What remediation steps do you suggest?<br>
Upgrade PyJWT to version 2.14.0 or later. Ensure applications do not mix HMAC and asymmetric algorithms in token handling. Review and validate PEM key format handling in token validation logic.
