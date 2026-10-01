# Lab 4 — Microsoft 365 Administration

## Objective
Practice Microsoft 365 administration and document completed tasks.

## 1. Tenant Domain Verification
Verified the domain in the Microsoft 365 admin center.

- Domain: Rnovsky.onmicrosoft.com
- Default domain: Yes
- Status: Healthy

![Microsoft 365 tenant domain verification](screenshots/01-tenant-domain.png)

## 2. User Onboarding and License Assignment

### License availability
Reviewed the Office 365 E5 license inventory before creating the user.

![License overview](screenshots/02-license-overview.png)

### User account creation
Created the following lab user:

- Display name: Pierrot Augustin
- Username: PAugustin@Rnovsky.onmicrosoft.com
- Automatically generated a temporary password.
- Required a password change at first sign-in.

![User account basics](screenshots/03-user-basics.png)

### License selection
Selected Office 365 E5 for the user and set the usage location to United States.

![License selection](screenshots/04-license-selection.png)

### User role
Kept the default User role with no administration access.

![User role configuration](screenshots/05-user-role.png)

### License verification
Refreshed the Active users list and confirmed that Office 365 E5 appeared for the user.

![User license confirmed](screenshots/06-user-license-confirmed.png)

### First sign-in
Signed in with the lab account, changed the temporary password, and verified access to the account portal.

![Successful user sign-in](screenshots/07-user-sign-in-success.png)

### Result
Completed account creation, license assignment, and first sign-in verification.

### Help Desk Skills Practiced
- New-user onboarding
- License availability checks and assignment
- Standard-user role configuration
- First-sign-in password changes
- Verification and documentation

  ## 3. Password Reset and Access Verification

### Scenario
Simulated a Help Desk request from a user who forgot their password.

### Reset settings
Selected Pierrot Augustin and enabled:
- Automatically create a password.
- Require the user to change their password at the next sign-in.

![Password reset settings](screenshots/08-password-reset-settings.png)

### Reset confirmation
Reset the password and verified the confirmation message:
"Password has been reset."

![Password reset confirmation](screenshots/09-password-reset-confirmed.png)

### Sign-in verification
Signed in using the new temporary password, completed the required password change, and verified access to the user account.

![Sign-in after password reset](screenshots/10-sign-in-after-password-reset.png)

### Result
Successfully reset the user's password and verified sign-in after the password change. No passwords were included in this documentation.

## 4. Microsoft 365 Group Management

### Scenario
Create an IT Support collaboration group, assign an owner and a member, and verify the configuration.

### Group creation
Created a Microsoft 365 group with the following configuration:

| Setting | Value |
|---|---|
| Name | IT Support |
| Email | itsupport@Rnovsky.onmicrosoft.com |
| Owner | Rischeld-Novsky Guillaume |
| Member added | Pierrot Augustin |
| Privacy | Private |
| Admin role assignment | Disabled |
| Microsoft Teams creation | No |

![Group basics](screenshots/11-group-basics.png)
![Owner assignment](screenshots/12-group-owner.png)
![Member assignment](screenshots/13-group-member.png)
![Group settings](screenshots/14-group-settings.png)

### Review and creation
Reviewed the configuration and confirmed successful group creation.

![Group review](screenshots/15-group-review.png)
![Group created](screenshots/16-group-created.png)

### Verification
Opened the group in Active teams and groups and verified its details, owner, and member.

![Group details](screenshots/17-group-details.png)
![Owner verified](screenshots/18-group-owner-verified.png)
![Member verified](screenshots/19-group-member-verified.png)

### Email configuration
Selected the option to send copies of group emails and events to members' inboxes. Kept the group private and external senders disabled.

![Group email settings](screenshots/20-group-email-settings.png)

### Result
Created the IT Support group and verified ownership and membership. Group creation did not assign user licenses; Pierrot's Office 365 E5 license was assigned separately in section 2.

## 5. Outlook Email Delivery Verification

### Scenario
Verify that an email addressed to IT Support reaches a group member's personal inbox, then test a reply to the sender.

### Test message
Sent an email from Rischeld's account to itsupport@Rnovsky.onmicrosoft.com.

Subject: Lab Test - IT Support Group Email

