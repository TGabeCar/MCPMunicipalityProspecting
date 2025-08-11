# Finalize Prospects Workflow

## Purpose
**EFFICIENCY-OPTIMIZED**: Verify contacts, apply T-Mobile targeting, and generate sales-ready output in one streamlined phase.
**TARGET**: Transform 100-400 raw contacts into polished prospect list in 20-30 minutes

## Input
`data/working/contacts-discovered.json` from rapid-research phase

## Streamlined 3-Step Process

### Step 1: Efficient Verification (10-15 minutes)

**Tiered Verification Strategy**
```markdown
TIER 1 CONTACTS (Deep verification - 2-3 minutes each):
- IT Directors, CIOs, City Managers, Police Chiefs
- Anyone with "Director" or "Chief" in title
- High-value decision makers for T-Mobile

TIER 2 CONTACTS (Quick verification - 30 seconds each):  
- Department managers, coordinators, supervisors
- Administrative staff with vendor contact responsibility
- Medium-value contacts for relationship building

TIER 3 CONTACTS (Format validation only - 10 seconds each):
- Support staff, assistants, specialists
- Include if contact info is complete and valid
- Volume contacts for comprehensive coverage
```

**Quick LinkedIn Verification (For Tier 1 & 2 only)**
```markdown
FOR high-value contacts:
1. SEARCH: "[Name] [Municipality] [Title] LinkedIn"
2. QUICK CHECK: Current employment (within 12 months)
3. VERIFY: Title accuracy and no recent job changes
4. MARK: High/Medium/Low confidence based on findings
5. MOVE ON: Don't spend more than 2 minutes per contact

CONFIDENCE SCORING:
- High (90+): LinkedIn confirms current employment + title
- Medium (70): Official website + format validation
- Low (50): Format validation only, no external confirmation
```

**Bulk Employment Validation**
```bash
# Quick employment status check for all contacts
for contact in $(jq -r '.[].email' data/working/contacts-discovered.json); do
    # Check if email domain matches municipality
    domain=$(echo "$contact" | cut -d'@' -f2)
    municipality=$(jq -r --arg email "$contact" '.[] | select(.email == $email) | .municipality' data/working/contacts-discovered.json)
    
    # Basic domain validation (quick check)
    if [[ "$domain" == *"gov"* || "$domain" == *"$municipality"* ]]; then
        employment_status="active"
    else
        employment_status="verify_needed"
    fi
done
```

### Step 2: Rapid T-Mobile Targeting (5-10 minutes)

**Pattern-Based Product Assignment**
```json
{
  "targeting_patterns": {
    "5g_infrastructure": {
      "title_keywords": ["IT Director", "CIO", "Technology Director", "Information Systems"],
      "department_keywords": ["Information Technology", "IT", "Technology"],
      "priority": "primary"
    },
    "enterprise_plans": {
      "title_keywords": ["City Manager", "Mayor", "Administrator", "Director", "Manager"],
      "department_keywords": ["Administration", "Executive", "Management"],
      "priority": "primary"
    },
    "public_safety_communications": {
      "title_keywords": ["Police Chief", "Fire Chief", "Sheriff", "Emergency", "Communications", "911", "Dispatch"],
      "department_keywords": ["Police", "Fire", "Emergency", "Public Safety", "Sheriff", "911", "Communications"],
      "priority": "primary"
    },
    "firstnet_emergency": {
      "title_keywords": ["911 Director", "Emergency Manager", "Communications Director", "Dispatch Supervisor"],
      "department_keywords": ["911", "Emergency Communications", "Dispatch", "Emergency Management"],
      "priority": "primary"
    },
    "iot_solutions": {
      "title_keywords": ["Public Works", "Engineering", "Utilities", "Operations", "Water Manager", "Fleet Manager"],
      "department_keywords": ["Public Works", "Engineering", "Utilities", "Water", "Streets", "Fleet", "Maintenance"],
      "priority": "secondary"
    },
    "fleet_connectivity": {
      "title_keywords": ["Fleet Manager", "Transportation", "Transit", "Vehicle", "Equipment"],
      "department_keywords": ["Transportation", "Transit", "Fleet", "Vehicle Services", "Equipment"],
      "priority": "secondary"
    },
    "public_connectivity": {
      "title_keywords": ["Parks", "Recreation", "Library", "Community", "Airport", "Transit"],
      "department_keywords": ["Parks", "Recreation", "Library", "Community Services", "Airport", "Transit"],
      "priority": "secondary"
    },
    "government_enterprise": {
      "title_keywords": ["County Manager", "District Manager", "Authority Director", "General Manager"],
      "department_keywords": ["County", "District", "Authority", "Regional"],
      "priority": "primary"
    }
  }
}
```

