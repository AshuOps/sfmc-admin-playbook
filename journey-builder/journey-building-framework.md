# Journey Builder Framework — Salesforce Marketing Cloud

A practical framework for designing, building, and optimizing customer
journeys in Salesforce Marketing Cloud Journey Builder.

---

## 🎯 Purpose

Journey Builder allows you to automate personalized, multi-step customer
experiences based on real-time behavior and data. This framework covers:
- How to plan and map journeys before building
- Step-by-step setup in SFMC Journey Builder
- Best practices for common journey types
- Testing and activation guidelines

---

## 📐 Journey Planning Framework

### Before You Build — Answer These Questions
- [ ] What is the **goal** of this journey? (Nurture, Onboard, Re-engage, Convert)
- [ ] Who is the **audience**? (Data Extension, Salesforce report, API event)
- [ ] What **triggers** entry into the journey?
- [ ] What **actions** happen at each step?
- [ ] What are the **exit criteria**?
- [ ] How will you **measure success**?

### Journey Map Template
Entry Source → Wait → Email 1 → Decision Split →
[Opened] → Wait 3 Days → Email 2 → Goal Met? → Exit
[Not Opened] → Wait 3 Days → SMS / Re-send → Exit

---

## 🗂 Common Journey Types

### 1. Welcome Journey
**Goal:** Onboard new subscribers and drive first engagement

| Step | Action | Timing |
|---|---|---|
| Entry | New subscriber added to Data Extension | Immediate |
| Step 1 | Send welcome email | Immediately |
| Step 2 | Wait | 3 days |
| Step 3 | Decision split — opened welcome email? | — |
| Step 4a | Yes — send product/feature highlight email | Immediately |
| Step 4b | No — send follow-up with different subject line | Immediately |
| Step 5 | Wait | 7 days |
| Step 6 | Send getting started guide | — |
| Exit | After final email sent | — |

---

### 2. Lead Nurture Journey
**Goal:** Move MQLs toward sales readiness

| Step | Action | Timing |
|---|---|---|
| Entry | Lead reaches MQL score threshold in Salesforce | Immediate |
| Step 1 | Send educational content email | Immediately |
| Step 2 | Wait | 5 days |
| Step 3 | Decision split — clicked any link? | — |
| Step 4a | Yes — send case study / social proof email | Immediately |
| Step 4b | No — send re-engagement email | Immediately |
| Step 5 | Wait | 5 days |
| Step 6 | Send demo / consultation offer | — |
| Step 7 | Update Salesforce lead score via Sales Cloud activity | — |
| Exit | Lead converts to SQL or completes journey | — |

---

### 3. Re-engagement Journey
**Goal:** Win back inactive subscribers

| Step | Action | Timing |
|---|---|---|
| Entry | No open or click in 90 days | Immediate |
| Step 1 | Send "We miss you" email | Immediately |
| Step 2 | Wait | 7 days |
| Step 3 | Decision split — opened or clicked? | — |
| Step 4a | Yes — move to active segment, exit journey | Immediately |
| Step 4b | No — send "Last chance" email | Immediately |
| Step 5 | Wait | 7 days |
| Step 6 | Decision split — opened or clicked? | — |
| Step 7a | Yes — move to active segment, exit journey | Immediately |
| Step 7b | No — move to suppression list, exit journey | Immediately |

---

### 4. Post Purchase Journey
**Goal:** Increase retention, upsell, and referrals

| Step | Action | Timing |
|---|---|---|
| Entry | Purchase recorded in Salesforce / Data Extension | Immediate |
| Step 1 | Send order confirmation / thank you email | Immediately |
| Step 2 | Wait | 3 days |
| Step 3 | Send onboarding / getting started email | — |
| Step 4 | Wait | 7 days |
| Step 5 | Send tips and best practices email | — |
| Step 6 | Wait | 14 days |
| Step 7 | Send review / referral request email | — |
| Exit | After referral email sent | — |

---

## ⚙️ Step-by-Step Journey Builder Setup

### Step 1 — Create a New Journey
1. Go to **Journey Builder → Journey Builder**
2. Click **Create New Journey**
3. Select **Multi-Step Journey**
4. Name your journey using convention:

   [Year]-[JourneyType]-[Audience]
