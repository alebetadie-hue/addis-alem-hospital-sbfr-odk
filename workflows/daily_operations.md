# Daily Operations Workflow

## Addis Alem Hospital SBFR Team - Daily Checklist

---

## Morning Briefing (8:00 AM - 8:30 AM)

### Pre-Work Setup
- [ ] Arrive at work station on time
- [ ] Boot up computer and open necessary applications
- [ ] Check email for urgent messages from supervisors
- [ ] Review daily schedule and assigned tasks
- [ ] Collect any printed forms or documents needed

### Team Briefing
- [ ] Participate in 8:30 AM team meeting
- [ ] Review daily targets and priorities
- [ ] Acknowledge any changes to workflows or procedures
- [ ] Raise any concerns or issues from previous day
- [ ] Confirm assignment of tasks for the day

---

## Data Collection (8:30 AM - 12:00 PM)

### Patient Intake Process
1. [ ] Greet patient and verify identity
2. [ ] Open Patient Intake Form
3. [ ] Collect demographic information:
   - Full name
   - Date of birth
   - Contact information
   - Insurance details (if applicable)
4. [ ] Record visit type (new/follow-up)
5. [ ] Document presenting complaint
6. [ ] Verify form completeness
7. [ ] Save form with correct naming convention: `PATIENT_[ID]_[DATE].json`

### Service Delivery Recording
1. [ ] Service ID assignment
2. [ ] Record service type (consultation, lab, imaging, etc.)
3. [ ] Document provider details
4. [ ] Record service date and time
5. [ ] Document service cost/billing information
6. [ ] Verify against service delivery schema
7. [ ] Save file with naming: `SERVICE_[ID]_[DATE].json`

### Quality Checks
- [ ] Verify all mandatory fields are completed
- [ ] Check data format matches schema requirements
- [ ] Ensure no duplicate entries
- [ ] Validate dates are realistic
- [ ] Cross-check with existing patient records

---

## Mid-Day Break (12:00 PM - 1:00 PM)

- [ ] Take lunch break
- [ ] Review morning data submissions
- [ ] Check for any validation errors
- [ ] Communicate any issues to supervisor

---

## Afternoon Data Processing (1:00 PM - 4:00 PM)

### Data Entry and Validation
1. [ ] Process forms from morning collection
2. [ ] Run data validation script:
   ```bash
   python implementation/scripts/data_validation.py --file morning_data.csv
   ```
3. [ ] Review validation report
4. [ ] Correct any flagged errors
5. [ ] Re-validate corrected data
6. [ ] Document corrections in audit log

### Financial Tracking
1. [ ] Record all financial transactions
2. [ ] Update financial tracking form
3. [ ] Reconcile daily receipts
4. [ ] Enter budget allocations
5. [ ] Verify amounts match documentation
6. [ ] Flag any discrepancies

### Data Import
1. [ ] Prepare data for import
2. [ ] Run import script:
   ```bash
   python implementation/scripts/data_import.py --source daily_data.xlsx --format xlsx
   ```
3. [ ] Verify import success
4. [ ] Check data in system
5. [ ] Document import in log

---

## End of Day Closure (4:00 PM - 4:30 PM)

### Final Checks
- [ ] Verify all data entered for the day
- [ ] Run daily data validation
- [ ] Review error logs
- [ ] Document any outstanding issues
- [ ] Prepare summary for supervisor review

### System Backup
- [ ] Backup daily data files
- [ ] Save all forms in archive folder
- [ ] Close all applications properly
- [ ] Lock workstation

### Handover Notes
- [ ] Write end-of-day report
- [ ] Note any pending items for next day
- [ ] Communicate to next shift (if applicable)
- [ ] File all physical documents

---

## Daily Report Template

```
DATE: [DATE]
STAFF NAME: [NAME]
STAFF ID: [ID]

MORNING ACTIVITIES:
- Patients processed: [NUMBER]
- Forms completed: [NUMBER]
- Issues encountered: [DETAILS]

AFTERNOON ACTIVITIES:
- Data validations: [NUMBER]
- Errors found: [NUMBER]
- Corrections made: [NUMBER]
- Financial transactions: [NUMBER]

END OF DAY STATUS:
- All data processed: YES / NO
- Outstanding issues: [DETAILS]
- Notes for next day: [DETAILS]

SUPERVISOR SIGN-OFF:
Name: ________________
Signature: ________________
Date: ________________
Time: ________________
```

---

## Important Reminders

✓ Always verify data before submission
✓ Use correct file naming conventions
✓ Follow data privacy guidelines
✓ Report errors immediately
✓ Keep audit logs updated
✓ Maintain confidentiality
✓ Ask supervisor if unsure
✓ Document all actions taken

---

## Contact Information

- **Direct Supervisor**: [Contact]
- **Data Manager**: [Contact]
- **IT Support**: [Contact]
- **Emergency Contact**: [Phone]

---

**Last Updated**: September 15, 2026
