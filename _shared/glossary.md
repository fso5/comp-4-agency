# Glossary

Plain-English definitions for terms a new team member might not know. Aimed at the newest agent (Jordan, 6 months in). Not exhaustive — additions welcome.

When the system uses a term that isn't in here and a new agent gets confused, add it. The glossary is a living artifact.

---

## System terms (specific to this ICM)

**ICM (Interpretable Context Methodology).** The folder-based system architecture we use. Each specialist is a folder. Each folder contains the same four files (identity, rules, examples, handoff). Cases flow between specialists via Handoff Packets.

**Case File.** A folder under `_cases/` representing one piece of work moving through the system. Named `YYYY-MM-DD-<lastname>-<intent>`. Contains `case.md` (the spine) plus artifact files produced by each specialist.

**case.md.** The spine of a Case File. Has a frontmatter header (case_id, client_name, stage, current_owner, etc.) plus a log of every action taken plus appended Handoff Packets.

**Handoff Packet.** A structured block of markdown appended to the bottom of `case.md` whenever a specialist hands off to another. Includes From, To, Why, What I'm passing forward, What I need back, Escalation conditions. The format spec is at `/_shared/handoff_packet_spec.md`.

**Specialist.** One of the five folders (00_orchestrator, 01_lead_qualifier, 02_property_research, 03_client_communication, 04_transaction_coordinator). Each owns one part of the workflow.

**Stage.** The case's current operational state. One of: `new_lead`, `qualified`, `researching`, `showing`, `offer_pending`, `under_contract`, `coordinating`, `closed`, `lost`, `dormant`.

**current_owner.** The specialist (or human) actively working the case. Updated by every specialist when they hand off.

**assigned_agent.** Which human on Diana's team owns the relationship. Independent of which specialist is currently working the case. Doesn't change unless explicitly reassigned.

**Priority.** One of `standard`, `warm`, `urgent`. Set on every case based on time-sensitivity.

**Voice card.** A specialist agent's voice profile, lives in `/_shared/agent_voices.md`. Used by 03_client_communication when drafting.

---

## Real estate terms (Texas / Austin context)

**ABoR.** Austin Board of Realtors. Our local MLS data source.

**Active listing.** Currently for sale.

**Addendum.** A document attached to a contract that modifies or supplements it. Most are TXR-promulgated.

**Amendment.** A change to an executed contract. Requires both parties' agreement and signatures. TREC has a standard amendment form.

**Appraisal contingency.** A clause letting the buyer terminate if the property appraises below contract price. Typical 21 days in TREC contracts.

**Appraisal-defense comps.** A research brief built specifically to challenge a low appraisal. Tighter geographic radius, more rigorous comp selection.

**Backup offer.** A secondary offer accepted by the seller that becomes the active offer if the primary deal falls through.

**Buyer's agent.** The agent representing the buyer.

**CD (Closing Disclosure).** A federal-mandated document delivered to the buyer at least 3 business days before close. Itemizes loan terms and closing costs. Changes to APR / loan product / prepayment penalty reset the 3-day clock.

**Clear to close.** Lender has finished underwriting and authorized the loan to fund. Final step before closing.

**Closing.** The transaction signing event. Buyer signs loan docs, deed, ID; seller signs deed transfer, payoff. Title funds and records.

**CMA (Comparative Market Analysis).** A research brief used to determine list price for a seller. Includes sold comps + active competition + property-specific adjustments.

**Comp / comparable.** A recently-sold or active property similar to the subject property. Used to determine value.

**Contingency.** A clause in a contract that lets the buyer terminate under specific conditions (financing, appraisal, inspection findings, etc.).

**DOM (Days on Market).** Number of days a property has been listed for sale.

**Earnest money.** Buyer's good-faith deposit, paid to title within 3 business days of contract execution. Typically 1% of purchase price. Refunded if buyer terminates during option period; can be forfeited if buyer terminates outside contingencies.

**Escrow.** The neutral third-party arrangement where funds and documents are held. Title is the escrow agent in Texas.

**Executed contract.** A contract signed by both parties (buyer and seller). Triggers the 04_transaction_coordinator pickup.

**Final walkthrough.** Buyer's last inspection of the property, typically morning of closing. Verifies the property hasn't changed since the inspection.

