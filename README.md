# Lendbuzz

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
