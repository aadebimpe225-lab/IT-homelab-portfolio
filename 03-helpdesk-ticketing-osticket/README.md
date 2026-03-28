Help Desk Ticketing System Practice — osTicket
Overview
A hands-on simulation of a real help desk environment using osTicket, an open-source ticketing platform used by IT departments worldwide. This project involved creating, managing, and resolving over 30 mock support tickets to practice the full lifecycle of help desk operations — from intake to resolution.
---
Skills Demonstrated
Help desk ticketing workflow (open → in-progress → resolved → closed)
Ticket categorization, prioritization, and escalation
Customer communication and professional follow-up
Common IT issue triage: password resets, email, printers, performance
Knowledge base building and documentation
SLA awareness and priority management
---
Platform Overview
osTicket is a widely-used, open-source help desk and ticketing system. It supports:
Web-based ticket submission portal (end-user facing)
Agent panel for ticket management and response
Departments, teams, and role-based assignments
SLA plans, canned responses, and internal notes
Knowledge base (FAQ) for self-service
---
Lab Environment Setup
Component	Details
Platform	osTicket (self-hosted)
Hosting	Local XAMPP / WAMP or virtual machine
Version	osTicket v1.18.x
Access	Admin panel + Agent panel + User portal
---
osTicket Configuration Completed
Departments Created
IT Help Desk (Tier 1)
Systems Administration (Tier 2 Escalation)
Network Operations
Management
Help Topics (Ticket Categories)
Password Reset
Email / Outlook Issues
Printer Connectivity
Slow Workstation Performance
Software Installation Request
Account Unlock
Hardware Issue
VPN / Remote Access
New User Setup
General Inquiry
SLA Plans Configured
Priority	Response Time	Resolution Time	Use Case
Critical (Sev-A)	1 hour	4 hours	System outage, security incident
High (Sev-B)	4 hours	8 hours	Multiple users affected
Normal (Sev-C)	8 hours	24 hours	Single user issue
Low (Sev-D)	24 hours	72 hours	General requests
---
Ticket Practice — Sample Tickets
A total of 30+ mock tickets were created and worked through. Below is a representative sample:
---
Ticket #001 — Password Reset
Status: Resolved  
Priority: Normal  
Category: Password Reset  
User Message: "Hi, I forgot my Windows login password and can't get into my computer this morning."  
Resolution Steps:
Verified user identity via employee ID
Unlocked account in Active Directory (was locked after failed attempts)
Reset temporary password, required change at next login
Confirmed user logged in successfully
Resolution Time: 8 minutes
---
Ticket #002 — Outlook Not Receiving Emails
Status: Resolved  
Priority: High  
Category: Email / Outlook Issues  
User Message: "I haven't received any emails since this morning. I can send but nothing comes in."  
Resolution Steps:
Confirmed send/receive was not paused (offline mode off)
Checked OST file size — was at 50GB limit
Archived old emails to reduce mailbox size
Ran `Send/Receive All` — emails began arriving
Recommended enabling AutoArchive going forward
Resolution Time: 22 minutes
---
Ticket #003 — Printer Not Connecting
Status: Resolved  
Priority: Normal  
Category: Printer Connectivity  
User Message: "The printer in our office shows as offline. Nobody on our team can print."  
Resolution Steps:
Verified printer showed offline in Print Management
Pinged printer IP — no response; determined printer had rebooted and received new IP from DHCP
Updated the printer port with the new IP address
Cleared stuck print queue
Verified test page printed successfully from two workstations
Resolution Time: 18 minutes
---
Ticket #004 — Slow Workstation
Status: Resolved  
Priority: Normal  
Category: Slow Workstation Performance  
User Message: "My computer has been extremely slow for the past two days. Everything takes forever to open."  
Resolution Steps:
Checked Task Manager — identified high CPU usage from Windows Update service
Allowed pending updates to finish installing
Checked startup programs and disabled 6 unnecessary startup entries
Cleared temporary files using Disk Cleanup
Ran SFC scan: `sfc /scannow` — no integrity violations found
Confirmed with user — performance returned to normal
Resolution Time: 35 minutes
---
Ticket #005 — Account Locked Out
Status: Resolved  
Priority: High  
Category: Account Unlock  
User Message: "I'm getting 'your account has been locked' when trying to log in. I have a presentation in 20 minutes!"  
Resolution Steps:
Immediately unlocked account via Active Directory Users and Computers
Investigated lockout source using Event Viewer (found stale credential in mapped drive)
Cleared cached credentials from Credential Manager
Confirmed user logged in and presentation was not impacted
Documented root cause and solution
Resolution Time: 6 minutes
---
Ticket #006 — VPN Not Connecting
Status: Resolved  
Priority: High  
Category: VPN / Remote Access  
User Message: "I'm working from home and my VPN keeps disconnecting every 10 minutes."  
Resolution Steps:
Verified VPN client version — was outdated
Guided user through VPN client update remotely
Checked split tunneling settings
Verified user's home router wasn't blocking VPN protocols (UDP 500/4500)
Connection stabilized after client update
Resolution Time: 30 minutes
---
Full Ticket Summary (30+ Tickets)
Category	Count	Avg Resolution Time
Password Reset / Account Unlock	8	7 min
Email / Outlook Issues	5	25 min
Printer Connectivity	5	20 min
Slow Workstation Performance	4	40 min
Software Installation Requests	4	15 min
VPN / Remote Access	3	30 min
Hardware Issues	2	45 min
New User Setup	2	20 min
General Inquiry	2	5 min
Total	35	~23 min avg
---
Communication Templates Practiced
Initial Response (Acknowledgment)
> "Hi [Name], thank you for reaching out to the IT Help Desk. I've received your ticket (#XXXX) regarding [issue]. I'm looking into this now and will follow up shortly. If this is urgent, please call the help desk directly at [number]."
Resolution Response
> "Hi [Name], I'm happy to report that your issue has been resolved. [Brief explanation of what was done]. Please let me know if you experience any further issues or have questions. Have a great day!"
Follow-Up After No Response (48 hours)
> "Hi [Name], I wanted to follow up on ticket #XXXX. We have a solution ready — please let us know if you're still experiencing the issue or if we can close this ticket. Thank you!"
---
Key Takeaways
Prioritization matters: Learned to assess urgency vs. impact — a single user locked out before a presentation is higher priority than a general inquiry
Documentation is critical: Good ticket notes allow any agent to pick up where another left off
Customer communication sets expectations: A quick acknowledgment prevents "is anyone working on this?" follow-up messages
Pattern recognition saves time: Seeing the same issue (e.g., Outlook OST size) multiple times builds a repeatable resolution path
Escalation judgment: Knowing when to escalate vs. handle at Tier 1 is a core help desk skill
---
Relevance to Help Desk / IT Support Roles
This lab directly mirrors a day in the life of a Tier 1 help desk analyst:
Working within a ticketing queue under SLA pressure
Communicating professionally with end users
Triaging and categorizing tickets accurately
Documenting resolutions for the knowledge base
Escalating appropriately when a ticket exceeds Tier 1 scope
---
Lab Status
Active — new ticket scenarios added weekly to expand coverage of common enterprise IT issues.