**Financing contingency.** A clause letting the buyer terminate if their loan is denied. Typical 21 days in TREC contracts.

**GreatSchools.** A national school-rating website. Useful for cross-checking AISD official ratings.

**HOA.** Homeowners Association. Charges a monthly fee, has bylaws, sometimes assessments.

**HOA resale package.** Documents required when selling a property in an HOA. Includes resale certificate, bylaws, financials, recent meeting minutes. 10-14 day turnaround typical.

**Hot / warm / cold.** 01_lead_qualifier's scoring tiers. Hot = verified financing + ≤90 day timeline + ≤2 neighborhoods. Warm = qualified but less tight. Cold = no financing signal + vague timeline.

**Inspection objection.** A document the buyer sends to seller after inspection requesting repairs or credits. Usually leads to a negotiation.

**Intent.** One of `buyer`, `seller`, `both`, `unknown`. Part of every case's metadata.

**Listing agent.** The agent representing the seller.

**MLS.** Multiple Listing Service. The agent-only listing database. In Austin, this is ABoR's system. Authoritative for sales data.

**Option fee.** Non-refundable fee paid by buyer to seller for the right to terminate during the option period. Typical $100-500.

**Option period.** Texas-unique. The first 5-10 days after contract execution during which the buyer can terminate for any reason. Buyer must give written notice before option period expires.

**Pre-approval letter.** Lender's letter stating the buyer is approved for a loan up to a certain amount. Verified financing, in qualification terms.

**Possession.** When the buyer can move in. Typically at funding (immediate at close). Sometimes delayed by a seller temp lease.

**Promulgated form.** A TREC-published standard form. Required for most Texas residential transactions (no custom contracts).

**Qualification score.** Hot, warm, cold, or disqualified. Produced by 01_lead_qualifier.

**Recording.** The act of filing the deed with the Travis County Clerk. Typically electronic, same-day.

**Resale certificate.** Part of the HOA resale package. Confirms HOA fees, any outstanding assessments, etc.

**Seller's Disclosure Notice (TXR-1406).** Required form where seller discloses known defects or issues with the property. Buyer reviews.

**Sold comp.** A recently-closed property used as a price reference. The gold standard for valuation work.

**Sold-to-list ratio.** Sold price divided by original list price. >100% means properties sold above list (hot market). <100% means below list (cooler market).

**SOP.** Standard Operating Procedure. Used here to mean "how we do things."

**Survey.** A drawing showing the property boundaries, structures, easements. New survey typically $400-700; or seller provides existing + T-47 affidavit.

**T-47 affidavit.** Seller's sworn statement that no changes have been made to property boundaries since the prior survey. Often used in lieu of ordering a new survey.

**TCAD.** Travis County Appraisal District. Source of authoritative tax records, square footage, lot size, ownership history.

**Termination.** Ending a contract before close. Different conditions apply (option period, financing, appraisal, etc.).

**Title commitment.** The title company's report on the property's title history, identifying any clouds (liens, easements, etc.). Delivered typically 14-21 days after execution.

**Title insurance.** Insurance against title defects (liens, prior ownership disputes, etc.). Required by lender; usually paid at closing.

**TREC.** Texas Real Estate Commission. The state regulatory body for real estate. Promulgates standard forms.

**TRID.** TILA-RESPA Integrated Disclosure. Federal rule requiring CD delivery 3 business days before close.

**TXR.** Texas Realtors (formerly Texas Association of Realtors). Publishes addendums and supplemental forms used alongside TREC promulgated contracts.

**Under contract.** A property currently in a deal. Buyer's offer accepted, contract executed, but not yet closed.

**Walkability / WalkScore.** A 0–100 measure of how walkable an area is. 70+ is "very walkable" in WalkScore's scale.

**Wire fraud.** Scammers intercepting email threads and sending fake wire instructions to redirect closing funds. Constant risk; verify all wire instructions by phone.

---

## Updating this glossary

If you hit a term in the system files that isn't here and you had to ask someone what it meant: that's a glossary gap. Add it. Two-line definition. Plain English.

The standard is: **Jordan should be able to read any system file without needing to ask what a word means.** When that breaks, this file needs work.
