# Rapid Discovery & Research Workflow

## Purpose
**SPEED-OPTIMIZED**: Discover municipalities and extract contacts in one fast combined phase.
**TARGET**: 100-400 raw contacts in 30-45 minutes

## Execution Strategy

### Quick County Assessment (2-3 minutes)

**County Size & Complexity Analysis**
```markdown
BEFORE starting extraction, do quick assessment:

1. SEARCH: "[County] [State] population"
2. SEARCH: "[County] [State] municipalities list" 
3. COUNT: Number of incorporated cities/towns
4. ASSESS: County government website sophistication

COUNTY CLASSIFICATION:
```

**Large County (500K+ population, 20+ municipalities):**
- Target contacts: 200-400
- County government target: 30-50 contacts
- Research time: County (10 min) + Others (45-60 min) = 55-70 min total

**Medium County (100K-500K population, 10-25 municipalities):**
- Target contacts: 100-250  
- County government target: 20-35 contacts
- Research time: County (8 min) + Others (30-45 min) = 38-53 min total

**Small County (25K-100K population, 5-15 municipalities):**
- Target contacts: 50-150
- County government target: 10-25 contacts  
- Research time: County (6 min) + Others (20-35 min) = 26-41 min total

**Rural County (under 25K population, 3-10 municipalities):**
- Target contacts: 25-75
- County government target: 8-15 contacts
- Research time: County (5 min) + Others (15-25 min) = 20-30 min total
```

**Rapid County Research**
```markdown
1. SEARCH: "[County] [State] municipalities list"
2. SEARCH: "[County] [State] cities towns government"  
3. FETCH: County official website municipal directory
4. SCAN: Wikipedia page for county municipalities
5. EXTRACT: Municipal entity names and websites quickly
```

**Comprehensive Entity Collection**
```markdown
TARGET ALL LOCAL GOVERNMENT ENTITIES:

BASIC MUNICIPALITIES:
✓ Cities, towns, villages, boroughs, townships
✓ County government offices and departments
✓ Municipal utilities (water, electric, gas, waste)

EMERGENCY & PUBLIC SAFETY:
✓ 911 Emergency Centers / Dispatch Centers
✓ Sheriff's Departments (county law enforcement)
✓ Municipal Police Departments
✓ Fire Departments / Fire Districts
✓ Emergency Management Agencies
✓ Emergency Medical Services (municipal)

SPECIAL DISTRICTS & AUTHORITIES:
✓ Water Districts / Water Authorities
✓ Sewer Districts / Sanitation Departments
✓ Transportation Authorities / Transit Agencies
✓ Airport Authorities
✓ Port Authorities (if applicable)
✓ Housing Authorities / Redevelopment Agencies
✓ Library Systems (municipal/county)
✓ Parks & Recreation Districts
✓ Cemetery Districts
✓ Hospital Districts (public)

SPECIALIZED SERVICES:
✓ Public Health Departments (local/county)
✓ Code Enforcement Departments
✓ Animal Control Services
✓ Building & Planning Departments
✓ Municipal Courts
✓ Probation Departments (local)
✓ Public Works Districts
✓ Flood Control Districts

SEARCH PATTERNS:
- "[County] [State] sheriff department"
- "[County] [State] 911 emergency center"
- "[County] [State] fire district"
- "[County] [State] water authority"
- "[County] [State] special districts"
- "[County] [State] transportation authority"
- "[County] [State] hospital district"
- "[County] [State] housing authority"

CREATE COMPREHENSIVE LIST:
[
  {"name": "Hamilton County Sheriff's Office", "website": "https://hcsheriff.gov", "type": "sheriff"},
  {"name": "Hamilton County 911", "website": "https://hamilton911.org", "type": "emergency"},
  {"name": "Chattanooga Fire Department", "website": "https://chattanooga.gov/fire", "type": "fire"},
  {"name": "Hamilton County Water Authority", "website": "https://hcwater.org", "type": "water_utility"},
  {"name": "CARTA (Transit Authority)", "website": "https://gocarta.org", "type": "transportation"},
  // ... continue for all found entities
]
```

### Aggressive Contact Extraction (25-35 minutes)

**High-Speed Contact Harvesting**
```markdown
FOR COUNTY GOVERNMENT (8-10 minutes - COMPREHENSIVE):

1. HIT MAIN COUNTY WEBSITE
   - Look for "Departments", "Staff Directory", "Organization Chart"
   - Search for "County Commission" or "County Council" staff
   - Find "Elected Officials" pages with staff listings