**Automated Product Mapping**
```markdown
FOR each contact:

1. ANALYZE title and department (30 seconds)
2. MATCH against T-Mobile product patterns
3. ASSIGN primary product based on best fit
4. ASSIGN secondary products for cross-selling
5. SET sales priority based on authority level

SALES PRIORITY LOGIC:
- Tier 1: Executive decision makers (Mayor, City Manager, IT Director, Police Chief)
- Tier 2: Department managers with budget authority  
- Tier 3: Operational staff and coordinators
```

**Quick Authority Assessment**
```json
{
  "authority_levels": {
    "executive": {
      "keywords": ["Mayor", "City Manager", "Administrator", "Chief"],
      "budget_authority": "high",
      "sales_priority": "tier_1"
    },
    "director": {
      "keywords": ["Director", "Manager", "Supervisor", "Coordinator"],
      "budget_authority": "medium", 
      "sales_priority": "tier_2"
    },
    "staff": {
      "keywords": ["Assistant", "Specialist", "Technician", "Clerk"],
      "budget_authority": "low",
      "sales_priority": "tier_3"
    }
  }
}
```

### Step 3: Immediate Output Generation (5-10 minutes)

**Rapid Output Formatting**
```markdown
READ: templates/output-format.md for structure

SORT contacts by:
1. Sales priority (Tier 1 → Tier 3)  
2. Municipality size (estimate by website sophistication)
3. Verification confidence (High → Medium → Low)

GENERATE sections:
- Executive Summary with statistics
- Tier 1 High-Priority Contacts  
- Tier 2 Medium-Priority Contacts
- Tier 3 Strategic Contacts
- Summary statistics and usage notes
```

**Contact Entry Format (Streamlined)**
```markdown
Contact: [Name]
Title: [Title] | Department: [Department]  
Municipality: [Municipality Name]
Email: [Email] | Phone: [Phone]
T-Mobile Focus: [Primary Product] + [Secondary Product]
Sales Priority: [Tier] | Confidence: [Level] | Verified: [Date]
---
```

**Statistics Generation (Auto-calculated)**
```bash
# Generate summary statistics quickly
total_contacts=$(jq length data/working/contacts-verified.json)
tier_1_count=$(jq '[.[] | select(.sales_priority == "tier_1")] | length' data/working/contacts-verified.json)
high_confidence=$(jq '[.[] | select(.confidence_score >= 80)] | length' data/working/contacts-verified.json)
municipalities_covered=$(jq '[.[].municipality] | unique | length' data/working/contacts-verified.json)

# IT/Technology contact breakdown
it_contacts=$(jq '[.[] | select(.department | contains("IT") or contains("Technology"))] | length' data/working/contacts-verified.json)
admin_contacts=$(jq '[.[] | select(.department | contains("Admin") or contains("Executive"))] | length' data/working/contacts-verified.json)
safety_contacts=$(jq '[.[] | select(.department | contains("Police") or contains("Fire") or contains("Emergency"))] | length' data/working/contacts-verified.json)
```

## Quality Assurance (Built-in Efficiency Checks)

**Contact Quality Distribution Target**
```yaml
acceptable_quality_distribution:
  high_confidence: 40-60%    # LinkedIn verified decision makers
  medium_confidence: 30-40%  # Website + format validated
  low_confidence: 10-20%     # Format validated only
  
contact_completeness_target:
  complete_records: 70%+     # Name, title, email, phone
  partial_records: 25%       # Missing 1 field
  minimal_records: 5%        # Name + email only
```

