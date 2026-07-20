# Is ScraperAPI Good? An Honest, Hands-On Verdict on Pricing, Real Costs, Site Success Rates, and Whether It's Worth It (Full Plan Breakdown and Latest Deals Inside)

You typed "is ScraperAPI good" into a search bar, which probably means you're standing at a fork in the road. Maybe you've been burned by a scraping API before — credits vanishing faster than the dashboard said they would, requests failing on the one site you actually needed, a bill that didn't match the sticker price. Or maybe you've never used one and you're trying to figure out whether ScraperAPI is the right place to start. Either way, you don't need a glossy landing page recap. You need someone to walk through the real numbers — what each plan actually delivers, where the service genuinely performs, where it falls flat, and how the credit math actually works — so you can decide with your eyes open.

That's what this piece does. I dug through ScraperAPI's pricing page, the official docs, third-party benchmarks, G2/Capterra/Trustpilot reviews, and competitor pricing to piece together a verdict that isn't trying to sell you anything. The short version: ScraperAPI is good for a specific kind of user doing a specific kind of work, and noticeably less good for everyone else. The longer version follows.

## **What ScraperAPI Actually Is (and Who It's Built For)**

ScraperAPI is a proxy rendering API. You send it a URL through a simple HTTP endpoint, it routes the request through a pool of more than 40 million residential IPs across 50+ countries, optionally renders JavaScript with headless Chrome, handles basic CAPTCHA solving, retries failed requests, and hands you back HTML or parsed JSON. Founded in 2018, headquartered in Las Vegas, the company says it now processes around 36 billion API requests per month and counts Deloitte, Sony, and Alibaba among its users.

The mental model that matters: ScraperAPI is **infrastructure**, not a platform. You own the scraper logic, the parsing, the storage, the scheduling, the deployment. They own the proxy layer. If you already have working scraper code and just need a reliable proxy rotation and rendering layer to drop in front of it, ScraperAPI is built for you. If you're starting from scratch with no code and no engineering bandwidth, you're looking at the wrong category of tool entirely — and I'll get to that later.

The core feature set covers the basics you'd expect: automatic proxy rotation, JavaScript rendering, country-level geotargeting, automatic retries, custom headers, session persistence, and 18 structured data endpoints that return parsed JSON for sites like Amazon, Google, Walmart, eBay, and Redfin. All plans, including the free tier, get access to the structured data endpoints.

## **The Credit Multiplier System — The Part Most Reviews Skip**

This is the single most important thing to understand about ScraperAPI, and almost no review explains it clearly. The headline "100,000 credits" on the Hobby plan reads like "100,000 requests." It almost never is.

Every request costs a base number of credits determined by the domain you're targeting:

| **Domain Category** | **Base Credits per Request** | **Examples** |
| --- | --- | --- |
| Normal websites | 1 | Blogs, news sites, simple HTML |
| E-commerce | 5 | Amazon, eBay, Walmart |
| SERP (search engines) | 25 | Google, Bing |
| Social media | 30 | LinkedIn |

On top of that, optional parameters add extra credits:

| **Parameter** | **Extra Credits** |
| --- | --- |
| `render=true` (JS rendering) | +10 |
| `premium=true` (premium proxy) | +10 |
| `screenshot=true` | +10 |
| `ultra_premium=true` (paid plans only) | +30 |
| Cloudflare / Datadome / PerimeterX bypass | +10 each (auto-detected) |
| `premium=true` + `render=true` combined | 25 total (not +20) |
| `ultra_premium=true` + `render=true` combined | 75 total (not +40) |

That last row is the kicker. Combining features costs **more** than the sum of the individual costs. Premium proxy plus JavaScript rendering should logically cost +20 credits, but ScraperAPI charges 25. Ultra-premium plus rendering should cost +40, but it's actually 75 — nearly double. This non-linear stacking is documented, but you have to dig for it, and it's the primary reason new users watch their credits disappear faster than expected.

A few more details worth knowing before you commit:

- **Domain-based pricing is automatic.** You don't opt into the 5-credit Amazon multiplier or the 25-credit Google multiplier. ScraperAPI applies it the moment it detects the domain. Same with anti-bot bypass credits.
- **Credits do not roll over.** Unused credits expire at the end of each billing cycle. No accumulation.
- **You're only billed for successful requests.** Failed scrapes (anything outside a 200 or 404 response) don't burn credits — a genuinely fair detail. Note that 404 responses do consume credits, and cancelled requests are charged if you pull the plug before the 70-second processing window completes.
- **Pay-As-You-Go overflow is only available from the Scaling plan upward.** On Hobby, Startup, or Business, running out of credits mid-cycle means upgrading or waiting. On Scaling, Professional, Advanced, and Enterprise, you can keep scraping at a fixed PAYG rate.

> A $49/month plan advertised as "100,000 credits" delivers only about **1,333 actual requests** when scraping protected sites with ultra-premium plus JavaScript rendering. That works out to roughly $36.75 per 1,000 pages — more expensive than many fully managed scraping services.

The cleanest way to estimate real costs before committing is the Domain Multiplier tool in the dashboard, or the `https://api.scraperapi.com/account/urlcost` endpoint, which returns the credit cost for any URL with any combination of parameters applied.

## **Full Plan Comparison: Every Tier on the Official Pricing Page**

ScraperAPI's plan lineup expanded in May 2026 with two new "Growth" tiers — Professional and Advanced — aimed at teams that need more than 5 million credits a month without having to talk to sales. All plans include the same core feature set: JS rendering, premium proxies, JSON auto-parsing, rotating proxy pools, custom headers, CAPTCHA/anti-bot bypass, custom sessions, automatic retries, unlimited bandwidth, and a 99.9% uptime guarantee. The differences are volume, concurrency, geotargeting scope, and whether pay-as-you-go overflow is available.

