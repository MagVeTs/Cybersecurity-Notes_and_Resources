Concrete plan for PJPT at 1-2 hrs/day.

  What to buy

  TCM PJPT exam bundle: $249 at https://certifications.tcm-sec.com/pjpt/

  The bundle includes:
  - The PJPT exam voucher (1 attempt + 1 free retake)
  - Access to the TCM courses relevant to PJPT scope (Practical Ethical Hacking + Active Directory content — confirm exact course list on the purchase page)
  - Voucher valid 12 months from purchase date

  Don't buy anything else yet. No HackTheBox subscription up front, no extra courses. You may add a $20 HTB VIP month near the end for AD box practice. That's it.

  Setup at home (free):
  - Install VirtualBox or VMware (free tier)
  - Download Kali Linux VM (free from kali.org)
  - Create a snapshot before each practice session so you can roll back cleanly

  Target total out-of-pocket: ~$250-$280 all-in.

  Target timeline at 1-2 hrs/day

  Realistic: 10-12 weeks from purchase to sitting the exam. You have 12 months on the voucher, so there's cushion if life happens.

  Phase 1 — Foundations (Weeks 1-4)

  Objective: Get fluent with the Kali toolkit and the basic Linux/web attack primitives.

  Work through TCM's Practical Ethical Hacking (PEH) course — the sections you need are:
  - Networking / Introduction to Linux (skim if comfortable)
  - Introduction to Python (skim if comfortable)
  - Information Gathering (Reconnaissance / Enumeration) — do thoroughly
  - Exploitation basics
  - Web application enumeration & exploitation (basics — this is lighter on PJPT than PNPT)
  - Introduction to Active Directory — the critical section, do very thoroughly

  PEH is ~25 hours of video total, but you can skim anything you already know. At 1-2 hrs/day, this phase takes ~4 weeks even accounting for lab exercises.

  Checkpoint at end of Phase 1: You can run nmap → enum4linux-ng / nxc smb → identify a foothold on a basic Linux VM without hints.

  Phase 2 — Active Directory core (Weeks 5-8)

  This is the heart of PJPT prep. Everything else is scaffolding.

  Work through TCM's Active Directory content in the course track. Build muscle memory on:

  1. AD enumeration tools:
    - nxc (NetExec, formerly crackmapexec) against SMB and LDAP
    - ldapsearch for raw LDAP queries
    - BloodHound with the bloodhound-python or rusthound collector
    - PowerView from a Windows foothold
  2. The core AD attacks:
    - Kerberoasting — impacket-GetUserSPNs, then hashcat -m 13100
    - ASREPRoasting — impacket-GetNPUsers, then hashcat -m 18200
    - Password spraying — kerbrute passwordspray or nxc smb --continue-on-success
    - ACL abuse — reading BloodHound results, exploiting GenericAll/WriteDacl via impacket-ntlmrelayx or bloodyAD
    - DCSync — impacket-secretsdump with a high-priv account
  3. Lateral movement:
    - impacket-psexec, impacket-wmiexec, impacket-smbexec
    - Pass-the-hash with nxc smb -H <hash>
    - Understanding when to use which (noise levels, logging differences)
  4. Windows privilege escalation (basics):
    - winPEAS output interpretation
    - Common privesc paths: unquoted service paths, weak service permissions, token impersonation (SeImpersonatePrivilege → Potato exploits)

  Build a practice AD lab. Free options, in increasing order of complexity:
  - TryHackMe "Attacktive Directory" room — ~2-3 hours, covers the basics end-to-end. Fastest intro.
  - TryHackMe "Breaching Active Directory" path — broader AD practice
  - Game of Active Directory (GOAD) — free open-source AD lab you self-host. Harder setup (needs ~16GB RAM) but mirrors real exam complexity. Setup guide: github.com/Orange-Cyberdefense/GOAD

  If you don't want to host GOAD, HackTheBox Starting Point Tier 2 + a $20 VIP month for retired AD boxes (Forest, Sauna, Return, Intelligence) is a good shortcut.

  Checkpoint at end of Phase 2: You can go from a given low-priv AD user → Domain Admin on GOAD or a HTB AD box in one sitting without hints.

  Phase 3 — Exam dress rehearsal (Weeks 9-10)

  Full-chain practice runs, no AI, no hints.

  Pick 2-3 AD-focused HTB boxes or the GOAD "beginner path" and do them end-to-end:
  - External enum → initial foothold → internal AD recon → privesc or lateral → Domain Admin
  - Take notes in real time in the exact format you'll use for the exam report
  - Time yourself — can you clear a full AD box in 4-6 hours?

  Write a practice report. This is the single most underestimated part. Download the TCM sample report template (comes with the course). Write a complete report on one of your practice boxes — executive summary, methodology, findings with severity, remediation guidance, appendix. Have a colleague or peer read it and give feedback.

  Checkpoint: You've written at least one full report and feel comfortable with the reporting rhythm.

  Phase 4 — Exam (Weeks 11-12)

  Book the exam through the TCM certifications portal. Exam environment gets provisioned when you start — you pick the start time.

  The day before:
  - Set up your notes/cheatsheets (open-book exam, so your personal notes are allowed)
  - Snapshot a clean Kali VM
  - Confirm your reporting template is ready
  - Sleep.

  Exam logistics:
  - 48 hours to compromise the network (2 external + 4 internal hosts, aim for Domain Admin)
  - 24 hours after that to submit your report
  - You don't need to work the full 48 hours straight — plan sleep. Most people get the external foothold and initial internal access in the first 8-12 hours, sleep, then finish the AD chain the next day.
  - Document as you go. Screenshots of every command and its output, timestamped. It's much faster than reconstructing later.

  If you fail the first attempt: you have one free retake. Debrief what you missed (you'll get feedback), spend 2-4 weeks on the specific gap, resit.

  Supplementary resources (free, use as needed)

  - HackTricks (book.hacktricks.xyz) — searchable encyclopedia of attack techniques. Keep this bookmarked during prep and (if TCM policy allows) during the exam.
  - PayloadsAllTheThings GitHub repo — payloads and bypass references.
  - The Hacker Recipes (www.thehacker.recipes) — excellent AD attack reference, well organized.
  - ired.team — windows/AD attack detailed writeups.

  Add these to your note vault as you go. By exam time you want them indexed and searchable.

  AI use:
Deliberately practice without AI during your prep sessions - PJPT (and any practical pentest exam) is a muscle-memory test. If you let AI write your impacket commands during practice, you won't retain the flags you need when the exam clock is ticking.
A good discipline: use AI freely for understanding concepts ("explain what ASREPRoasting actually does at the Kerberos protocol level") but turn it off for executing attacks ("what command do I run"). The first builds knowledge; the second builds dependency.

  Summary

  - Buy: PJPT bundle, $249
  - Timeline: ~10-12 weeks at 1-2 hrs/day
  - Phases: Foundations (4w) → AD core (4w) → Dress rehearsal (2w) → Exam (2w)
  - Main cost beyond the bundle: maybe a $20 HTB VIP month in Phase 2-3
  - Key habit: practice without AI assistance; write at least one practice report before the exam

