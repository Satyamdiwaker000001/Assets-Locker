# Resource Lifecycle

A resource progresses through a lightweight review lifecycle:

```text
to-review → verified → used
     ↘ archived ← verified / used
```

## Status definitions

- **to-review:** captured as a candidate; usefulness, URL, and license terms are not fully checked.
- **verified:** URL and purpose reviewed, and available license or attribution terms inspected. This is not a legal guarantee.
- **used:** applied in a named project or workflow; record the project and implementation notes.
- **archived:** broken, superseded, irrelevant, or no longer maintained for the intended use.

## Review checklist

- Does the resource solve a clear design or engineering need?
- Is the URL canonical and accessible?
- Is it a tool, library, reference, article, or asset collection?
- Which stack and project contexts does it fit?
- Are license, attribution, redistribution, and commercial-use terms clear?
- Are there limitations, pricing, account requirements, or framework constraints?
- Is an equivalent resource already listed?

## Review dates

Use ISO date format (`YYYY-MM-DD`) only when a review actually occurs. Revisit high-value resources when using them and periodically review links.

## Licensing caution

A resource being visible, downloadable, or free to access does not automatically grant permission to redistribute it or use it commercially. Inspect the current terms at the source.
