# Synthetic Content Scan Credential Schema

This repository defines a **W3C Verifiable Credential schema** for synthetic content detection results. It is designed for interoperability with the [cheqd network](https://cheqd.io), DID-linked resources, and multi-detector AI verification.

---

## 📄 Schema URL

The schema is hosted at:

```
https://maxxdedev.github.io/synthetic-scan-vc-schema/schemas/synthetic-content-scan.schema.v1.json
```

Use this as the `credentialSchema.id` in any Verifiable Credential referencing this schema.

---

## 🧩 Features

- ✅ W3C Verifiable Credential–compliant
- ✅ Extensible and versioned (e.g. v1, v2...)
- ✅ Supports multiple detection engines (e.g. SynthID, watermarking, classification)
- ✅ Compatible with DID-linked resources on cheqd
- ✅ Includes confidence scoring, provenance, and evidence fields

---

## 📦 Example Credential Usage

```json
{
  "@context": ["https://www.w3.org/2018/credentials/v1"],
  "type": ["VerifiableCredential", "SyntheticContentScanCredential"],
  "issuer": "did:cheqd:testnet:issuer123",
  "credentialSubject": {
    "id": "did:cheqd:testnet:subject456",
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
    "id": "https://maxxdedev.github.io/synthetic-scan-vc-schema/schemas/synthetic-content-scan.schema.v1.json",
    "type": "JsonSchemaValidator2020"
  }
}
```

---

## 🛠 Versioning

Schemas are located in `/schemas/` and follow this format:

- `synthetic-content-scan.schema.v1.json`
- `synthetic-content-scan.schema.v2.json` *(future-proofed)*

---

## 🔖 License

This schema is published under [MIT](./LICENSE). Use freely with attribution.

---