e.g. 2025-WelcomeSeries-NewSubscribers

### Step 2 — Configure Entry Source
1. Drag **Entry Source** onto canvas
2. Select entry type:
   - **Data Extension** — for batch or scheduled entry
   - **Salesforce Data** — for CRM-triggered entry
   - **API Event** — for real-time behavioral triggers
   - **Audience** — for one-time sends
3. Select your Data Extension or configure API event
4. Set **Entry Schedule:**
   - Run Once
   - Run Daily / Weekly
   - Run on Event (real-time)
5. Configure **Re-entry settings:**
   - No re-entry (recommended for most journeys)
   - Re-entry anytime (for transactional journeys)
   - Re-entry only after exiting

### Step 3 — Add Activities
Drag activities onto the canvas:

| Activity | Use Case |
|---|---|
| Send Email | Deliver email from Content Builder |
| Send SMS | Deliver SMS via Mobile Studio |
| Wait | Pause before next step (time or event based) |
| Decision Split | Branch based on engagement or data |
| Engagement Split | Branch based on email open / click |
| Random Split | A/B test different journey paths |
| Update Contact | Update Data Extension field |
| Salesforce Activity | Create task, update record in Salesforce CRM |
| Ad Audience | Add/remove from Advertising Studio audience |

### Step 4 — Configure Decision Splits
1. Drag **Decision Split** or **Engagement Split** onto canvas
2. For Engagement Split:
   - Select the email activity to evaluate
   - Set split criteria: Opened, Clicked, Not Opened
   - Set evaluation period (recommend 3–7 days)
3. For Decision Split:
   - Select Data Extension field to evaluate
   - Set conditions (e.g. Lead Score > 50)

### Step 5 — Set Journey Goal
1. Click **Goal** at the top of the canvas
2. Define goal criteria:
   - Data Extension field update
   - Salesforce record update
   - Email engagement
3. Set goal percentage target
4. Enable **"Exit when goal is met"** to avoid over-messaging

### Step 6 — Configure Exit Criteria
1. Click **Exit Criteria** at top of canvas
2. Set conditions for early exit:
   - Contact unsubscribes
   - Contact converts / purchases
   - Contact reaches specific engagement threshold

---

## ✅ Journey Testing Checklist

- [ ] Journey mapped and reviewed before building
- [ ] Entry source Data Extension has test records
- [ ] All email activities linked to correct Content Builder emails
- [ ] Wait times set correctly for each step
- [ ] Decision split evaluation periods confirmed
- [ ] Goal criteria defined and tested
- [ ] Exit criteria configured
- [ ] Test contacts added to entry Data Extension
- [ ] Journey validated — no errors showing in canvas
- [ ] Test mode activated and test contacts moved through journey
- [ ] All emails render correctly at each step
- [ ] Salesforce activity updates tested (if applicable)

---

## 📅 Journey Activation Steps

1. Click **Activate** in top right corner
2. Review summary — confirm audience count and settings
3. Click **Activate Journey**
4. Monitor **Journey Analytics** dashboard for first 24–48 hours:
   - Total contacts in journey
   - Emails sent and delivery rate
   - Drop-off points between steps
   - Goal completion rate

---

## 🚫 Common Journey Builder Mistakes

| Mistake | Impact | Fix |
|---|---|---|
| No exit criteria set | Contacts loop or over-receive | Always set exit criteria |
| Wait times too short | Feels spammy to contacts | Minimum 3 days between emails |
| No goal defined | Can't measure journey success | Always set a measurable goal |
| Re-entry enabled accidentally | Contacts enter journey multiple times | Default to no re-entry |
| Not testing before activation | Live errors reach real contacts | Always run test mode first |
| Too many steps | High drop-off rate | Keep journeys under 6–8 steps |

---

## 📝 Notes

> Always clone an existing journey rather than editing a live one.
> Pause the journey before making structural changes.
> Built from hands-on Salesforce Marketing Cloud Journey Builder
> experience managing automated customer lifecycle campaigns.
> 
