# Wazuh decoders and rules for Sophos XGS (WAF + IDP)

Custom Wazuh decoders and rules to parse Sophos XGS Web Application Firewall (WAF) and Intrusion Detection/Prevention (IDP) logs.  
Focus: clean extraction of key fields and simple, robust rules you can extend.

## Features

**WAF (log_type="WAF")**
- Extracts: log_type, reason, http_status, url, http_method, http_query, domain, srcip, dstip, protocol, message, content_type, http_user_agent, http_response_time, bytes_sent, bytes_received, fw_rule_id, fw_rule_name, fw_rule_section, total_score (from message)
- Rules (example IDs 100600+):
  - 100600: all WAF events
  - 100601: WAF anomaly (reason="WAF Anomaly")
  - 100602: blocked 403 (suppressed when total_score >= 10)
  - 100603/100604/100605: score tiers >=5 / >=10 / >=20

**IDP (log_type="IDP")**
- Extracts: log_type, classification, rule_priority, srcip, dstip
- Rules (example IDs 100620+):
  - 100620: all IDP events
  - 100621: IDP drop (log_subtype="Drop")
  - 100622: IDP detect (log_subtype="Detect")

> The decoders use `type="pcre2"` and modular sibling decoders for resilience.

## Repository layout
