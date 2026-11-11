# Contract Lifecycle

The common contract-lifecycle vocabulary -- the contracts a business holds, the clauses in them, the obligations they create and the templates they are drafted from -- distilled from the APIs that already exist. Signing belongs to the e-signature context. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Contract Management, CLM, Contract Lifecycle Management, Contract Intelligence, Legal Tech, Contract Analytics in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| contract | 10 | 9 | id 100%, status 100%, name 89%, created_at 56% | contracts 8, agreements 2, agreement 1 |
| contract_template | 5 | 4 | id 100%, name 100% | templates 5 |

Cohort: 45 providers with harvested OpenAPI, 10 crosswalks. Of the providers exposing a contract: 90% create, 90% list, 80% fetch, 80% update, 60% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- A contract agrees only on id, name, status and created_at. Counterparty, value, effective and expiration dates -- the facts a contract system exists to track -- are each carried by a minority under different names.
- Contract lifecycle publishes little (45 providers, 11 mapped), and the analysis that sets CLM apart -- clauses, obligations -- is almost never a resource of its own.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- Signing is e-signature's: envelopes and recipients are not duplicated. Agreements count as contracts here unless they are clickwrap acceptance records.
- Templates are `/contract-templates`: e-signature owns `/templates`.
- Clauses and obligations were measured and dropped.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
