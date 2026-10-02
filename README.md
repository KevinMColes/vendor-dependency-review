# Vendor Dependency Review

**A leadership review for the vendors your business cannot run without.**

By Kevin M. Coles · Version 1.2 · October 2026 · Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

---

## Why this exists

Most companies scrutinize a vendor once, before the contract is signed. Security questionnaires get completed, documents get exchanged, and someone approves the risk. After that, the vendor is renewed, not reviewed.

The vendor you approved two years ago is not necessarily the vendor you depend on today. Their infrastructure changes, their subcontractors change, their ownership changes, and your reliance on them quietly grows. Vendor approval is a point in time decision. Vendor risk is not.

You can outsource the work. You cannot outsource ownership of the decision. When a critical vendor fails, your customers, regulators, insurers, and board will ask what *you* knew and what *you* decided. They will not accept "the vendor handled it" as an answer.

This review gives leadership a structured way to answer those questions before anyone asks them. It is deliberately short on security jargon and long on decisions, because the gaps that hurt companies are rarely technical. They are decisions nobody owned.

## What this is, and what it is not

This is a **leadership** review. It is designed to be completed by the people accountable for the business, with input from whoever manages the vendor day to day.

It is **not** a security questionnaire. Detailed control assessments (SOC 2 reports, penetration test results, security questionnaires) still matter, and your security team or provider should keep doing them. This review sits above that work and asks whether the business has made a conscious decision about each dependency.

It is **not** legal advice. Where it asks what a contract says, have counsel confirm the answer before you rely on it.

---

## Part 1: Decide which vendors deserve a review

Most companies have dozens or hundreds of vendors. Only a handful can seriously hurt the business. Review those, and review them properly.

A vendor is **critical** if any one of these is true:

| Test | Critical if... |
|---|---|
| **Operational** | Losing the vendor for one business day would stop or seriously degrade revenue, operations, or customer service. |
| **Data** | The vendor stores or processes customer, employee, financial, health, or other regulated data at meaningful volume. |
| **Access** | The vendor has administrative or broad access into your systems (for example, a managed service provider or a security tool). |
| **Substitution** | Replacing the vendor would take longer than six months. |

In our experience with companies of 50 to 500 employees, the list usually runs five to twelve vendors. It almost always includes your email and identity platform, your core line of business system, your payments or finance platform, your managed service provider if you have one, your primary cloud platform, and, increasingly, the AI tools your staff use every day.

If your list has more than fifteen vendors, the bar is set too low. If it has fewer than five, someone is missing something.

---

## Part 2: The concentration map

Complete this once, across all critical vendors, before reviewing any individual vendor.

Individual vendor reviews miss the most dangerous pattern: one vendor quietly running several functions you would need at the same moment. When that vendor has a bad day, the business does not lose one capability. It loses several, including the one it would use to coordinate the response.

Mark each row with the vendor that provides that capability and, if you know it, the cloud or hosting provider that vendor runs on.

| Capability | Vendor | Runs on (cloud or hosting provider) | Same vendor or provider as another row? |
|---|---|---|---|
| Email | | | |
| Identity and sign in (including single sign on) | | | |
| File storage and sharing | | | |
| Internal chat and meetings | | | |
| Endpoint security | | | |
| Backup and recovery | | | |
| Core line of business system | | | |
| Customer communication (phone, SMS, support) | | | |
| Payments and finance | | | |
| AI tools used in daily work | | | |
| Managed IT or security provider | | | |

Then answer four questions:

1. **If any single vendor on this list went down for a full business day, which rows go dark together?**
2. **Where would leadership coordinate during that outage?** If the answer is a tool on the same vendor that just failed, you have no coordination channel.
3. **Which vendor controls sign in?** If you use single sign on, your identity provider is a hidden single point of failure for every system connected to it. It deserves the first review.
4. **Which different vendors share the same underlying provider?** Five vendors running on one cloud region may be one dependency, not five.

> **Why this matters.** In August 2026, a major Microsoft 365 authentication incident disrupted Exchange Online and other services at the same time. For companies standardized on one ecosystem, email, files, identity, and Teams can all sit behind the same point of failure, including the channel employees are told to use when something goes wrong. Consolidating around a strategic vendor can be a sound decision. Calling another service from the same vendor your contingency plan is not.

---

## Part 3: The individual vendor review

Complete one review per critical vendor. Plan on 60 to 90 minutes with the people who actually know the answers, and have these in the room:

