## APPENDIX A - USED SIGNALS ADDENDUM

> Copy/paste-ready. One row per signal used in this brief.
> If the Used Signals Register was not consulted, use provisional ids: `prov-YYYYMMDD-###`.

### Option 1: Table (recommended for LinkedIn readability)

| signal_id | initiative_id | issue_id | issue_date | status | geography | domain | dpi_components | milestone_type | milestone_date | canonical_headline | entities | source_url | source_pub_date | impact_rating | pilot_watch | time_sensitive | time_window | follow_through_of | duplicate_of |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| prov-YYYYMMDD-001 | INIT-EXAMPLE | Issue-XX | YYYY-MM-DD | NEW | Trinidad & Tobago | DPI\|AI | ID\|TrustLayer | REPORT | YYYY-MM-DD | Example canonical headline | MPA\|UNDP | https://... | YYYY-MM-DD | HIGH | YES | YES | Q1-2026 |  |  |

### Option 2: JSON-like list (best for automation)

[
  {
    "signal_id": "prov-YYYYMMDD-001",
    "initiative_id": "INIT-EXAMPLE",
    "issue_id": "Issue-XX",
    "issue_date": "YYYY-MM-DD",
    "status": "NEW",
    "follow_through_of": "",
    "duplicate_of": "",
    "geography": "Trinidad & Tobago",
    "domain": "DPI|AI",
    "dpi_components": "ID|TrustLayer",
    "milestone_type": "REPORT",
    "milestone_date": "YYYY-MM-DD",
    "canonical_headline": "Example canonical headline",
    "entities": "MPA|UNDP",
    "source_url": "https://...",
    "source_pub_date": "YYYY-MM-DD",
    "impact_rating": "HIGH",
    "pilot_watch": "YES",
    "time_sensitive": "YES",
    "time_window": "Q1-2026",
    "notes": ""
  }
]
