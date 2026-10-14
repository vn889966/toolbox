# toolbox

Web-based utility tools. Single static page, zero dependencies, all logic runs locally in the browser.

## Tools

| Tool | What it does |
|---|---|
| IP lookup | Your public IP + geo/ASN (via ipify / ipapi) |
| Cert lookup | Query crt.sh CT logs: issuer, validity, days remaining |
| Site probe | Batch reachability + latency check |
| Encoding | Base64 / URL / `\uXXXX` / Hex, both directions |
| Timestamp | Unix <-> readable time, local/ISO/UTC/weekday |
| Regex | Live match highlighting + count |
| JSON | Format / minify / escape to string |

## Usage

Open https://vn889966.github.io/toolbox/ — works on mobile too.

No build step, no server, no tracking. Fork it and edit `index.html`.

## Known limits

- **Cert lookup** uses crt.sh public CT logs, not a real TLS handshake. For exact expiry use:
  `echo | openssl s_client -connect host:port -servername host 2>/dev/null | openssl x509 -noout -dates`
- **Site probe** is limited by browser CORS: it can only tell reachable/unreachable, not HTTP status codes. For status codes use:
  `curl -sk -o /dev/null -w '%{http_code} %{size_download}' URL`
