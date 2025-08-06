# Wazuh + Sophos XGS (WAF & IDP)

This repository provides **custom decoders and rules** for ingesting and alerting on **Sophos XGS** logs in **Wazuh**.  
It focuses on reliable field extraction (PCRE2) and actionable alerts for both **WAF** and **IDP** events.

## What’s inside
- **Decoders**
  - `0001-decoder-sophos-xgs-waf-anomaly.xml` — parses WAF fields (e.g., reason, http_status, url, srcip/dstip, score, fw_rule_*).
  - `0002-decoder-sophos-xgs-idp.xml` — parses IDP fields (e.g., classification, rule_priority, srcip/dstip).
- **Rules**
  - `0001-rules-sophos-waf-idp.xml` — groups, severities, and score tiers; all important alerts carry the tag **`sophos_xgs_critical`**.
- **Samples**
  - `samples/sample-waf.log`, `samples/sample-idp.log` — ready for the Wazuh log tester.

## How it works
- Decoders enrich Sophos events with normalized fields (Phase 2).
- Rules evaluate these fields and generate alerts (Phase 3), with meaningful grouping for Discover filtering.

## Documentation
For step-by-step setup (Web GUI), testing, and Discover filters/columns, see the **`documentation`** file in this repository.
