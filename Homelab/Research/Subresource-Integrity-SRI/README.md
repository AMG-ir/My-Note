# Subresource Integrity (SRI)

**Category:** Web Security  
**Status:** Research in Progress  
**Type:** Technical Research

## Research Question

What is Subresource Integrity (SRI), and how does it help protect a website when it loads JavaScript or CSS files from a third-party source?

## Purpose

Understand how a browser can check that an external script or stylesheet has not changed unexpectedly, and recognize when SRI may be useful during a basic website security review.

## Background

Websites sometimes load JavaScript or CSS from another domain, such as a CDN or a third-party service. If that resource is unexpectedly modified, the website may load content different from what its developers intended.

Subresource Integrity (SRI) lets a developer provide a cryptographic hash for a resource. The browser compares the downloaded resource with the expected hash before using it. If the content does not match, the browser refuses to load that resource.

SRI is commonly configured with the `integrity` attribute on supported `<script>` and `<link>` elements.

## How It Works

1. The developer obtains the expected hash for a specific version of a JavaScript or CSS file.
2. The hash is placed in the element's `integrity` attribute.
3. The browser downloads the resource and calculates its hash.
4. The browser compares the calculated hash with the expected value.
5. If the hashes do not match, the browser blocks the resource from being used.

SRI can help limit the impact of unexpected changes to third-party resources, but it does not replace other security controls.

## Important Attributes

- **`integrity`:** Contains the expected cryptographic hash. Common supported algorithms include SHA-256, SHA-384, and SHA-512.
- **`crossorigin="anonymous"`:** Commonly used when applying SRI to a cross-origin resource. The resource host must also support the required CORS behavior.

## Example

The following is a **placeholder example**. The URL and hash are illustrative and are not intended to work.

```html
<script
  src="https://cdn.example.com/library.js"
  integrity="sha384-REPLACE_WITH_THE_REAL_BASE64_HASH"
  crossorigin="anonymous"></script>
```

The hash must be generated from the exact resource version being loaded. A placeholder or incorrect hash will not provide a valid integrity check.

## Benefits

- Helps detect unexpected changes to external scripts and stylesheets.
- Reduces reliance on trusting that a third-party host will always serve unchanged content.
- Gives the browser a clear expected version of a supported resource.

## Limitations and Considerations

- If the resource changes during a legitimate update, its hash must also be updated; otherwise, the browser may block it.
- Cross-origin SRI requires appropriate CORS support from the resource host.
- Some services generate or change resource URLs or contents dynamically, which can make SRI harder to maintain.
- When a script element is created dynamically with JavaScript, SRI metadata must be set on that element as part of the loading process; simply checking the page's original HTML may not reveal every resource loaded at runtime.
- The absence of SRI is a hardening observation, not proof by itself that a website is exploitable. The resource, loading method, and surrounding security controls also matter.
- SRI does not prove that the original resource is safe; it only checks whether the downloaded content matches the expected hash.

## Connection to Website Security Reviews

While reviewing how websites load third-party JavaScript, SRI is one mechanism worth checking. If a page loads an external script without integrity metadata, record the observation and investigate the context before drawing conclusions.

For scripts inserted dynamically at runtime, inspect how the element is created and whether integrity metadata is applied. Consider whether the third-party resource is versioned and stable enough for SRI to be practical.

## Practical Verification

This note records conceptual research and review of technical documentation. A separate controlled browser test comparing a matching hash with a mismatched hash has not been documented here.

## Conclusion

SRI allows a website to tell the browser which exact content is expected from a supported external JavaScript or stylesheet resource. It can reduce certain third-party resource risks, but correct hashes, CORS support where required, and a suitable resource-loading method are essential.

## References

- [MDN: Subresource Integrity](https://developer.mozilla.org/en-US/docs/Web/Security/Defenses/Subresource_Integrity)
- [MDN: Subresource Integrity implementation guide](https://developer.mozilla.org/en-US/docs/Web/Security/Practical_implementation_guides/SRI)
- [W3C: Subresource Integrity specification](https://www.w3.org/TR/SRI/)

---

Part of [My-Note](../../README.md) — personal technical knowledge base.
