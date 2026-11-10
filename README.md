# Awesome-Smart-Retry-Payment-Recovery

# Awesome Smart Retry & Payment Recovery

> A curated list of top Smart Retry and Payment Recovery platforms — both SaaS/Hosted commercial solutions and open-source alternatives for recovering failed subscription payments, reducing involuntary churn, and optimizing retry logic.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Stripe Smart Retries](#stripe-smart-retries)
  - [Chargebee Smart Dunning](#chargebee-smart-dunning)
  - [Churn Buster](#churn-buster)
  - [Butter Payments](#butter-payments)
  - [FlexPay](#flexpay)
  - [Gravy Solutions](#gravy-solutions)
  - [Recurly Revenue Optimization](#recurly-revenue-optimization)
  - [Zuora Payment Retries](#zuora-payment-retries)
  - [Paddle Retain](#paddle-retain)
- [Open-Source Software](#-open-source-software)
  - [Recurso](#recurso)
  - [Lago](#lago)
  - [Kill Bill](#kill-bill)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Smart Retry and Payment Recovery platforms. These are not open-source but are included as reference points for feature comparison.

### Stripe Smart Retries
**Type:** ML-driven retry timing within Stripe Billing  
Stripe Smart Retries use data points to find the optimal time to retry a failed payment, and are described as more effective than scheduled retries [citation:2]. Revenue recovery features include recovery analytics, automatic customer emails for failed payments and expiring cards, no-code automations for custom dunning flows, and automatic card updates [citation:2]. Setup is entirely no-code through the Stripe Dashboard [citation:2]. **Trade-off:** Limited to the Stripe ecosystem; you remain the merchant of record and own tax compliance.

### Chargebee Smart Dunning
**Type:** ML-powered retry optimization within Chargebee  
Chargebee's Smart Dunning customizes retry frequency based on analysis of past transaction data and patterns to achieve better success rates, with up to 12 retries [citation:12]. It is available only on the Scale plan and above [citation:12]. Standard Dunning allows configurable retry counts (1-5 for direct debit) and final actions (mark unpaid, void, write-off, or reverse invoice) [citation:1]. **Trade-off:** Smart Dunning is gated to higher-tier plans; you must contact support to enable it [citation:12].

### Churn Buster
**Type:** Dedicated failed payment recovery with human tuning  
Churn Buster has focused exclusively on subscription churn since 2013, handling 50+ million failed payments across $5+ billion in recurring revenue [citation:4]. Its differentiator is **retries paired with branded email and SMS sent from dedicated infrastructure on the brand's own domain** — retry-only tools send nothing to the customer [citation:4]. The team tunes retry timing by decline code and tests copy, send times, and campaign length. Pricing starts at $269/mo based on MRR tier, with a flat fee rather than a percentage of recovered revenue [citation:4]. Supports 17+ platforms including Stripe, Shopify, Recharge, Loop, Braintree, and Recurly [citation:4]. **Trade-off:** Not a platform-native solution; requires setup with the Churn Buster team (about an hour) [citation:15].

### Butter Payments
**Type:** ML-powered payment recovery with per-payment optimization  
Butter processes each failed payment individually rather than in batches, building ML models customized to the business's subscription value, cadence, and regional customer base [citation:7]. It integrates directly with payment processors and subscription platforms including Stripe, Recharge, and custom in-house stacks [citation:7]. Butter operates on revenue-share contracts with no retainer fees, claiming 10%+ ARR growth from recovered payments [citation:7]. SOC 2 Type 2 and PCI DSS Level 2 compliant, with no PII required [citation:7].

### FlexPay
**Type:** Retry scheduling with API-driven control  
FlexPay provides a Scheduler for auto-retries with API endpoints for payment status, stopping retries (via refund or redact), and reconciliation using `initialMerchantTransactionId` [citation:6]. Merchants can disable customer recovery per request and redact payment methods to block further transactions [citation:6]. Sandbox testing is available for integration validation [citation:6].

### Gravy Solutions
**Type:** Human-led recovery for service businesses  
Gravy specializes in failed payment recovery for service-based businesses (memberships, courses, coaching), with a 30-day customized communication cadence rather than plug-and-play automation [citation:5]. The service handles access management (removing/restoring access), billing questions, upsells/downsells, and cancellation management on the client's behalf [citation:5]. Claims $10M recovered since 2020, with an average of $379K monthly recovered for services clients [citation:5]. **Trade-off:** Human-intensive and service-oriented rather than software-only.

### Recurly Revenue Optimization
**Type:** AI-powered churn prevention within Recurly  
Recurly's All-Access plan includes intelligent churn-prevention tools with multiple dunning campaigns, AI-powered agents and analytics, and payments orchestration across multiple gateways [citation:8]. The Engage product adds an AI propensity-to-churn model, personalized offers, cancel-save flows, and A/B testing [citation:8]. Starter plans include only static churn-prevention tools and one dunning campaign [citation:8]. **Trade-off:** Advanced recovery features require the All-Access tier with a $1M billing volume minimum [citation:8].

### Zuora Payment Retries
**Type:** Configurable retries with AI optimization  
Zuora provides configurable payment retry schedules with AI-driven algorithms to maximize recovery, plus automated customer notifications tied to retry schedules and real-time analytics on decline trends [citation:9]. Supports segmentation of customers to adjust retry logic, and distinguishing soft vs. hard declines to reduce transaction fees [citation:9].

### Paddle Retain
**Type:** Integrated retry and retention within Paddle  
Paddle Retain (formerly ProfitWell Retain) uses its own algorithms built on billions of data points to reduce churn, and is fully integrated with Paddle Billing for automatic dunning and retention [citation:3]. It can also connect to external billing platforms including Braintree, Chargebee, and Chargify via read-only API access [citation:3]. Retain supports multi-user targeting via the ProfitWell.js snippet for in-app messages to past-due users [citation:14].

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
