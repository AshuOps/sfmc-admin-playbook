# Email Campaign Setup Guide — Salesforce Marketing Cloud

A step-by-step guide for building, testing, and sending email campaigns
in Salesforce Marketing Cloud Email Studio.

---

## 🎯 Purpose

This guide covers the end-to-end process for setting up a professional,
deliverable, and trackable email campaign in SFMC — from audience
selection to post-send reporting.

---

## 📐 Pre-Send Checklist

Before building any email campaign, confirm:

- [ ] Campaign goal is defined (lead gen, nurture, promotional, transactional)
- [ ] Target audience / Data Extension is ready and clean
- [ ] Suppression list is up to date
- [ ] UTM parameters are planned for all links
- [ ] Sender profile and reply mail management is configured
- [ ] Send classification is set correctly (commercial vs transactional)

---

## ⚙️ Step 1 — Create the Email in Content Builder

1. Go to **Email Studio → Content Builder**
2. Click **Create → Email Message**
3. Choose a template or start from scratch
4. Fill in:
   - **Email Name:** Use naming convention `[Year]-[Month]-[Campaign]-[Audience]`
   - **Subject Line:** Keep under 40 characters for mobile optimization
   - **Preheader Text:** 85–100 characters — supports and extends subject line
5. Build email content using drag-and-drop or HTML editor
6. Add **dynamic content blocks** for personalization where relevant
7. Add **UTM parameters** to every link before saving

### Email Naming Convention
2025-Q2-ProductLaunch-ExistingCustomers
2025-Q2-ProductLaunch-ProspectList
2025-Q2-Newsletter-AllSubscribers

---

## ⚙️ Step 2 — Configure Sender Profile

1. Go to **Email Studio → Admin → Sender Profiles**
2. Select or create a sender profile with:
   - **From Name:** Company name or recognizable sender name
   - **From Email:** Must be authenticated domain (SPF + DKIM configured)
   - **Reply Email:** Active monitored inbox

### Authentication Requirements
| Setting | Requirement |
|---|---|
| SPF Record | Must include SFMC sending IPs |
| DKIM | Must be configured via SAP or custom domain |
| DMARC | Recommended — set to p=quarantine minimum |
| Reply Mail Management | Configure bounce handling rules |

---

## ⚙️ Step 3 — Build or Select Your Audience

### Option A — Data Extension Send
1. Go to **Email Studio → Subscribers → Data Extensions**
2. Select target Data Extension
3. Verify field mapping — ensure Email Address field is mapped correctly
4. Check record count — confirm expected audience size

### Option B — Filtered Data Extension
1. Create a Filtered Data Extension from master list
2. Apply filters:
   - Engagement tier (Highly Engaged, Moderately Engaged)
   - Lifecycle stage
   - Geography or industry segment
3. Refresh filter before send to ensure up-to-date audience

### Suppression List Setup
- Always apply **Global Unsubscribe** suppression
- Apply campaign-specific suppression lists where relevant
- Exclude recent purchasers or active opportunities if promotional send

---

## ⚙️ Step 4 — Configure the Send

1. Go to **Email Studio → Email → Send**
2. Select your email from Content Builder
3. Configure send details:
   - **Send Classification:** Commercial or Transactional
   - **Sender Profile:** Select authenticated profile
   - **Delivery Profile:** Select appropriate IP pool
4. Select audience — Data Extension or list
5. Apply suppression lists
6. Set **send date and time:**
   - B2B optimal: Tuesday–Thursday, 9–11am recipient local time
   - B2C optimal: Tuesday–Thursday, 6–8pm recipient local time

---

## ⚙️ Step 5 — Test Before Sending

### Inbox Testing Checklist
- [ ] Send test email to internal test list
- [ ] Check rendering on desktop (Outlook, Gmail, Apple Mail)
- [ ] Check rendering on mobile (iOS, Android)
- [ ] Verify all links work and UTM parameters are correct
- [ ] Verify unsubscribe link works
- [ ] Check personalization tokens render correctly
- [ ] Verify dynamic content blocks display correctly
- [ ] Run spam score check (aim for score below 3)

### SFMC Test Send
1. Click **Test Send** before scheduling
2. Send to a dedicated internal test Data Extension
3. Review rendering in actual email clients — not just SFMC preview

---

## ⚙️ Step 6 — Schedule or Send

### Scheduled Send
1. Select **Schedule** option
2. Set date, time, and timezone
3. Confirm audience count one final time
4. Click **Schedule Send**

### Triggered Send
For automated or event-based sends:
1. Configure **Triggered Send Definition** in Email Studio
2. Set trigger criteria (form submission, API call, journey entry)
3. Test trigger with a test record before activating

---

## 📊 Step 7 — Post Send Reporting

### Metrics to Review Within 24 Hours
| Metric | Where to Find | Healthy Benchmark |
|---|---|---|
| Delivery Rate | Email Studio Tracking | > 98% |
| Open Rate | Email Studio Tracking | > 20% |
| Click Through Rate | Email Studio Tracking | > 2% |
| Bounce Rate | Email Studio Tracking | < 2% |
| Unsubscribe Rate | Email Studio Tracking | < 0.2% |
| Spam Complaints | Email Studio Tracking | < 0.08% |

### Where to Find Reports
1. **Email Studio → Tracking → Send Reports**
2. Select your send from the list
3. Review Summary, Bounce, Click, and Unsubscribe tabs
4. Export CSV for archiving and deeper analysis

---

## 🚫 Common Mistakes to Avoid

| Mistake | Impact | Fix |
|---|---|---|
| Not testing on mobile | Poor rendering for 60%+ of opens | Always test on iOS and Android |
| Missing UTM parameters | Lost attribution data | Build UTMs into template before send |
| Wrong send classification | Deliverability issues | Always verify commercial vs transactional |
| Not suppressing unsubscribes | CAN-SPAM / GDPR violation | Always apply Global Unsubscribe list |
| Sending to full list without segmentation | High unsubscribe rate | Always segment by engagement tier |
| No preheader text | Lower open rates | Always add preheader to support subject line |

---

## 📝 Notes

> Always archive send reports monthly — SFMC only retains tracking
> data for 6 months by default.
> Built from hands-on Salesforce Marketing Cloud Email Studio experience
> managing multi-channel marketing campaigns.
