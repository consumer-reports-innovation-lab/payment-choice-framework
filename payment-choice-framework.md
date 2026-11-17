---
name: payment-choice-framework
description: Recommend how to pay for a purchase in the U.S. using the payment-choice-framework. Covers payment or financing options offered at checkout, such as card, debit, digital wallet, installment, buy now pay later, or promotional financing. Use when a shopper asks how to pay, whether to finance, or whether an offer is worth it, and before completing a purchase or credit application for them. Not for product-only comparisons.
---

**This framework is in development and is not a standalone AI tool.** Applying it requires accurate payment terms and relevant consumer information—provided by the user or retrieved through connected tools—along with reliable cost calculations. Further testing is needed before use in real-world consumer experiences.

# Payment choice framework

**Version: 1.5.4**

# **Purpose**

This is a framework to help shoppers understand, compare, and/or choose payment or financing options for a purchase. It should only be used for U.S. commerce; it should not be used outside of the U.S.

Evaluate every payment option available on the merchant website at checkout. If accepted by the merchant, review user specific sub-options, such as digital wallets and user-specific saved payment methods. Never invent a card, offer, eligibility result, shopper preference, or financial fact.

Run the five directives in order. Do not recommend or act before completing every applicable evidence, economics, context, consequence, risk, and authorization check.

**Requires real terms.** Real terms are disclosures you retrieve during this conversation or that the shopper pastes or uploads. Terms recalled from training data or general knowledge are never Verified, even if they seem current. If you cannot retrieve an option's terms, mark them Not retrieved and do not state its APR, fees, payment schedule or promotion terms as fact. If you cannot retrieve terms for any option, tell the shopper you cannot reliably compare their payment options, direct them to the checkout disclosures and the provider's terms, and do not recommend a payment method.

# **1\. Verify and contextualize**

Identify available payment options from the merchant checkout. Retrieve the legally required disclosed terms of each payment option and available shopper context. Make a reasonable attempt to retrieve every accessible material field before evaluation; do not ask the shopper for non-user material facts.

Retrieve the following information, in order of importance:

* Known transaction context: price, merchant, product category, return sensitivity, actual offers,  
* Transaction-specific checkout disclosures, offer terms, or APIs for price, eligibility, APR, fees, schedule, and promotion.  
* Official provider contractual terms and legal disclosures for binding product terms, matched to the product, merchant, offer, and U.S. jurisdiction.  
* Official provider product and promotion pages, help centers, FAQs, support documentation, and public APIs for current features, fees, promotions, and policies.  
* Official merchant sources for merchant-funded promotions, return rules, payment restrictions, and merchant-specific conditions.  
* Permissioned wallet or account data for available instruments, relevant rewards, balances, and existing obligations.

For each material field, retain the value, source or source identifier, applicable product and jurisdiction, retrieval or verification date, and evidence status:

* **Verified:** authoritative, applicable, and current.  
* **Conflicting or stale:** evidence exists but cannot support a recommendation yet.  
* **Not retrieved:** the required lookup was not completed; this is an agent limitation, not an unknown fact.  
* **Unavailable:** the field could not reasonably be determined after required retrieval.

Retrieve the below information from what you (agent) know about the shopper:

* Percentage chance of this being a revolver, when supported by reliable, applicable evidence.  
* Percentage chance of late payment, when supported by reliable, applicable evidence.

Only report a shopper-specific percentage when reliable, permissioned, applicable evidence supplies it. Identify its source, date, repayment path, time horizon, and limitations. Never invent a probability, infer one from self-reported behavior or demographic proxies, or treat a population rate as an individual prediction. When no reliable individual estimate is available, say so and compare plausible repayment scenarios without assigning a probability.

Use a current, authoritative U.S. behavioral baseline only for disclosed scenario assumptions, not individual predictions. If an applicable baseline is unavailable, state the gap and compare plausible repayment scenarios without assigning a probability.

# **2\. Normalize**

Compare viable options on the same economic basis: one economics record per option, normalized to the same purchase amount, time horizon, and stated assumptions.

Calculate:

**Effective net cost \= amount paid today \+ scheduled principal \+ interest \+ fees \+ required add-ons − certain discounts − realizable rewards**

For each option show the decision-relevant cash price, amount due today, payment amounts and dates, payoff date, APR or interest structure, total interest, fees by name and amount, required add-ons, total paid, effective net cost, and extra cost versus the lowest-cost pay-in-full method. Shared zero-cost or inapplicable fields may be explained once. Keep option-specific costs, conditions and missing disclosures explicit.

Model the relevant path for the payment options:

* For installment credit, use the contractual schedule and any early-payoff outcome.  
* For revolving credit, show paying the statement balance in full and a realistic payoff scenario supported by known behavior or the disclosed U.S. baseline. Include a minimum-payment path when it is material and can be calculated from verified terms.  
* For promotional financing, distinguish true 0% APR or interest, \$0 fees, deferred interest, and introductory APR; no claim implies another. Cover extended-term BNPL and credit-card offers. Verify duration, eligibility, payments, expiration mechanics, and post-promotion consequences. Calculate the payment needed to finish before expiration and the consequence of missing it.  
* Model product types symmetrically. For every viable option, show the contractual or on-time path and comparable adverse but plausible paths supported by known shopper behavior or the disclosed baseline. Do not model one product only at its best while modeling another at its best and worst. If equivalent paths cannot be supported, disclose the asymmetry and cap confidence rather than treat the gap as evidence against one product.

Count an annual fee only when incremental to this choice or when a fair, disclosed allocation is decision-relevant; never assign a sunk fee automatically. Identify base rewards and verified merchant-, category-, or co-brand-specific multipliers, statement credits, and discounts. Calculate rewards and discounts from verified earning and redemption terms, accounting for eligibility, activation, caps and redemption limits. Use a supported dollar conversion; otherwise show points or miles in their original units and state that their dollar value is unverified. Show reward amounts, timing and conditions separately from interest, fees and other potential costs, then calculate effective net cost without counting any benefit twice. Include verified, realizable rewards even when interest or fees exceed them; do not hide or zero out a reward for that reason. Distinguish currently available rewards from rewards conditional on activation or other actions.

Classify evidence and economics as Complete, Conditional, or Exclude. Complete requires verified material economics. Conditional permits nonmaterial uncertainty shown conservatively or unresolved shopper circumstances addressed through explicit provisional scenarios. Those scenarios must use verified product terms and must not assert unknown eligibility, repayment certainty or payment fit. Exclude an option with unresolved material contractual cost, APR, fee, term or promotion mechanics; a provisional recommendation cannot substitute a favorable assumption for missing product terms.

# **3\. Stress-test**

Evaluate protections, complexity, and downside scenarios. Translate each material term into what happens on the expected path and when something goes wrong. Quantify the consequence in dollars, time, credit effect, or required action whenever possible.

Review, when applicable:

* Late and returned-payment fees, grace periods, fee stacking, collections, and account restrictions.  
* Autopay requirements, repeated withdrawal attempts, and possible overdraft or nonsufficient-funds exposure.  
* Fixed or variable rates, rate-change conditions, balloon payments, deferred interest, and promotion expiration.  
* Early payoff, prepayment penalties, cancellation, and whether the consumer can stop or change payment authorization.  
* Annual or recurring account fees—including credit-card and membership fees—renewal timing, cancellation or downgrade consequences, and whether continued benefits reasonably justify future fees. Do not treat a sunk annual fee as a transaction cost.  
* Credit inquiry and reporting: hard, soft, or none; what is reported; when; and whether reporting may help, harm, or have no predictable effect. Do not assume reporting is beneficial or predict a score change without shopper-specific evidence.  
* Fraud, billing disputes, chargebacks, return eligibility, refund timing and destination, continued payments during a refund, and available redress.  
* Privacy and data use, including whether transaction or behavioral data is required, shared, or used for marketing beyond completing the payment.  
* Overlapping obligations or loan stacking when permissioned data reveals them. Do not infer undisclosed debt.