- The master agreement, statement of work, and any data processing terms
- The most recent SOC 2 report or equivalent assurance from the vendor
- Your cyber insurance policy
- The latest invoice and the renewal date

Three rules:

1. **Write a name, not a department,** wherever the review asks who. "IT" is not an owner.
2. **"We don't know" is a valid answer.** It is also a finding. Record it rather than guessing.
3. **Every review ends in a decision** (Part 5). A review that does not end in a decision is just paperwork.

Questions marked **RF** are red flag questions. Part 4 explains what the answers mean.

### Section 1: Dependency

| Question | Answer |
|---|---|
| Which business processes depend on this vendor? | |
| What stops if this vendor is unavailable for 90 minutes? For one day? For one week? | |
| How long could we operate before customers noticed? | |
| **RF** Is our backup or contingency plan provided by this same vendor? | |
| **RF** Has anyone actually practiced operating without this vendor? | |
| **RF** Can the vendor push updates or configuration changes into our environment without our approval, and can we stage or delay them? | |
| What has the vendor's actual outage and incident record been over the last 24 months? | |
| Is the vendor financially stable, and does the product depend on a small number of key people? | |

> **Why this matters.** On September 3, 2026, several major AI assistants experienced overlapping outages. Paying for more than one tool did not create resilience for companies that had never decided which work could stop, for how long, and what the fallback was. Resilience is not the number of logos in the stack. It is whether failure was considered before it arrived.

### Section 2: Ownership

| Question | Answer |
|---|---|
| Who approved this vendor originally, and when? | |
| What was the basis for that decision? Is it documented anywhere? | |
| **RF** Who owns the relationship today, by name? | |
| **RF** When was the decision to use this vendor last reviewed by leadership? | |
| **RF** Who has the authority to decide that we should leave? | |

### Section 3: Data and access

| Question | Answer |
|---|---|
| What data does this vendor store or process for us? | |
| Does that include customer, employee, financial, health, or other regulated data? | |
| What access does the vendor have into our systems, and at what level? | |
| **RF** Could we remove all of the vendor's access within one business day if we had to? | |
| **RF** Do we know which of *their* subcontractors can reach our data? | |
| Where is our data physically and legally located? | |
| **RF** Do we, not the vendor, hold the top level administrator accounts, our domain registration, DNS, and ownership of our cloud tenants? | |

**For AI vendors, and any vendor that has added AI features:**

| Question | Answer |
|---|---|
| **RF** Does the vendor use our data, prompts, or outputs to train or improve its models? | |
| **RF** If we have opted out, is that commitment in the contract, or only in a settings page the vendor can change? | |
| How long does the vendor retain our prompts and outputs? | |
| Which of our people are using this tool, with what data, and who approved that? | |

### Section 4: What the contract actually says

The contract matters most on the day the vendor fails. Read it with that day in mind.

| Question | Answer |
|---|---|
| **RF** What is the vendor's limitation of liability, and how does it compare to our realistic loss from one serious failure? | |
| How quickly must the vendor notify us of a security incident affecting our data? | |
| Who pays for incident response, notification, and remediation if the incident starts on their side? | |
| Are service level remedies limited to service credits? | |
| **RF** What happens to our data when the contract ends? In what format do we get it back, and how fast? | |
| Do we have audit or assessment rights? Have we ever used them? | |
| What changes if the vendor is acquired? | |
| What is the notice period and cost to terminate? | |
| What do we spend with this vendor each year, and when does the contract renew? | |
| **RF** What is the auto renewal notice deadline, and whose calendar is it on? | |

> **Why this matters.** In July 2024, a faulty CrowdStrike update crashed roughly 8.5 million Windows systems. Delta Air Lines canceled about 7,000 flights and put its losses at about $500 million. CrowdStrike has said its contractual liability was capped in the single digit millions, so Delta's path to recovery ran through a lawsuit arguing the cap should not apply. Other major airlines hit by the same update recovered within a day or two; Delta took most of a week. The vendor caused the failure. The contract decided who would pay for it, and Delta's own recovery capability largely decided how long it lasted. Both were set long before anything broke.

### Section 5: When they fail

| Question | Answer |
|---|---|
| How would we find out the vendor has failed: from them, from our monitoring, or from our customers? | |
| Who on our side is responsible for the first 24 hours? | |
| What is the manual or alternate process while the vendor is down? | |
| Who decides what we tell customers, and when? | |
| Do we have notification obligations to regulators, partners, or lenders? | |
| **RF** Does our cyber insurance cover incidents that originate at a vendor, and under what conditions? | |

