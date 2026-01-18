# Used Signals Register (Caribbean CTO Brief)

## Purpose
This register is the authoritative log used to **dedupe** signals across the workstream and to track **follow-through milestones** (RFP -> award -> go-live -> KPI).

**File:** `register/used_signals_register.csv`
- **1 row = 1 milestone** (not 1 initiative).
- Multiple rows may share the same `initiative_id` as the initiative progresses.

## Core rules
### Dedupe
Treat a proposed signal as **already used** if it matches a prior row on **2 of 3**:
1) Material overlap in `geography` + `entities`
2) Same `initiative_id` (or clearly the same real-world initiative)
3) Same `milestone_type` within the same `milestone_date` window

### Follow-through
Allowed ONLY when there is a **new milestone** (award/go-live/legal commencement/funding approval/KPI/public results/major scope change).
- Add a new row.
- Set `status=FOLLOW-THROUGH`.
- Set `follow_through_of=<prior signal_id>`.

### IDs
- `initiative_id` is a stable slug for the initiative (e.g., `INIT-TRIDENT-ID`, `INIT-TT-AI-READINESS`).
- `signal_id` is a unique milestone id: `SIG-YYYYMMDD-###`.

## Column definitions
### Identity + grouping
- `signal_id`: unique row id for this milestone.
- `initiative_id`: stable id grouping milestones for the same initiative.
- `workstream`: optional (default: `Caribbean-CTO-Brief`).

### Where it appeared
- `issue_id`: e.g., `Issue-07`.
- `issue_date`: `YYYY-MM-DD`.
- `status`: `NEW | EXISTING | FOLLOW-THROUGH | RECAP`.
- `follow_through_of`: prior `signal_id` when `status=FOLLOW-THROUGH`.
- `duplicate_of`: prior `signal_id` if you explicitly mark a row as a duplicate rather than recording it.

### Classification
- `geography`: country/region (e.g., `Trinidad & Tobago`, `CARICOM`, `OECS`).
- `domain`: pipe-separated tags (e.g., `DPI|Cyber|AI`).
- `dpi_components`: pipe-separated (see list below). Leave blank if not DPI-related.
- `milestone_type`: controlled list (below).
- `milestone_date`: `YYYY-MM-DD` (prefer the event date; else use `source_pub_date`).

### Canonical wording
These fields prevent near-duplicate rewrites of the same story.
- `canonical_headline`: stable 6-14 word phrasing.
- `canonical_summary`: one sentence, <= 220 chars.
- `entities`: pipe-separated orgs/agencies/vendors (e.g., `MPA|UNDP|UNESCO`).

### Source + quality
- `source_name`: publisher or origin (e.g., `CTU`, `Official release`).
- `source_url`: full URL or `(link not provided)`.
- `source_pub_date`: `YYYY-MM-DD` or `(date not provided)`.
- `confidence`: `HIGH | MEDIUM | LOW`.

### Execution knobs
- `impact_rating`: `LOW | MEDIUM | HIGH` (or a sourced metric).
- `pilot_watch`: `YES | MAYBE | NO`.
- `time_sensitive`: `YES | NO`.
- `time_window`: e.g., `Q1-2026` or `2026-01-10..2026-02-15`.
- `notes`: short execution notes (procurement risk, sequencing, dependencies).

## Controlled lists
### milestone_type
- POLICY
- LAW
- PROCUREMENT_RFP
- PROCUREMENT_AWARD
- LAUNCH
- PILOT
- FUNDING
- PARTNERSHIP
- REPORT
- INCIDENT
- EVENT

### dpi_components
Use consistently when relevant:
- ID
- Payments
- DataExchange
- Registries
- TrustLayer
- Cyber
- ConsentPrivacy
- Location
- MessagingNotify
- ServiceFrontDoor

## Appendix A mapping
Your brief should output **Appendix A - Used Signals Addendum** using the same columns (or the minimum subset below), so updates can be copy/paste merged:
Minimum subset:
`signal_id,initiative_id,issue_id,issue_date,status,geography,domain,dpi_components,milestone_type,milestone_date,canonical_headline,entities,source_url,source_pub_date,impact_rating,pilot_watch,time_sensitive,time_window`
