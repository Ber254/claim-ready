# claim-ready

> *Your NAS as your best witness: a private home inventory, claim-ready in seconds.*

A UGOS AI Skill for UGREEN AI NAS that turns the photos, invoices, and warranties already stored on your device into a structured insurance claim report — organized exactly the way a claims adjuster needs it.

**All processing stays local. No files leave your NAS.**

---

## The problem

Most people are unprepared when they need to file an insurance claim. They can't find purchase receipts. They don't know serial numbers. Their photos are scattered across folders and phones. They feel insecure and unsure whether they're doing it right — and that uncertainty costs them time, money, and coverage.

claim-ready solves this before disaster strikes.

---

## What it does

1. **Discovers** your asset photos, invoices, and warranty documents already stored on your NAS
2. **Organizes** them by room and category (electronics, appliances, furniture, tools, jewelry…)
3. **Extracts** item details: brand, model, serial number, purchase date, estimated value
4. **Generates** a structured Markdown report ready to hand to your insurance advisor

The output looks like this:

```
# Home Inventory — Claim Report
Generated: 2026-10-28

## Summary
- Total items catalogued: 47
- Items with full documentation: 31
- Items with photos only (no invoice): 16

## Electronics
| Item        | Brand/Model         | Serial #   | Purchase Date | Value  | Invoice | Photo |
|-------------|---------------------|------------|---------------|--------|---------|-------|
| 55" TV      | Samsung QN90B       | SN-4829XX  | 2023-03-15    | $1,200 | ✓       | ✓     |
| MacBook Pro | Apple MacBook Pro   | C02GXXXXXX | 2022-08-01    | $2,499 | ✗       | ✓     |

## Items Requiring Attention
These items have incomplete documentation and may affect your claim:
- MacBook Pro: no invoice found
- Espresso machine: no serial number visible in photo
```

---

## Who it's for

Anyone who owns valuable belongings and wants to be prepared — homeowners, renters, families. If you already store your photos and documents on a UGREEN AI NAS, claim-ready makes those files work for you.

---

## How to use it

In your UGOS AI assistant, say:

- *"Generate my home inventory claim report"*
- *"Prepare my insurance inventory"*
- *"Create a claim-ready report for my electronics"*

The skill will ask for confirmation before writing anything, and save the report wherever you specify.

---

## Privacy

This is the core reason claim-ready belongs on a NAS rather than in a cloud app.

Your home inventory is sensitive information: it lists what you own, what it's worth, and where it is. That data shouldn't live on someone else's server. claim-ready processes everything locally on your UGREEN AI NAS. No files, photos, or extracted data are sent anywhere.

---

## NAS Capabilities Used

claim-ready chains three native UGOS capabilities:

| Capability | What it does in this skill |
|------------|---------------------------|
| **Files** | Finds photos, invoices, and warranty documents |
| **Albums** | Groups photos by room and item category |
| **Documents** | Reads and extracts structured data from invoices and warranties |

---

## Hackathon context

Built for the **UGREEN NAS Skill Hackathon 2026**.

The idea came from insurance industry experience: policyholders consistently face the same problem — they know they own things, but they can't prove it. Purchase invoices are gone. Serial numbers are unknown. Photos are scattered. The documentation gap is the silent killer of legitimate claims.

The UGREEN AI NAS solves this naturally: it already stores your photos and documents. claim-ready connects those files to the one moment you actually need them.

---

## Skill package structure

```
claim-ready/
├── SKILL.md       # Uliya Skill Development Standard — required
└── README.md      # This file
```

---

## Author

Bernardo Foco  
Insurance & Insurtech professional  
bernardofoco@gmail.com
