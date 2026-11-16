# Free IT Tools by MiLabs

**20 free tools for DNS, email deliverability, Microsoft 365, security and networking. Everything runs in your browser, with no sign-up and no tracking.**

🔗 **Live site:** https://milabs-tools-qfoxksbr.onslate.com
🏢 **Built by:** [MiLabs](https://milabs.co.il), IT, security and automation services

![MiLabs Tools](docs/screenshots/home.png)

> The interface is in Hebrew (RTL). Domain names, records and technical values are shown left-to-right as usual.

---

## Tools

### Domain & DNS
| Tool | What it does |
|---|---|
| **Full domain check** | One-click health report: NS, MX (with provider detection), SPF, DMARC, DKIM, DNSSEC, CAA, MTA-STS, TLS-RPT and BIMI, with a score. |
| **DNS lookup** | A, AAAA, CNAME, MX, NS, TXT, SOA, CAA, SRV, DS, DNSKEY and HTTPS records. Enter an IP to get its reverse DNS (PTR) record. |
| **Resolver comparison** | Runs the same query against several public resolvers to check whether a DNS change has propagated, and shows the remaining TTL. |
| **Certificates & subdomains** | Searches Certificate Transparency logs (via crt.sh). Finds forgotten subdomains and certificates that are about to expire. |

### Email
| Tool | What it does |
|---|---|
| **SPF checker** | Follows every `include` recursively, counts DNS lookups against the 10-lookup limit, and flags `+all`, `ptr`, void lookups and duplicate records. |
| **SPF generator** | Build a record from common senders: Microsoft 365, Google Workspace, Zoho, SES, SendGrid, Mailchimp, Brevo and more. Can count lookups live. |
| **DMARC checker** | Parses every tag, explains it, and handles policy inherited from the organizational domain and external report authorization. |
| **DMARC generator** | Guided record builder with recommendations for rolling out from `none` to `reject`. |
| **DMARC report analyzer** | Drop aggregate reports (`.xml`, `.gz` or `.zip`) and see who sends mail as your domain, with pass rates per source IP and reverse DNS. |
| **DKIM checker** | Checks a specific selector, or scans about 30 common ones. Reports the RSA key length. |
| **Email header analyzer** | SPF/DKIM/DMARC results, the hop-by-hop route with delays, and Microsoft SCL / spam headers. |

### Microsoft 365
| Tool | What it does |
|---|---|
| **M365 domain check** | Tenant ID lookup, MX, Autodiscover, SPF, DKIM (selector1/2), DMARC, and Intune / Entra join records. |
| **M365 DNS generator** | Every record needed to connect a domain to Microsoft 365, each with a copy button. |

### Security
| Tool | What it does |
|---|---|
| **Certificate & CSR decoder** | Paste PEM to see the subject, SANs, issuer, validity, key type and size, key usage / EKU, and SHA-1 and SHA-256 fingerprints. Refuses to process private keys. |
| **Password generator** | Uses `crypto.getRandomValues`, can exclude ambiguous characters, and shows an entropy meter. |
| **JWT decoder** | Decodes the header and payload, shows expiry, and explains Microsoft Entra ID claims (`tid`, `oid`, `scp`, `roles`, `amr`, …). |

### Network & utilities
| Tool | What it does |
|---|---|
| **Subnet calculator** | IPv4 (CIDR or dotted mask) and IPv6: network, broadcast, host range, wildcard, binary view and a subnetting table. |
| **Encode & hash** | Base64, Base64URL, URL encoding, Hex, MD5, SHA-1, SHA-256 and SHA-512, all UTF-8 safe. |
| **QR generator** | URL / text, Wi-Fi network and email codes. Download as PNG or SVG. |
| **What's my browser** | Browser, OS, screen, language and time zone, with a one-click copy for support tickets. |

## Screenshots

| SPF generator | Subnet calculator |
|---|---|
| ![SPF generator](docs/screenshots/spfgen.png) | ![Subnet calculator](docs/screenshots/subnet.png) |
| **JWT decoder** | **Certificate decoder** |
| ![JWT decoder](docs/screenshots/jwt.png) | ![Certificate decoder](docs/screenshots/certdec.png) |

## Privacy

- **Nothing is sent to MiLabs.** There is no backend, no analytics and no cookies.
- **DNS queries** go directly from your browser to public DNS-over-HTTPS resolvers (Cloudflare and Google, plus a few others for the resolver comparison).
- **Certificate search** queries [crt.sh](https://crt.sh) directly from your browser.
- **The Microsoft 365 tenant lookup** reads Microsoft's public OpenID configuration endpoint.
- **Fonts** (Heebo, JetBrains Mono) are loaded from Google Fonts.
- **Everything else stays on your device:** header analysis, DMARC reports, certificate and JWT decoding, passwords, hashing and QR codes. You can confirm this by reading `index.html`.

## How it works

The whole site is a single, dependency-free `index.html`: plain HTML, CSS and JavaScript, with no build step. DNS lookups use the [DNS-over-HTTPS JSON API](https://developers.cloudflare.com/1.1.1.1/encryption/dns-over-https/make-api-requests/dns-json/). Certificates are parsed with a small built-in ASN.1/X.509 decoder.

### Run it yourself

```bash
# any static web server works, for example:
npx serve .
# or
python3 -m http.server 8080
```

Serve it over HTTP or HTTPS. Opening the file directly from disk works for the offline tools, but some browsers block DNS requests from `file://`.

## Deep links

Each tool has its own URL, and domain-based tools accept a domain:

```
https://milabs-tools-qfoxksbr.onslate.com/#health/example.com
https://milabs-tools-qfoxksbr.onslate.com/#spf/example.com
https://milabs-tools-qfoxksbr.onslate.com/#subnet
```

## License

[GNU AGPL-3.0](LICENSE). You may use, study and modify this code. If you run a modified version as a public service, you must publish your source code under the same license.

Bundled third-party code: [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) 1.4.4 by Kazuhiko Arase, under the MIT license.

---

Need help fixing what these tools found? **[MiLabs](https://milabs.co.il)** handles email deliverability, Microsoft 365, DNS and security for businesses.