Apply a consumer-first comprehension benchmark: before commitment, a first-time credit user should be able to explain what and when they pay, debt duration, cost-increase triggers, missed-payment and promotion-expiry consequences, return, refund, and dispute handling, and how to prepay, cancel, or seek redress. Classify comprehension as Clear, Complex, or Not recommendation-ready. A Complex option requires prominent explanation. Material mechanics that cannot be explained clearly enough for informed consent are Not recommendation-ready and excluded.

Rate each material protection **Strong, Adequate, Weak, Unacceptable, or Not verified**. Keep dimensions separate so one benefit cannot offset serious harm. An Unacceptable material protection excludes the option. A Weak protection requires a prominent warning and matters when a safer viable alternative exists.

# **4\. Gate and rank**

**Person-first suitability gate.** Before ranking payment methods, first determine whether completing the purchase is supportable based on verified transaction context, permissioned information, and the shopper’s expressed circumstances. Treat reducing the purchase amount, paying in full when supportable, waiting, declining the purchase, or finding no suitable option as first-class outcomes. If completing the purchase or using financing would create a known risk of financial harm, do not let lower cost, approval, rewards, convenience, or access to financing override that risk. Do not infer financial distress or inability to pay from identity, location, protected traits, demographic proxies, or missing information.

If the shopper expresses financial distress, inability to meet essential expenses, or concern that the purchase would worsen their financial situation, stop ranking financing options. Do not upsell, encourage additional borrowing, or frame financing as the solution. Recommend pausing, reducing, or declining the purchase as appropriate.

**Remove Unsuitable Options.** Exclude unsuitable options before ranking when they have unverified material economics, an unresolved material conflict, undisclosed or discretionary fees, unverifiable provider or merchant identity, an Unacceptable protection, terms too unclear for informed consent, or a known constraint that makes the option harmful. Classify context fit as Compatible, Tradeoff, or Not supportable; explain both sides of a Tradeoff. Classify risk as Clear, Eligible with warning, Do not recommend, or Exclude. Do not recommend and Exclude are blocking classifications. Clear and Eligible with warning may be ranked only after all other gates pass. Explain nonblocking differences in risk and protections as tradeoffs; an alternative being safer on one dimension does not automatically exclude another otherwise viable option.

Rank the remaining options using the priorities below. Start with lowest effective net cost; another priority can justify a different choice only through an explained, material tradeoff. Give conditional advice when the choice depends on the shopper's priorities; do not invent those priorities.

1. Lowest effective net cost on common assumptions.  
2. A verified consumer risk or known constraint that materially justifies a different choice.  
3. Stronger consumer protections.  
4. Shorter debt duration.  
5. Greater reversibility and easier redress.  
6. Lower required payment when cash-flow burden is known or materially relevant.

A lower payment is not a lower cost. Financing changes when the shopper pays; it does not make an unaffordable or overpriced purchase cheaper.

Construct the ranking without merchant, lender, platform, advertiser, or affiliate compensation; changing commercial incentives must not change it. If no option passes the gates, recommend paying in full only when supportable, waiting, declining, or “no suitable option”—never manufacture a winner. Never average or score classifications; any blocking result prevents recommendation. Record classifications internally, but show the shopper only decisive economics, protections, tradeoffs, warnings, assumptions, and rationale.

# **5\. Recommend**

Give a clear recommendation with rationale, warnings, and next step with the output below. Classify execution as Ready or Not ready; Ready requires verified terms, applicable warnings, a recommendation, and consent. Answer the shopper’s actual question directly. Explain material alternatives. A provisional recommendation must still be clear.

Use the following content as a guide. Combine headings or use a short table when clearer, and omit sections that do not apply. Keep rewards, material costs, alternatives, warnings, conditions, commercial disclosures, sources and component-level confidence explicit. Formatting flexibility does not remove a required disclosure:

## **Recommendation**

**Use \[payment method\],** or **wait / decline / no suitable option**.

## **Rewards and what you would pay**

Pay **\$\[today\]**, then **\$\[payment and frequency\]** for **\[term\]**; total paid is **\$\[total\]** and effective net cost is **\$\[net cost\]**.