**Volume Quality Check**
```bash
# Quick validation of output quality
final_count=$(grep -c "^Contact:" data/outputs/$(ls data/outputs/ | tail -1))
decision_makers=$(grep -c "Sales Priority: tier_1" data/outputs/$(ls data/outputs/ | tail -1))
complete_contacts=$(grep -c "Email:.*Phone:" data/outputs/$(ls data/outputs/ | tail -1))

echo "Final prospect count: $final_count"
echo "Decision makers (Tier 1): $decision_makers"  
echo "Complete contact records: $complete_contacts"

# SUCCESS CRITERIA (Relaxed for volume):
# - 80+ total contacts
# - 15+ tier 1 decision makers
# - 70+ complete contact records
```

## Enhanced Contact Record Structure

**Final Contact Data Format**
```json
{
  "contact_id": "hamilton_001_verified",
  "name": "John Smith", 
  "title": "IT Director",
  "department": "Information Technology",
  "municipality": "City of Chattanooga",
  "municipality_size": "large",
  "email": "john.smith@chattanooga.gov",
  "phone": "(423) 643-7000",
  "verification": {
    "confidence_score": 85,
    "verified_sources": ["official_website", "linkedin"],
    "employment_status": "current",
    "last_verified": "2024-01-15"
  },
  "tmobile_targeting": {
    "primary_product": "5G Infrastructure",
    "secondary_products": ["Enterprise Plans", "IoT Solutions"],
    "value_proposition": "Municipal network modernization and smart city infrastructure",
    "sales_priority": "tier_1",
    "authority_level": "executive",
    "budget_influence": "high"
  },
  "sales_notes": {
    "recommended_approach": "Technical demonstration with ROI focus",
    "best_contact_method": "email_then_phone",
    "decision_timeline": "municipal_budget_cycle"
  }
}
```

## Output File Structure (Optimized)

**Header Section**
```markdown
[COUNTY], [STATE] - T-MOBILE MUNICIPAL PROSPECTS
Generated: [Date] | Contacts: [Total] | Coverage: [X] municipalities
Quality: [X]% verified | Priority Targets: [X] decision makers

=== EXECUTIVE SUMMARY ===
Total Municipalities: [X] | Contact Distribution: IT([X]) Admin([X]) Safety([X]) Works([X])
Sales Ready: [X] Tier 1 + [X] Tier 2 contacts
Verification: [X]% High Confidence, [X]% Medium Confidence
```

**Contact Sections (Priority-Sorted)**
```markdown
=== TIER 1: HIGH-PRIORITY DECISION MAKERS ===
[Primary targets - executives, IT directors, chiefs]

=== TIER 2: DEPARTMENT MANAGERS ===  
[Secondary targets - managers, supervisors, coordinators]

=== TIER 3: STRATEGIC CONTACTS ===
[Relationship building - staff, specialists, support roles]

=== CONTACT USAGE GUIDE ===
Data Currency: Verified [Date] | Recommend outreach within 30 days
Tier 1: Immediate focus for high-value deals
Tier 2: Pipeline development and relationship building  
Tier 3: Comprehensive coverage and long-term relationships
```

## Success Criteria (Phase 2)

**Delivery Targets**
- [ ] 80+ final contacts (minimum acceptable volume)
- [ ] 15+ tier 1 decision makers identified
- [ ] 60%+ verification confidence rate
- [ ] 100% contacts have T-Mobile product targeting
- [ ] Sales-ready format with clear prioritization
- [ ] Execution completed in 20-30 minutes

**Quality Metrics**
- [ ] Contact completeness rate 70%+
- [ ] Municipality coverage 80%+  
- [ ] Decision maker identification 15%+ of total
- [ ] Product targeting accuracy validated by pattern matching
- [ ] Output format ready for immediate sales use

## Final Output Deliverable

**File Created**: `data/outputs/[County]_[State]_Prospects_[YYYY-MM-DD].txt`
**Content**: 80-300+ verified municipal contacts with T-Mobile targeting
**Format**: Sales-optimized prospect list ready for immediate outreach
**Quality**: Professional document suitable for sales team distribution