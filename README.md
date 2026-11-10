# PhishSight IOCs

Phishing and malware-delivery indicators, and the kit backends behind them (phishing panels, C2 and mobile exploit
servers), confirmed as malicious by [PhishSight](https://newtonpaul.com). Updated automatically when new indicators
are confirmed. Last change: **2026-11-10 06:27 UTC**.

| Folder | Indicators |
|---|---|
| [`credential-phishing/`](credential-phishing/) | 2,117 |
| [`device-code-phishing/`](device-code-phishing/) | 2,275 |
| [`clickfix/`](clickfix/) | 4,981 |
| [`malware/`](malware/) | 149 |
| [`kit-backends/`](kit-backends/) | 705 |
| [`payloads/`](payloads/) | 164 files |

## Files in each threat folder

| File | Contents |
|---|---|
| `indicators.json` | Every indicator with its details: role, status, campaign, impersonated brand, URL, hostnames, first/last seen, hosting, ASN, country, DNS and IP history. ClickFix entries also carry the pasted command (defanged) and the hosts it fetches from. |
| `indicators.csv` | The same, one row per indicator (lists space-separated; commands `\|`-separated). |
| `iocs.txt` | IOCs only: domains, hostnames and IPs, one per line. |
| `iocs-online.txt` | IOCs only, for indicators online at the last check. |
| `urls.txt` | Phishing URLs. Victim emails and long tokens in paths are replaced with `[redacted]`; query strings are removed. |

`payloads/` has delivered executables, installers and archives: `payloads.json`, `payloads.csv` and `sha256.txt`,
`sha1.txt`, `md5.txt`. `campaigns.json` describes the named campaigns referenced by the `campaign` field.

## Fields

- `role`: `Phishing page` (serves the lure or sign-in page), `Redirector` (forwards victims to it, often a
  compromised legitimate site), `Operator infrastructure` (panels, backends, C2), `Delivery`.
- `backend_for` (`kit-backends/` only): what the server runs: `phishing` (a phishing kit's panel or token
  backend), `mobile-exploit` (a mobile exploit kit: exploit server or operator panel), `clickfix` or `malware` (C2).
- `status`: `online` or `offline` at the last check. Checks are regular but can lag.

## Caution

Many redirectors are **compromised legitimate websites**: block them, but treat their owners as victims. Hostnames
are not defanged in these files; don't open them in a normal browser. Provided as-is for defensive use.
