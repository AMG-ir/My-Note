# security.txt

**Category:** Web Security  
**Type:** Technical Research  
**Status:** Research Notes

## Research Question

What is `security.txt`, where is it published, and how does it help security researchers report vulnerabilities to a website owner?

## Purpose

Understand the purpose of `security.txt` after encountering the concept during a website-related project, and learn how to locate and interpret it during a basic security review.

## Background

`security.txt` is a plain-text file that gives security researchers information about how an organization prefers to receive vulnerability reports. It helps make the disclosure process easier to find and follow.

The standard location is:

```text
https://example.com/.well-known/security.txt
```

A site may also publish a copy at `/security.txt`, but the well-known location is the standard location defined by RFC 9116.

## Example

This is an illustrative example only; the contact and dates must be replaced with valid information before use.

```text
Contact: mailto:security@example.com
Expires: 2027-01-01T00:00:00.000Z
Preferred-Languages: en
Policy: https://example.com/security-policy
Canonical: https://example.com/.well-known/security.txt
```

## Important Fields

- **`Contact`:** Provides a way to contact the organization about security issues. This is a required field in the RFC.
- **`Expires`:** Indicates when the information should be considered expired. This is also required; the file should be reviewed and renewed before that date.
- **`Preferred-Languages`:** Lists languages the organization can use for security communications.
- **`Policy`:** Links to the organization's vulnerability-disclosure policy or reporting instructions.
- **`Canonical`:** Identifies the canonical URL of the security.txt file.
- **`Encryption`:** Can point to information for encrypting sensitive reports, where supported.

These are examples of fields, not a requirement that every possible field be present. Refer to RFC 9116 for the complete format and rules.

## Why It Matters

- Makes the organization's security-reporting contact easier to discover.
- Can direct researchers to a disclosure policy and clarify the preferred reporting process.
- May reduce confusion about where to report a suspected vulnerability.
- Can provide language preferences and information for protecting sensitive reports.

## Limitations and Security Considerations

- `security.txt` is a disclosure-contact mechanism, not a security control. It does not prevent attacks or prove that a website is secure.
- A published file does not prove that the listed contact is monitored or that the organization will respond.
- An absent file is not, by itself, proof of a vulnerability.
- A file can contain outdated, incorrect, or misleading information, so check its expiry and whether its links and contact methods work.
- Do not send sensitive vulnerability details to an unverified address. Follow the organization's published policy and applicable authorization boundaries.

## Basic Review Steps

1. Visit `https://TARGET/.well-known/security.txt` for a domain you are authorized to review.
2. Check whether the file is reachable and whether it contains a valid `Contact` and `Expires` field.
3. Review any `Policy` link and note the permitted reporting process.
4. Check whether the expiry date has passed and whether the contact details appear relevant.
5. Record the observation separately from any confirmed security vulnerability.

Replace `TARGET` with the authorized test domain. These are manual review steps; no automated test result is claimed by this note.

## Connection to Website Security Reviews

During a website-related project, learning about `security.txt` helped identify a standard place to look for vulnerability-reporting instructions. It is useful to check alongside other website configuration and hardening observations, but its presence or absence should not be treated as a vulnerability finding on its own.

## Practical Verification

This note documents the concept and a basic review procedure. It does not claim that a particular site's `security.txt` was successfully fetched, validated, or tested. Add target-specific observations only when they have been confirmed during an authorized review.

## Conclusion

`security.txt`, standardized in RFC 9116, gives organizations a predictable way to publish security contact and disclosure information. It supports coordinated vulnerability reporting, but does not itself protect a site from exploitation.

## References

- [RFC 9116: A File Format to Aid in Security Vulnerability Disclosure](https://www.rfc-editor.org/rfc/rfc9116)
- [MDN: security.txt](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/security.txt)

---

Part of [My-Note](../../README.md) — personal technical knowledge base.
