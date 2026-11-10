# Awesome-Smart-Retry-Payment-Recovery

# Awesome Smart Retry & Payment Recovery

> A curated list of top Smart Retry and Payment Recovery platforms — both SaaS/Hosted commercial solutions and open-source alternatives for recovering failed subscription payments, reducing involuntary churn, and optimizing retry logic.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [Sector Overview & Market Dynamics](#-sector-overview--market-dynamics)
- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
- [Open-Source Software](#-open-source-software)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 📈 Sector Overview & Market Dynamics

The subscription payment recovery and smart dunning sector addresses an estimated **$129+ billion annual loss** in involuntary churn and failed recurring payments globally, with passive declines accounting for 20% to 40% of all subscription subscriber cancellations. The market is **moderately fragmented**: core payment processors (e.g., Stripe, Adyen) provide baseline algorithmic retries in a high-concentration gateway layer, while specialized AI recovery engines, multi-gateway orchestrators, and high-touch retention services capture substantial independent market share through cross-processor intelligence and multi-channel customer dunning.

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Smart Retry and Payment Recovery platforms.

| Product | Pricing (Starting Tier) | Free Tier / Trial Limits | Company Size (Valuation / Revenue) | Description & Key Features | Supported Platforms |
|:---|:---|:---|:---|:---|:---|
| [Stripe Smart Retries](https://stripe.com/billing) | 0.7% per recurring transaction (Stripe Billing) | Free forever baseline: Smart Retries included with no extra monthly fee; test mode sandbox included free | $70B Valuation / ~$4.2B Net Revenue | ML-driven retry optimization timing trained on billions of transaction data points across global Stripe card traffic; automatic card account updater | Stripe ecosystem |
| [Zuora Payment Retries](https://www.zuora.com) | ~$45,000/year base contract ($3,750/mo) | No free forever tier; demo sandbox available on request for qualified prospective enterprise accounts | $1.7B Valuation (Silver Lake / GIC buyout) / ~$450M ARR | Enterprise AI-driven configurable retry engine distinguishing soft vs. hard declines; automated custom notification cadences and collections workflows | Enterprise multi-gateway |
| [Paddle Retain](https://www.paddle.com/retain) | $500/mo flat fee or performance fee (% of recovered revenue) | Free trial via live churn / recovery audit on historical data; free metrics tracking via ProfitWell Metrics | $1.4B Valuation (Series D) / ~$100M ARR | Algorithmic churn reduction and dunning engine built on billions in SaaS metrics; in-app credit card update paywalls via ProfitWell.js | Paddle, Stripe, Chargebee, Braintree |
| [Chargebee Smart Dunning](https://www.chargebee.com) | $599/mo (Performance Plan, billed annually) | Free Starter tier up to $250k lifetime billing (includes static dunning; Smart Dunning requires 14-day Performance trial or upgrade) | $3.5B Valuation (Series H) / ~$200M ARR | ML-powered dynamic retry timing adjusting attempt frequencies based on decline reasons, time zones, and bank behavior with up to 12 retries | 30+ gateways (Stripe, Braintree, Adyen) |
| [Recurly Revenue Optimization](https://recurly.com) | $249/mo + 0.9% revenue (Starter Plan; All-Access custom) | 90-day free trial on Starter plan ($40,000 billing volume allowance included during trial) | $39M+ VC Funding / ~$55M–$60M Revenue | AI propensity-to-churn models, multi-gateway failover routing, statistical machine learning retry intervals, and dynamic cancel-save workflows | Recurly gateway network |
| [Butter Payments](https://www.butterpayments.com) | Performance fee (custom revenue share of recovered revenue only; no retainer) | 30-day "First month free" trial of full recovery lift + free payment health & churn analysis audit | $100M Valuation (Series A) / ~$6M ARR ($37.5M raised) | Per-payment machine learning models tailored to card issuer behavior, subscription cadence, and geography; zero customer outreach spam | Stripe, Recharge, custom APIs |
| [Gravy Solutions](https://gravysolutions.io) | $997/mo flat fee (custom-tailored based on MRR volume) | Free 30-day failed payment recovery audit of active subscriber accounts; no software-only free tier | $4.5M Series A / ~$7.2M Revenue ($43M raised) | Human-powered recovery combining US-based customer retention agents with custom SMS, phone outreach, and 30-day personalized cadences for digital products | Stripe, Infusionsoft, Chargebee |
| [FlexPay](https://flexpay.io) | Performance fee / ROI-mapped custom fee (typically 10%–20% of recovered revenue) | Free payment decline & churn audit of historical batch records; developer sandbox credentials upon consultation | Seed/Series A / ~$6.5M–$7.2M ARR | Invisible Recovery™ using machine learning to analyze decline codes and bank algorithms for non-intrusive payment retries without client friction | 40+ gateways & CRMs |
| [Churn Buster](https://churnbuster.io) | $269/mo (Starter Dunning based on MRR tier) | Free forever "Measure" tier (baseline payment churn analytics & tracking with zero monthly subscription cost) | Bootstrapped / Profitable ($5B+ processed) | Decline-code specific retry schedules combined with high-deliverability branded dunning emails and SMS sent from custom merchant domains | 17+ platforms (Stripe, Shopify, Recharge, Braintree) |

---

## 🟩 Open-Source Software

Self-hosted, community-driven Smart Retry and Payment Recovery tools. The open-source ecosystem for **dedicated payment recovery** is extremely limited; available options are billing engines that include dunning as a feature.

### Recurso
**Stack:** Go / PostgreSQL / TigerBeetle (optional) | **License:** MIT  
Recurso is an open-source billing engine for SaaS with subscriptions, invoicing, multi-currency payments, and a **bandit-retry engine for dunning** alongside a Collections operator layer [citation:11]. It includes a built-in double-entry ledger with ASC 606 revenue recognition, usage-based billing with exact rational math, and self-serve importers from Stripe and Chargebee [citation:11]. Integrates with Stripe, Razorpay, GoCardless, and Adyen for payments, and syncs to QuickBooks, Xero, NetSuite, and Tally [citation:11]. Deploys with a single `make demo` command for local testing [citation:11]. **Trade-off:** The dunning engine is one feature within a broader billing platform, not a standalone recovery service with human tuning or multi-platform support.  
**Best for:** Teams wanting an MIT-licensed billing engine with dunning built in, accepting that retry optimization is algorithmic rather than ML-driven with human tuning.

### Lago
**Stack:** Ruby / PostgreSQL / Redis | **License:** AGPL-3.0  
Lago is an open-source billing engine for usage-based and subscription pricing, explicitly positioned as an alternative to Chargebee, Recurly, and Stripe Billing. It calculates charges and pushes invoices to Stripe, Adyen, or GoCardless for collection. **Limitation for recovery:** Lago does not process payments itself and does not include a dedicated smart retry engine — dunning and retry logic would need to be implemented on top of the invoicing layer, or delegated to the connected payment gateway.  
**Best for:** Teams wanting open-source usage billing with Stripe collection, accepting that smart retry logic must come from Stripe or custom implementation.

### Kill Bill
**Stack:** Java / MySQL/MariaDB/PostgreSQL | **License:** Apache-2.0  
Kill Bill is a mature open-source subscription billing platform with invoice and payment management. It supports overdue accounts and payment retries as part of its billing lifecycle, with configurable retry policies. Payment plugins for Stripe, Braintree, and Adyen handle gateway interactions. **Limitation:** Kill Bill provides the billing engine and retry primitives, but does not include an ML-driven smart retry algorithm or branded customer communication layer comparable to Churn Buster or Butter.  
**Best for:** Teams wanting a permissively licensed billing platform with retry primitives they can configure, accepting that advanced recovery optimization is not built in.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Smart Retry | Customer Comms | Platform Coverage | Self-Hosted | Best For |
|----------|---------|-------|-------------|----------------|-------------------|-------------|----------|
| **Stripe Smart Retries** | Proprietary | Cloud | ✅ ML timing | ✅ Emails | Stripe only | ❌ | Stripe-native recovery |
| **Chargebee Smart Dunning** | Proprietary | Cloud | ✅ ML (Scale+) | ✅ Emails | Chargebee only | ❌ | Chargebee Scale users |
| **Churn Buster** | Proprietary | Cloud | ✅ Decline-code tuned | ✅ Branded email/SMS | 17+ platforms | ❌ | Multi-platform + human tuning |
| **Butter Payments** | Proprietary | Cloud | ✅ Per-payment ML | (Check) | Stripe, Recharge, custom | ❌ | ML per-payment optimization |
| **FlexPay** | Proprietary | Cloud | ✅ Scheduler | (Check) | (Check) | ❌ | API-driven retry control |
| **Gravy Solutions** | Proprietary | Cloud (Human) | ✅ Custom cadence | ✅ Human outreach | Services businesses | ❌ | Human-led service recovery |
| **Recurly** | Proprietary | Cloud | ✅ AI (All-Access) | ✅ | Recurly only | ❌ | Recurly All-Access users |
| **Zuora** | Proprietary | Cloud | ✅ AI configurable | ✅ | Zuora only | ❌ | Zuora enterprises |
| **Recurso** | MIT | Go/Postgres | ✅ Bandit engine | (Check) | Stripe, Razorpay, GoCardless | ✅ | Open-source billing + dunning |
| **Lago** | AGPL-3.0 | Ruby/Postgres | ❌ (Via gateway) | ❌ | Stripe, Adyen, GoCardless | ✅ | OSS billing → Stripe collection |
| **Kill Bill** | Apache-2.0 | Java/DB | ✅ Configurable | (Check) | Via plugins | ✅ | OSS billing with retry primitives |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Smart Retry or Payment Recovery tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the open-source ecosystem for **dedicated payment recovery** is essentially nonexistent — payment recovery is dominated by specialized commercial services that combine ML-driven retry timing, branded customer communication, and human tuning. **Recurso** is the most notable open-source option, offering a bandit-retry dunning engine within a broader MIT-licensed billing platform [citation:11]. **Churn Buster** and **Butter Payments** represent the commercial gold standard for multi-platform recovery with ML optimization and human oversight [citation:4][citation:7]. For teams already on Stripe, **Stripe Smart Retries** provides ML-driven recovery without additional tooling, though it cannot match the multi-platform coverage or human tuning of dedicated services [citation:2].

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