| **Plan** | **Monthly Price** | **Annual (per mo, ~10% off)** | **API Credits / Month** | **Concurrent Threads** | **Geotargeting** | **PAYG Overflow** | **Get Started** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Free Trial | $0 (7 days) | — | 5,000 (one-time) | 5 | — | No |  [Start free trial, no card needed](https://dashboard.scraperapi.com/signup?fp_ref=coupons) |
| Free Plan | $0 | — | 1,000 (recurring monthly) | 5 | — | No |  [Claim 1,000 free monthly credits](https://www.scraperapi.com/pricing/?fp_ref=coupons#free) |
| Hobby | $49/mo | $44.10/mo | 100,000 | 20 | US & EU only | No |  [Get the Hobby plan](https://www.scraperapi.com/pricing/?fp_ref=coupons#hobby) |
| Startup | $149/mo | $134.10/mo | 1,000,000 | 50 | US & EU only | No |  [Get the Startup plan](https://www.scraperapi.com/pricing/?fp_ref=coupons#startup) |
| Business | $299/mo | $269.10/mo | 3,000,000 | 100 | Global (country-level) | No |  [Get the Business plan](https://www.scraperapi.com/pricing/?fp_ref=coupons#business) |
| Scaling (Most Popular) | $475/mo | $427.50/mo | 5,000,000 | 200 | Global | Yes |  [Get the Scaling plan](https://www.scraperapi.com/pricing/?fp_ref=coupons#scaling) |
| Professional | $975/mo | $877.50/mo | 10,500,000 (+250K bonus) | 300 | Global | Yes |  [Get the Professional plan](https://www.scraperapi.com/pricing/?fp_ref=coupons#professional) |
| Advanced | $1,975/mo | $1,777.50/mo | 21,500,000 (+500K bonus) | 500 | Global | Yes |  [Get the Advanced plan](https://www.scraperapi.com/pricing/?fp_ref=coupons#advanced) |
| Enterprise | Custom quote | Custom quote | 22,000,000+ | 500+ | Global | Yes |  [Contact sales for Enterprise pricing](https://www.scraperapi.com/pricing/?fp_ref=coupons#enterprise) |

A few things worth noting from this table that aren't obvious at a glance:

- **Geotargeting is gated by tier.** Hobby and Startup are limited to US & EU proxies. If your project needs country-level targeting anywhere else, you need at least the Business plan.
- **The annual billing discount is automatic.** Choose annual instead of monthly and you save 10% on every plan, no coupon code required.
- **The two new Growth plans (Professional and Advanced) include bonus credits as a limited-time offer** — 250K and 500K respectively — and both unlock pay-as-you-go overflow so you're never hard-capped mid-month.
- **Unlimited analytics history** kicks in at the Business plan. Hobby and Startup are capped at 30 days of dashboard history.
- **Credits don't roll over.** Match your plan size to your actual monthly usage rather than overbuying "just in case."

## **Real Cost per Request: Where ScraperAPI Wins and Where It Gets Expensive**

Headline pricing is meaningless until you account for multipliers. Here's the effective cost per 1,000 requests at each tier, factoring in the most common scenarios:

| **Plan** | **Standard (1 credit)** | **JS Rendering (10)** | **E-commerce (5)** | **SERP (25)** | **Ultra-Premium + JS (75)** |
| --- | --- | --- | --- | --- | --- |
| Hobby ($49) | $0.49 | $4.90 | $2.45 | $12.25 | $36.75 |
| Startup ($149) | $0.15 | $1.49 | $0.75 | $3.73 | $11.18 |
| Business ($299) | $0.10 | $1.00 | $0.50 | $2.49 | $7.48 |
| Scaling ($475) | $0.10 | $0.95 | $0.48 | $2.38 | $7.13 |
| Professional ($975) | $0.09 | $0.93 | $0.47 | $2.21 | $6.60 |

For plain HTML scraping on unprotected sites, ScraperAPI is genuinely cheap — the Hobby plan at $0.49 per 1,000 standard requests is competitive with anything on the market. The cost curve bends sharply upward the moment rendering, premium proxies, or high-multiplier domains enter the picture. At ultra-premium plus rendering on the Hobby plan, you're paying $36.75 per 1,000 pages — which is more than several fully managed scraping platforms charge for the same workload.

The takeaway isn't that ScraperAPI is overpriced. It's that **the right plan depends entirely on what you're scraping**. A team scraping 100,000 plain pages a month on the Hobby plan is paying $49 — a great deal. A team scraping 100,000 Amazon pages with rendering on the same plan would burn through 1.5 million credits (5 base + 10 render = 15 credits each), exhausting the allowance in a few days and forcing an upgrade to Startup or Business. Run your own math before committing.

## **Site-Specific Success Rates: Where ScraperAPI Shines and Where It Fails**

No scraping API performs equally well on every website. Independent benchmarks from Scrapeway and Proxyway paint a sharply bimodal picture — ScraperAPI is either excellent or completely useless depending on the target.

| **Target Site** | **Success Rate** | **Avg Speed** | **Cost per 1K (Business Plan)** |
| --- | --- | --- | --- |
| Zillow | 100% | 10.5s | $0.49 |
| Etsy | 99% | 4.8s | $4.90 |
| Amazon | 98% | 6.5s | $2.45 |
| LinkedIn | 95% | 17.8s | $14.70 |
| Walmart | 93% | 11.4s | $2.45 |
| Indeed | 90% | 15.8s | $4.90 |
| StockX | 84% | 3.9s | $4.90 |
| Realtor.com | 12% | 11.8s | $0.49 |
| Instagram | 0% | — | — |
| Booking.com | 0% | — | — |
| Twitter/X | 0% | — | — |

The overall average success rate sits around 63.7%, slightly above the industry average of about 59.5%. Average response time is 5.2–7.3 seconds, which is better than the industry average of 9.8 seconds. So on raw speed and overall reliability, ScraperAPI is above average — but the average hides a wide spread.

**Where ScraperAPI performs well:** e-commerce (Amazon, Walmart, Etsy) and real estate (Zillow). The structured data endpoints for these sites return parsed JSON with high reliability, often above 95%. If your primary use case is scraping Amazon product pages or Google SERPs, ScraperAPI is a reasonable choice.

**Where ScraperAPI falls short:**

- **Social media is a dead zone.** Instagram, Twitter/X, and Booking.com all show 0% success rates in independent testing. LinkedIn works at 95%, but at 30 credits per request, the cost is steep.
- **Login-required sites are off-limits.** ScraperAPI supports session persistence via the `session_number` parameter, but it explicitly forbids scraping data behind login walls. It cannot handle form filling, two-factor authentication, or complex auth flows.
- **Stale data on protected targets.** ScraperAPI applies a 10-minute forced result cache on difficult targets, meaning if you're scraping time-sensitive data like pricing or stock levels, you may receive results up to 10 minutes old.

## **What Real Users Say: Sentiment Across G2, Capterra, and Trustpilot**

Independent review aggregation paints a fairly consistent picture. ScraperAPI sits at roughly **4.5/5 on Trustpilot** (43 reviews), **4.4/5 on G2** (16 reviews), and **4.6/5 on Capterra** (62 reviews). Capterra sub-ratings: Ease of Use 4.9/5, Customer Service 4.6/5, Features 4.5/5, Value for Money 4.5/5.

The recurring praise points are the same across most platforms:

- Clean documentation and a genuinely simple integration — drop it into existing code as a proxy replacement and you're scraping within minutes.
- Responsive customer support.
- Reliable performance on mainstream targets like Amazon, Google, and Zillow.
- Only charging for successful requests (200 and 404 responses), so you're not paying for the service's own failures.

The recurring complaints cluster around a different set of themes:

- **Pricing transparency.** "Breakdown of credit costs can be confusing," one Capterra reviewer wrote. Multiple users reported being surprised by how fast credits burned once multipliers kicked in.
- **Reliability on harder targets.** "ScraperAPI becomes shaky for heavy duty jobs," one community commenter noted. Several Reddit users described 80% failure rates on specific protected sites.
- **Pricing creep over time.** One Capterra reviewer from late 2022 complained that "prices increased by 1000% and quality degraded" — worth noting, though the company has since added new plans and features.
- **No proactive usage alerts.** You have to manually check the dashboard to know when credits are running low. There's no email or SMS notification.

## **Pros and Cons at a Glance**

| **Pros** | **Cons** |
| --- | --- |
| Strong proxy infrastructure (40M+ IPs, 50+ countries) | Credit multiplier system — combining features costs more than the sum |
| Excellent documentation and easy initial setup (Capterra Ease of Use: 4.9/5) | Credits don't roll over month to month |
| Reliable on Amazon, Google, Zillow, Etsy (95–100% success) | 0% success on Instagram, Twitter/X, Booking.com |
| Only charges for successful requests (200/404) | 404 responses still consume credits |
| 18 structured data endpoints with parsed JSON output | Login-required sites explicitly forbidden by ToS |
| Available on all plans including Free | Pay-As-You-Go only on Scaling ($475/mo) and above |
| 7-day no-questions-asked refund policy | 10-minute forced cache on difficult targets — stale data risk |
| New Growth plans (Professional, Advanced) for high-volume teams | Geotargeting beyond US & EU requires Business plan ($299/mo) |
| Annual billing auto-applies a 10% discount | No proactive usage alerts — must manually check dashboard |

## **When ScraperAPI Is the Right Choice — and When It Isn't**

This is the question that actually answers "is ScraperAPI good" for your specific situation. The honest answer is that it depends almost entirely on what you're scraping and who's doing the scraping.

**ScraperAPI is good if:**

- You have working scraper code (Scrapy, Playwright, custom Python/Node.js) and just need a drop-in proxy/rendering layer.
- Your targets are well-supported mainstream sites — Amazon, Google, Walmart, Zillow, Etsy, Indeed.
- You're fetching under 500K pages per month, where the Hobby or Startup plan comfortably covers your volume.
- You already have infrastructure for storage, scheduling, and retries — Airflow, Cron, a managed queue, etc.
- You need a quick proof-of-concept and want to validate an idea without long-term commitment.

**ScraperAPI is not the right fit if:**

- You're starting from scratch with no code and no engineering bandwidth. ScraperAPI is developer infrastructure, not a no-code tool.
- You need to automate end-to-end workflows (scrape → filter → notify → store). ScraperAPI only handles the proxy layer; you build everything else.
- You need global geolocation on a budget. Country-level targeting outside the US and EU requires the Business plan at $299/month.
- You're scraping JavaScript-heavy sites at very high volume. Rendering costs add up fast — at 500K rendered pages per month you're easily at $300+ just for the proxy layer.
- Your targets include Instagram, Twitter/X, Booking.com, or any site requiring login. ScraperAPI simply won't work on these.
- You need enterprise-grade compliance, SLAs, or KYC. ScraperAPI is straightforward but not positioned as enterprise-grade — providers like Bright Data fill that gap.

## **How ScraperAPI Compares to Other Scraping APIs**

For context, here's roughly how the positioning shakes out against the most commonly compared alternatives:

- **vs. Bright Data** — More powerful, more expensive enterprise option. Best for teams that need the highest possible success rates on protected sites regardless of cost. Bright Data's Web Unlocker is the only major provider that doesn't charge extra for JavaScript rendering — all requests cost the same flat rate.
- **vs. ScrapingBee** — Similar developer experience and a comparable $49/month entry point. Generally without the same credit multiplier system, which makes its costs more predictable for some workloads. Note that ScrapingBee enables JavaScript rendering by default at 5 credits, while ScraperAPI leaves it off by default.
- **vs. Scrape.do** — Undercuts ScraperAPI on raw entry price (around $29/month). Appeals to budget-conscious solo developers running simple, unprotected scrapes.
- **vs. Scrapfly** — Strong on JavaScript rendering and cost predictability. Worth comparing head-to-head if rendering is your primary use case.
- **vs. ZenRows** — Comparable feature set but tends to be more expensive at the ~$300/month tier for protected-site scraping.

None of these are universally better. The right choice depends on whether your priority is price predictability, raw success rate on hard targets, or ease of integration. For most developers running moderate-volume scrapes against mainstream sites, ScraperAPI's balance of price and simplicity is exactly why it remains one of the most recommended starting points in the category.

## **Practical Tips for Getting the Most Out of ScraperAPI**

If you've read this far and ScraperAPI still looks like the right fit, a few habits will save you money and headaches:

1. **Test your real targets during the 7-day trial.** You get 5,000 credits with no credit card required. Point them at the exact sites you plan to scrape in production. Document which sites need rendering, premium proxies, or anti-bot bypass so you can estimate realistic monthly costs before paying for anything.
2. **Use the Domain Multiplier and API Playground before running batch jobs.** The dashboard's Domain Cost Estimator and the `https://api.scraperapi.com/account/urlcost` endpoint both tell you the exact credit cost for any URL with any parameter combination before you spend a credit on it.
3. **Disable premium features unless the target requires them.** ScraperAPI does not auto-enable `render=true`, `premium=true`, or `ultra_premium=true` — you have to set them explicitly. But domain-based pricing is automatic, so always know your target's base multiplier before running a batch.
4. **Use Structured Data Endpoints for supported sites.** If you're scraping Amazon or Google, the SDEs save real development time even though they cost more credits. For unsupported sites, evaluate whether a no-code tool would be faster and cheaper than building a custom parser.
5. **Monitor your credit consumption daily during the first month.** There are no proactive usage alerts — set a calendar reminder to check the dashboard every day until you've built intuition for how fast credits burn on your specific targets.
6. **Match your plan size to actual monthly usage.** Credits don't roll over. Sizing up "just in case" is a guaranteed way to overpay.
7. **Choose annual billing if you're confident in the service.** The automatic 10% discount is applied at checkout with no code needed and applies to every plan.

## **Latest Deals, Discount Codes, and How to Save**

A few ways to reduce your ScraperAPI bill:

- **The 7-day free trial with 5,000 credits, no credit card required.** This is the lowest-risk way to test the service against your actual targets before committing any money. 👉 [Start your free trial here](https://dashboard.scraperapi.com/signup?fp_ref=coupons)
- **Automatic 10% off with annual billing.** Applied at checkout on every plan, no code required. On the Hobby plan, that drops the effective monthly rate from $49 to $44.10. On Business, from $299 to $269.10.
- **The recurring free plan with 1,000 monthly credits.** Stays active indefinitely for small scraping projects, with 5 concurrent connections.
- **Promotional coupon codes floating around the web.** Codes like `DATALOVER`, `ANWAR10`, and `rohit44` have been reported to provide 10% off monthly subscriptions, and `BOOM10` has been advertised at up to 30% off. Coupon code availability and validity change frequently — the most reliable way to lock in current promotional pricing is to sign up through an active partner link before subscribing, since introductory offers are typically applied automatically. 👉 [Check the current sign-up offer and start your free trial](https://www.scraperapi.com/pricing/?fp_ref=coupons)
- **Bonus credits on the new Growth plans.** The Professional plan includes a limited-time bonus of 250K credits on top of the 10.5M monthly allowance, and the Advanced plan includes 500K bonus credits on top of 21.5M. Both also unlock pay-as-you-go overflow so you're never hard-capped mid-cycle.
- **7-day no-questions-asked refund.** If you subscribe and decide it isn't working for your targets, you can request a full refund within 7 days.

## **Frequently Asked Questions**

**Is ScraperAPI free?**

Yes, in two ways. There's a recurring free plan with 1,000 API credits per month (5 concurrent connections, no credit card required), and a 7-day trial that bumps you up to 5,000 credits to test the service at larger scale. Credit multipliers mean your real capacity may be lower than the raw credit count — 1,000 credits against a normal blog gets you 1,000 requests; the same 1,000 credits against Amazon with rendering gets you about 66.

**Is ScraperAPI good for scraping Amazon?**

Yes — it's one of ScraperAPI's strongest use cases. The Amazon Structured Data Endpoint has a roughly 98% success rate in independent benchmarks and returns 18+ parsed fields (price, reviews, BSR, variants, images, seller info, etc.) across 21 regional marketplaces. The catch is cost: each Amazon request is 5 credits minimum, more with rendering or premium proxies, so costs add up at scale. For high-volume Amazon scraping, the Business plan or above is usually the right fit.

**Is ScraperAPI good for scraping Google?**

Yes, with caveats. Google SERP requests cost 25 credits each — the highest base multiplier along with LinkedIn. The Google Structured Data Endpoint returns organic results, ads, featured snippets, People Also Ask, and related questions. Independent benchmarks have noted that ScraperAPI had the lowest Google success rate among major providers in one 2025 Proxyway test (around 81.7%), so it's worth testing on your specific queries during the trial before committing.

**What happens if I run out of credits mid-month?**

On Hobby, Startup, and Business, you're cut off until the next billing period or you upgrade to a higher tier. On Scaling, Professional, Advanced, and Enterprise, pay-as-you-go overflow kicks in at a fixed rate so you can keep scraping without interruption.

**Can ScraperAPI scrape sites that require login?**

No. ScraperAPI supports session persistence via the `session_number` parameter (same IP across multiple requests), but it explicitly forbids scraping data behind login walls. It cannot handle form filling, two-factor authentication, or complex auth flows.

**Can ScraperAPI handle Cloudflare, Datadome, and PerimeterX?**

Partially. ScraperAPI automatically detects and bypasses these anti-bot systems, but each bypass adds 10 credits per request on top of the base cost. For sites with the most aggressive anti-bot systems, success rates may still be inconsistent — pair ScraperAPI with additional techniques or use a provider like Bright Data with Web Unlocker if you need maximum success rates on heavily protected targets.

**Do unused credits roll over to the next month?**

No. Your credit balance resets at each renewal. Match your plan size to your actual monthly usage rather than overbuying.

**Is there a refund policy?**

Yes — ScraperAPI offers a 7-day, no-questions-asked refund if you're not satisfied with the service.

## **The Bottom Line: Is ScraperAPI Good?**

Here's where I landed after all the research:

**ScraperAPI is good — for the right user.** If you're a developer or technical team with working scraper code, scraping mainstream targets (Amazon, Google, Walmart, Zillow, Etsy, Indeed) at moderate volume, and you already have infrastructure for storage and scheduling, ScraperAPI is one of the most reliable and cost-effective proxy rendering APIs on the market. The documentation is genuinely excellent, the integration is genuinely simple, and the structured data endpoints save real development time on supported sites.

**It is not good for everyone.** If you're a non-technical user who needs structured data without writing code, you're in the wrong category — a no-code browser-based tool will get you there faster and cheaper. If your targets include Instagram, Twitter/X, Booking.com, or any login-required site, ScraperAPI simply won't work. If you need global geolocation on a budget, the $299/month Business plan requirement is a hard jump. And if you don't understand the credit multiplier system before you start, you will overspend — full stop.

The cleanest way to find out whether ScraperAPI is good for your specific workload is to test it. Sign up for the free trial, point it at your real targets, watch your credit consumption in the dashboard, and run your own numbers through the multiplier table before deciding anything. Five thousand credits, no credit card, seven days — that's enough to answer the question for yourself.

👉 [Start your free ScraperAPI trial — 5,000 credits, no credit card required](https://dashboard.scraperapi.com/signup?fp_ref=coupons)

👉 [Compare all plans and current pricing on the official pricing page](https://www.scraperapi.com/pricing/?fp_ref=coupons)