2. HIT ALL COUNTY DEPARTMENT PAGES INDIVIDUALLY:
   - /administration or /county-manager
   - /information-technology or /it
   - /finance or /budget or /accounting  
   - /human-resources or /hr or /personnel
   - /engineering or /public-works
   - /planning or /development or /zoning
   - /health or /health-department
   - /emergency-management or /ema
   - /parks or /parks-recreation
   - /clerk or /county-clerk
   - /treasurer or /finance-director
   - /assessor or /property-assessor
   - /elections or /election-commission
   - /probation or /corrections
   - /courts or /judicial

3. SEARCH FOR COUNTY-SPECIFIC TERMS:
   - "Hamilton County staff directory"
   - "Hamilton County organizational chart"
   - "Hamilton County department heads"
   - "Hamilton County commission staff"
   - "Hamilton County employee directory"

4. CHECK BUDGET/ANNUAL REPORTS:
   - Often list all department heads and key personnel
   - Search "[County] annual report" or "[County] budget"

FOR OTHER MUNICIPALITIES (2-3 minutes max per entity):

1. HIT MAIN WEBSITE
   - Look for "Staff Directory", "Contact Us", "Departments"
   - Grab ALL contacts with email addresses immediately
   - Don't verify accuracy yet - just collect

2. HIT DEPARTMENT PAGES
   - /administration, /it, /police, /fire, /public-works, /parks
   - Extract any staff listings with contact info
   - Include administrative assistants and coordinators

3. HIT CONTACT/STAFF PAGES  
   - Grab names, titles, emails, phones in bulk
   - Include deputy positions and department staff
   - Don't skip "lesser" positions - volume matters

4. QUICK PATTERN EXTRACTION
   Extract contacts matching these patterns:
   - firstname.lastname@countyname.gov (for county)
   - firstname.lastname@cityname.gov (for cities)
   - department@countyname.gov  
   - Any @[government domain].gov emails
   - Phone numbers in (XXX) XXX-XXXX format
```

**Contact Data Structure (Minimal for Speed)**
```json
{
  "contact_id": "auto_generated",
  "name": "John Smith",
  "title": "IT Director", 
  "department": "Information Technology",
  "municipality": "City of Chattanooga",
  "email": "john.smith@chattanooga.gov",
  "phone": "(423) 555-0123",
  "source_url": "https://chattanooga.gov/staff",
  "extraction_date": "2024-01-15",
  "needs_verification": true
}
```

### Volume-Focused Extraction Rules

**INCLUDE THESE ROLES (cast wide net):**
```yaml
Administration:
  - City Manager, Mayor, Assistant Manager, City Clerk
  - Administrative Assistant, Executive Secretary  
  - Deputy positions, Coordinators

Technology:
  - IT Director, CIO, Technology Manager
  - Network Administrator, Systems Admin, IT Support
  - Technology Coordinator, IT Specialist

Public Safety:
  - Police Chief, Deputy Chief, Captain, Commander
  - Fire Chief, Deputy Fire Chief, Battalion Chief
  - Emergency Manager, Communications Supervisor

Operations:
  - Public Works Director, City Engineer, Streets Supervisor
  - Parks Director, Recreation Director, Facilities Manager
  - Utilities Manager, Water Supervisor, Building Inspector

Support Staff:
  - Department secretaries with direct emails
  - Program coordinators with decision input
  - Assistant directors and deputy positions
```

**EXTRACTION EFFICIENCY RULES:**
```markdown
✓ Grab contact if they have municipal email + title
✓ Include assistants - they often handle vendor outreach
✓ Don't skip small departments or single-person offices
✓ Include interim/acting positions
✓ Grab contacts even with minimal information

