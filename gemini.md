# Project Constitution (gemini.md)

## Data Schemas

### Conversion Payload
```json
{
  "source_code": "string (Selenium Java)",
  "source_type": "testng_selenium",
  "target_language": "javascript | typescript",
  "converted_code": "string (Playwright)"
}
```

## Behavioral Rules
- Priority: Reliability over speed.
- Deterministic logic: Business logic must be deterministic.
- Self-healing: Automation should attempt to recover from transient failures.

## Architectural Invariants
- 3-Layer Architecture (Architecture, Navigation, Tools).
- Mandatory protocol check before coding.
