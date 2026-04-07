# Microsoft Entra ID User Management Lab  
## User Administration, Password Reset, and Account Recovery

---

## Overview
In this lab, I worked with user management in Microsoft Entra ID, including account creation, password reset scenarios, account disabling, and troubleshooting login issues.

The goal was to simulate real-world admin tasks and handle an unexpected authentication issue.

---

## Tasks Performed

### 1. User Creation
- Created new user accounts in Microsoft Entra ID  
- Assigned basic (non-admin) roles for testing  

---

### 2. Password Reset

Tested two password reset methods:

- **Self-Service Password Reset (SSPR)**  
  - User resets their own password using verification methods  

- **Admin Reset**  
  - Admin manually resets the password via Entra ID  
  - Option to force password change on next login  

---

### 3. Account Disable / Enable

- Disabled a user account to simulate access restriction  
- Re-enabled the account to restore access  

This is commonly used when:
- a user leaves the organization temporarily  
- suspicious activity is detected  

---

### 4. Login Issue (Unexpected Scenario)

During testing, I encountered a login issue where a user was unable to complete sign-in.

### Issue

- User credentials were correct  
- Initial login step succeeded  
- However, the user was redirected to a security page and received:

> **InternalServerError**

No clear explanation was provided by the system.

---

### Investigation

- Verified Conditional Access policy → no issues  
- Checked user credentials → correct  
- Observed multiple failed login attempts in sign-in logs  
- Identified that the issue was likely related to:
  - MFA / security info registration  
  - authentication flow not completing properly  

---

### Root Cause (Assumed)

The issue was likely caused by:

> **Incomplete or misconfigured authentication methods (MFA / security info)**

This caused the authentication process to fail during the registration step, resulting in a generic internal server error.

---

### Resolution

To resolve the issue, I used **Temporary Access Pass (TAP)**:

- Generated a Temporary Access Pass for the user  
- User signed in using TAP  
- Redirected to:
  - `https://aka.ms/mysecurityinfo`  

- User completed authentication setup  

After this:
- login worked successfully  
- authentication flow completed without errors  

---

### Key Takeaway

- Internal server errors during login may be caused by broken MFA or security registration flows  
- Temporary Access Pass can be used as a recovery method to restore access  
- Admins should always verify authentication methods when troubleshooting login issues  

---

## Skills Practiced

- User management in Microsoft Entra ID  
- Password reset (SSPR and admin reset)  
- Account access control (disable/enable)  
- Authentication troubleshooting  
- MFA / security info configuration  
- Temporary Access Pass usage  
- Sign-in log analysis  
- Real-world issue investigation and resolution  

---

## Summary

This lab demonstrates practical administrative tasks in Microsoft Entra ID, along with troubleshooting a real authentication issue.

It highlights the importance of:
- understanding authentication flows  
- verifying MFA configuration  
- and using recovery tools such as Temporary Access Pass
