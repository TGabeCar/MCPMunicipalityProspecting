# Municipal Prospecting System

**T-Mobile Municipal Contact Generation and Sales Prospecting Platform**

A comprehensive system for discovering, researching, and qualifying municipal government contacts across entire counties for T-Mobile sales outreach.

## 🎯 What It Does

The Municipal Prospecting System generates comprehensive prospect lists of municipal government contacts with T-Mobile product targeting and sales prioritization. It discovers municipal entities across an entire county, extracts contact information from government websites, verifies employment status, and applies T-Mobile product recommendations to create sales-ready prospect lists.

## ⚡ Quick Start

```bash
# Generate comprehensive county coverage
/prospect-county Hamilton County, TN

# Results in 60-90 minutes:
# → 150-250 municipal contacts
# → Decision makers identified and prioritized  
# → T-Mobile products mapped to each contact
# → Sales-ready prospect list generated
```

## 📊 Expected Results

### Contact Volume by County Size
- **Large counties** (500K+ population): **200-400 contacts**
- **Medium counties** (100K-500K): **100-250 contacts**  
- **Small counties** (25K-100K): **50-150 contacts**
- **Rural counties** (under 25K): **25-75 contacts**

### Contact Type Distribution (Typical Medium County)
- **County Government**: 20-35 contacts (20-25% of total)
- **IT/Technology**: 15-30 contacts (5G, IoT, enterprise solutions)
- **Administration**: 25-50 contacts (enterprise plans, smart city)
- **Public Safety**: 30-60 contacts (FirstNet, emergency communications)
- **Emergency Services**: 10-25 contacts (911 centers, emergency management)
- **Sheriff's Departments**: 8-20 contacts (county law enforcement)
- **Public Works/Utilities**: 20-45 contacts (IoT sensors, field communications)
- **Special Districts**: 15-35 contacts (water, transit, housing authorities)
- **Parks/Recreation**: 10-25 contacts (public WiFi, connectivity)
- **Support Staff**: 15-40 contacts (comprehensive coverage)

## 🔄 2-Phase Workflow

```
/prospect-county Orange County, CA
    ↓
County Assessment: Quick analysis (2-3 min)
• Determine county size and complexity  
• Set realistic contact targets
• Allocate appropriate research time
    ↓
Phase 1: Rapid Discovery & Research (25-60 min depending on county size)
• County Government: Dedicated time (5-10 min) 
• Discover all municipalities in county
• Extract contacts from ALL municipal sources
• Focus on volume and comprehensive coverage
    ↓
Phase 2: Finalize Prospects (15-25 min)  
• Efficient verification of decision makers
• T-Mobile product targeting for all contacts
• Sales prioritization and final output
    ↓
Result: 25-400 verified contacts (based on county size)
```

## 📁 File Structure

```
MunicipalProspecting/
├── .claude/commands/
│   └── prospect-county.md              # Main orchestrator
├── workflows/
│   ├── rapid-research.md              # Phase 1: Discovery + Research
│   └── finalize-prospects.md          # Phase 2: Verification + Targeting + Output
├── data/
│   ├── working/
│   │   ├── contacts-discovered.json   # Phase 1 output (raw contacts)
│   │   └── contacts-final.json        # Phase 2 output (verified & targeted)
│   └── outputs/
│       └── [County]_[State]_[Date].txt # Final prospect list
├── PROSPECTING.md                     # Global rules and guidelines
└── README.md                          # System documentation
```

## 🎯 Contact Extraction Strategy

### Target Roles (Comprehensive Coverage)
```yaml
IT/Technology (20-40 contacts per county):
  executives: [CIO, IT Director, Technology Manager]
  staff: [Network Admin, Systems Admin, IT Support, Technology Specialist]

Administration (30-60 contacts per county):
  executives: [Mayor, City Manager, Administrator]  
  staff: [Assistant Manager, City Clerk, Administrative Assistant]

Public Safety (40-80 contacts per county):
  executives: [Police Chief, Fire Chief, Sheriff, Emergency Manager]
  staff: [Deputy Chief, Captain, Commander, Communications Supervisor]

Operations (25-50 contacts per county):
  executives: [Public Works Director, Parks Director, Utilities Manager]
  staff: [City Engineer, Streets Supervisor, Recreation Coordinator]
```

### Entity Coverage
```markdown
MUNICIPAL GOVERNMENTS:
✓ Cities, towns, villages, boroughs, townships
✓ County government offices and departments
✓ Municipal utilities (water, electric, gas, waste)

EMERGENCY & PUBLIC SAFETY:
✓ 911 Emergency Centers / Dispatch Centers
✓ Sheriff's Departments (county law enforcement)
✓ Municipal Police and Fire Departments
✓ Emergency Management Agencies

SPECIAL DISTRICTS & AUTHORITIES:
✓ Water/Sewer Districts and Authorities
✓ Transportation/Transit Agencies
✓ Airport and Port Authorities
✓ Housing Authorities and Redevelopment Agencies
✓ Library Systems and Hospital Districts
✓ Parks & Recreation Districts
```

## 📋 Sample Output (Hamilton County, TN)

