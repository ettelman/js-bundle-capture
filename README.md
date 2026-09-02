<p align="center">
  <img src="logo_js_bundle.png" width="190" alt="JS Bundle Capture logo">
</p>

<h1 align="center">JS Bundle Capture</h1>

<p align="center">
  Capture, prettify, search, and triage JavaScript bundles directly inside Burp Suite.
</p>

## What it does

JS Bundle Capture collects JavaScript response bodies from Burp Proxy history or live traffic without re-requesting resources or modifying proxied responses.

- Capture from Proxy history or while browsing.
- Filter by Burp scope, exact host, or all Proxy traffic.
- Deduplicate bundles by SHA-256.
- Export byte-exact originals to `raw/` and readable copies to `prettified/`.
- Search every captured bundle using text or guarded regex.
- Run local AppSec triage rules for DOM XSS, `postMessage`, dynamic execution, secrets, endpoints, source maps, and browser storage.
- Load custom JSON rule packs and export analysis candidates as JSON.

Everything runs locally. The extension sends no telemetry, executes no captured JavaScript, and makes no additional HTTP requests.

## Install

1. Download the latest `.jar` from [GitHub Releases](../../releases/latest).
2. In Burp Suite, open **Extensions → Installed → Add**.
3. Select extension type **Java** and choose the JAR.
4. Open the new **JS Bundle Capture** tab.

Requires a current Burp Suite release and Java 17 or newer.

## Quick start

1. Select **Burp target scope**, **Selected host**, or **All proxy traffic**.
2. Click **Scan Proxy history**, or start live capture and browse the application.
3. Open **Analysis** to search the bundles or run the built-in rules.
4. Export the capture as ZIP or the current analysis results as JSON.

```text
capture.zip
├── manifest.jsonl
├── raw/
│   └── app-7f83b1657ff1.js
└── prettified/
    └── app-7f83b1657ff1.js
```

## Important

Analysis results are pattern-based review candidates, not confirmed vulnerabilities. Validate data flow, trust boundaries, reachability, sanitization, and exploitability manually before reporting a finding.

Captured bundles, URLs, snippets, and exported results may contain sensitive engagement data. Handle exports accordingly.

## Build

```bash
./gradlew clean test jar
```

Windows Command Prompt:

```bat
gradlew.bat clean test jar
```

## Status

Version **0.3.0 beta**. Feedback and real-world testing are welcome.

## License

MIT
