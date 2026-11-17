# Payment Choice Framework for AI Assistants

**From Affirm and Consumer Reports · Version 1.5.5 · Draft for review**

> **Not ready for use.** This framework is in development and is not a standalone AI
> tool. Do not use it to make real payment decisions or build it into a consumer-facing
> product.
>
> The framework contains no payment terms of its own. Applying it requires accurate
> payment terms and relevant consumer information, provided by the user or retrieved
> through connected tools, along with reliable cost calculations. It has been tested
> only in simulated conversations where the assistant had tools to retrieve predefined
> terms and run calculations. If you paste it into a general-purpose AI assistant, the
> assistant may state interest rates, fees, payment schedules or promotion terms from
> memory that are wrong or out of date, and may make arithmetic errors.

## What it is

A set of written instructions that helps an AI assistant recommend how to pay for a
purchase: card, debit, digital wallet, installment, buy now pay later, or promotional
financing. It asks the assistant to look beyond an appealing offer or monthly payment,
consider the person's circumstances, translate the fine print into plain language, and
explain the tradeoffs. The best recommendation might be to finance, pay in full, choose
another provider, wait, or decide against the purchase. It covers U.S. purchases only.

The framework is in [payment-choice-framework.md](payment-choice-framework.md). It
guides the assistant through five steps:

1. **Verify and contextualize:** gather the available payment options, their terms, and
   what is known about the consumer's circumstances.
2. **Normalize:** compare costs and repayment obligations using the same assumptions.
3. **Stress-test:** consider the risks and what could happen if circumstances change.
4. **Gate and rank:** assess which options fit the consumer's needs and which should be
   ruled out.
5. **Recommend:** explain the recommendation, alternatives, and any uncertainties, and
   take no action without the consumer's confirmation.

The framework is not a financial adviser or a finished consumer product. It cannot
access accounts or make purchases on its own.

## Requires real terms

Real terms are disclosures the assistant retrieves during the conversation, or that the
shopper pastes or uploads from checkout. Terms a model remembers from training are never
treated as verified. When an option's real terms are missing, the framework tells the
assistant to leave that option out instead of estimating. When no option has real terms,
the assistant should say it cannot compare them reliably.

Written instructions do not guarantee that an AI will follow them. The mode where the
shopper pastes terms has not been tested.

## If you test it

Give the assistant the actual checkout disclosures and provider terms for each option,
check every number against those documents, and do not act on its recommendation.

## How it was tested

The framework was tested in simulated, multi-turn shopping conversations, comparing
responses with and without it.

The 30 scenarios covered common payment decisions and the ways they go wrong: deferred
interest and promotional deadlines, minimum payments on a credit card, missed payments
and late fees, rewards with caps, refunds while still paying off a purchase, monthly
payments that strain a budget, missing or conflicting terms, a shopper in financial
distress, a sponsored option, and hidden instructions planted in retrieved pages.

Each conversation was graded against the framework's requirements, such as whether the
assistant:

- Calculated costs correctly.
- Explained tradeoffs between options and the assumptions behind its recommendation.
- Showed what could go wrong, such as a missed payment or a return.
- Handled missing information without making things up.
- Considered alternatives to financing, including waiting or not buying.
- Kept the ranking free of commercial influence and took no action without consent.

A conversation passed when it met all the requirements that applied to its scenario.
Four models each attempted the 30 scenarios three times per condition, producing 720
conversations. Pass rates were higher with the framework for every model, with an
equal-model average of 48.6% without it and 71.8% with it.

| Model | Without the framework | With the framework |
| --- | ---: | ---: |
| GPT-6.1 Sol | 73.3% | 93.3% |
| GPT-5.6 Luna | 30.0% | 51.1% |
| Claude Sonnet 5.5 | 53.3% | 71.7% |
| Claude Haiku 5.5 | 37.8% | 71.1% |

These results have limits:

- Payment terms were predefined and retrieved through tools from controlled sources.
  The tests did not cover finding or verifying terms on live websites.
- Shoppers were simulated and supplied structured information that real people may not
  know or provide.
- Not all models were run under the same conditions. One model's latest run used revised
  framework and simulator instructions, so the comparison across models is descriptive.
- The results evaluate AI responses, not consumer outcomes. They do not establish
  improved outcomes or readiness for consumer use.

The framework was tested and revised against the
[Consumer Finance AI Standard](https://innovation.consumerreports.org/consumer-finance-ai-standard/)
from Consumer Reports.

## Who made it

Affirm developed the original framework and tested it against the Consumer Finance AI
Standard. Affirm and Consumer Reports then worked together to evaluate the framework and to incorporate more of the
Standard's requirements.

## Feedback and collaboration

Affirm and Consumer Reports welcome AI developers, financial technology companies,
payment providers, researchers and consumer organizations interested in helping advance
this work. We're especially interested in:

- Additional test scenarios.
- Feedback on the framework and the test results.
- Exploring potential integrations.

To contribute to testing or explore collaboration, contact
[CorporateEngagement@cr.consumer.org](mailto:CorporateEngagement@cr.consumer.org).