# Streamlined Prospect County Command

## Command: `/prospect-county`

**High-volume municipal prospecting optimized for speed and comprehensive coverage.**

**Target**: 100-300+ contacts per county in 60-90 minutes

## Input: $ARGUMENTS
County name and state (e.g., "Hamilton County, TN")

## Streamlined 2-Phase Execution

### 0. **Quick Setup** ⚙️ (2 minutes)
- **Parse input**: Extract county and state from $ARGUMENTS
- **Create workspace**: Set up `data/working/` directory
- **Load context**: READ `PROSPECTING.md` for updated efficiency rules

### 1. **Phase 1: Rapid Discovery & Research** 🔍 (30-45 minutes)
```bash
EXECUTE: workflows/rapid-research.md
INPUT: County name and state
OUTPUT: data/working/contacts-discovered.json (100-400 raw contacts)
TARGET: Comprehensive contact extraction, verification later
```

**What Phase 1 Does:**
- Discovers all municipalities in county (15-40 entities)
- Extracts contacts from ALL municipal sources rapidly
- Includes directors, managers, coordinators, assistants, specialists
- Focuses on quantity and coverage, not perfect verification
- Gets contact info from staff directories, department pages, contact pages

### 2. **Phase 2: Finalize Prospects** ✅ (20-30 minutes)
```bash
EXECUTE: workflows/finalize-prospects.md  
INPUT: data/working/contacts-discovered.json
OUTPUT: data/outputs/[County]_[State]_Prospects_[Date].txt
TARGET: Efficient verification, targeting, and sales-ready output
```

**What Phase 2 Does:**
- Bulk verification through LinkedIn for decision makers
- Format validation and employment checks for all contacts
- T-Mobile product targeting using pattern matching
- Sales prioritization and final formatted output
- Quality scoring without over-analysis

### 3. **Completion Summary** 📊 (2 minutes)
- **Validate output**: Confirm prospect file created with target contact volume
- **Report metrics**: Total contacts, verification rate, municipality coverage
- **Cleanup**: Archive working files and prepare summary

## Validation Gates (Streamlined)

### Phase 1 Gate: Volume Check (Dynamic)
```bash
discovered_contacts=$(jq length data/working/contacts-discovered.json)
municipalities_found=$(jq '[.[].municipality] | unique | length' data/working/contacts-discovered.json)
county_gov_contacts=$(jq '[.[] | select(.municipality | contains("County"))] | length' data/working/contacts-discovered.json)

echo "Raw contacts discovered: $discovered_contacts"
echo "Municipalities covered: $municipalities_found"
echo "County government contacts: $county_gov_contacts"

# DYNAMIC SUCCESS CRITERIA BASED ON COUNTY ASSESSMENT:
# Large County: 150+ contacts, 30+ county gov
# Medium County: 80+ contacts, 20+ county gov  
# Small County: 40+ contacts, 10+ county gov
# Rural County: 20+ contacts, 8+ county gov
# 80%+ of discovered municipalities have contacts (75% for small, 70% for rural)
```

### Phase 2 Gate: Quality Check
```bash
final_contacts=$(grep -c "^Contact:" data/outputs/$(ls data/outputs/ | tail -1))
verified_contacts=$(grep -c "Confidence: High\|Medium" data/outputs/$(ls data/outputs/ | tail -1))
verification_rate=$((verified_contacts * 100 / final_contacts))

echo "Final prospect count: $final_contacts"
echo "Verification rate: $verification_rate%"

# SUCCESS CRITERIA:
# - 80+ final contacts minimum
# - 60%+ verification rate (relaxed from 80%)
# - All contacts have T-Mobile product targeting
```

## Performance Targets

### Contact Volume Expectations
```yaml
Large County (500K+ population, 20+ municipalities):
  target_contacts: 200-400
  county_government: 30-50 contacts
  execution_time: 55-70 minutes

Medium County (100K-500K population, 10-25 municipalities):  
  target_contacts: 100-250
  county_government: 20-35 contacts
  execution_time: 38-53 minutes

Small County (25K-100K population, 5-15 municipalities):
  target_contacts: 50-150
  county_government: 10-25 contacts
  execution_time: 26-41 minutes

Rural County (under 25K population, 3-10 municipalities):
  target_contacts: 25-75
  county_government: 8-15 contacts
  execution_time: 20-30 minutes
```

### Speed Optimizations Applied
- **Combined workflows**: Reduced 5 phases to 2 phases
- **Bulk processing**: Process all municipalities then all contacts
- **Relaxed verification**: 60% threshold vs 80% for speed
- **Pattern matching**: Quick targeting vs deep analysis
- **Parallel mindset**: Extract volume first, refine second

## Error Handling (Simplified)

### Phase 1 Recovery
```markdown
IF contact discovery < 50:
1. Extend search to cached website versions
2. Include smaller municipal entities (parks districts, etc.)
3. Search for regional government cooperatives
4. Include county department contacts

IF municipality discovery < 10:
1. Search Wikipedia for municipality lists
2. Check state government municipal databases  
3. Include unincorporated areas with services
4. Search for special districts and authorities
```

### Phase 2 Recovery  
```markdown
IF verification rate < 50%:
1. Reduce verification requirements to format validation only
2. Include contacts with title + email as "medium confidence"
3. Focus verification on decision makers only
4. Use professional associations for batch verification

IF targeting assignment fails:
1. Apply department-based pattern matching
2. Use title keyword matching for product assignment
3. Default to enterprise plans for unclear roles
4. Include all contacts with basic targeting
```

## Success Criteria (Updated)
- [ ] 80+ final contacts minimum (vs 12 previously)
- [ ] 60%+ verification rate (pragmatic vs perfectionist)
- [ ] 90%+ municipalities covered with at least one contact
- [ ] 100% contacts have T-Mobile product targeting
- [ ] Execution time under 90 minutes total
- [ ] Sales-ready output format with clear prioritization
- [ ] Quality metrics documented but not restrictive

## Anti-Patterns to Avoid (Updated)
- ❌ Don't spend excessive time verifying every contact detail
- ❌ Don't skip municipalities due to limited web presence  
- ❌ Don't exclude contacts for minor information gaps
- ❌ Don't over-analyze during rapid extraction phase
- ❌ Don't let perfect be the enemy of good (volume matters)
- ❌ Don't spend more than 3 minutes per municipality in Phase 1

## Output Promise
**Delivery**: 100-300+ municipal contacts with T-Mobile targeting in 60-90 minutes
**Quality**: Professional prospect list ready for immediate sales outreach  
**Coverage**: Comprehensive county-wide municipal contact coverage