# Synthetic Content Scan Credential Schema

This repository defines a **W3C Verifiable Credential schema** for synthetic content detection results, optimized for use with [cheqd DID-linked resources](https://cheqd.io) and multi-detector AI verification pipelines.

---

## 📄 Schema URL

Use this as the main `credentialSchema.id`:

```
https://raw.githubusercontent.com/maxxdedev/synthetic-scan-vc-schema/main/schemas/synthetic-content-scan.schema.v2.json
```

This schema references sub-schemas in `schemas` for detector types and evidence formats.

---

## 🧠 JSON-LD `@context` 

To support JSON-LD processors, include this in your credential:

```
https://raw.githubusercontent.com/maxxdedev/synthetic-scan-vc-schema/main/contexts/synthetic-content-scan.v2.jsonld
```

Add it after the base VC context:

```json
"@context": [
  "https://www.w3.org/2018/credentials/v1",
  "https://raw.githubusercontent.com/maxxdedev/synthetic-scan-vc-schema/main/contexts/synthetic-content-scan.v2.jsonld"
]
```

---

## 🧩 Features

- ✅ W3C Verifiable Credential–compliant (`JsonSchemaValidator2020`)
- ✅ Modular sub-schema references (e.g. `ContentDetectionResult`, `DefinedTerm`, `Document`)
- ✅ Multiple AI detectors supported (SynthID, classification, watermarking, etc.)
- ✅ Designed for cheqd DID resolution and VC publishing

---

## 📦 Example Credential Usage

For a full example see: https://github.com/maxxeddev/synthetic-scan-vc-schema/blob/main/examples/example-vc

```json
{
  "@context": ["https://www.w3.org/2018/credentials/v1"],
  "type": ["VerifiableCredential", "SyntheticContentScanCredential"],
  "issuer": "did:cheqd:testnet:issuer123",
  "credentialSubject": {
    "id": "did:cheqd:testnet:subject456",
    "version": "2.0.0",
    "contentHash": "b1946ac92492d2347c6235b4d2611184",
    "scanResult": {
      "summary": "ai-generated",
      "detectors": [
        {
          "type": "ContentDetectionResult",
          "name": "SynthID",
          "version": "2.1",
          "vendor": "Google DeepMind",
          "method": "watermark",
          "result": "positive",
          "confidence": 0.94
        }
      ]
    },
    "scanTimestamp": "2025-05-28T10:59:00Z"
  },
  "credentialSchema": {
    "id": "https://raw.githubusercontent.com/maxxdedev/synthetic-scan-vc-schema/main/schemas/synthetic-content-scan.schema.v2.json",
    "type": "JsonSchemaValidator2020"
  }
}
```

---

## 🛠 Versioning Strategy

- **`synthetic-content-scan.schema.v2.json`** → Primary credential structure
- **`schemas/`** → Modular sub-schemas (e.g. `ContentDetectionResult`, `evidence`, `criteria`)
- Future versions (`v3`, etc.) can continue referencing or extending these modules

