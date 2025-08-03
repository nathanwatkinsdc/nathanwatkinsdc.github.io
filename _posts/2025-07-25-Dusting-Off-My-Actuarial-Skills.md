---
layout: default
title: "Dusting Off My Actuarial Skills"
date: 2025-07-25
thumbnail: /assets/images/actuarial.png
description: A rough actuarial analysis of my friend's pretty awesome job options.
---

# 🥼 Doctors make a good living
My pathologist friend recently found himself choosing between two *very* competitive compensation offers in Florida. He told me he had a hunch I would know how to compare the two packages and asked for my help.

# 📍Assumptions: what both offers have in common

Here are the assumptions and parameters that apply to both jobs:
- Male white-collar professional, current age 42
- No state income tax, current tax brackets
- Maxed-out 401k with 8% employer match
- Saving 50% of post-tax income in brokerage account with an assumed 7% annual return

# 🚪Door 1: buy into a partnership in Tampa

Here are the assumptions and parameters for the job in Tampa:
- Year 0: pay $700k upfront to buy into the partnership track
- Years 1-4: annual income of $400k
- Year 4: become a partner
- Years 4-23: annual income of $850k/year
- At age 65: $700k lump sum return (balloon payment)

Immediately we can make some observations about the Tampa offer. Compensation for the first 4 years resembles a 4-year immediate annuity, and compensation after that resembles a deferred annuity before a lump sum return of the balloon payment at the end of the deferral term. My friend was right about me being able to help - this is starting to feel like an actuarial exam!

# 🚪Door 2: earn more sooner in Jacksonville
And here are the assumptions for the job in Jacksonville:
- Years 1-23: $600k/year
- At age 65: $200k/year pension

Compensation for this option is simpler: higher pay from the start with a pension on the tail end. I confirmed with my friend that the pension was based on a benefit formula that worked out to about $200k/year based on service as of his retirement age 65. He didn’t know more about the plan, so I just decided to keep using $200k as a rough estimate of the benefit amount and keep going with the analysis, assuming there would be COLAs but not letting the nitty-gritty details get in the way of the quick-and-dirty analysis my friend was asking me to do for him.

# 💡Seeing the light: this is an elegant problem
As it turns out, this problem is very elegant and could even make a fine actuarial exam problem. The advantage of taking the Tampa offer, if there is one, is the present value of $250k for 19 years (the difference between $850k and $600k) minus the cost of buying into the partnership. The advantage of the Jacksonville offeris the present value of the extra $200k earned over the first four years as well as the extra $200k earned over all the retirement years. 

Note that we could calculate all these present values as annuities with biweekly payments, but that's not necessary so long as we're consistent. These are just estimates after all. Let's run some numbers, using 7% as our discount rate and the RP-2014 White Collar Male Mortality Table as our mortality table.

The difference between the two offers can be represented as: **🧮 Present Value of Difference =** 

$$
\text{Tampa Advantage} = \text{PV of } 250\text{k for 19 years starting in year 5}
$$

$$
\text{Jacksonville Advantage} = \text{PV of } 200\text{k for 4 years} + \text{PV of } 200\text{k for life starting at 65},
$$

where

- \\(T\\) = Present value of 19-year deferred annuity of $250k
- \\(J₁\\) = PV of 4-year annuity of $200k (years 1–4)
- \\(J₂\\) = PV of life annuity starting at 65 of $200k
  
so that

$$
\text{Net Value of Tampa over Jacksonville} = T - (J₁ + J₂).
$$

As a result, under the assumptions we've made, it looks like Tampa better offer financially speaking, presenting a financial advantage of about $580k vs. the Jacksonville offer:

| Item                                                                                      | Value      |
| ----------------------------------------------------------------------------------------- | ---------- |
| Adjusted Tampa Advantage (PV of $250k for 19 years + $700k returned at 65 – $700k buy-in) | $1,807,237 |
| Jacksonville Advantage (PV of $200k for 4 years + $200k/year for life starting at 65)     | $1,226,917 |
| Adjusted Net Present Value (Tampa – Jacksonville)                                         | $580,320   |

It's worth noting that different assumptions will produce different results. Most importantly, a different discount rate assumption will have a significant impact on the analysis.
