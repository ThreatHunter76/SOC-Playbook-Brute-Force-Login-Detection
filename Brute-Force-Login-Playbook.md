SOC Playbook: Brute Force Login Detection
📌 1. Use Case

Detection and response to multiple failed login attempts indicating a potential brute force attack.

🎯 2. Objective
Identify suspicious login activity
Determine if the activity is malicious
Take appropriate action to prevent unauthorized access


🧰 3. Data Sources
Windows Security Event Logs
SIEM tools like Wazuh or Splunk


🚨 4. Alert Trigger
Multiple failed login attempts (Event ID 4625) within a short period
Possible successful login after failures (Event ID 4624)
🔍 5. Investigation Steps

Step 1: Review Alert Details

Check username involved
Note timestamp and frequency of failed attempts

Step 2: Identify Source of Attempts

Extract source IP address
Determine if IP is internal or external

Step 3: Check for Successful Login


Look for Event ID 4624 after multiple failures
Confirm if access was eventually granted


Step 4: Analyze Behavior

Multiple usernames from one IP → Likely brute force
One username targeted → Possible credential stuffing

Step 5: Correlate Logs


Check firewall, VPN, or endpoint logs for same IP activity
⚖️ 6. Decision Criteria
Condition	Interpretation
Few failed attempts	Normal user mistake
Many failed attempts (short time)	Suspicious activity
Successful login after failures	Possible compromise

🚑 7. Response Actions
Block or blacklist malicious IP address
Disable or lock affected user account
Force password reset
Enable multi-factor authentication (MFA) if not already active
Escalate to Tier 2 if compromise is confirmed

📝 8. Documentation & Reporting
Record:
Username
Source IP
Number of attempts
Outcome (success/failure)
Create incident report and update ticketing system
🔄 9. Lessons Learned
Improve detection rules if alert was missed or delayed
Update playbook if new attack pattern is observed