❌ Don't spend time verifying employment status
❌ Don't skip municipalities with poor websites
❌ Don't exclude contacts for missing phone numbers
❌ Don't overthink title variations or accuracy
```

### Municipal Coverage Strategy

**Research Time Allocation (Based on County Assessment):**
```markdown
COUNTY GOVERNMENT (DEDICATED TIME - doesn't reduce other municipality time):
- Large County: 10 minutes dedicated to county government
- Medium County: 8 minutes dedicated to county government  
- Small County: 6 minutes dedicated to county government
- Rural County: 5 minutes dedicated to county government

OTHER MUNICIPALITIES (separate time allocation):
- Large cities/towns: 3-4 minutes each
- Medium cities/towns: 2-3 minutes each
- Small towns: 1-2 minutes each
- Special districts: 1-2 minutes each

TOTAL TIME EXAMPLES:
- Large County: 10 min (county) + 50 min (others) = 60 min total
- Medium County: 8 min (county) + 35 min (others) = 43 min total
- Small County: 6 min (county) + 25 min (others) = 31 min total
- Rural County: 5 min (county) + 20 min (others) = 25 min total

COUNTY GOVERNMENT RESEARCH STRATEGY (use dedicated time):
1. SEARCH: "[County] [State] government departments"
2. SEARCH: "[County] [State] organizational chart"
3. SEARCH: "[County] [State] staff directory"
4. SEARCH: "[County] [State] department contacts"
5. HIT INDIVIDUAL DEPARTMENT PAGES:
   - /administration, /finance, /hr, /it, /engineering
   - /planning, /development, /health, /parks
   - /clerk, /treasurer, /assessor, /elections
   - /probation, /courts, /emergency-management
6. SEARCH: "[County] commission staff" or "[County] council staff"
7. CHECK: Recent county budget documents (often list department heads)

GOAL: County government gets appropriate attention without reducing other municipality coverage
```

### Rapid Quality Checks (Built-in, not separate)

**During Extraction (30 seconds per contact):**
```bash
# Quick format validation
valid_email=$(echo "$email" | grep -E '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$')
valid_phone=$(echo "$phone" | grep -E '^\(?[0-9]{3}\)?[-. ]?[0-9]{3}[-. ]?[0-9]{4}')

# Basic completeness check
if [[ -n "$name" && -n "$email" && -n "$municipality" ]]; then
    quality_level="complete"
elif [[ -n "$name" && -n "$email" ]]; then
    quality_level="partial"  
else
    quality_level="minimal"
fi
```

**Deduplication (Quick Pass):**
```markdown
WHILE EXTRACTING:
- Flag obvious duplicates (same email address)
- Note title variations for same person
- Don't spend time resolving - mark for later cleanup
```

## Output Generation

**Create `data/working/contacts-discovered.json`:**
```json
[
  {
    "contact_id": "hamilton_001",
    "name": "John Smith",
    "title": "IT Director",
    "department": "Information Technology", 
    "municipality": "City of Chattanooga",
    "municipality_type": "city",
    "email": "john.smith@chattanooga.gov",
    "phone": "(423) 643-7000",
    "source_url": "https://chattanooga.gov/staff-directory",
    "extraction_date": "2024-01-15",
    "quality_level": "complete",
    "needs_verification": true,
    "preliminary_tmobile_target": "5G infrastructure, enterprise plans"
  }
  // ... 100-400 more contacts
]
```

## Success Metrics for Phase 1

**Volume Targets (Minimum):**
```bash
# Contact volume by county size
small_county_min=50    # Under 100K population
medium_county_min=100  # 100K-500K population  
large_county_min=150   # 500K+ population

# Municipality coverage
municipality_coverage_min=80  # 80% of discovered entities

# Contact quality distribution
complete_contacts_min=60      # 60% with name, title, email, phone
partial_contacts_max=35       # 35% missing 1-2 fields
minimal_contacts_max=5        # 5% with just name/email
```

**Time Targets:**
```markdown
Municipality Discovery: 5-10 minutes total
Contact Extraction: 20-35 minutes total (2-3 min per municipality)
Data Formatting: 5 minutes
TOTAL PHASE 1: 30-45 minutes maximum
```

## Handoff to Phase 2

**File Created**: `data/working/contacts-discovered.json`
**Next Workflow**: `workflows/finalize-prospects.md`

**What Phase 2 Gets**:
- 100-400 raw municipal contacts
- Basic format validation completed
- Municipal coverage across county
- Volume optimized for comprehensive sales prospecting
- Ready for efficient verification and T-Mobile targeting

**Phase 1 Success Criteria (Dynamic Based on County Assessment)**:

**Large County Success Criteria:**
- [ ] 150+ contacts minimum (target 200-400)
- [ ] County government: 30-50 contacts (15-20% of total)
- [ ] 80%+ municipalities covered
- [ ] Execution completed in 55-70 minutes

**Medium County Success Criteria:**
- [ ] 80+ contacts minimum (target 100-250)
- [ ] County government: 20-35 contacts (20-25% of total)
- [ ] 80%+ municipalities covered  
- [ ] Execution completed in 38-53 minutes

**Small County Success Criteria:**
- [ ] 40+ contacts minimum (target 50-150)
- [ ] County government: 10-25 contacts (20-30% of total)
- [ ] 75%+ municipalities covered
- [ ] Execution completed in 26-41 minutes

**Rural County Success Criteria:**
- [ ] 20+ contacts minimum (target 25-75)
- [ ] County government: 8-15 contacts (25-35% of total)
- [ ] 70%+ municipalities covered
- [ ] Execution completed in 20-30 minutes

**Universal Quality Criteria (All Counties):**
- [ ] 60%+ contacts have complete basic information
- [ ] All contacts have municipal email addresses
- [ ] County departments well-represented (IT, Finance, Planning, Health, etc.)
- [ ] No reduction in other municipality coverage due to county focus