# Data Collection Workflow

## Complete Guide for Addis Alem Hospital SBFR Team

---

## Phase 1: Preparation (Before Data Collection)

### Step 1.1: Planning
- [ ] Identify data collection period
- [ ] Determine target population or sample
- [ ] Prepare collection schedule
- [ ] Allocate staff resources
- [ ] Ensure forms are available
- [ ] Brief team members

### Step 1.2: Resource Allocation
- [ ] Print required forms (if needed)
- [ ] Download digital forms
- [ ] Prepare Excel templates
- [ ] Set up data entry stations
- [ ] Test all systems and equipment
- [ ] Charge all devices (tablets/laptops)

### Step 1.3: Staff Briefing
- [ ] Review data collection procedures
- [ ] Discuss quality standards
- [ ] Answer staff questions
- [ ] Distribute contact information
- [ ] Assign roles and responsibilities
- [ ] Confirm understanding of tasks

---

## Phase 2: Data Collection (Active Collection)

### Step 2.1: Initial Contact
**Procedure**:
1. Greet respondent/patient professionally
2. Introduce yourself and your role
3. Explain purpose of data collection
4. Confirm willingness to participate
5. Ensure privacy and confidentiality
6. Obtain informed consent (if required)

**Documentation**:
```json
{
  "encounter_id": "ENC_20260915_001",
  "date_time": "2026-09-15T09:30:00Z",
  "collector_name": "[Name]",
  "collector_id": "[ID]",
  "respondent_consent": "YES",
  "consent_timestamp": "2026-09-15T09:30:00Z"
}
```

### Step 2.2: Form Completion
**For Each Form**:
1. [ ] Verify form version is current
2. [ ] Check form is blank/unused
3. [ ] Record date and time of collection
4. [ ] Complete all mandatory fields:
   - Respondent information
   - Service details
   - Clinical information (if applicable)
   - Financial information (if applicable)
5. [ ] Use clear, legible handwriting (paper forms)
6. [ ] Record values as numbers (not text) when applicable
7. [ ] Verify data entry accuracy before submission
8. [ ] Obtain respondent signature/thumbprint
9. [ ] Record collector name and signature
10. [ ] Assign unique form ID

**Form Naming Convention**:
```
[FORM_TYPE]_[DATE]_[COUNTER]_[COLLECTOR_ID].json
Example: PATIENT_20260915_001_COL001.json
```

### Step 2.3: Quality Assurance During Collection

**Real-time Checks**:
- [ ] Missing data items identified immediately
- [ ] Invalid entries flagged during completion
- [ ] Respondent asked to clarify ambiguous responses
- [ ] Cross-checks performed (e.g., age vs. DOB)
- [ ] Form completeness verified before moving on

**Field-level Validation**:
```
Validation Rules:
- Age: Must be between 0-120
- Phone: Must match format +251[9][0-9]{8}
- Date: Must be realistic (not future date for birth)
- Amount: Must be non-negative number
- Required fields: Cannot be empty
```

---

## Phase 3: Data Entry (After Collection)

### Step 3.1: Form Transfer
1. [ ] Collect completed forms from field
2. [ ] Sort forms by collector and date
3. [ ] Create collection batch:
   ```
   BATCH_[DATE]_[COLLECTOR]_[COUNT].zip
   Example: BATCH_20260915_COL001_025.zip
   ```
4. [ ] Verify all forms accounted for
5. [ ] Create backup copy
6. [ ] Transport securely to data entry station

### Step 3.2: Data Entry Process

**Setup**:
```bash
# Navigate to data-collection directory
cd data-collection/

# Create today's entry folder
mkdir entries/20260915/

# Open form template
open forms/patient_intake_form.json
```

**Entry Steps**:
1. [ ] Open form in JSON editor or Excel
2. [ ] Transfer data from paper form OR digital form
3. [ ] Verify each entry against original
4. [ ] Apply standard formatting:
   - Dates: YYYY-MM-DD
   - Phone: +251 format
   - Names: Proper case
   - Currency: Two decimal places
5. [ ] Save entry with timestamp
6. [ ] Move to validation queue

**Data Entry Validation**:
```bash
# Run real-time validation
python implementation/scripts/data_validation.py \
  --file entries/20260915/form_001.json \
  --schema schemas/patient_schema.json
```

### Step 3.3: Error Correction

**When Errors Found**:
1. [ ] Document error in error log
2. [ ] Attempt to clarify with original respondent (if possible)
3. [ ] Make corrections with audit trail
4. [ ] Document reason for correction
5. [ ] Initial correction with name and date
6. [ ] Re-validate corrected data