> **Why this matters.** When a widely used credit union technology vendor was taken offline by a cyberattack in 2026, many of its credit union customers reported that they could not yet tell their own members what data had been exposed. Those credit unions had outsourced the infrastructure. They had not outsourced the fact that members and regulators would hold *them* accountable.

### Section 6: Exit

| Question | Answer |
|---|---|
| **RF** If we had to replace this vendor, how long would it realistically take? | |
| What would it cost, including migration, retraining, and running both systems in parallel? | |
| Is our data portable in a usable format, or locked into the vendor's structure? | |
| Is there a credible alternative vendor today? | |

---

## Part 4: Reading the answers

The questions only matter if the answers change a decision. This is where most vendor reviews stop short.

| Red flag answer | What it means | Pushes the decision toward |
|---|---|---|
| **No named owner,** or "IT owns it" | The decision is running on inertia. Nobody is accountable for whether it is still right. | Assign an owner first. No other decision is valid until someone owns this one. |
| **Not reviewed by leadership in over two years** | You are relying on a decision made about a different vendor, in a different business. | Re-decide. The original rationale no longer counts as evidence. |
| **Nobody knows who can decide to leave** | The vendor relationship cannot be ended deliberately, only by crisis. | Name the decision authority alongside the owner. |
| **The contingency plan uses the same vendor** | You do not have a contingency plan. You have a second product behind the same point of failure. | Reduce dependency. |
| **Vendor can push changes you cannot stage or delay** | Their release process is now part of your change management, and you do not control it. | Accept with conditions: confirm staged rollout options, or reduce dependency. |
| **Nobody has practiced operating without the vendor** | The fallback exists on paper only. The first real test will be the real incident. | Accept with conditions: run a tabletop exercise within 90 days. |
| **Vendor access cannot be removed within one day** | If the vendor is compromised, you cannot cut them off fast enough to matter. | Accept with conditions: document and test an access removal procedure. |
| **The vendor holds the keys** (admin accounts, domain, DNS, tenant ownership) | If the relationship ends badly, or the vendor is compromised, they control your environment. | Accept with conditions: transfer ownership and set up emergency access you control within 30 days. |
| **Unknown subcontractors** | Your data's real exposure includes companies you have never evaluated. | Accept with conditions: request the subprocessor list and notification commitments. |
| **AI vendor can train on your data, or the opt out is not contractual** | Sensitive information may leave your control in ways you cannot reverse. | Accept with conditions (contractual opt out, data restrictions) or exit for sensitive use. |
| **Liability cap is a fraction of your realistic loss** | The contract is not your protection. You are self insuring the gap, whether you decided to or not. | Accept with conditions: determine with your broker whether any of the gap is insurable, and renegotiate at renewal. |
| **No clear data return at exit** | You have handed the vendor your leverage. | Accept with conditions: fix the exit terms before the next renewal. |
| **Insurance does not cover vendor originated incidents** | The risk you thought was transferred is still entirely yours. | Have the broker confirm in writing whether vendor originated incidents are covered, and at what sublimit, before the earlier of the policy or vendor renewal. |
| **Nobody knows the auto renewal deadline** | You will renew by default, and every condition that depends on renewal leverage disappears. | Calendar the deadline under the owner's name now. |
| **Replacement would take over twelve months** | You are locked in. Your negotiating position weakens every year. | Plan exit options before renewal, even if you intend to stay. |

**Two patterns deserve escalation to the CEO or board, regardless of anything else:**

1. **High dependency plus hard exit.** The business stops within a day without this vendor (Section 1), *and* replacing it would take more than a year (Section 6). This is the most consequential vendor relationship you have, and it should never be on autopilot.
2. **Concentration plus no coordination channel.** The concentration map shows several critical functions on one vendor, *and* leadership's crisis communication runs through that same vendor.

**"Accept as is" is only a valid decision** if the review found no red flags, or if every red flag has been explicitly accepted, in writing, by someone with authority proportionate to the exposure. Either escalation pattern requires acceptance by the CEO or board. Accepting a risk is a legitimate decision. Not noticing one is not.

---

## Part 5: The decision

Choose one outcome and record it.

- [ ] **Accept as is.** The dependency is understood and appropriate, and any red flags are explicitly accepted by someone with authority proportionate to the exposure.
- [ ] **Accept with conditions.** Keep the vendor, but close specific gaps by specific dates.
- [ ] **Reduce dependency.** Keep the vendor, but deliberately limit how much of the business relies on it.
- [ ] **Plan an exit.** The dependency is no longer acceptable.

