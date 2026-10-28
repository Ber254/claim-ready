---
name: claim-ready
description: Scans photos, invoices, and warranties stored on your UGREEN AI NAS to generate a structured insurance claim report — organized by room and item category, with serial numbers, purchase dates, and estimated values — so you are prepared before disaster strikes. All processing stays local; no files leave your NAS.
---

# claim-ready

**Goal:** Turn the photos, invoices, and warranty documents already stored on your NAS into a ready-to-submit insurance claim report, organized exactly the way a claims adjuster needs it.

**When to use:** Say something like:
- "Generate my home inventory claim report"
- "Prepare my insurance inventory"
- "Create a claim-ready report for my belongings"

---

## Required Inputs

| Input | Description | Example |
|-------|-------------|---------|
| `scan_path` | NAS folder to scan (default: all authorized folders) | `/photos/home`, `/documents/invoices` |
| `output_path` | Where to save the report | `/documents/claim-ready-report` |
| `report_date` | Date for the report header | today's date |

Ask for confirmation before writing any files or moving content.

---

## Supported NAS Capabilities Used

This skill chains three native UGOS capabilities in sequence:

1. **Files** — locate asset photos, invoices, warranty PDFs, and receipts
2. **Albums** — group photos by room or item category
3. **Documents** — extract structured data from invoices and warranties

---

## Expert Agent Orchestration Workflow

### Step 1 — Discover assets (Files)
Search the authorized NAS folders for:
- Photos of physical items (`.jpg`, `.png`, `.heic`)
- Invoice and receipt documents (`.pdf`, `.jpg`, `.png`)
- Warranty certificates (`.pdf`)
- Any file named or tagged with item descriptions

Group results by folder/album structure when available.

If no files are found in the requested path, report clearly and stop. Do not substitute unrelated content.

### Step 2 — Organize by category (Albums)
Using the Albums capability, group discovered photos by:
- Room (living room, kitchen, bedroom, garage, etc.) — inferred from album names or folder structure
- Item category (electronics, furniture, appliances, jewelry, tools, vehicles, etc.)

If album metadata is unavailable, group by folder name.

Present the category summary to the user and ask for confirmation before proceeding:
> "I found [N] items across [M] categories. Here's the summary: [list]. Shall I continue and extract details?"

### Step 3 — Extract item data (Documents)
For each invoice, receipt, or warranty found, extract:
- Item name / description
- Brand and model
- Serial number (if present)
- Purchase date
- Purchase price / estimated value
- Warranty expiration (if present)
- Retailer or supplier

If a document is illegible or data is missing, note it as `[not found]` — never invent values.

### Step 4 — Generate claim report
Compile all extracted data into a structured Markdown report saved to `output_path`:

```
# Home Inventory — Claim Report
**Generated:** [report_date]
**Prepared by:** [NAS owner name if available]

---

## Summary
- Total items catalogued: [N]
- Categories: [list]
- Items with full documentation: [N]
- Items with partial documentation: [N]
- Items with photos only (no invoice): [N]

---

## [Category: Electronics]

| Item | Brand/Model | Serial # | Purchase Date | Value | Invoice | Photo |
|------|-------------|----------|---------------|-------|---------|-------|
| 55" TV | Samsung QN90B | SN-XXXXXX | 2023-03-15 | $1,200 | ✓ | ✓ |
| Laptop | Apple MacBook Pro | C02XXXXXX | 2022-08-01 | $2,499 | ✗ | ✓ |

## [Category: Appliances]
...

---

## Items Requiring Attention
Items with missing documentation that may affect claim approval:
- [list items with gaps]

---

## Notes for Your Insurance Advisor
[Any flags, gaps, or recommendations based on what was found]
```

### Step 5 — Confirm and save
Before writing:
> "Your claim-ready report is ready with [N] items. Shall I save it to [output_path]?"

Wait for user confirmation. Then save the report.

---

## Completion Handling

| Situation | Response |
|-----------|----------|
| Report generated successfully | Confirm save location and item count |
| No files found | Report clearly, suggest checking the scan path |
| Partial data only | Generate report with gaps marked, note what's missing |
| User cancels at confirmation | Discard without writing, confirm cancellation |

---

## Failure Handling

- **Document unreadable:** Mark as `[unreadable — manual review needed]`, continue with remaining items
- **Album capability unavailable:** Fall back to folder-based grouping using Files capability
- **No invoices found:** Generate photo-only inventory, flag all items as "photo evidence only"
- **Permission denied on a folder:** Skip it, note which folder was skipped

---

## Privacy and Data Handling

- All processing occurs locally on your UGREEN AI NAS
- No files, photos, or extracted data are transmitted externally
- The report is saved only to the path you confirm
- This skill does not store, index, or cache any data between sessions

---

## Disclosure

**Principal functionality developed for this Hackathon:** The full claim-ready workflow — asset discovery, category organization, data extraction, and report generation — was developed specifically for the UGREEN NAS Skill Hackathon 2026.

**AI tools used:** Claude (Anthropic) via the UGOS Skill Creation Tool, used for skill design, workflow orchestration logic, and documentation.

**Third-party components:** None. This skill uses only native UGOS NAS capabilities (Files, Albums, Documents) as documented in the UGOS Skill Developer Package.

**Open source libraries:** None required.
