# Awesome-Operating-System-Browser-Compatibility-Matrix

# Awesome Operating System & Browser Compatibility Matrix

> A curated list of top Operating System and Browser Compatibility Matrix platforms — both SaaS/Hosted commercial device clouds and open-source data projects for determining which browsers and OS versions support specific web features.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [BrowserStack Platform Matrix](#browserstack-platform-matrix)
  - [Sauce Labs Platform Configurator](#sauce-labs-platform-configurator)
  - [LambdaTest Capability Generator](#lambdatest-capability-generator)
  - [Browserling OS Matrix](#browserling-os-matrix)
- [Open-Source Software](#-open-source-software)
  - [MDN Browser Compat Data (BCD)](#mdn-browser-compat-data-bcd)
  - [Can I Use (Raw Data)](#can-i-use-raw-data)
  - [browser-compat-mcp-server](#browser-compat-mcp-server)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Operating System and Browser Compatibility Matrix platforms. These are not open-source but are included as reference points for feature comparison.

### BrowserStack Platform Matrix
**Type:** Comprehensive OS and browser version listing for automation
BrowserStack publishes supported OS and browser versions for each automation framework. For **Puppeteer**, the `os` capability accepts Windows (11, 10, 8.1, 8, 7) and OS X (Golden Gate, Tahoe, Sequoia, Sonoma, Ventura, Monterey, Big Sur, Catalina, Mojave, High Sierra, Sierra, El Capitan), while `browser` accepts chrome, firefox, and edge . Version ranges are broad: **Chrome 72+**, **Firefox 86+**, and **Edge 80+**, with `latest`, `latest-beta`, and `latest-N` shorthand for testing the newest releases. The interactive **list-of-browsers-and-platforms** page lets you select an OS (e.g., macOS Sonoma, Ventura, Monterey) and see supported browsers including Chrome, Firefox, Safari, Samsung Internet, and UC Browser . Mobile coverage spans Galaxy S20 through S26, Pixel 6 through 11, and iPhone 7 through 18 Pro Max, with corresponding iOS versions .
**Best for:** Teams running automated tests on BrowserStack needing the exact capability values for a specific framework and OS/browser combination.

### Sauce Labs Platform Configurator
**Type:** Capability generator with full platform listing
Sauce Labs provides a **Platform Configurator** that generates Selenium and Appium code snippets for desired capabilities in the language of your choice . The supported platforms page states that Sauce Labs supports **thousands of browser/OS combinations**, including **1,700+ emulators and simulators** and **7,500+ iOS and Android real devices** across global data centers . Coverage includes Chrome, Firefox, Safari, and Edge, with region-specific availability noted (not all configurations are available in all regions) . The platform aims to support the latest browser releases within 48 hours .
**Best for:** Teams wanting programmatic capability generation with a single source of truth for supported combinations across desktop and mobile.

### LambdaTest Capability Generator
**Type:** Capability generator with forward-compatible OS and browser matrix
LambdaTest (TestMu AI) provides a **Capability Generator** that produces key-value pairs for test environments . For Playwright, `browserName` accepts Chrome, Microsoft Edge, and Playwright-bundled browsers (`pw-chromium`, `pw-webkit`, `pw-firefox`), while `platform` accepts Windows (11, 10, 8, 8.1, 7) and macOS (Monterey, Big Sur, Catalina, Mojave) . Version support includes **Chrome 83+** and **Edge 83+**. The generator covers every combination available on the TestMu AI cloud, with beta browser support and day-zero enablement of new devices and OS releases . An interactive blog post describes picking framework, browser, OS, device, and resolution to generate the needed capability in your language .
**Best for:** Teams wanting capability generation with a broad browser-OS matrix and forward compatibility for new releases.

### Browserling OS Matrix
**Type:** Real OS and browser version testing with version history
Browserling provides online cross-browser testing on real (not emulated) Windows and macOS installations. **Windows** coverage includes 11, 10, 8.1, 8, 7, and XP, with browsers Chrome (versions 1–130), Firefox (3–132), Opera (10–120), Internet Explorer (6–11), Edge, Safari, and Tor . **macOS** coverage includes macOS 26 (Tahoe), 15 (Sequoia), 14 (Sonoma), 13 (Ventura), and 12 (Monterey), with native Safari versions (26, 18, 17, 16, 15), Chrome and Edge from 120+, and Firefox from 113+ . The **free tier** provides access to Safari 18 on macOS 15 and Windows 10 with Edge 120; additional combinations require a developer plan . A **Live API** allows embedding any browser version on any Windows version into web pages for CI/CD workflows .
**Best for:** Developers needing to verify behavior on specific legacy or historical browser versions across real Windows and macOS environments.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Operating System and Browser Compatibility Matrix tools. The open-source ecosystem is **anchored by MDN's Browser Compat Data** as the canonical machine-readable dataset, with Can I Use providing feature-level support tables.

### MDN Browser Compat Data (BCD)
**Stack:** JSON / Node.js / TypeScript | **License:** CC0 1.0
MDN's **browser-compat-data** (BCD) is the foundational open-source dataset for browser compatibility information, containing **over 15,000 features** covering Web APIs, JavaScript features, CSS properties, HTML elements, and HTTP headers . Key characteristics:
- **Machine-readable**: installable via `npm install @mdn/browser-compat-data`, importable in Node.js, Deno, or browsers, with raw `data.json` available via CDN 
- **Used by MDN Web Docs, CanIUse, Visual Studio Code, WebStorm, and more** 
- **Structured schema**: feature support data is accessed via dictionary properties (e.g., `bcd.css.properties.background.__compat`), with browser data at the leaves 
- **TypeScript definitions** are automatically generated from the schema 
- **Release index ordering**: target versions are ordered by BCD's release index rather than parsed version strings, avoiding incorrect comparisons 

The dataset is the authoritative source for programmatic compatibility checks, though it requires engineering effort to build a user-facing matrix on top.
**Best for:** Developers building tooling, documentation, or compatibility checks who need a comprehensive, machine-readable, and openly licensed dataset as the foundation.

### Can I Use (Raw Data)
**Stack:** JSON | **License:** CC BY 4.0
The **caniuse** raw data repository provides the support tables behind caniuse.com in JSON format, with `fulldata-json/data-2.0.json` containing all support data . It is used by developers who want feature-level browser support data without scraping the website. The data is available under **CC BY 4.0** (attribution required), and some data within caniuse.com is sourced from BCD rather than this repository . It covers HTML, CSS, JavaScript, and other web platform features with browser-by-browser support notes, partial support flags, and version ranges.
**Best for:** Developers wanting feature-level support tables with notes on partial implementations and caveats, accepting the attribution requirement.

### browser-compat-mcp-server
**Stack:** TypeScript / MCP | **License:** Open Source
browser-compat-mcp-server exposes browser compatibility and **Baseline** status for any web feature to AI agents, built on MDN's browser-compat-data, web-features, and caniuse . Key characteristics:
- **Fully offline**: all four datasets are bundled and loaded in process—no runtime network calls, no API key, no rate limit 
- **Baseline** is read per BCD key from `status.by_compat_key`, never rolled up from the feature level, because keys under one feature legitimately disagree 
- **One shared resolver** behind every tool: exact BCD key, then web-features id, then a `moved` redirect, then search index matches under `resolve: true` 
- **Honest verdicts**: a pass is never claimed for a browser that was not evaluated—a target without data appears in `unchecked_targets` and makes the verdict `inconclusive` 
- **Misses are results, not failures**: `found: false` with guidance naming the next call 
- **Usage figures** state the population they are a share of and carry caniuse attribution 

A public instance is available at `https://browser-compat.caseyjhand.com/mcp` with no installation required .
**Best for:** Developers using AI coding agents (Claude, Cursor) wanting offline, verifiable compatibility data directly within their agent session, particularly for Baseline status checks.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Machine-Readable | Feature-Level Data | OS/Browser Matrix | Self-Hosted | Best For |
|----------|---------|-------|------------------|-------------------|-------------------|-------------|----------|
| **BrowserStack** | Proprietary | Cloud | (Capability values) | ❌ | ✅ Version ranges | ❌ | Automation capability lookup |
| **Sauce Labs** | Proprietary | Cloud | ✅ Configurator | ❌ | ✅ Full listing | ❌ | Capability generation |
| **LambdaTest** | Proprietary | Cloud | ✅ Generator | ❌ | ✅ Forward-compatible | ❌ | Capability generation |
| **Browserling** | Proprietary | Cloud | (Live API) | ❌ | ✅ Historical versions | ❌ | Legacy version testing |
| **MDN BCD** | CC0 1.0 | JSON/Node | ✅ npm package | ✅ 15,000+ features | ❌ | ✅ (Data) | Programmatic compatibility checks |
| **Can I Use** | CC BY 4.0 | JSON | ✅ Raw JSON | ✅ Feature tables | ❌ | ✅ (Data) | Feature support with caveats |
| **browser-compat-mcp** | Open Source | TypeScript/MCP | ✅ MCP tools | ✅ BCD + Baseline | ❌ | ✅ (MCP) | AI-agent compatibility queries |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Operating System or Browser Compatibility Matrix tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source.

**Note on the ecosystem:** Compatibility matrices split between **commercial device clouds** that tell you what OS/browser combinations they support for test execution (BrowserStack, Sauce Labs, LambdaTest, Browserling) and **open-source datasets** that tell you which browsers support a given web feature (MDN BCD, Can I Use). These serve fundamentally different purposes: the former answers "can I run a test on this configuration?" while the latter answers "does this feature work on this browser?" **MDN BCD** is the canonical open-source foundation used by MDN, CanIUse, VS Code, and WebStorm , while **browser-compat-mcp-server** makes this data accessible to AI agents with offline operation and honest inconclusive verdicts . No open-source project replicates the full commercial device cloud matrix of supported test configurations—for that, the vendor documentation remains the source of truth.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