Verified the message in Sent Items.

![Test email sent](screenshots/21-group-test-email-sent.png)

### Member inbox verification
Signed in to Outlook as Pierrot Augustin and confirmed that the test message appeared in his personal Inbox.

![Test email received](screenshots/22-group-test-email-received.png)

### Reply verification
Replied from Pierrot's account and verified receipt in Rischeld's Inbox.

![Reply received](screenshots/23-email-reply-received.png)

### Result
Verified group email delivery to Pierrot's Inbox and successful reply delivery to Rischeld.

### Skills demonstrated
- Microsoft 365 group creation and configuration.
- Owner and member assignment.
- Membership verification.
- Group email delivery configuration.
- Outlook send, receive, and reply testing.
- Documentation of actions and results.


## 6. User Sign-in Blocking and Access Recovery

### Scenario
Temporarily suspend a test user's access, verify that sign-in is denied, then restore access and verify Outlook availability.

**Test user:** Pierrot Augustin  
**Username:** PAugustin@Rnovsky.onmicrosoft.com

### Block sign-in
Opened the user's account in Microsoft 365 admin center, selected **Block sign-in**, enabled **Block this user from signing in**, and saved the change.

The admin center confirmed that the user was blocked.

![User sign-in blocked](screenshots/24-user-sign-in-blocked.png)

### Verify blocked access
Attempted to access Outlook as Pierrot. Microsoft displayed an account-locked message and denied access.

![Blocked sign-in test](screenshots/25-blocked-sign-in-test.png)

### Restore access
Cleared **Block this user from signing in** and saved the change. Reopened the panel to verify that the option was unchecked.

![User sign-in unblocked](screenshots/26-user-sign-in-unblocked.png)

### Verify access recovery
Retested Outlook access as Pierrot and confirmed that his inbox loaded successfully.

![Outlook access after unblock](screenshots/27-sign-in-after-unblock.png)

### Troubleshooting observation
During recovery, Outlook initially returned a **401** error while loading startup data. A later attempt successfully opened the inbox. The exact cause of the temporary error was not confirmed.

### Result
Verified access denial after blocking the user and successful Outlook access after restoring sign-in.

### Skills demonstrated
- User access suspension and restoration
- Sign-in and application access verification
- Authentication error identification
- Documentation of administrative changes and test results

  ## 7. Shared Mailbox Configuration and Testing

### Scenario
Configure a Help Desk shared mailbox so a support user can read requests and reply using the Help Desk identity.

### Mailbox and User
- Shared mailbox: Help Desk
- Email: helpdesk@Rnovsky.onmicrosoft.com
- Authorized user: Pierrot Augustin
- User account: PAugustin@Rnovsky.onmicrosoft.com

### Create the Shared Mailbox
Created the Help Desk mailbox in the Microsoft 365 admin center.

![Shared mailbox created](screenshots/29-shared-mailbox-created.png)

### Add a Member
Added Pierrot Augustin as a shared mailbox member.

![Shared mailbox member](screenshots/30-shared-mailbox-member.png)

### Verify Permissions
Verified that Pierrot had both permissions:
- **Full Access:** open the mailbox and read/manage messages.
- **Send As:** send messages using the Help Desk identity.

![Full Access permission](screenshots/31-shared-mailbox-full-access.png)

![Send As permission](screenshots/32-shared-mailbox-send-as.png)

### Test Mail Delivery and Access
Sent a test support request from Rischeld to the Help Desk address.

![Test email sent](screenshots/33-shared-mailbox-test-sent.png)

Using Pierrot's Outlook session, opened the shared mailbox and verified that the request arrived.

![Test email received](screenshots/34-shared-mailbox-test-received.png)

### Test the Reply
Replied from the shared mailbox. Verified that Rischeld received the response with **Help Desk** displayed as the sender.

![Shared mailbox reply received](screenshots/35-shared-mailbox-reply-received.png)

### Result
Successfully tested shared mailbox access, incoming mail delivery, and a reply using the Help Desk identity.

### Skills Practiced
- Shared mailbox administration
- Mailbox membership and delegated permissions
- Full Access and Send As verification
- Outlook shared mailbox access
- Email delivery and reply testing
