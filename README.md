# IATA Air Cargo AWB & Aviation Validator — TypeScript / JavaScript SDK

[![npm version](https://img.shields.io/npm/v/@stanzaapi/iata-validator.svg)](https://www.npmjs.com/package/@stanzaapi/iata-validator)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> Validate IATA Resolution 600a Air Waybills (11-digit MOD-7), e-tickets, and airline accounting prefixes in sub-5ms.

Official, zero-dependency Node.js and TypeScript client for **IATA Air Cargo AWB & Aviation Validator**, powered by the [Stanza Micro-API Network](https://stanzaapi.com). Delivers deterministic, sub-5ms V8 isolate execution directly to your application without 3rd-party proxies.

* 🌐 **Live Web Sandbox:** [Try interactive queries online](https://stanzaapi.com/tools/iata-validator)
* 📚 **API Reference:** [Read complete OpenAPI specification](https://stanzaapi.com/tools/iata-validator)
* ⚡ **Platform Overview:** [Discover the Stanza Edge Portfolio](https://stanzaapi.com)

---

## 📦 Installation

```bash
npm install @stanzaapi/iata-validator
# or
pnpm add @stanzaapi/iata-validator
# or
yarn add @stanzaapi/iata-validator
```

---

## 🚀 Quickstart

```typescript
import { IataValidatorClient } from '@stanzaapi/iata-validator';

// Initialize client (API key optional for sandbox tier evaluation)
const client = new IataValidatorClient({
  apiKey: process.env.STANZA_API_KEY,
});

async function main() {
  const result = await client.validate('020-12345675');

  if (result.success) {
    console.log('Verification Success:', result.data);
  } else {
    console.error('Validation Error:', result.error, result.code);
  }
}

main().catch(console.error);
```

---

## 📄 Example JSON Response

```json
{
  "success": true,
  "data": {
    "valid": true,
    "prefix": "020",
    "airline": "Lufthansa Cargo",
    "serial_number": "1234567",
    "check_digit": 5
  }
}
```

---

## ⚙️ Client Configuration Options

| Option | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `apiKey` | `string` | `process.env.STANZA_API_KEY` | Your [Stanza API Key](https://stanzaapi.com). Required for high-throughput production tiers. |
| `baseUrl` | `string` | `https://api.stanzaapi.com/iata-validator` | Public edge API base URL. |
| `timeoutMs` | `number` | `15000` | Request timeout in milliseconds (uses native `AbortSignal.timeout`). |


---

## 🛡️ Response Envelope & Error Handling

All responses return a typed envelope:

```typescript
export interface ApiResponse<T> {
  success: boolean;
  data?: T;
  error?: string;
  code?: 'VALIDATION_ERROR' | 'UNAUTHORIZED' | 'PAYLOAD_TOO_LARGE' | 'RATE_LIMITED' | 'INTERNAL_ERROR';
}
```

---

## 🔗 Related Resources

* [IATA Air Cargo AWB & Aviation Validator Interactive Playground](https://stanzaapi.com/tools/iata-validator)
* [Stanza Microservices Directory](https://stanzaapi.com)
* [Report an Issue on GitHub](https://github.com/StanzaAPI/iata-validator-typescript/issues)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).