A condition not closed by its date does not roll forward. It becomes a leadership escalation.

| | |
|---|---|
| **Vendor** | |
| **Critical because** (Part 1 tests met) | |
| **Red flags found** | |
| **Decision** | |
| **Rationale** | |
| **Gaps to close, with owners and dates** | |
| **Risks explicitly accepted** | |
| **Decision owner (name)** | |
| **Date** | |
| **Next review date** | |

Review early, without waiting for the date, if the vendor is acquired, has a material outage or incident, adds AI features that touch your data, changes key subcontractors, or takes on a larger share of the business.

---

## Part 6: The one page leadership summary

Once each critical vendor has been reviewed, roll the results into a single page for the CEO, leadership team, or board. This is the page that turns a stack of reviews into governance.

| Vendor | Critical because | Red flags | Decision | Owner | Next review |
|---|---|---|---|---|---|
| | | | | | |
| | | | | | |
| | | | | | |

Below the table, add three lines:

1. **Concentration:** which vendor, if it failed, would take down the most at once.
2. **Escalations:** any vendor that triggered one of the two escalation patterns in Part 4.
3. **Open conditions:** the gaps still being closed, with dates.

If leadership can read this page in five minutes and know where the business is exposed, the review has done its job.

---

## A worked example

*A fictional 140 person regional distribution company reviews its dispatch and routing software vendor.*

| | |
|---|---|
| **Critical because** | Operational (drivers cannot be dispatched without it) and Substitution (an estimated 15 to 18 months to replace). |
| **Dependency** | Dispatch stops within an hour. Customers notice the same day. The documented fallback is paper route sheets, which nobody has used in three years. Updates are pushed on the vendor's schedule with no staging. |
| **Ownership** | Approved in 2021 by the former operations director, who has since left. Nobody currently owns the relationship. Renewal is handled by accounts payable. |
| **Data and access** | Customer addresses, delivery records, driver location data. The vendor has a permanent remote support connection and shared credentials nobody has inventoried; removing them would take days. Subcontractors are unknown. The company does hold its own admin accounts. |
| **Contract** | Annual spend about $60,000, auto renewing each March with a 90 day notice window nobody had calendared. Liability is capped at fees paid in the prior 12 months, roughly $60,000. One day of lost dispatch costs the company more than that. Data is returned at exit "in a format determined by the vendor." |
| **When they fail** | The company would most likely learn about an outage from drivers. Nobody knows whether the cyber insurance policy covers vendor originated incidents. |
| **Exit** | No credible alternative has been evaluated. |
| **Red flags** | No named owner. Not reviewed by leadership since 2021. Fallback never practiced. Vendor pushes updates with no staging. Remote access cannot be quickly removed. Unknown subcontractors. Liability cap far below realistic loss. No clear data return. Insurance coverage unknown. Renewal deadline not calendared. Replacement over twelve months. **Escalation pattern 1:** high dependency plus hard exit. |
| **Decision** | **Accept with conditions,** escalated to the CEO. |
| **Conditions** | COO named as owner and decision authority (immediately). Renewal notice deadline calendared (immediately). Shared vendor credentials inventoried and rotated, and remote access converted to on request only (30 days). Broker confirms vendor incident coverage (30 days). Staged update options confirmed with the vendor (30 days). Tabletop exercise using the paper fallback (60 days). One alternative vendor evaluated, and exit terms and subprocessor disclosure negotiated, before the December notice deadline. |
| **Risks explicitly accepted** | The liability gap, pending the broker's answer, accepted by the CEO until renewal. |
| **Next review** | After renewal, then annually. |

Notice that the decision is not "replace the vendor." The software works. The problem was that nobody had made a conscious decision about depending on it.

---

## If you only have ten minutes

Answer these four questions for each critical vendor:

1. What stops if this vendor is down for a day?
2. Who, by name, owns the decision to keep using them?
3. What does the contract actually protect us from, and is that enough?
4. Does our backup plan depend on the same vendor?

If any answer is "we don't know," that is where to start.

---

*Kevin M. Coles is the founder of [Coles Technical Group](https://colestechnicalgroup.com), a technology governance and fractional CIO/CTO consulting firm based in Phoenix, Arizona. He writes weekly at [substack.com/@kevinmcoles](https://substack.com/@kevinmcoles).*

*You are free to share and adapt this review for any purpose, including commercial use, provided you give appropriate credit to Kevin M. Coles and link to the license. Suggested credit: "Vendor Dependency Review by Kevin M. Coles, licensed under CC BY 4.0."*
