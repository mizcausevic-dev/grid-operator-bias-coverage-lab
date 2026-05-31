# Changelog

## 1.0.0-prod — 2026-05-31

- Hardened to v1.0-prod per squad doctrine; member of the EnergyTech vertical 6-pack.
- Spec-component repo (no Pages deploy required); AGPL-3.0-or-later, synthetic example data only.
- Pulse universe entry not applicable (no custom subdomain).



## [0.1] — 2026-05-30

### Added

- Initial profile.
- **Population-level-equity framing** — first Suite bias lab where the harm pattern is uneven distribution of critical infrastructure outcomes across communities, not uneven treatment of individual applicants.
- 9 subgroup taxonomies: EPA EJSCREEN EJ designation, state DAC designations (CalEnviroScreen / NY DAC / MA EJ / IL Energy Communities / WA Health Disparities), DOE LEAD energy-burden bands, HUD LMI bands, BIA tribal land status, USDA-ERS rural-urban codes, renter/owner status, critical medical equipment household, LEP.
- 7 additional dimensions including census-tract id, feeder-or-circuit id, outage duration bands, EV charging port deployment density per capita, DR enrollment rate by subgroup, low-income program enrollment rate by subgroup.
- 12 required metrics covering load shed frequency + duration per census tract, outage restoration time + frequency, DR enrollment + payment per household, EV charging deployment density, low-income program enrollment + arrearage payoff, energy efficiency program participation, rate-class burden, critical-medical-equipment household outage response time.
- 11 coverage status codes including **EnergyTech-unique pattern detectors**: `load-shed-disparity-pattern-detected`, `restoration-priority-disparity-pattern-detected`, `critical-medical-equipment-response-time-violation`. Plus EnergyTech regulator pathways: `epa-ej-finding-pending`, `state-puc-ej-impact-assessment-failure`.
- **7-day freshness window** for load shed events — shortest in the Suite (energy emergencies don't tolerate quarterly review cadence).
- 8 intended consumers from utility CEO/chief-equity-officer through EPA EJ staff, DOJ Civil Rights staff, tribal energy advocacy orgs, and low-income customer advocacy orgs.

### Not yet

- Heat-event-specific overlay (cooling assistance program equity during heat waves).
- Cold-event-specific overlay (heating assistance program equity during freeze events).
- Wildfire Power Safety Shutoff (PSPS) equity overlay (CA-specific currently).
- Rooftop solar interconnection time equity overlay.
- Microgrid + BESS deployment equity overlay.