```
HAMILTON COUNTY, TN - T-MOBILE MUNICIPAL PROSPECTS
Generated: January 15, 2024
Contacts: 287 | Municipalities: 32 | Quality: 68% verified

=== EXECUTIVE SUMMARY ===
Decision Makers: 58 | IT Contacts: 45 | Public Safety: 72 | County Gov: 42
High Priority (Tier 1): 58 contacts | Medium Priority (Tier 2): 154 contacts

=== TIER 1: HIGH-PRIORITY DECISION MAKERS ===

HAMILTON COUNTY GOVERNMENT - https://hamiltontn.gov
Contact: Dr. James Johnson | Title: County Manager | Department: Administration
Email: james.johnson@hamiltontn.gov | Phone: (423) 209-6500
T-Mobile Focus: Enterprise Plans + Cost Optimization
Sales Priority: Tier 1 | Confidence: High | Verified: 2024-01-15

Contact: Michael Chen | Title: IT Director | Department: Information Technology
Email: michael.chen@hamiltontn.gov | Phone: (423) 209-6550
T-Mobile Focus: 5G Infrastructure + Enterprise Solutions
Sales Priority: Tier 1 | Confidence: High | Verified: 2024-01-15

[... additional contacts ...]

TOTAL: 287 municipal contacts across 32 entities
COVERAGE: County Gov(42) IT(45) Admin(62) Public Safety(72) Emergency(28) Sheriff(18) Public Works(38)
```

## 🎯 T-Mobile Product Targeting

### Automated Product Mapping
- **IT Directors/CIOs**: 5G infrastructure, enterprise plans, IoT platform, smart city solutions
- **Mayors/City Managers**: Enterprise communications, cost optimization, strategic solutions
- **Police/Fire Chiefs**: Public safety communications, FirstNet, mobile data plans
- **Sheriff's Departments**: FirstNet, public safety communications, vehicle connectivity
- **911/Emergency Centers**: FirstNet emergency, mission-critical communications, dispatch solutions
- **Public Works Directors**: IoT sensors, asset monitoring, field communications
- **Special District Managers**: Enterprise plans, IoT solutions, operational connectivity
- **Transportation Authorities**: Fleet connectivity, mobile data plans, vehicle tracking
- **Water/Utility Authorities**: IoT sensors, asset monitoring, SCADA connectivity
- **Parks Directors**: Public WiFi, event connectivity, digital community services

### Sales Priority Scoring
- **Tier 1 (High Priority)**: Executive decision makers with budget authority
- **Tier 2 (Medium Priority)**: Department managers with influence
- **Tier 3 (Strategic)**: Operational staff for relationship building

## ⚙️ System Configuration

### Quality Standards
```yaml
verification_approach: "tiered_efficiency"
  tier_1_contacts: "linkedin_plus_employment_check"  
  tier_2_contacts: "website_plus_format_validation"
  tier_3_contacts: "format_validation_only"

volume_targets:
  minimum_contacts: 80
  target_contacts: 150-250  
  maximum_time: 90 minutes

quality_standards:
  verification_rate: 60%
  completeness_rate: 70% (name, title, email, phone)
  municipality_coverage: 80%
```

### Customization Options
- **Different vendors**: Modify targeting for other product portfolios
- **Regional optimization**: Adapt for state-specific municipal patterns
- **Industry focus**: Target specific municipal departments
- **Output formats**: Customize for CRM integration needs

## 🚨 Quality Assurance

### Quality Metrics
- **Format validation**: All email/phone formats checked
- **Employment status**: Current employment verified for decision makers
- **Duplicate detection**: Same person/email across sources identified
- **Confidence scoring**: High/Medium/Low confidence levels assigned
- **Municipality coverage**: 80%+ of entities covered with contacts

### Contact Currency
- **Data verification**: Within 6 months of generation
- **Update frequency**: Quarterly for active territories
- **Contact stability**: Municipal staff typically stable 1-2 years
- **Re-verification**: After major municipal elections

## 📞 Usage Guidelines

### Immediate Actions
1. **Focus on Tier 1 contacts first**: Highest ROI for sales efforts
2. **Verify high-priority contacts**: Double-check decision makers before outreach
3. **Use product targeting**: Tailor pitches to mapped T-Mobile solutions
4. **Track municipality budget cycles**: Time outreach for budget planning

### Expected Delivery Timeline
- **County assessment**: 2-3 minutes
- **Contact discovery**: 25-60 minutes (varies by county size)
- **Verification and targeting**: 15-25 minutes
- **Total execution time**: 60-90 minutes
- **Final deliverable**: Sales-ready prospect list

## 🛠️ Troubleshooting

### Volume Expectations by County Size
- **Large counties**: Target 150+ contacts minimum
- **Medium counties**: Target 80+ contacts minimum  
- **Small counties**: Target 40+ contacts minimum
- **Rural counties**: Target 20+ contacts minimum

### County Government Coverage
**Expected county government contacts:**
- **Large counties**: 30-50 contacts
- **Medium counties**: 20-35 contacts
- **Small counties**: 10-25 contacts  
- **Rural counties**: 8-15 contacts

### Quality Thresholds
1. **Verification rate**: 60% minimum acceptable
2. **Municipality coverage**: 80% minimum
3. **Decision maker identification**: 15%+ of total contacts
4. **Complete contact records**: 70%+ with full information

---

**Ready to generate comprehensive municipal prospect lists?**

```bash
/prospect-county [Your County], [State]
```

**Expected delivery**: 100-300+ municipal contacts with T-Mobile targeting in 60-90 minutes