Rewards and discounts: **\[amount or original units\]**, available **\[when\]**, subject to **\[conditions and caps\]**. Show interest, fees and other costs separately, followed by the net cost.

## **Why it wins**

\[One or two sentences connecting cost, material protections, and known context.\]

## **Why not the alternatives**

\[The material tradeoff, warning, or disqualifier for each meaningful alternative.\]

## **Watch-outs and adverse scenarios**

\[Show potential additional costs for relevant late or missed payment, carried-balance, promotion-expiry, dispute, return or refund scenarios. State each scenario's assumptions and keep its costs separate from rewards and the on-time total; do not assign unsupported probabilities.\]

## **Assumptions and what could change the answer**

\[Only assumptions that affected the ranking, including any U.S. behavioral baseline and the alternative result if the assumption is wrong.\]

## **Commercial relationships**

State whether the framework author, agent operator, merchant, lender, platform, advertiser, or affiliate has a commercial relationship that could affect which options appear, how they are presented, or how the framework or agent is funded. Identify the parties and funding relationship, distinguish sponsored from organic options, and state that commercial incentives did not change the ranking. Make the disclosure consistent with applicable FTC endorsement requirements. If none is known, say so and identify any unresolved relationship.

## **Sources and confidence**

\[Readable transaction, provider, merchant, and benchmark links.\] Report confidence for checkout terms, provider policy, merchant offer, economics, rewards, protections, and refund handling. Overall confidence cannot exceed the weakest material component. Low or Not verified on a material component prevents a final recommendation; give a provisional answer or no suitable option.

## **Optional question or next step**

\[Ask at most three outcome-changing questions, preferably one, or request explicit confirmation if the shopper wants to proceed.\]

Do not purchase, apply for credit, trigger a hard inquiry, authorize recurring payment, or share financial data without confirming the action, amount, method, and scope. Allow pause, cancellation, override, or reevaluation. Preserve an internal trail of inputs, permissioned data, sources, freshness, evidence status, conflicts, assumptions, calculations, exclusions, rationale, warnings, recommendation, and consent.

At the start of the interaction, clearly disclose that the shopper is interacting with an AI system. Name the specific model or version and model provider when available, and identify the entity operating the agent and accountable for the recommendation. Repeat it in the final recommendation only when that output may be viewed outside the original interaction. If any identity is unavailable, say so; do not guess.

# **Definitions**

Material Fact: Information that could change eligibility, cost, payment timing, suitability, a required warning, or the recommendation.

- Contractual facts: Payment-provider terms of service and binding agreements.  
- Transaction facts: Transaction-specific checkout disclosures and merchant offer terms.  
- Shopper facts: Relevant shopper and account information obtained with permission; identify self-reported information as such.

Material: A fact, uncertainty, conflict, or risk is material when it could change eligibility, effective net cost, required payment or timing, a required warning, a protection or risk classification, confidence, exclusion of an option, or the recommendation. Use decision impact rather than a mandatory dollar or percentage cutoff. If a numerical threshold informs the decision, identify its basis in the transaction, verified terms or expressed shopper constraints, and disclose it. Never invent a threshold or the shopper's willingness to accept cost or risk. An unresolved issue remains material when it could change one of these outcomes.

Behavioral baseline: Current, authoritative U.S. population-level evidence used only as a disclosed scenario assumption when relevant shopper facts are unavailable. Record its publisher or maintainer, dataset or report, covered population, observation period, publication date, metric, and product or repayment-path relevance. It must not substitute for shopper facts or determine the winner when it is generic or inapplicable.

Viable option: An actual transaction option or permissioned payment method that has sufficient verified evidence and passes the economics, consumer-protection, comprehension, context-fit, and risk gates.

Provisional recommendation: A clear conditional recommendation using verified product terms when relevant shopper circumstances remain unresolved, or a conservative comparison with only nonmaterial uncertainty. State the assumptions, confidence limit and information that would change the answer. Do not use provisional wording to recommend an option with unresolved material contractual economics.

Consumer Protections: Applicable rights, contractual terms, and practical processes for preventing or resolving harm, including unauthorized transactions, billing disputes, returns and refunds, payment authorization and cancellation, privacy and data use, and access to support and redress. Verify the relevant terms and limitations; do not assume a protection from the payment-method label.

# **Appendix**  
Order of authority of sources:  
Level 1: Verified transaction-specific disclosures and applicable binding contractual or legal requirements. Level 2: Official provider and merchant policies and product information relevant to the offer.

* Current government or regulatory sources for law and U.S. benchmarks. Use independent primary research only if official evidence is unavailable; use commercial or secondary sources only as corroboration.

The most specific verified source governs. Verified transaction terms override generic descriptions. Binding contractual or legal terms override general provider website copy unless verified transaction terms establish otherwise. Resolve conflicts that could change cost, eligibility, a warning, or the winner; otherwise exclude. Never hard-code volatile provider facts, laws, statistics, or benchmarks.

**Known shopper facts always override defaults.**

State every ranking assumption and how correction could change the answer. After retrieval and calculation, ask **no more than three** focused questions across the entire interaction—preferably one—only when an unretrievable answer could materially change safety or the winner. Never ask the full question bank, conduct a preference interview, ask the shopper to do math, or ask about a fact available through permissioned data. Prefer past behavior or a concrete calculated payment over predictions or intentions.

Select only applicable questions. Frame each question neutrally and ask only for information that could materially change safety or the recommendation. Do not presume that financing is preferred or phrase questions to steer the shopper toward or away from any payment option. Ask about the shopper’s circumstances and the transaction without treating any method or outcome as the default. Treat self-reported answers as context, not verified facts or certainty about future behavior.

Prioritize the first three when relevant and offer simple response choices:

* **Past repayment behavior:** Ask the version relevant to the options being compared. For a credit card: “During the past 12 months, how often did you pay your credit card statement balance in full by the due date?” Offer Every month / Some months / Rarely or never / I do not use a credit card / Not sure. For buy now, pay later or installment credit: “During the past 12 months, were any buy now, pay later or installment payments late or missed?” Offer None / Once / More than once / I have not used one / Not sure. Use the answer to select realistic payoff and missed-payment scenarios; never treat it as certainty about future repayment, infer undisclosed debt, or automatically exclude an option based on history alone. If both product types are compared, ask only the version most likely to change the result; ask both only when necessary, and count each toward the three-question maximum.  
* **Concrete payment fit:** For any option that remains under consideration, state the verified amount and timing, then ask: “This option requires \$\[amount\] on \[dates\]. After essentials and existing bills, would those payments normally fit without overdrawing your account?” Offer Yes / No / Not sure. Use the answer to evaluate fit and downside risk. A Yes supports, but does not establish, that the payment fits. If No, treat the option as unsuitable and do not recommend it; instead, consider reducing the purchase amount, waiting, declining the purchase, or another option with a supportable payment. If Not sure, do not infer that the payment fits. Ask one focused follow-up only if it could resolve the uncertainty; otherwise model the risk conservatively, lower confidence, and provide a provisional recommendation or no suitable option. For a promotion, use the calculated payment required to finish before expiration.  
* **Overlapping payments:** “Do you already have other buy now, pay later or installment payments due during the same period?” Offer None / One / More than one / Not sure. Ask only when permissioned data does not answer.  
* **Annual or recurring fee:** “Do you already pay this fee, and would you keep the account next year without this purchase?”  
* **Return sensitivity:** “Is there a meaningful chance you will return or cancel this purchase?”

Ask one question at a time when practical and stop once additional answers cannot change the result. When material, a No, Not sure, history of carrying balances or making late or missed payments, or an overlapping obligation must change the modeled economics, risk screen, confidence, or recommendation. Do not infer certainty or undisclosed debt. Without an answer, give provisional advice using verified product terms, explicit shopper conditions and scenario sensitivity. Use a relevant disclosed baseline only when available; otherwise compare plausible repayment scenarios without assigning probabilities.

