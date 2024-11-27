# SOPS-Check Glossary

## Core Concepts

**SOPS (Secrets OPerationS)** A encryption tool that supports encrypting files using one or more encryption keys, allowing secure storage of sensitive information in version control systems. See [getsops.io](https://getsops.io/) for more information.

**Trust Anchor** An encryption key used to encrypt a SOPS file. Trust anchors serve as the foundation of security for SOPS files and can be various types of keys, such as [AWS KMS keys](https://getsops.io/docs/#usage) or [AGE keys](https://getsops.io/docs/#encrypting-using-age).

**Compliance Checker** SOPS-Check is a security linter tool that validates SOPS files against predefined rules to ensure they follow security best practices and organizational requirements without decrypting the files.

## Rule Types

**Match Rule** A rule that requires exact matching of a trust anchor. For example, matching a specific AWS KMS key ARN.

**Match Regex Rule** A rule that matches trust anchors using regular expressions, allowing for flexible pattern matching across similar keys.

**All Of Rule (AND)** A rule that requires all specified nested rules to match. Used when multiple conditions must be satisfied simultaneously.

**Any Of Rule (OR)** A rule that requires at least one of the specified nested rules to match. Used when multiple alternative conditions are acceptable.

**One Of Rule (XOR)** A rule that requires exactly one of the specified nested rules to match. Used to enforce mutual exclusivity between different options.

**Not Rule** A rule that inverts the matching behavior of another rule. Used to explicitly forbid certain trust anchors or patterns.

## Security Concepts

**Excess Trust Anchors** Trust anchors in a SOPS file that don't match any of the defined rules. These represent potential security risks and can be rejected by the compliance checker.

**Trust Anchor Pairs** Sets of two related trust anchors, often used for redundancy. For example, AWS KMS keys from different regions to increase availability.

**Environment Separation** The practice of maintaining distinct trust anchors for different environments (e.g., production, staging, development) to prevent unauthorized access across environments.

## Technical Components

**Rule Configuration** A JSON/YAML file that defines the compliance rules using a specific schema, including rule definitions and their relationships.

**Rule Metadata** Additional information attached to rules, such as descriptions and documentation URLs, to provide context and guidance to users.

**SARIF Output** A standardized format for reporting static analysis results, used by the compliance checker to provide machine-readable output.

## Operational Concepts

**Disaster Recovery Key** A special type of trust anchor (typically an AGE key) stored offline that ensures access to encrypted data even if cloud services are unavailable.

**CI/CD Integration** The ability to incorporate the compliance checker into continuous integration and deployment pipelines for automated validation.

**Soft Errors** Rule violations that generate warnings rather than failures, allowing for more flexible policy enforcement when needed.

## Access Control

**Least Privilege Access** A security principle implemented through trust anchor selection, ensuring users and systems have only the minimum necessary access to encrypted data.

**Team-Specific Keys** Trust anchors designated for specific teams, allowing for segmented access control and reduced blast radius in case of security incidents.

**Deployment Keys** Special trust anchors used specifically for automated deployment processes, typically with decrypt-only permissions to prevent tampering.  