**Error Log Entry**:
```json
{
  "error_id": "ERR_20260915_001",
  "form_id": "PATIENT_20260915_001_COL001",
  "field": "date_of_birth",
  "original_value": "2000-01-35",
  "corrected_value": "2000-01-15",
  "reason": "Invalid date - corrected with patient",
  "corrected_by": "[Name]",
  "correction_date": "2026-09-15",
  "status": "resolved"
}
```

---

## Phase 4: Data Validation (Quality Control)

### Step 4.1: Automated Validation

```bash
# Run complete validation suite
python implementation/scripts/data_validation.py \
  --directory entries/20260915/ \
  --report validation_report_20260915.html
```

**Validation Checks**:
- [ ] All mandatory fields present
- [ ] Data types correct (date, number, text)
- [ ] Values within acceptable ranges
- [ ] No duplicate entries
- [ ] Logical consistency (e.g., service date after patient registration)
- [ ] Referential integrity (if applicable)

### Step 4.2: Manual Review

**Spot Checks** (Review 10% of entries):
1. [ ] Select random sample of forms
2. [ ] Compare data entry to original form
3. [ ] Verify accuracy of transcription
4. [ ] Check data formatting
5. [ ] Note any patterns of error
6. [ ] Escalate systematic issues to supervisor

**Quality Review Checklist**:
```
Form ID: _______________
Reviewer Name: _______________
Review Date: _______________

Data Entry Accuracy:
[ ] All fields entered correctly
[ ] Data format correct
[ ] No transcription errors
[ ] Values match original form

Data Quality:
[ ] No missing required data
[ ] Reasonable data values
[ ] Consistent with other entries
[ ] Clear and legible

Documentation:
[ ] All audit trails present
[ ] Signatures/initials present
[ ] Timestamps recorded
[ ] Error log up to date

Status: PASS / FAIL
Comments: _______________
Reviewer Signature: _______________
```

### Step 4.3: Data Approval

**Sign-off Process**:
1. [ ] All validations passed
2. [ ] All errors corrected
3. [ ] Manual review completed
4. [ ] Supervisor review completed
5. [ ] Approval signature obtained
6. [ ] Data locked for import

---

## Phase 5: Data Management

### Step 5.1: Data Import

```bash
# Prepare data for import
python implementation/scripts/data_import.py \
  --source entries/20260915/ \
  --format json \
  --destination database \
  --create-backup yes
```

**Import Verification**:
- [ ] Import completes without errors
- [ ] Record count matches source
- [ ] Data integrity verified
- [ ] Backup created successfully
- [ ] System reports show all records

### Step 5.2: Data Backup

```bash
# Create backup of collected data
tar -czf backups/collection_20260915.tar.gz entries/20260915/
cp backups/collection_20260915.tar.gz /external_drive/
```

**Backup Checklist**:
- [ ] Local backup created
- [ ] External backup created
- [ ] Backup integrity verified
- [ ] Backup location documented
- [ ] Backup access restricted to authorized staff

### Step 5.3: Data Archiving

**Archive Protocol**:
1. [ ] Move validated data to archive folder
2. [ ] Update archive inventory
3. [ ] Document archive location
4. [ ] Restrict archive access
5. [ ] Plan retention schedule
6. [ ] Schedule secure deletion (per policy)

---

## Phase 6: Reporting

### Step 6.1: Generate Summary Reports

```bash
# Generate automated report
python implementation/scripts/generate_reports.py \
  --data-source entries/20260915/ \
  --report-type summary \
  --output-format html \
  --output-file reports/summary_20260915.html
```

### Step 6.2: Create Data Summary

**Summary Report Contents**:
- Total records collected: [NUMBER]
- Forms by type: [BREAKDOWN]
- Data quality score: [PERCENTAGE]
- Errors found: [NUMBER]
- Errors corrected: [NUMBER]
- Records approved: [NUMBER]
- Records pending: [NUMBER]
- Collection duration: [TIME]
- Staff involved: [NAMES]

---

## Troubleshooting Guide

### Common Issues and Solutions

**Issue**: Missing data in required field
- **Solution**: Contact respondent for clarification, update correction log

**Issue**: Invalid date format
- **Solution**: Correct to YYYY-MM-DD format, document in error log

**Issue**: Duplicate form submissions
- **Solution**: Identify duplicate, mark original as invalid, keep latest

**Issue**: Data import fails
- **Solution**: Check file format, run validation, contact IT support

**Issue**: Validation script error
- **Solution**: Check schema file, verify Python installation, review error log

---

## Documentation and Audit Trail

### Required Documentation
- [ ] Collection date and time
- [ ] Collector name and ID
- [ ] Form version used
- [ ] Respondent consent
- [ ] Data validation results
- [ ] Corrections made
- [ ] Supervisor approval
- [ ] Data import confirmation

---

**Last Updated**: September 15, 2026
