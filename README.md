# Lendbuzz

Lendbuzz is a Boston-headquartered auto finance platform, founded in 2015, that uses machine learning
and alternative data — bank transaction history, education, employment and income signals rather than a
traditional FICO file — to underwrite consumers with thin or no US credit history. It originates retail
auto loans through a nationwide network of franchise and independent dealerships, and provides dealers
with floor planning and an AI-assisted "Express Contract" digital contracting flow. All loans are made by
Lendbuzz Funding, LLC (NMLS ID #1636296).

- Website: https://www.lendbuzz.com/
- Dealer Portal: https://app.lendbuzz.com/dealer_portal
- System Status: https://www.lendbuzz.com/system-status
- GitHub: https://github.com/LendBuzz

## API surface

**No public API.** Contract discovery run 2026-08-01 found no OpenAPI/Swagger, no GraphQL, no MCP server,
and no A2A agent card on any Lendbuzz host:

| Probe | Result |
|---|---|
| `/openapi.json`, `/openapi.yaml`, `/swagger.json`, `/api-docs`, `/llms.txt` on `www`, apex, `app`, `api` | 404 on the marketing site; `app.lendbuzz.com` returns 200 with an HTML redirect shell (SPA catch-all — verified not JSON) |
| `developer.` / `docs.` / `developers.` / `api-docs.` / `partner(s).` / `sandbox.` `.lendbuzz.com` | NXDOMAIN |
| `api.lendbuzz.com` | DNS resolves (AWS) but TCP 443 and 80 both time out — not publicly reachable |
| `lendbuzz.readme.io` / `lendbuzz.gitbook.io` | 404 |
| `lendbuzz.stoplight.io` | Unclaimed placeholder workspace ("Create your own free Stoplight workspace") — no projects, Stoplight API returns 404 |
| `/.well-known/*` (security.txt, openid-configuration, oauth-authorization-server, api-catalog, ai-plugin.json, agent-card.json, agent.json) | 404 on every host |
| GitHub org `LendBuzz` | 2 public repos (an interview exercise, a versioning GitHub Action) — no SDKs, no specs |

Dealer integration is intermediated by the **Dealertrack** and **RouteOne** F&I networks — dealers submit
credit applications through those platforms or directly in the Lendbuzz Dealer Portal.

## Artifacts

| Path | Type | Method |
|---|---|---|
| `apis.yml` | APIs.json 0.20 | searched |
| `lifecycle/lendbuzz-lifecycle.yml` | Lifecycle / StatusPage / SLA | searched |
| `conformance/lendbuzz-conformance.yml` | Conformance (regulatory) | searched |
| `security/lendbuzz-domain-security.yml` | DomainSecurity | probed |
| `well-known/lendbuzz-well-known.yml` | probe record (nothing published) | probed |
| `llms/lendbuzz-llms.txt` | LLMsTxt | generated |

No vulnerability disclosure program, security.txt, bug bounty or trust center was found
(`probe-security-programs.py` → `vdp=none trust=none`).
