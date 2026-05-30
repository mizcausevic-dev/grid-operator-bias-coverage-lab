# grid-operator-bias-coverage-lab

> **EnergyTech Evidence Bundle (bias) — Spec #4 of the EnergyTech 6-pack.** Pre-deployment + ongoing-monitoring bias / equity-coverage evidence for AI tools used by utilities, grid operators, and pipeline operators. Anchored to EPA Title VI environmental justice + Justice40 Initiative + state PUC EJ impact assessment requirements (CA / MA / IL / WA) + CalEnviroScreen / NY DAC / EPA EJSCREEN / DOE LEAD Tool.

Part of the [Kinetic Gain Protocol Suite](https://suite.kineticgain.com).

> Status: v0.1 draft. Profile at [`profile.json`](./profile.json).

## EnergyTech-distinctive design

**This lab measures POPULATION-LEVEL equity in essential service delivery — not individual decisioning bias.**

Most sibling bias labs (HR Tech, FinTech, InsurTech) measure whether AI tools treat individuals fairly: did the model approve/deny applicants at equivalent rates across protected classes? EnergyTech is different. The harm pattern in grid operations is **uneven distribution of critical infrastructure outcomes** across census tracts, environmental-justice communities, and energy-burden bands — not biased individual decisioning. A load shed AI is "fair" when it sheds proportionally across communities, not when it gives each individual an equivalent chance of being shed.

That shift matters for what to measure and how to act on findings.

## What this lab covers

| Bias dimension | Why it matters | Anchor |
| --- | --- | --- |
| Load shed allocation | 2021 Texas freeze: poor neighborhoods + non-white tracts shed first + longest | TX-PUCT Staff Guidance 55718 mandates load-shed allocation publication |
| Outage restoration priority | Low-income areas restored last is a documented pattern (Hurricane Sandy 2012, etc.) | State PUC equity orders |
| Demand response program participation | Renters + non-English speakers + LMI households often excluded | FERC Order 2222 fairness + state PUC EJ orders |
| EV charging deployment | DOE Justice40: 40% of clean-energy benefits to disadvantaged communities | DOE EO 14008 Justice40 |
| Rate-class design | Tariff structure can disproportionately burden low-income or high-energy-burden households | State PUC prudency review |
| Low-income program enrollment | LIHEAP / arrearage / percentage-of-income payment plan access patterns | State PUC + DOE LEAD |
| Critical medical equipment household response | Registered customers with medical baselines deserve priority response | State PUC critical-care customer registry rules |

## Subgroup taxonomies (9)

Energy-sector-specific taxonomies that distinguish this lab from sibling-vertical bias labs:

| Taxonomy | Source |
| --- | --- |
| `ej_designation_epa_ejscreen` | EPA EJSCREEN + Justice40 CEJST |
| `state_disadvantaged_community_designation` | CalEnviroScreen 4.0, NY DAC, MA EJ Population, IL Energy Communities, WA Health Disparities Index |
| `energy_burden_band` | DOE LEAD Tool — % of household income spent on energy |
| `lmi_designation` | HUD AMI bands |
| `tribal_land_status` | BIA tribal-land geographic designation |
| `rural_urban_band` | USDA-ERS Rural-Urban Continuum Codes |
| `renter_owner_status` | Census ACS (DR program access matters here) |
| `critical_medical_equipment_household` | Utility critical-care customer registry |
| `limited_english_proficiency` | Census ACS + utility customer language preference |

## EnergyTech-unique coverage status codes

11 coverage statuses including three unique pattern-detectors not seen in sibling-vertical bias labs:

- **`load-shed-disparity-pattern-detected`** — load shed events systematically favor non-DAC tracts. Explicit alert; mandatory state PUC + DOJ Civil Rights notification consideration.
- **`restoration-priority-disparity-pattern-detected`** — outage restoration time systematically longer in DAC tracts.
- **`critical-medical-equipment-response-time-violation`** — registered critical-medical-equipment households had outage response time materially worse than baseline.

Plus EnergyTech-specific regulator pathways: `epa-ej-finding-pending`, `state-puc-ej-impact-assessment-failure`.

## Thresholds

| Threshold | Value |
| --- | --- |
| `minimum_subgroup_n_per_census_tract` | 100 |
| `performance_gap_alert_threshold` | 20pp absolute OR disparate-impact ratio < 0.80 |
| `disparate_impact_ratio_threshold` | 0.80 (canonical four-fifths) |
| `freshness_window_critical_event_load_shed` | P7D — load shed events under regulatory review every week |
| `freshness_window_outage_restoration` | P30D |
| `freshness_window_program_enrollment` | P90D |
| `freshness_window_annual_planning` | P365D |

The 7-day freshness window for load shed events is the shortest in the Suite — energy emergencies don't tolerate quarterly review cadence.

## Use

```bash
# Validate the profile is well-formed
node -e "JSON.parse(require('fs').readFileSync('profile.json','utf8'))"
```

## Composes with

- [`evidence-bundle-spec`](https://github.com/mizcausevic-dev/evidence-bundle-spec) — upstream spec this profile conforms to
- [`grid-decision-record-audit-stream`](https://github.com/mizcausevic-dev/grid-decision-record-audit-stream) — sibling Operator audit-stream that emits load-shed and restoration events into this lab's evidence
- [`state-puc-ai-disclosure-tracker`](https://github.com/mizcausevic-dev/state-puc-ai-disclosure-tracker) — sibling state PUC lifecycle tracker; many state PUC orders specifically reference EJ impact assessment
- [`nerc-cip-readiness-evidence-bundle`](https://github.com/mizcausevic-dev/nerc-cip-readiness-evidence-bundle) — sibling compliance bundle
- [Kinetic Gain Protocol Suite](https://suite.kineticgain.com) — umbrella

## Compliance posture

**Equity-readiness scaffolding** for utility AI tools touching essential service delivery. Producing a complete bias coverage record is evidence of equity-program maturity, not certification of EPA Title VI compliance, Justice40 conformance, or state PUC EJ impact assessment approval. Each of those is a separate regulator-led process — per the standing public-language guardrail across the Suite.

## License

Profile + supporting documentation: MIT.
