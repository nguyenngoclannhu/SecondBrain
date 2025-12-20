# Why Healthcare AI Is 20 Years Behind

![rw-book-cover](https://substackcdn.com/icons/substack/apple-touch-icon-1024x1024.png)

## Metadata
- Author: [[Sergei from AI Health Uncut]]
- Full Title: Why Healthcare AI Is 20 Years Behind
- Category: #articles
- Summary: The author argues healthcare AI is far behind because incentives, regulators, and incumbents block real innovation. Venture capitalism and sloppy startups have worsened the problem, creating “AI tourists” instead of useful tools. True progress needs better data curation, clinical expertise, and aligned business models.
- URL: mailto:reader-forwarded-email/0f4b514ff499763b51cfa913c2a26821

## Full Document
[![](https://substackcdn.com/image/fetch/$s_!6va3!,w_1100,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ffe418031-7dbb-49a1-a053-002cf63b15af_2488x587.png)](https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9zZXJnZWlhaS5zdWJzdGFjay5jb20vcC93aHktaGVhbHRoY2FyZS1haS1pcy0yMC15ZWFycy1iZWhpbmQ_dXRtX2NhbXBhaWduPWVtYWlsLWhhbGYtcG9zdCZyPTZxNmVnbCZ0b2tlbj1leUoxYzJWeVgybGtJam8wTURZM05qVTNORGtzSW5CdmMzUmZhV1FpT2pFM09USTBNRFUyTWl3aWFXRjBJam94TnpZek5qWTJOVFF5TENKbGVIQWlPakUzTmpZeU5UZzFORElzSW1semN5STZJbkIxWWkweE9UQTFNakkySWl3aWMzVmlJam9pY0c5emRDMXlaV0ZqZEdsdmJpSjkuNVY0Nk4zV1pVQWRPUGVNYVBpUUhzT2ZzV3U0X3ZFNGtiZmh6eXczci15MCIsInAiOjE3OTI0MDU2MiwicyI6MTkwNTIyNiwiZiI6dHJ1ZSwidSI6NDA2NzY1NzQ5LCJpYXQiOjE3NjM2NjY1NDIsImV4cCI6MjA3OTI0MjU0MiwiaXNzIjoicHViLTAiLCJzdWIiOiJsaW5rLXJlZGlyZWN0In0.wYyRyyIeV9ba93TXTl8lJeRfYquXiNPxWwo4taR5Wj4?)

##### 100+ carefully crafted slides, as a thank-you to my dedicated paid subscribers and amazing Founding Members.

[![](https://substackcdn.com/image/fetch/$s_!iWi5!,w_1100,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4a0ac2c4-a772-46e7-831c-cfe3abaa73b2_2880x1620.png)](https://substack.com/redirect/714310ff-58c9-4465-976a-b2df016bcb03?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g)***Welcome to AI Health Uncut, a brutally honest newsletter on AI, innovation, and the state of the healthcare market. If you’d like to sign up to receive issues over email, you can do so [here](https://substack.com/redirect/b9fc4cec-7a4b-4bd0-8f44-e917d6d73618?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g).***

I’ve been fortunate to be invited to speak at quite a few healthcare AI events this year. Along the way, I’ve built 100+ carefully crafted slides. I’ve used parts of them to drive home some of my strongest points during recent talks, including the past two weeks at [the Health AI Summit in Albuquerque, New Mexico](https://substack.com/redirect/f6ae7cb0-e946-48c2-ae41-4fb1deba1c9a?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g) and at [Health2Tech in Vilnius, Lithuania](https://substack.com/redirect/065f5dc4-7316-4977-b17e-70448705444b?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g).

Not a single soul has seen all of my slides yet.

Today I want to offer a small gift to my paid subscribers and especially to my Founding Members for their loyalty and support. I’m sharing all 100+ slides. (Well, 141 to be exact. 😉) Thank you for backing my mission to expose bad actors in health tech and healthcare AI, to dissect AI models and AI products in healthcare, and to ultimately make healthcare better for all of us.

But first, if you’ve been following my healthcare fraud investigations, including my three-part deep dive into **Hippocratic AI** — [here](https://substack.com/redirect/e277d9e9-8621-4253-a9c7-ad48b1fa578c?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g), [here](https://substack.com/redirect/ef49c38e-d953-4698-a8bc-ae4c1d670ba5?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g), and [here](https://substack.com/redirect/1c429044-dc4e-4dd0-bfbb-ba5a6df625ee?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g) — you already know that much of my work comes from sources “behind the enemy lines.” These are the brave men and women inside these organizations who refuse to stay silent when they see things that are wrong, unethical, or outright illegal. They reach out to me because mainstream outlets either won’t challenge their own sponsors. Or hide behind the excuse of “not enough evidence.” Or simply don’t give a sh\*t.

So **I’m reaching out to all of you to help shine a light on two more organizations**:

* **Commure** (yet another shady Hemant Taneja’s creation)
* **Mayo Clinic** (a massive institution where, yes, some things look good, but plenty does not)

I believe I already have enough to publish some deeply alarming pieces on both. Still, if you know any stories or insights, or can introduce me to people who do, about what’s happening inside these organizations — illegal, unethical, or, on the flip side, constructive and positive — please don’t stay silent.

*If you want to share, everything remains strictly confidential. I’ve been doing these investigations for almost three years. I would never reveal my sources. Not to the FBI. Not to the DOJ. Not to anyone.*

[![Cover Image for Health2Tech NYC, December 4, 2025](https://substackcdn.com/image/fetch/$s_!0QAQ!,w_400,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F24c310c2-d73c-43b5-83b3-c238e417556e_800x800.jpeg "Cover Image for Health2Tech NYC, December 4, 2025")](https://substack.com/redirect/e1ce3169-6e19-4d1b-849c-a1b2d12950d7?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g)Also, if you are in NYC on Thursday, December 4, don’t be a stranger. **[Register](https://substack.com/redirect/a3949700-0dbb-4f88-97e9-bea2c04eeb2d?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g)** and say hi at Health2Tech, where I’ll be moderating a panel on innovation in healthcare AI, real tech adoption in clinical workflows, and what healthcare providers actually expect from AI.

OK, back to my slides… If you joined any of my lectures this year, you know I promised to share my slides with you. Today, I’m making them available exclusively to my paid Substack subscribers and Founding Members through this post. I’m putting the slides behind a paywall to keep them out of reach of LLMs and search engines, especially given how AI companies have been shamelessly stealing copyrighted material.

These 100+ slides represent months and months of meticulous research. Enjoy.

And a reminder. If you can’t afford this article — maybe you’re a student or between jobs — just reach out. That’s exactly why I created the AI Health Uncut Founding Member Club. Thanks to generous support from the people in that exclusive group of (currently) 19, I’m able to offer access to anyone who needs it.

*If you’d like to become a Founding Member of the AI Health Uncut community, you can join through **[this link](https://substack.com/redirect/e182aa7e-03a9-41a8-b271-09c83d48b4eb?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g)**. You’ll be making a real impact and helping me keep pushing for better outcomes in healthcare through AI, technology, policy, and beyond.*

Here are the titles of all 100+ slides (the real number is 141 😉):

> **1. Title Slide: Paging Dr. Watson: Why Healthcare AI Is 20 Years Behind**

> **2. Disclaimer: Cite My Work, Please!**

> **3. Reach Out to Me on Social Media**

> **4. WellAI, My Startup (Merged with Chart2Chart)**

> **5. AI Health Uncut, My Substack Newsletter**

> **6. My Dataset of 132 Digital Health Companies**

> **7. I Critique Flawed AI Models in Healthcare…**

> **8. …Especially Those Embarrassingly Hyped by Mass Media**

> **9. I Investigate Healthcare Fraud**

> **10. And of Course, I Expose Bad Actors in Digital Health**

> **11. Selected List of Companies I’ve Investigated**

> **12. I Also Cohost the “Digital Health Inside Out”  
> Podcast With Alex Koshykov**

> **13. I’m Also on the Advisory Board of PeriOptima.ai**

> **14. I’m Also on the Board of Health2Tech, a Nonprofit That Organizes Health Tech Events Around the World**

> **15. Health2Tech Branches Around the World**

> **16. Google’s Transformers (2017) and Covid (2020) Had a Far Greater Impact on AI Adoption Outside of Healthcare**

> **17. But Maybe Things Are Finally Turning Around for AI Adoption in Healthcare…**

> **18. Even Though on the Ground It Sure Feels Like We’re Far Behind in Medicine**

> **19. The Healthcare AI Paradox**

> **20. Treating the Sick Is Profitable. Keeping People Healthy Isn’t.**

> **21. Healthcare Innovation Is Being Killed As Problems Run Rampant**

> **22. Why Does It Take Just a Few Lines of Code to Access the Most Advanced AI Model Ever Built,…**

> **23. …While the Entire Healthtech Industry Has Spent Over a Decade Failing to Reliably Access Patient Records?**

> **24. American Healthcare Is Complex — But It Doesn’t Have to Be**

> **25. American Healthcare is Also Big. It is the #1 Employer and the #2 Contributor to GDP After Technology.**

> **26. Two Primary Barriers to Healthcare Innovation**

> **27. The Margin and the Mission Must Align**

> **28. What Makes Innovating in Healthcare Hard?**

> **29. Customers Make Innovating Hard**

> **30. Incumbents Make Innovating** ***Really*** **Hard — The Market Is Highly Concentrated**

> **31. Incumbents Make Innovating** ***Really*** **Hard — Their Size Is Massive**

> **32. Incumbents Make Innovating** ***Really*** **Hard — Every Company Is A Healthcare Company These Days**

> **33. Incumbents Make Innovating** ***Really*** **Hard — They Hate Innovation**

> **34. Incumbents Are Swallowing the Healthcare System Piece by Piece**

> **35. Epic Has No Real Incentive to Innovate**

> **36. Regulators Make Innovating Hard — Regulators Capture Rules Healthcare**

> **37. Regulators Make Innovating Hard — Policy, Not Innovation, Drives American Healthcare**

> **38. EU’s AI Laws Are Even Tougher**

> **39. History of Artificial Intelligence**

> **40. Warner V. Slack, MD, Pioneer of Patient-Centered Computing & Medical Informatics**

> **41. Eliza, the First Medical AI Agent**

> **42. Why Machines Don’t Need to Think Like Humans**

> **43. These 13 Influential Voices and 9 AI Companies Think AI Will Replace Doctors**

> **44. While It’s Fashionable to Claim That AI is More Accurate Than Doctors,…**

> **45. ...Most AI Accuracy Claims in Healthcare Have Been Debunked!**

> **46. Let’s be honest, AI still ain’t ready for healthcare yet… A Story of Pruning Shears.**

> **47. This Banana Was Diagnosed With Melanoma by 3 Out of 3 Leading AI Dermatology Image-identification Apps**

> **48. LLMs Weren’t Built for Medical Diagnostics. Using Them as Such Could Be Dangerous.**

> **49. The Cough That Broke 8 LLMs**

> **50. AI Hasn’t Solved Healthcare’s Problems Because the System of Incentives Is Broken**

> **51. Geoff Hinton’s 2016 Claim That AI Would Replace Radiologists “Within Five Years” Aged Poorly. There Are ~40,000 Radiologists in 2025, Up From ~34,500 in 2016.**

> **52. Why Do AI Predictions for Healthcare So Often Fail? Because They’re Usually Made By People Who Are Nowhere Near Healthcare.**

> **53. As With Any New Invention, Physicians Won’t Disappear. They’ll Learn AI.**

> **54. AI Isn’t Replacing Clinicians. It’s Changing What “Being a Clinician” Means.**

> **55. If Anyone Gets Replaced by AI, It’s the Useless Consultants 😄** 

> **56. Fast Forward to 2025: OpenEvidence Takes the Stage**

> **57. OpenEvidence: Healthcare’s Most Data-Intensive Scientific Engine**

> **58. Fast Forward to 2025: OpenAI Develops AI Consult**

> **59. OpenAI’s AI Consult: The Man-Made Babysitter for LLMs**

> **60. OpenAI’s AI Consult: A Human + AI Safety Net, Not a Standalone AI**

> **61. Meredith Whittaker: Brutal Truth on LLMs, Tech Power & Privacy**

> **62. Most Startups Fail**

> **63. We All Know About High Startup Failure Rates**

> **64. Not Failing Means You’re Not Working Hard Enough**

> **65. You Miss 100% of the Shots You Don’t Take**

> **66. Tech-enabled Healthcare Services Margins Falls Somewhere Between Traditional Healthcare and Traditional Software**

> **67. Who Pays For Digital Health? In Theory, Multiple Parties…**

> **68. In Reality, Most Startups Sell to Providers**

> **69. What Is the Business Model of Digital Health?**

> **70. The Importance of Aligning the Margin and the Mission**

> **71. Startups Are Risky, Therefore VC Is Risky**

> **72. Non-VC-Backed Startups Either Die Quickly or Eventually Beat VC-Backed Ones**

> **73. VCs Have Caused Billions in Losses for U.S.-Listed Digital Health Companies Over the Past 5 Years**

> **74. The Story Remains Consistent Over Time: VCs Continue to Pick Sh\*tty Digital Health Companies Year After Year**

> **75. Even If a Company Has Found a Sweet Spot, It May Not Want VC Funding**

> **76. Out of the Top 10 Most Successful Publicly Traded Digital Health Companies, Only Two Are VC-Backed**

> **77. Bankrupt Digital Health Companies Have Overwhelmingly Been Backed by VC and PE Firms**

> **78. The Magic of Venture Capital in Digital Health: The Great Disappearance Act**

> **79. VCs Are Playing Straight Into the Hands of Healthcare Monopolies by Eliminating Competition**

> **80. Averages Don’t Tell Sh\*t: While VCs Often Murder Digital Health Startups, Even Most Non-VC-Backed Startups Are Doomed to Die**

> **81. VCs Can’t Pick Winners Anymore. Instead, They’re Picking Mediocre Startups They Plan to Unload Onto the Next Sucker.**

> **82. VC Underperformed Equities and 60/40 in Every Possible Period Over the Past 25 Years!**

> **83. VC and PE Returns Have Been Disastrous. And Nobody’s Even Mentioning Risk-Adjusted Returns—Unlike Stocks, You Can’t Just Hit a Button and Pull Your VC Money Out.**

> **84. VC Distributions Are Hovering Near Their Lowest Levels in Decades**

> **85. Morgan Stanley: VC Returns Plummet to 28-Year Low**

> **86. If You’re an LP, You Now Have to Wait Over 10 Years Just to Get Your Money Back!**

> **87. “Traditional” VC Playbook: The Infinite Loop of Fundraising**

> **88. VC Funding Is Killing the Startup Ecosystem**

> **89. “VC Pump & Dump”: Valuation Cycle of a Typical Digital Health Startup**

> **90. Increasing Allocations to VC and PE at the Expense of Public Markets Has Been a Disastrous Move for Pension Funds**

> **91. CalPERS Lost 24.8% on Their VC Positions in 2022. What Did They Do Next? They Didn’t Just Double Down. They Sextupled Down!**

> **92. Since 1997, VC Investors Have Invested More Money Than They Received Back From VC Funds**

> **93. “You Can’t Be Fired by Investing in General Catalyst”**

> **94. When You Can’t Pick Winners if Your Life Depended on It, What Do You Do? You Build an Empire, Because at That Point, 2% Is Bigger Than 20%.**

> **95. The Only Truthful Thing Hemant Taneja Has Ever Said**

> **96. What Good Is VC Diversification Without Liquidation?**

> **97. And of Course, VCs Also Pat Themselves on the Back by Sponsoring Fake Rankings**

> **98. The Healthcare VC Mafia Org Chart**

> **99. Digital Health’s Political Cartel Org Chart**

> **100. The Healthcare VC Mafia Rules**

> **101. Over Half of Late-Stage Deals Originate From VC Referrals. These Firms Leverage Their Elite Networks for Superior Deal Flow. And Yet, They Still Consistently Underperform in the Long Run.**

> **102. How Venture Capital Is Cannibalizing the Economy**

> **103. Digital Health Unicorns Have Disappeared—Because Mediocrity Trumps Innovation**

> **104. But Maybe 2025 Is the Turning Point?**

> **105. The IPO Party Is Over**

> **106. The VC Culture of Mediocrity and the Incumbents’ Suppression of Innovation Have Created an Industry Dominated by “AI Tourists” and “AI Wrappers”**

> **107. Is the Death of the AI Scribe Imminent?**

> **108. Not a Single AI Scribe Has FDA Approval. It’s the Wild Wild West of Medicine.**

> **109. I Haven’t Seen Any Real Innovations in Digital Health**

> **110. Primary Care Is in the Worst Shape Ever—and the Lack of Digital Health Innovation & Shrinking Reimbursement Rates (Despite Healthcare Inflation!) Ain’t Helping**

> **111. Sexism in Venture Capital: What Future Awaits My Daughters?**

> **112. 21-Factor Quantitative Dashboard for Health AI IPO Valuation**

> **113. 8 Digital Health Failure Patterns**

> **114. Toxic Culture Is Eating Digital Health for Breakfast**

> **115. Livongo: One of the Biggest Snake-Oil Deals in Financial Market History**

> **116. Why Teladoc’s Acquisition of Livongo Was Disastrous**

> **117. Theranos: One Drop of Lies, A Sea of Fraud**

> **118. Better Theranos? People Sure Have Short Memories.**

> **119. Hippocratic AI: $9/Hour “AI Nurses” and the Web of Lies**

> **120. Babylon Health: The Madoff of Digital Health**

> **121. Wall Street Analysts Were in Bed With Babylon’s Management**

> **122. “Stock Markets Are Either Too Optimistic or Too Negative, but Eventually, They Settle on the Right Value.” Babylon’s Value Has Settled at $0 Four Months Later…**

> **123. Olive AI: The Poster Child of “Champagne and Cocaine” Spending**

> **124. October 2021 Was Peak Olive: “Frisson by Olive” Fragrance and the Notorious “Olive Bus”**

> **125. Truepill: The Poster Child for VC Extortion**

> **126. Truepill’s Trajectory: From Founders’ Fantasy to VC Nightmare**

> **127. Truepill’s Founders’ Dilution via VC Extortion: An 8-Step Program From 100% Ownership to 0%**

> **128. Suki: Digital Health’s Poster Child for “AI Tourism”**

> **129. Suki: When There’s Zero Innovation, “Borrowing” Someone Else’s Tech Ain’t “Hard at All”**

> **130. 7 Digital Health Success Patterns**

> **131. Veeva Systems: The Secret to Success—Say No to VCs**

> **132. Doximity: Wall Street’s Pariah, Doctors’ Darling**

> **133. Startup Success Formula**

> **134. My Mission and Exploring Possible Solutions**

> **135. Staying Active on Policy Issues is Important**

> **136. Solutions to U.S. Healthcare Crisis**

> **137. Medical AI Success Depends Not on Raw Computational Power, But on Sophisticated Knowledge Curation and Conflict Resolution**

> **138. Multimodal AI for Next-Generation Healthcare**

> **139. A Rare Healthcare AI Success Story. Smartwatches That Actually Work for Atrial Fibrillation (AF) Detection.**

> **140. Another Healthcare AI Success Story: Digital Twin GPT (DT-GPT) — LLMs Forecasting Patient Health Trajectories.**

> **141. The Future of AI in Medicine...**

#### Continue reading this post for free in the Substack app

[Claim my free post](https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9zZXJnZWlhaS5zdWJzdGFjay5jb20vcC93aHktaGVhbHRoY2FyZS1haS1pcy0yMC15ZWFycy1iZWhpbmQ_dXRtX2NhbXBhaWduPWVtYWlsLXBvc3Qmcj02cTZlZ2wmdG9rZW49ZXlKMWMyVnlYMmxrSWpvME1EWTNOalUzTkRrc0luQnZjM1JmYVdRaU9qRTNPVEkwTURVMk1pd2lhV0YwSWpveE56WXpOalkyTlRReUxDSmxlSEFpT2pFM05qWXlOVGcxTkRJc0ltbHpjeUk2SW5CMVlpMHhPVEExTWpJMklpd2ljM1ZpSWpvaWNHOXpkQzF5WldGamRHbHZiaUo5LjVWNDZOM1daVUFkT1BlTWFQaVFIc09mc1d1NF92RTRrYmZoenl3M3IteTAiLCJwIjoxNzkyNDA1NjIsInMiOjE5MDUyMjYsImYiOnRydWUsInUiOjQwNjc2NTc0OSwiaWF0IjoxNzYzNjY2NTQyLCJleHAiOjIwNzkyNDI1NDIsImlzcyI6InB1Yi0wIiwic3ViIjoibGluay1yZWRpcmVjdCJ9.A-VGF8vvSbeOaRGKLhQljpc1Y7FRMqInrtoxSuW4Tz4?&launch_post_unlock_offer=true)

[Or upgrade your subscription. **Upgrade to paid**](https://substack.com/redirect/0f714936-8a1a-4704-ada4-3c8209ff8373?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI_zv_M4N2A50pyRXMoP1g)

[View in app](https://substack.com/app-link/post?publication_id=1905226&post_id=179240562&utm_source=post-email-title&utm_campaign=email-post-title&isFreemail=true&r=6q6egl&token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3OTI0MDU2MiwiaWF0IjoxNzYzNjY2NTQyLCJleHAiOjE3NjYyNTg1NDIsImlzcyI6InB1Yi0xOTA1MjI2Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.5V46N3WZUAdOPeMaPiQHsOfsWu4_vE4kbfhzyw3r-y0)

<div>
<img alt="" border="0" height="1" src="https://eotrx.substackcdn.com/open?token=eyJtIjoiPDIwMjUxMTIwMTkyMjA3LjMuNjM4ODVjZmM5OTNhNmE1YUBtZy1kMC5zdWJzdGFjay5jb20-IiwidSI6NDA2NzY1NzQ5LCJyIjoiaW1lb2J2bmtAbGlicmFyeS5yZWFkd2lzZS5pbyIsImQiOiJtZy1kMC5zdWJzdGFjay5jb20iLCJwIjoxNzkyNDA1NjIsInQiOiJuZXdzbGV0dGVyIiwiYSI6Im9ubHlfcGFpZCIsInMiOjE5MDUyMjYsImMiOiJwb3N0IiwiZiI6dHJ1ZSwicG9zaXRpb24iOiJ0b3AiLCJpYXQiOjE3NjM2NjY1NDIsImV4cCI6MTc2NjI1ODU0MiwiaXNzIjoicHViLTAiLCJzdWIiOiJlbyJ9.hfXJqiE8iqDA3n291aByyFPRbtovlZwqHz9WG7ihfQQ" style="height:1px !important;width:1px !important;border-width:0 !important;margin-top:0 !important;margin-bottom:0 !important;margin-right:0 !important;margin-left:0 !important;padding-top:0 !important;padding-bottom:0 !important;padding-right:0 !important;padding-left:0 !important;" width="1"/><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="100%"><tbody>
<tr>
<td></td>
<td width="550"></td>
<td></td>
</tr>
<tr>
<td></td>
<td align="left" width="550"><div style="font-size: 16px;line-height: 26px;max-width: 550px;width: 100%;margin: 0 auto;overflow-wrap: break-word;">
<table border="0" cellpadding="0" cellspacing="0" role="presentation" width="100%"><tbody><tr><td align="right" style="height:20px;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><span style="font-family: SF Pro Text, -apple-system, system-ui, BlinkMacSystemFont, Inter, Segoe UI, Roboto, Helvetica, Arial, sans-serif, Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol;font-size: 13px;color: unset;list-style: none;text-decoration: unset;margin: 0;"><div style="list-style: none;color: unset;text-align: right;font-size: 12px;line-height: 16px;text-decoration: unset;margin: 0;"><span style="list-style: none;color: unset;text-decoration: unset;margin: 0;" translated="">Forwarded this email? <a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9zZXJnZWlhaS5zdWJzdGFjay5jb20vc3Vic2NyaWJlP3V0bV9zb3VyY2U9ZW1haWwmdXRtX2NhbXBhaWduPWVtYWlsLXN1YnNjcmliZSZyPTZxNmVnbCZuZXh0PWh0dHBzJTNBJTJGJTJGc2VyZ2VpYWkuc3Vic3RhY2suY29tJTJGcCUyRndoeS1oZWFsdGhjYXJlLWFpLWlzLTIwLXllYXJzLWJlaGluZCIsInAiOjE3OTI0MDU2MiwicyI6MTkwNTIyNiwiZiI6dHJ1ZSwidSI6NDA2NzY1NzQ5LCJpYXQiOjE3NjM2NjY1NDIsImV4cCI6MjA3OTI0MjU0MiwiaXNzIjoicHViLTAiLCJzdWIiOiJsaW5rLXJlZGlyZWN0In0.GRzYvfkVuVUmwBapEE7bnMBtnOh2tn3RpqHgN45q-RQ?" style="list-style: none;color: unset;text-decoration: unset;margin: 0;-webkit-text-decoration-line: underline;text-decoration-line: underline;">Subscribe here</a> for more</span></div></span></td></tr></tbody></table></td></tr></tbody></table>
<table role="presentation" style="border-spacing: 0;padding: 16px 0 32px;"><tbody><tr><td align="center" style="text-align: center;padding: 0;"><a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9zZXJnZWlhaS5zdWJzdGFjay5jb20vcC93aHktaGVhbHRoY2FyZS1haS1pcy0yMC15ZWFycy1iZWhpbmQ\_dXRtX2NhbXBhaWduPWVtYWlsLWhhbGYtcG9zdCZyPTZxNmVnbCZ0b2tlbj1leUoxYzJWeVgybGtJam8wTURZM05qVTNORGtzSW5CdmMzUmZhV1FpT2pFM09USTBNRFUyTWl3aWFXRjBJam94TnpZek5qWTJOVFF5TENKbGVIQWlPakUzTmpZeU5UZzFORElzSW1semN5STZJbkIxWWkweE9UQTFNakkySWl3aWMzVmlJam9pY0c5emRDMXlaV0ZqZEdsdmJpSjkuNVY0Nk4zV1pVQWRPUGVNYVBpUUhzT2ZzV3U0X3ZFNGtiZmh6eXczci15MCIsInAiOjE3OTI0MDU2MiwicyI6MTkwNTIyNiwiZiI6dHJ1ZSwidSI6NDA2NzY1NzQ5LCJpYXQiOjE3NjM2NjY1NDIsImV4cCI6MjA3OTI0MjU0MiwiaXNzIjoicHViLTAiLCJzdWIiOiJsaW5rLXJlZGlyZWN0In0.wYyRyyIeV9ba93TXTl8lJeRfYquXiNPxWwo4taR5Wj4?"><img height="130" role="presentation" src="https://substackcdn.com/image/fetch/%24s\_!6va3!,w\_1100,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Ffe418031-7dbb-49a1-a053-002cf63b15af\_2488x587.png" style="border: none !important;vertical-align: middle;max-width: 550px;display: block;margin: 0 auto;height: auto;width: 100%;" width="550"/></a></td></tr></tbody></table>
<div dir="auto" style="--image-offset-margin: -120px;padding: 32px 0 0 0;font-size: 16px;line-height: 26px;"><div aria-label="Post header" role="region" style="font-size: 16px;line-height: 26px;">
<h1 dir="auto" style="direction: auto;text-align: start;unicode-bidi: isolate;color: rgb(54,55,55);font-family: 'SF Pro Display',-apple-system-headline,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: bold;-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;margin: 0;line-height: 36px;font-size: 32px;"><a href="https://substack.com/app-link/post?publication\_id=1905226&amp;post\_id=179240562&amp;utm\_source=post-email-title&amp;utm\_campaign=email-post-title&amp;isFreemail=true&amp;r=6q6egl&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3OTI0MDU2MiwiaWF0IjoxNzYzNjY2NTQyLCJleHAiOjE3NjYyNTg1NDIsImlzcyI6InB1Yi0xOTA1MjI2Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.5V46N3WZUAdOPeMaPiQHsOfsWu4\_vE4kbfhzyw3r-y0" style="color: rgb(54,55,55);text-decoration: none;">Why Healthcare AI Is 20 Years Behind</a></h1>
<h3 dir="auto" style="direction: auto;text-align: start;unicode-bidi: isolate;font-family: 'SF Pro Display',-apple-system-headline,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: normal;-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;margin: 4px 0 0;color: #777777;line-height: 24px;font-size: 18px;margin-top: 12px;">100+ carefully crafted slides, as a thank-you to my dedicated paid subscribers and amazing Founding Members.</h3>
<table border="0" cellpadding="0" cellspacing="0" role="presentation" style="margin: 1em 0;height: 20px;align-items: center;" width="100%"><tbody><tr>
<td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><div style="list-style: none;font-size: 11px;line-height: 20px;text-decoration: unset;color: rgb(54,55,55);margin: 0;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;"><a href="https://substack.com/@sergeiai" style="list-style: none;color: rgb(54,55,55);margin: 0;font-size: 11px;line-height: 20px;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;text-decoration: none">Sergei Polevikov</a></div></td></tr></tbody></table></td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><div style="list-style: none;font-size: 11px;line-height: 20px;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;"><time datetime="2025-11-20T19:22:15.102Z">Nov 20</time></div></td>
<td style="min-width: 4px" width="4"></td>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><div style="list-style: none;font-size: 11px;line-height: 20px;text-decoration: unset;color: rgb(119,119,119);margin: 0;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;">∙</div></td>
<td style="min-width: 4px" width="4"></td>
<td style="vertical-align:middle;"><div style="list-style: none;font-size: 11px;line-height: 20px;text-decoration: unset;color: rgb(94,73,217);margin: 0;font-family: 'SF Compact',-apple-system,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';font-weight: 500;text-transform: uppercase;letter-spacing: .2px;" translated="">Preview</div></td>
</tr></tbody></table></td>
</tr></tbody></table></td></tr>
</tbody></table></td>
<td align="right"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><a href="https://substack.com/@sergeiai"><img height="40" src="https://substackcdn.com/image/fetch/%24s\_!slE2!,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc91ada74-8686-4e3f-a6e8-28e218393ec5\_530x532.jpeg" style="box-sizing: border-box;border-radius: 500000px;max-width: 550px;border: none;vertical-align: middle;width: 40px;height: 40px;min-width: 40px;min-height: 40px;object-fit: cover;margin: 0px;display: inline" width="40"/></a></td></tr></tbody></table></td>
</tr></tbody></table>
<table border="0" cellpadding="0" cellspacing="0" role="presentation" style="border-top: 1px solid rgb(0,0,0,.1);border-bottom: 1px solid rgb(0,0,0,.1);min-width: 100%;" width="100%"><tbody>
<tr height="16"><td height="16" style="font-size:0px;line-height:0;"> </td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="100%"><tbody><tr>
<td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="38"><tbody><tr><td align="center"><a href="https://substack.com/app-link/post?publication\_id=1905226&amp;post\_id=179240562&amp;utm\_source=substack&amp;isFreemail=true&amp;submitLike=true&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3OTI0MDU2MiwicmVhY3Rpb24iOiLinaQiLCJpYXQiOjE3NjM2NjY1NDIsImV4cCI6MTc2NjI1ODU0MiwiaXNzIjoicHViLTE5MDUyMjYiLCJzdWIiOiJyZWFjdGlvbiJ9.Rf1XeTsV7sRj9NUK\_oGp9MO7JNrpERKVYMjBjnJMJ5U&amp;utm\_medium=email&amp;utm\_campaign=email-reaction&amp;r=6q6egl" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 1;padding: 9px 0;text-decoration: none;color: rgb(119,119,119);min-width: 38px;box-sizing: border-box;width: 38px"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!PeVs!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="border: none;vertical-align: middle;max-width: 18px" width="18"/></a></td></tr></tbody></table></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="38"><tbody><tr><td align="center"><a href="https://substack.com/app-link/post?publication\_id=1905226&amp;post\_id=179240562&amp;utm\_source=substack&amp;utm\_medium=email&amp;isFreemail=true&amp;comments=true&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3OTI0MDU2MiwiaWF0IjoxNzYzNjY2NTQyLCJleHAiOjE3NjYyNTg1NDIsImlzcyI6InB1Yi0xOTA1MjI2Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.5V46N3WZUAdOPeMaPiQHsOfsWu4\_vE4kbfhzyw3r-y0&amp;r=6q6egl&amp;utm\_campaign=email-half-magic-comments&amp;action=post-comment&amp;utm\_source=substack&amp;utm\_medium=email" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 1;padding: 9px 0;text-decoration: none;color: rgb(119,119,119);min-width: 38px;box-sizing: border-box;width: 38px"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!x1tS!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideComments%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="border: none;vertical-align: middle;max-width: 18px" width="18"/></a></td></tr></tbody></table></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="38"><tbody><tr><td align="center"><a href="https://substack.com/app-link/post?publication\_id=1905226&amp;post\_id=179240562&amp;utm\_source=substack&amp;utm\_medium=email&amp;utm\_content=share&amp;utm\_campaign=email-share&amp;action=share&amp;triggerShare=true&amp;isFreemail=true&amp;r=6q6egl&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3OTI0MDU2MiwiaWF0IjoxNzYzNjY2NTQyLCJleHAiOjE3NjYyNTg1NDIsImlzcyI6InB1Yi0xOTA1MjI2Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.5V46N3WZUAdOPeMaPiQHsOfsWu4\_vE4kbfhzyw3r-y0" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 1;padding: 9px 0;text-decoration: none;color: rgb(119,119,119);min-width: 38px;box-sizing: border-box;width: 38px"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!\_L14!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideShare2%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="border: none;vertical-align: middle;max-width: 18px" width="18"/></a></td></tr></tbody></table></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="38"><tbody><tr><td align="center"><a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9vcGVuLnN1YnN0YWNrLmNvbS9wdWIvc2VyZ2VpYWkvcC93aHktaGVhbHRoY2FyZS1haS1pcy0yMC15ZWFycy1iZWhpbmQ\_dXRtX3NvdXJjZT1zdWJzdGFjayZ1dG1fbWVkaXVtPWVtYWlsJnV0bV9jYW1wYWlnbj1lbWFpbC1yZXN0YWNrLWNvbW1lbnQmYWN0aW9uPXJlc3RhY2stY29tbWVudCZyPTZxNmVnbCZ0b2tlbj1leUoxYzJWeVgybGtJam8wTURZM05qVTNORGtzSW5CdmMzUmZhV1FpT2pFM09USTBNRFUyTWl3aWFXRjBJam94TnpZek5qWTJOVFF5TENKbGVIQWlPakUzTmpZeU5UZzFORElzSW1semN5STZJbkIxWWkweE9UQTFNakkySWl3aWMzVmlJam9pY0c5emRDMXlaV0ZqZEdsdmJpSjkuNVY0Nk4zV1pVQWRPUGVNYVBpUUhzT2ZzV3U0X3ZFNGtiZmh6eXczci15MCIsInAiOjE3OTI0MDU2MiwicyI6MTkwNTIyNiwiZiI6dHJ1ZSwidSI6NDA2NzY1NzQ5LCJpYXQiOjE3NjM2NjY1NDIsImV4cCI6MjA3OTI0MjU0MiwiaXNzIjoicHViLTAiLCJzdWIiOiJsaW5rLXJlZGlyZWN0In0.lDXwxUqUonDkNHTXnCiWQ3JoeGwHJiJGqLfJMV0FkeA?&amp;utm\_source=substack&amp;utm\_medium=email" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 1;padding: 9px 0;text-decoration: none;color: rgb(119,119,119);min-width: 38px;box-sizing: border-box;width: 38px"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!5EGt!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="border: none;vertical-align: middle;max-width: 18px" width="18"/></a></td></tr></tbody></table></td>
</tr></tbody></table></td>
<td align="right"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td align="center"><a href="https://open.substack.com/pub/sergeiai/p/why-healthcare-ai-is-20-years-behind?utm\_source=email&amp;redirect=app-store&amp;utm\_campaign=email-read-in-app" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 12px;padding: 9px 14px;text-decoration: none;color: rgb(119,119,119);"><div style="font-size: 16px;line-height: 26px;display: inline-block;vertical-align: middle;max-width: 0;min-height: 18px;"></div>
<span style="vertical-align: middle;margin-right: 4px">READ IN APP</span><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!ET-\_!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideArrowUpRight%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="min-width: 18px;min-height: 18px;border: none;vertical-align: middle;margin-right: 0;margin-left: 0;max-width: 18px" width="18"/></a></td></tr></tbody></table></td></tr></tbody></table></td>
</tr></tbody></table></td></tr>
<tr height="16"><td height="16" style="font-size:0px;line-height:0;"> </td></tr>
</tbody></table>
</div></div>
<div dir="auto" style="--image-offset-margin: -120px;padding: 32px 0 0 0;font-size: 16px;line-height: 26px;"><div dir="auto" style="text-align: initial;font-size: 16px;line-height: 26px;width: 100%;word-break: break-word;margin-bottom: 16px;">
<div style="font-size: 16px;line-height: 26px;margin: 32px auto;margin-top: 0;"><figure style="width: 100%;margin: 0 auto;"><table border="0" cellpadding="0" cellspacing="0" data-component-name="Image2ToDOMStatic" style="mso-padding-alt: 1em 0 1.6em;" width="100%"><tbody><tr>
<td style="text-align: center;"></td>
<td align="left" style="text-align: center;" width="1200"><a href="https://substack.com/redirect/714310ff-58c9-4465-976a-b2df016bcb03?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="position: relative;flex-direction: column;align-items: center;padding: 0;width: auto;height: auto;border: none;text-decoration: none;display: block;margin: 0;margin-top: 0;margin-bottom: 0;" target="\_blank"><img alt="" data-attrs='{"src":"https://substack-post-media.s3.amazonaws.com/public/images/4a0ac2c4-a772-46e7-831c-cfe3abaa73b2\_2880x1620.png","srcNoWatermark":null,"fullscreen":false,"imageSize":"large","height":819,"width":1456,"resizeWidth":1200,"bytes":2886311,"alt":null,"title":null,"type":"image/png","href":null,"belowTheFold":false,"topImage":true,"internalRedirect":"https://sergeiai.substack.com/i/179240562?img=https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4a0ac2c4-a772-46e7-831c-cfe3abaa73b2\_2880x1620.png","isProcessing":false,"align":"center","offset":false}' height="309.375" src="https://substackcdn.com/image/fetch/%24s\_!iWi5!,w\_1100,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F4a0ac2c4-a772-46e7-831c-cfe3abaa73b2\_2880x1620.png" style="border: none !important;vertical-align: middle;display: block;-ms-interpolation-mode: bicubic;height: auto;margin-bottom: 0;width: auto !important;max-width: 100% !important;margin: 0 auto;" width="550"/></a></td>
<td style="text-align: center;"></td>
</tr></tbody></table></figure></div>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><em><strong><span>Welcome to AI Health Uncut, a brutally honest newsletter on AI, innovation, and the state of the healthcare market. If you’d like to sign up to receive issues over email, you can do so </span><a href="https://substack.com/redirect/b9fc4cec-7a4b-4bd0-8f44-e917d6d73618?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: rgb(54,55,55);text-decoration: underline;">here</a><span>.</span></strong></em></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>I’ve been fortunate to be invited to speak at quite a few healthcare AI events this year. Along the way, I’ve built 100+ carefully crafted slides. I’ve used parts of them to drive home some of my strongest points during recent talks, including the past two weeks at </span><a href="https://substack.com/redirect/f6ae7cb0-e946-48c2-ae41-4fb1deba1c9a?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: rgb(54,55,55);text-decoration: underline;">the Health AI Summit in Albuquerque, New Mexico</a><span> and at </span><a href="https://substack.com/redirect/065f5dc4-7316-4977-b17e-70448705444b?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: rgb(54,55,55);text-decoration: underline;">Health2Tech in Vilnius, Lithuania</a><span>.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">Not a single soul has seen all of my slides yet.</p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">Today I want to offer a small gift to my paid subscribers and especially to my Founding Members for their loyalty and support. I’m sharing all 100+ slides. (Well, 141 to be exact. 😉) Thank you for backing my mission to expose bad actors in health tech and healthcare AI, to dissect AI models and AI products in healthcare, and to ultimately make healthcare better for all of us.</p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>But first, if you’ve been following my healthcare fraud investigations, including my three-part deep dive into </span><strong>Hippocratic AI</strong><span> — </span><a href="https://substack.com/redirect/e277d9e9-8621-4253-a9c7-ad48b1fa578c?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: rgb(54,55,55);text-decoration: underline;">here</a><span>, </span><a href="https://substack.com/redirect/ef49c38e-d953-4698-a8bc-ae4c1d670ba5?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: rgb(54,55,55);text-decoration: underline;">here</a><span>, and </span><a href="https://substack.com/redirect/1c429044-dc4e-4dd0-bfbb-ba5a6df625ee?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: rgb(54,55,55);text-decoration: underline;">here</a><span> — you already know that much of my work comes from sources “behind the enemy lines.” These are the brave men and women inside these organizations who refuse to stay silent when they see things that are wrong, unethical, or outright illegal. They reach out to me because mainstream outlets either won’t challenge their own sponsors. Or hide behind the excuse of “not enough evidence.” Or simply don’t give a sh\*t.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>So </span><strong>I’m reaching out to all of you to help shine a light on two more organizations</strong><span>:</span></p>
<ul style="margin-top: 0;padding: 0;">
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><strong>Commure</strong><span> (yet another shady Hemant Taneja’s creation)</span></p></li>
<li style="margin: 8px 0 0 32px;mso-special-format: bullet;"><p style="color: rgb(54,55,55);line-height: 26px;margin-bottom: 0;box-sizing: border-box;padding-left: 4px;font-size: 16px;margin: 0;"><strong>Mayo Clinic</strong><span> (a massive institution where, yes, some things look good, but plenty does not)</span></p></li>
</ul>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">I believe I already have enough to publish some deeply alarming pieces on both. Still, if you know any stories or insights, or can introduce me to people who do, about what’s happening inside these organizations — illegal, unethical, or, on the flip side, constructive and positive — please don’t stay silent.</p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><em>If you want to share, everything remains strictly confidential. I’ve been doing these investigations for almost three years. I would never reveal my sources. Not to the FBI. Not to the DOJ. Not to anyone.</em></p>
<div style="font-size: 16px;line-height: 26px;margin: 32px auto;"><figure style="width: 100%;margin: 0 auto;"><table border="0" cellpadding="0" cellspacing="0" data-component-name="Image2ToDOMStatic" style="mso-padding-alt: 1em 0 1.6em;" width="100%"><tbody><tr>
<td style="text-align: center;"></td>
<td align="left" style="text-align: center;" width="400"><a href="https://substack.com/redirect/e1ce3169-6e19-4d1b-849c-a1b2d12950d7?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="position: relative;flex-direction: column;align-items: center;padding: 0;width: auto;height: auto;border: none;text-decoration: none;display: block;margin: 0;" target="\_blank"><img alt="Cover Image for Health2Tech NYC, December 4, 2025" data-attrs='{"src":"https://substack-post-media.s3.amazonaws.com/public/images/24c310c2-d73c-43b5-83b3-c238e417556e\_800x800.jpeg","srcNoWatermark":null,"fullscreen":null,"imageSize":null,"height":800,"width":800,"resizeWidth":400,"bytes":null,"alt":"Cover Image for Health2Tech NYC, December 4, 2025","title":null,"type":null,"href":"https://luma.com/y6kvixw6?tk=MjI1Ri","belowTheFold":true,"topImage":false,"internalRedirect":null,"isProcessing":false,"align":null,"offset":false}' height="400" src="https://substackcdn.com/image/fetch/%24s\_!0QAQ!,w\_400,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F24c310c2-d73c-43b5-83b3-c238e417556e\_800x800.jpeg" style="border: none !important;vertical-align: middle;display: block;-ms-interpolation-mode: bicubic;height: auto;margin-bottom: 0;width: auto !important;max-width: 100% !important;margin: 0 auto;" title="Cover Image for Health2Tech NYC, December 4, 2025" width="400"/></a></td>
<td style="text-align: center;"></td>
</tr></tbody></table></figure></div>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><span>Also, if you are in NYC on Thursday, December 4, don’t be a stranger. </span><strong><a href="https://substack.com/redirect/a3949700-0dbb-4f88-97e9-bea2c04eeb2d?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: rgb(54,55,55);text-decoration: underline;">Register</a></strong><span> and say hi at Health2Tech, where I’ll be moderating a panel on innovation in healthcare AI, real tech adoption in clinical workflows, and what healthcare providers actually expect from AI.</span></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">OK, back to my slides… If you joined any of my lectures this year, you know I promised to share my slides with you. Today, I’m making them available exclusively to my paid Substack subscribers and Founding Members through this post. I’m putting the slides behind a paywall to keep them out of reach of LLMs and search engines, especially given how AI companies have been shamelessly stealing copyrighted material.</p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">These 100+ slides represent months and months of meticulous research. Enjoy.</p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">And a reminder. If you can’t afford this article — maybe you’re a student or between jobs — just reach out. That’s exactly why I created the AI Health Uncut Founding Member Club. Thanks to generous support from the people in that exclusive group of (currently) 19, I’m able to offer access to anyone who needs it.</p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;"><em><span>If you’d like to become a Founding Member of the AI Health Uncut community, you can join through </span><strong><a href="https://substack.com/redirect/e182aa7e-03a9-41a8-b271-09c83d48b4eb?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="color: rgb(54,55,55);text-decoration: underline;">this link</a></strong><span>. You’ll be making a real impact and helping me keep pushing for better outcomes in healthcare through AI, technology, policy, and beyond.</span></em></p>
<p data-attrs='{"url":"https://sergeiai.substack.com/subscribe?tier=founding","text":"Become a Founding Member","action":null,"class":"button-wrapper"}' data-component-name="ButtonCreateButton" style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;text-align: center;cursor: pointer;border-radius: 4px;"><a href="https://substack.com/redirect/e182aa7e-03a9-41a8-b271-09c83d48b4eb?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" rel="" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;box-sizing: border-box;border: none;font-size: 14px;line-height: 20px;font-weight: 600;margin: 0;opacity: 1;outline: none;white-space: nowrap;color: #363737 !important;text-decoration: none !important;text-align: center;cursor: pointer;border-radius: 4px;background-color: #8AE1A2;padding: 12px 20px;height: auto;"><span style="color: #363737;text-decoration: none;">Become a Founding Member</span></a></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);line-height: 26px;font-size: 16px;">Here are the titles of all 100+ slides (the real number is 141 😉):</p>
<blockquote style="border-left: 4px solid #8AE1A2;margin: 20px 0;padding: 0;margin-bottom: 0;">
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>1. Title Slide: Paging Dr. Watson: Why Healthcare AI Is 20 Years Behind</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>2. Disclaimer: Cite My Work, Please!</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>3. Reach Out to Me on Social Media</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>4. WellAI, My Startup (Merged with Chart2Chart)</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>5. AI Health Uncut, My Substack Newsletter</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>6. My Dataset of 132 Digital Health Companies</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>7. I Critique Flawed AI Models in Healthcare…</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>8. …Especially Those Embarrassingly Hyped by Mass Media</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>9. I Investigate Healthcare Fraud</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>10. And of Course, I Expose Bad Actors in Digital Health</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>11. Selected List of Companies I’ve Investigated</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong><span>12. I Also Cohost the “Digital Health Inside Out”</span><br/><span>Podcast With Alex Koshykov</span></strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>13. I’m Also on the Advisory Board of PeriOptima.ai</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>14. I’m Also on the Board of Health2Tech, a Nonprofit That Organizes Health Tech Events Around the World</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>15. Health2Tech Branches Around the World</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>16. Google’s Transformers (2017) and Covid (2020) Had a Far Greater Impact on AI Adoption Outside of Healthcare</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>17. But Maybe Things Are Finally Turning Around for AI Adoption in Healthcare…</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>18. Even Though on the Ground It Sure Feels Like We’re Far Behind in Medicine</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>19. The Healthcare AI Paradox</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>20. Treating the Sick Is Profitable. Keeping People Healthy Isn’t.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>21. Healthcare Innovation Is Being Killed As Problems Run Rampant</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>22. Why Does It Take Just a Few Lines of Code to Access the Most Advanced AI Model Ever Built,…</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>23. …While the Entire Healthtech Industry Has Spent Over a Decade Failing to Reliably Access Patient Records?</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>24. American Healthcare Is Complex — But It Doesn’t Have to Be</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>25. American Healthcare is Also Big. It is the #1 Employer and the #2 Contributor to GDP After Technology.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>26. Two Primary Barriers to Healthcare Innovation</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>27. The Margin and the Mission Must Align</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>28. What Makes Innovating in Healthcare Hard?</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>29. Customers Make Innovating Hard</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>30. Incumbents Make Innovating </strong><em><strong>Really</strong></em><strong> Hard — The Market Is Highly Concentrated</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>31. Incumbents Make Innovating </strong><em><strong>Really</strong></em><strong> Hard — Their Size Is Massive</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>32. Incumbents Make Innovating </strong><em><strong>Really</strong></em><strong> Hard — Every Company Is A Healthcare Company These Days</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>33. Incumbents Make Innovating </strong><em><strong>Really</strong></em><strong> Hard — They Hate Innovation</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>34. Incumbents Are Swallowing the Healthcare System Piece by Piece</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>35. Epic Has No Real Incentive to Innovate</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>36. Regulators Make Innovating Hard — Regulators Capture Rules Healthcare</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>37. Regulators Make Innovating Hard — Policy, Not Innovation, Drives American Healthcare</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>38. EU’s AI Laws Are Even Tougher</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>39. History of Artificial Intelligence</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>40. Warner V. Slack, MD, Pioneer of Patient-Centered Computing &amp; Medical Informatics</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>41. Eliza, the First Medical AI Agent</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>42. Why Machines Don’t Need to Think Like Humans</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>43. These 13 Influential Voices and 9 AI Companies Think AI Will Replace Doctors</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>44. While It’s Fashionable to Claim That AI is More Accurate Than Doctors,…</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>45. ...Most AI Accuracy Claims in Healthcare Have Been Debunked!</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>46. Let’s be honest, AI still ain’t ready for healthcare yet… A Story of Pruning Shears.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>47. This Banana Was Diagnosed With Melanoma by 3 Out of 3 Leading AI Dermatology Image-identification Apps</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>48. LLMs Weren’t Built for Medical Diagnostics. Using Them as Such Could Be Dangerous.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>49. The Cough That Broke 8 LLMs</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>50. AI Hasn’t Solved Healthcare’s Problems Because the System of Incentives Is Broken</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>51. Geoff Hinton’s 2016 Claim That AI Would Replace Radiologists “Within Five Years” Aged Poorly. There Are ~40,000 Radiologists in 2025, Up From ~34,500 in 2016.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>52. Why Do AI Predictions for Healthcare So Often Fail? Because They’re Usually Made By People Who Are Nowhere Near Healthcare.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>53. As With Any New Invention, Physicians Won’t Disappear. They’ll Learn AI.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>54. AI Isn’t Replacing Clinicians. It’s Changing What “Being a Clinician” Means.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>55. If Anyone Gets Replaced by AI, It’s the Useless Consultants 😄 </strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>56. Fast Forward to 2025: OpenEvidence Takes the Stage</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>57. OpenEvidence: Healthcare’s Most Data-Intensive Scientific Engine</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>58. Fast Forward to 2025: OpenAI Develops AI Consult</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>59. OpenAI’s AI Consult: The Man-Made Babysitter for LLMs</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>60. OpenAI’s AI Consult: A Human + AI Safety Net, Not a Standalone AI</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>61. Meredith Whittaker: Brutal Truth on LLMs, Tech Power &amp; Privacy</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>62. Most Startups Fail</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>63. We All Know About High Startup Failure Rates</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>64. Not Failing Means You’re Not Working Hard Enough</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>65. You Miss 100% of the Shots You Don’t Take</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>66. Tech-enabled Healthcare Services Margins Falls Somewhere Between Traditional Healthcare and Traditional Software</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>67. Who Pays For Digital Health? In Theory, Multiple Parties…</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>68. In Reality, Most Startups Sell to Providers</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>69. What Is the Business Model of Digital Health?</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>70. The Importance of Aligning the Margin and the Mission</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>71. Startups Are Risky, Therefore VC Is Risky</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>72. Non-VC-Backed Startups Either Die Quickly or Eventually Beat VC-Backed Ones</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>73. VCs Have Caused Billions in Losses for U.S.-Listed Digital Health Companies Over the Past 5 Years</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>74. The Story Remains Consistent Over Time: VCs Continue to Pick Sh\*tty Digital Health Companies Year After Year</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>75. Even If a Company Has Found a Sweet Spot, It May Not Want VC Funding</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>76. Out of the Top 10 Most Successful Publicly Traded Digital Health Companies, Only Two Are VC-Backed</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>77. Bankrupt Digital Health Companies Have Overwhelmingly Been Backed by VC and PE Firms</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>78. The Magic of Venture Capital in Digital Health: The Great Disappearance Act</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>79. VCs Are Playing Straight Into the Hands of Healthcare Monopolies by Eliminating Competition</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>80. Averages Don’t Tell Sh\*t: While VCs Often Murder Digital Health Startups, Even Most Non-VC-Backed Startups Are Doomed to Die</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>81. VCs Can’t Pick Winners Anymore. Instead, They’re Picking Mediocre Startups They Plan to Unload Onto the Next Sucker.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>82. VC Underperformed Equities and 60/40 in Every Possible Period Over the Past 25 Years!</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>83. VC and PE Returns Have Been Disastrous. And Nobody’s Even Mentioning Risk-Adjusted Returns—Unlike Stocks, You Can’t Just Hit a Button and Pull Your VC Money Out.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>84. VC Distributions Are Hovering Near Their Lowest Levels in Decades</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>85. Morgan Stanley: VC Returns Plummet to 28-Year Low</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>86. If You’re an LP, You Now Have to Wait Over 10 Years Just to Get Your Money Back!</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>87. “Traditional” VC Playbook: The Infinite Loop of Fundraising</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>88. VC Funding Is Killing the Startup Ecosystem</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>89. “VC Pump &amp; Dump”: Valuation Cycle of a Typical Digital Health Startup</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>90. Increasing Allocations to VC and PE at the Expense of Public Markets Has Been a Disastrous Move for Pension Funds</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>91. CalPERS Lost 24.8% on Their VC Positions in 2022. What Did They Do Next? They Didn’t Just Double Down. They Sextupled Down!</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>92. Since 1997, VC Investors Have Invested More Money Than They Received Back From VC Funds</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>93. “You Can’t Be Fired by Investing in General Catalyst”</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>94. When You Can’t Pick Winners if Your Life Depended on It, What Do You Do? You Build an Empire, Because at That Point, 2% Is Bigger Than 20%.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>95. The Only Truthful Thing Hemant Taneja Has Ever Said</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>96. What Good Is VC Diversification Without Liquidation?</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>97. And of Course, VCs Also Pat Themselves on the Back by Sponsoring Fake Rankings</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>98. The Healthcare VC Mafia Org Chart</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>99. Digital Health’s Political Cartel Org Chart</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>100. The Healthcare VC Mafia Rules</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>101. Over Half of Late-Stage Deals Originate From VC Referrals. These Firms Leverage Their Elite Networks for Superior Deal Flow. And Yet, They Still Consistently Underperform in the Long Run.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>102. How Venture Capital Is Cannibalizing the Economy</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>103. Digital Health Unicorns Have Disappeared—Because Mediocrity Trumps Innovation</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>104. But Maybe 2025 Is the Turning Point?</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>105. The IPO Party Is Over</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>106. The VC Culture of Mediocrity and the Incumbents’ Suppression of Innovation Have Created an Industry Dominated by “AI Tourists” and “AI Wrappers”</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>107. Is the Death of the AI Scribe Imminent?</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>108. Not a Single AI Scribe Has FDA Approval. It’s the Wild Wild West of Medicine.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>109. I Haven’t Seen Any Real Innovations in Digital Health</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>110. Primary Care Is in the Worst Shape Ever—and the Lack of Digital Health Innovation &amp; Shrinking Reimbursement Rates (Despite Healthcare Inflation!) Ain’t Helping</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>111. Sexism in Venture Capital: What Future Awaits My Daughters?</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>112. 21-Factor Quantitative Dashboard for Health AI IPO Valuation</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>113. 8 Digital Health Failure Patterns</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>114. Toxic Culture Is Eating Digital Health for Breakfast</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>115. Livongo: One of the Biggest Snake-Oil Deals in Financial Market History</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>116. Why Teladoc’s Acquisition of Livongo Was Disastrous</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>117. Theranos: One Drop of Lies, A Sea of Fraud</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>118. Better Theranos? People Sure Have Short Memories.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>119. Hippocratic AI: $9/Hour “AI Nurses” and the Web of Lies</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>120. Babylon Health: The Madoff of Digital Health</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>121. Wall Street Analysts Were in Bed With Babylon’s Management</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>122. “Stock Markets Are Either Too Optimistic or Too Negative, but Eventually, They Settle on the Right Value.” Babylon’s Value Has Settled at $0 Four Months Later…</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>123. Olive AI: The Poster Child of “Champagne and Cocaine” Spending</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>124. October 2021 Was Peak Olive: “Frisson by Olive” Fragrance and the Notorious “Olive Bus”</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>125. Truepill: The Poster Child for VC Extortion</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>126. Truepill’s Trajectory: From Founders’ Fantasy to VC Nightmare</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>127. Truepill’s Founders’ Dilution via VC Extortion: An 8-Step Program From 100% Ownership to 0%</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>128. Suki: Digital Health’s Poster Child for “AI Tourism”</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>129. Suki: When There’s Zero Innovation, “Borrowing” Someone Else’s Tech Ain’t “Hard at All”</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>130. 7 Digital Health Success Patterns</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>131. Veeva Systems: The Secret to Success—Say No to VCs</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>132. Doximity: Wall Street’s Pariah, Doctors’ Darling</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>133. Startup Success Formula</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>134. My Mission and Exploring Possible Solutions</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>135. Staying Active on Policy Issues is Important</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>136. Solutions to U.S. Healthcare Crisis</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>137. Medical AI Success Depends Not on Raw Computational Power, But on Sophisticated Knowledge Curation and Conflict Resolution</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>138. Multimodal AI for Next-Generation Healthcare</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>139. A Rare Healthcare AI Success Story. Smartwatches That Actually Work for Atrial Fibrillation (AF) Detection.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>140. Another Healthcare AI Success Story: Digital Twin GPT (DT-GPT) — LLMs Forecasting Patient Health Trajectories.</strong></p>
<p style="margin: 0 0 20px 0;color: rgb(54,55,55);margin-left: 20px;line-height: 26px;font-size: 16px;"><strong>141. The Future of AI in Medicine...</strong></p>
</blockquote>
</div></div>
<div aria-label="Paywall" data-component-name="Paywall" data-testid="paywall" role="region" style="position: relative;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';text-align: center;margin-bottom: 16px;cursor: default;-webkit-user-select: none;-moz-user-select: none;-ms-user-select: none;user-select: none;line-height: 26px;font-size: 16px;padding: 32px 24px 16px 24px;background: rgb(255,255,255);color: rgb(54,55,55);border-top: solid 2px #8ae1a2;margin-top: 6px;">
<div style="margin: auto;text-decoration: unset;list-style: none;border-radius: 9999px;display: flex;position: relative;justify-content: center;align-items: center;width: 64px;height: 64px;outline: 1px solid rgb(0,0,0,.1);outline-offset: -1px;background-color: rgb(238,238,238);flex: none;overflow: hidden;box-sizing: border-box;-webkit-user-select: none;user-select: none;font-size: 16px;line-height: 26px;--scale: 64px"><div style="text-decoration: unset;list-style: none;border-radius: 9999px;display: flex;position: relative;justify-content: center;align-items: center;width: 64px;height: 64px;outline: 1px solid rgb(0,0,0,.1);outline-offset: -1px;background-color: rgb(238,238,238);flex: none;overflow: hidden;box-sizing: border-box;-webkit-user-select: none;user-select: none;font-size: 16px;line-height: 26px;--scale: 64px" title="User"><picture><source sizes="64px" srcset="https://substackcdn.com/image/fetch/$s\_!slE2!,w\_64,h\_64,c\_fill,f\_webp,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc91ada74-8686-4e3f-a6e8-28e218393ec5\_530x532.jpeg 64w, https://substackcdn.com/image/fetch/$s\_!slE2!,w\_128,h\_128,c\_fill,f\_webp,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc91ada74-8686-4e3f-a6e8-28e218393ec5\_530x532.jpeg 128w, https://substackcdn.com/image/fetch/$s\_!slE2!,w\_192,h\_192,c\_fill,f\_webp,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc91ada74-8686-4e3f-a6e8-28e218393ec5\_530x532.jpeg 192w" type="image/webp"/><img alt="User's avatar" draggable="false" height="64" sizes="64px" src="https://substackcdn.com/image/fetch/%24s\_!slE2!,w\_64,h\_64,c\_fill,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc91ada74-8686-4e3f-a6e8-28e218393ec5\_530x532.jpeg" srcset="https://substackcdn.com/image/fetch/$s\_!slE2!,w\_64,h\_64,c\_fill,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc91ada74-8686-4e3f-a6e8-28e218393ec5\_530x532.jpeg 64w, https://substackcdn.com/image/fetch/$s\_!slE2!,w\_128,h\_128,c\_fill,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc91ada74-8686-4e3f-a6e8-28e218393ec5\_530x532.jpeg 128w, https://substackcdn.com/image/fetch/$s\_!slE2!,w\_192,h\_192,c\_fill,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fc91ada74-8686-4e3f-a6e8-28e218393ec5\_530x532.jpeg 192w" style="text-decoration: unset;list-style: none;display: flex;object-fit: cover;max-width: 550px;border: none !important;vertical-align: middle;" width="64"/></picture></div></div>
<h2 style="font-family: 'SF Pro Display',-apple-system-headline,system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';-webkit-font-smoothing: antialiased;-moz-osx-font-smoothing: antialiased;-webkit-appearance: optimizelegibility;-moz-appearance: optimizelegibility;appearance: optimizelegibility;margin: 0 auto;color: inherit !important;font-size: 22px;line-height: 33px;font-weight: 500;margin-top: 8px;margin-bottom: 20px;">Continue reading this post for free in the Substack app</h2>
<div style="font-size: 16px;line-height: 26px;margin-top: 0;"><a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9zZXJnZWlhaS5zdWJzdGFjay5jb20vcC93aHktaGVhbHRoY2FyZS1haS1pcy0yMC15ZWFycy1iZWhpbmQ\_dXRtX2NhbXBhaWduPWVtYWlsLXBvc3Qmcj02cTZlZ2wmdG9rZW49ZXlKMWMyVnlYMmxrSWpvME1EWTNOalUzTkRrc0luQnZjM1JmYVdRaU9qRTNPVEkwTURVMk1pd2lhV0YwSWpveE56WXpOalkyTlRReUxDSmxlSEFpT2pFM05qWXlOVGcxTkRJc0ltbHpjeUk2SW5CMVlpMHhPVEExTWpJMklpd2ljM1ZpSWpvaWNHOXpkQzF5WldGamRHbHZiaUo5LjVWNDZOM1daVUFkT1BlTWFQaVFIc09mc1d1NF92RTRrYmZoenl3M3IteTAiLCJwIjoxNzkyNDA1NjIsInMiOjE5MDUyMjYsImYiOnRydWUsInUiOjQwNjc2NTc0OSwiaWF0IjoxNzYzNjY2NTQyLCJleHAiOjIwNzkyNDI1NDIsImlzcyI6InB1Yi0wIiwic3ViIjoibGluay1yZWRpcmVjdCJ9.A-VGF8vvSbeOaRGKLhQljpc1Y7FRMqInrtoxSuW4Tz4?&amp;launch\_post\_unlock\_offer=true" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;box-sizing: border-box;cursor: pointer;border: none;border-radius: 8px;font-size: 14px;line-height: 20px;font-weight: 600;text-align: center;margin: 0;opacity: 1;outline: none;white-space: nowrap;background-color: #8AE1A2;text-decoration: none !important;color: #363737 !important;padding: 12px 16px;height: auto;">Claim my free post</a></div>
<div style="line-height: 26px;margin-top: 20px;font-size: 12px;font-weight: 300;"><a href="https://substack.com/redirect/0f714936-8a1a-4704-ada4-3c8209ff8373?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" style="color: inherit;text-decoration: none;">Or upgrade your subscription. <b>Upgrade to paid</b></a></div>
</div>
<table border="0" cellpadding="0" cellspacing="0" role="presentation" style="border-top: 1px solid rgb(0,0,0,.1);border-bottom: 1px solid rgb(0,0,0,.1);min-width: 100%;" width="100%"><tbody>
<tr height="16"><td height="16" style="font-size:0px;line-height:0;"> </td></tr>
<tr><td><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="100%"><tbody><tr>
<td><table border="0" cellpadding="0" cellspacing="0" role="presentation" style="margin:0 auto;" width="auto"><tbody><tr>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td align="center"><a href="https://substack.com/app-link/post?publication\_id=1905226&amp;post\_id=179240562&amp;utm\_source=substack&amp;isFreemail=true&amp;submitLike=true&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3OTI0MDU2MiwicmVhY3Rpb24iOiLinaQiLCJpYXQiOjE3NjM2NjY1NDIsImV4cCI6MTc2NjI1ODU0MiwiaXNzIjoicHViLTE5MDUyMjYiLCJzdWIiOiJyZWFjdGlvbiJ9.Rf1XeTsV7sRj9NUK\_oGp9MO7JNrpERKVYMjBjnJMJ5U&amp;utm\_medium=email&amp;utm\_campaign=email-reaction&amp;r=6q6egl" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 12px;padding: 9px 14px;text-decoration: none;color: rgb(119,119,119);"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!PeVs!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideHeart%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="margin-right: 8px;min-width: 18px;min-height: 18px;border: none;vertical-align: middle;max-width: 18px" width="18"/><span style="vertical-align: middle;">Like</span></a></td></tr></tbody></table></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td align="center"><a href="https://substack.com/app-link/post?publication\_id=1905226&amp;post\_id=179240562&amp;utm\_source=substack&amp;utm\_medium=email&amp;isFreemail=true&amp;comments=true&amp;token=eyJ1c2VyX2lkIjo0MDY3NjU3NDksInBvc3RfaWQiOjE3OTI0MDU2MiwiaWF0IjoxNzYzNjY2NTQyLCJleHAiOjE3NjYyNTg1NDIsImlzcyI6InB1Yi0xOTA1MjI2Iiwic3ViIjoicG9zdC1yZWFjdGlvbiJ9.5V46N3WZUAdOPeMaPiQHsOfsWu4\_vE4kbfhzyw3r-y0&amp;r=6q6egl&amp;utm\_campaign=email-half-magic-comments&amp;action=post-comment&amp;utm\_source=substack&amp;utm\_medium=email" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 12px;padding: 9px 14px;text-decoration: none;color: rgb(119,119,119);"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!x1tS!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FLucideComments%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="margin-right: 8px;min-width: 18px;min-height: 18px;border: none;vertical-align: middle;max-width: 18px" width="18"/><span style="vertical-align: middle;">Comment</span></a></td></tr></tbody></table></td>
<td style="min-width: 8px" width="8"></td>
<td style="vertical-align:middle;"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr><td align="center"><a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9vcGVuLnN1YnN0YWNrLmNvbS9wdWIvc2VyZ2VpYWkvcC93aHktaGVhbHRoY2FyZS1haS1pcy0yMC15ZWFycy1iZWhpbmQ\_dXRtX3NvdXJjZT1zdWJzdGFjayZ1dG1fbWVkaXVtPWVtYWlsJnV0bV9jYW1wYWlnbj1lbWFpbC1yZXN0YWNrLWNvbW1lbnQmYWN0aW9uPXJlc3RhY2stY29tbWVudCZyPTZxNmVnbCZ0b2tlbj1leUoxYzJWeVgybGtJam8wTURZM05qVTNORGtzSW5CdmMzUmZhV1FpT2pFM09USTBNRFUyTWl3aWFXRjBJam94TnpZek5qWTJOVFF5TENKbGVIQWlPakUzTmpZeU5UZzFORElzSW1semN5STZJbkIxWWkweE9UQTFNakkySWl3aWMzVmlJam9pY0c5emRDMXlaV0ZqZEdsdmJpSjkuNVY0Nk4zV1pVQWRPUGVNYVBpUUhzT2ZzV3U0X3ZFNGtiZmh6eXczci15MCIsInAiOjE3OTI0MDU2MiwicyI6MTkwNTIyNiwiZiI6dHJ1ZSwidSI6NDA2NzY1NzQ5LCJpYXQiOjE3NjM2NjY1NDIsImV4cCI6MjA3OTI0MjU0MiwiaXNzIjoicHViLTAiLCJzdWIiOiJsaW5rLXJlZGlyZWN0In0.lDXwxUqUonDkNHTXnCiWQ3JoeGwHJiJGqLfJMV0FkeA?&amp;utm\_source=substack&amp;utm\_medium=email" style="font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';display: inline-block;font-weight: 500;border: 1px solid rgb(0,0,0,.1);border-radius: 9999px;text-transform: uppercase;font-size: 12px;line-height: 12px;padding: 9px 14px;text-decoration: none;color: rgb(119,119,119);"><img alt="" height="18" src="https://substackcdn.com/image/fetch/%24s\_!5EGt!,w\_36,c\_scale,f\_png,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Ficon%2FNoteForwardIcon%3Fv%3D4%26height%3D36%26fill%3Dnone%26stroke%3D%2523808080%26strokeWidth%3D2" style="margin-right: 8px;min-width: 18px;min-height: 18px;border: none;vertical-align: middle;max-width: 18px" width="18"/><span style="vertical-align: middle;">Restack</span></a></td></tr></tbody></table></td>
</tr></tbody></table></td>
<td align="right"><table border="0" cellpadding="0" cellspacing="0" role="presentation" width="auto"><tbody><tr></tr></tbody></table></td>
</tr></tbody></table></td></tr>
<tr height="16"><td height="16" style="font-size:0px;line-height:0;"> </td></tr>
</tbody></table>
<div style="color: rgb(119,119,119);text-align: center;font-size: 16px;line-height: 26px;padding: 24px0;">
<div style="font-size: 16px;line-height: 26px;padding-bottom: 24px"><p style="list-style: none;font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';padding-bottom: 0;font-size: 12px;line-height: 16px;margin: 0;color: rgb(119,119,119);text-decoration: unset;">© 2025 <span>Sergei Polevikov</span><br/>548 Market Street PMB 72296, San Francisco, CA 94104 <br/><a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9zZXJnZWlhaS5zdWJzdGFjay5jb20vYWN0aW9uL2Rpc2FibGVfZW1haWw\_dG9rZW49ZXlKMWMyVnlYMmxrSWpvME1EWTNOalUzTkRrc0luQnZjM1JmYVdRaU9qRTNPVEkwTURVMk1pd2lhV0YwSWpveE56WXpOalkyTlRReUxDSmxlSEFpT2pFM09UVXlNREkxTkRJc0ltbHpjeUk2SW5CMVlpMHhPVEExTWpJMklpd2ljM1ZpSWpvaVpHbHpZV0pzWlY5bGJXRnBiQ0o5LlR6dGVycTdDM3hqZXAxZXplOVluU3BrYThqdnNBREtNUFlTUUJDVTFDeTAiLCJwIjoxNzkyNDA1NjIsInMiOjE5MDUyMjYsImYiOnRydWUsInUiOjQwNjc2NTc0OSwiaWF0IjoxNzYzNjY2NTQyLCJleHAiOjIwNzkyNDI1NDIsImlzcyI6InB1Yi0wIiwic3ViIjoibGluay1yZWRpcmVjdCJ9.uwNNFxcKCOKxKpLHztmq4GBKvX\_fLCPp6uGt\_4xoPuI?" style="text-decoration: underline;color: rgb(119,119,119);"><span style="color: rgb(119,119,119);text-decoration: underline;">Unsubscribe</span></a></p></div>
<p style="padding: 0 24px;font-size: 12px;line-height: 20px;margin: 0;color: rgb(119,119,119);font-family: system-ui,-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Helvetica,Arial,sans-serif,'Apple Color Emoji','Segoe UI Emoji','Segoe UI Symbol';padding-bottom: 0;margin-top: 0;"><a href="https://substack.com/redirect/02d0fb0f-799e-429d-a0bc-34bc5a17ee82?j=eyJ1IjoiNnE2ZWdsIn0.JeUaI03hkTZe3g0Y-WbKcpI\_zv\_M4N2A50pyRXMoP1g" style="color: rgb(119,119,119);text-decoration: none;display: inline-block;margin: 0 4px;"><img alt="Get the app" height="40" src="https://substackcdn.com/image/fetch/%24s\_!IzGP!,w\_262,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fgeneric-app-button%402x.png" srcset="https://substackcdn.com/image/fetch/$s\_!DIki!,w\_131,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fgeneric-app-button.png, https://substackcdn.com/image/fetch/$s\_!IzGP!,w\_262,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fgeneric-app-button%402x.png 2x, https://substackcdn.com/image/fetch/$s\_!QWua!,w\_393,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fgeneric-app-button%403x.png 3x" style="max-width: 550px;border: none !important;vertical-align: middle;" width="131"/></a><a href="https://substack.com/redirect/2/eyJlIjoiaHR0cHM6Ly9zdWJzdGFjay5jb20vc2lnbnVwP3V0bV9zb3VyY2U9c3Vic3RhY2smdXRtX21lZGl1bT1lbWFpbCZ1dG1fY29udGVudD1mb290ZXImdXRtX2NhbXBhaWduPWF1dG9maWxsZWQtZm9vdGVyJmZyZWVTaWdudXBFbWFpbD1pbWVvYnZua0BsaWJyYXJ5LnJlYWR3aXNlLmlvJnI9NnE2ZWdsIiwicCI6MTc5MjQwNTYyLCJzIjoxOTA1MjI2LCJmIjp0cnVlLCJ1Ijo0MDY3NjU3NDksImlhdCI6MTc2MzY2NjU0MiwiZXhwIjoyMDc5MjQyNTQyLCJpc3MiOiJwdWItMCIsInN1YiI6ImxpbmstcmVkaXJlY3QifQ.UMkSGyPY2Fbujp2ajB3VkPi4\_5O5jJ8VcrYdZV\_gFR4?" style="color: rgb(119,119,119);text-decoration: none;display: inline-block;margin: 0 4px;"><img alt="Start writing" height="40" src="https://substackcdn.com/image/fetch/%24s\_!LkrL!,w\_270,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%402x.png" srcset="https://substackcdn.com/image/fetch/$s\_!wgfj!,w\_135,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button.png, https://substackcdn.com/image/fetch/$s\_!LkrL!,w\_270,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%402x.png 2x, https://substackcdn.com/image/fetch/$s\_!KjtY!,w\_405,c\_limit,f\_auto,q\_auto:good,fl\_progressive:steep/https%3A%2F%2Fsubstack.com%2Fimg%2Femail%2Fpublish-button%403x.png 3x" style="max-width: 550px;border: none !important;vertical-align: middle;" width="135"/></a></p>
</div>
</div></td>
<td></td>
</tr>
</tbody></table>
<img alt="" border="0" height="1" src="https://eotrx.substackcdn.com/open?token=eyJtIjoiPDIwMjUxMTIwMTkyMjA3LjMuNjM4ODVjZmM5OTNhNmE1YUBtZy1kMC5zdWJzdGFjay5jb20-IiwidSI6NDA2NzY1NzQ5LCJyIjoiaW1lb2J2bmtAbGlicmFyeS5yZWFkd2lzZS5pbyIsImQiOiJtZy1kMC5zdWJzdGFjay5jb20iLCJwIjoxNzkyNDA1NjIsInQiOiJuZXdzbGV0dGVyIiwiYSI6Im9ubHlfcGFpZCIsInMiOjE5MDUyMjYsImMiOiJwb3N0IiwiZiI6dHJ1ZSwicG9zaXRpb24iOiJib3R0b20iLCJpYXQiOjE3NjM2NjY1NDIsImV4cCI6MTc2NjI1ODU0MiwiaXNzIjoicHViLTAiLCJzdWIiOiJlbyJ9.Ma71cd0l0wNU3R5lfDDaGHhGBD3dSrwwyU-ZjNVpX0o" style="height:1px !important;width:1px !important;border-width:0 !important;margin-top:0 !important;margin-bottom:0 !important;margin-right:0 !important;margin-left:0 !important;padding-top:0 !important;padding-bottom:0 !important;padding-right:0 !important;padding-left:0 !important;" width="1"/><img alt="" height="1" src="https://email.mg-d0.substack.com/o/eJxEkNuq6yAURb-mvp2gxkt98FvCUldyFk00eGnJ32\_abtivY8JgMCN03Eq9\_FlaZ8mbGVadGHphzWyM0UoxPID2ZcOMFTqmBfrfKq1w7L9X3EUn5jkYoayFVeoYjVKgkwmrNZGRl1xqISQXTkpup3ky8\_2u4xqdm8GAhpvix\_Yv8amN0DrExxTLwagta8VPgu91IHuHLjASYY7oS96v5QRKX07JC-uk4trIL-nXiT7jq-3YO1Z2jrDEchwjU78WzBB2TL\_mEXaK0Knkj8hxLaVh1dOBJTzz46b4TqFCvaaKkF7UcKLC2gipHEDZN6wbEhDr3z9Hw\_pWKW6s0VY59vTyJwAA\_\_-WHXr1" width="1"/>
</div>
