
Guidera
/

privacy.html
html


terms.html
html


support.html
144 lines

html

I changed the Guidera reference with the last updates.
Tell me where to change, edit etc. I can replace them after you send me the updated ones.

1:36 AM
Looking at the uploaded reference doc and your project memories, I can see a few discrepancies. Let me check the actual files to compare precisely.


Viewed 4 files
Viewed 4 files
Now let me check the reference doc for recent changes:


Check the GUIDERA_REFERENCE.md in the project
Check the GUIDERA_REFERENCE.md in the project
OK, I've reviewed everything. Here's what I found comparing the GUIDERA_REFERENCE.md against the project context/system prompt and the legal documents:

The GUIDERA_REFERENCE.md itself looks accurate and up to date. The file structure, features, monetization, analytics, and architecture all match your current state. No changes needed there.

The project context (system prompt pasted into this Claude project) has a few inaccuracies you should fix:

1. "Third-party dependencies: None — Apple frameworks only" This is wrong. The reference doc correctly lists Firebase iOS SDK and Google Mobile Ads SDK via SPM. Update this line to match.

2. Monetization section is too sparse: The project context says "Free: Map exploration, AI descriptions, settings, local caching" and "Premium: Curated tours, custom tour creation, and tour-related features" — this is missing a lot of detail that the reference doc has (daily limits, rewarded video, personas, ads, paywall, specific pass tiers). Either expand it or just say "See GUIDERA_REFERENCE.md for full monetization details."

3. Missing Firebase/Analytics/Crashlytics entirely: The project context doesn't mention Firebase at all, while it's a significant part of the app (analytics events, Crashlytics, GoogleService-Info.plist). Worth at least a line.

4. Missing ATT (App Tracking Transparency): Referenced in the reference doc and privacy policy but absent from the project context.

For the three legal HTML files, a few things to check:

5. support.html — style mismatch: The support page uses a dark theme (black background, 
#F5F5F5 text, green accents 
#6EE7B7) while privacy.html and terms.html use a light editorial theme (cream background, serif headings, indigo accent). This will look jarring if users navigate between them. You might want to unify support.html to match the privacy/terms style.

6. support.html — footer copyright says "© 2026 Selim": The privacy and terms pages use your full legal name "Mehmet Selim Çetin." The support page just says "Selim." Probably should be consistent.

7. support.html — missing Firebase/Analytics mention in FAQ: The "How do I delete my data?" FAQ says "No account or server-side data exists." Technically Firebase Analytics and Crashlytics do send data to Google servers. Your privacy policy correctly addresses this ("Firebase/Google may retain analytics/ad data under their own policies"), but the support FAQ oversimplifies it. Consider adding something like "Analytics data collected by Firebase is subject to Google's retention policies" or just keeping the FAQ focused on on-device data without the absolute claim.

8. privacy.html — email addresses show as [email protected]: The email links on lines 135, 211, and 220 all show Cloudflare's email obfuscation markup (data-cfemail, __cf_email__). This happens because the HTML was fetched through Cloudflare. Your local source files are probably fine, but double-check that the actual files you'll deploy to GitHub Pages have the real privacy@guidera.app email addresses and not the obfuscated versions.

9. privacy.html — no mention of Firebase Analytics: Section 4 (Third-Party Services) lists Gemini, OpenAI, AdMob, and Apple — but doesn't mention Firebase Analytics or Crashlytics as a separate third-party service, even though the reference doc has a whole section on what data goes to Firebase. This is a gap for GDPR transparency. Consider adding a "4.5 Firebase Analytics & Crashlytics" subsection explaining that you use Firebase for anonymous app analytics and crash reporting, what data it collects (app instance ID, events with place names, crash stack traces), and linking to Google's Firebase privacy docs.

So to summarize what needs action:

For the project context (this Claude project's system prompt): fix the dependencies line, expand monetization, add Firebase/ATT mentions.

For support.html: unify the visual theme with privacy/terms, use full legal name, soften the "no server-side data" claim.

For privacy.html: add Firebase Analytics & Crashlytics as a listed third-party service, verify email addresses aren't Cloudflare-obfuscated in your source files.

Want me to produce updated versions of any of these files?

yes produce

1:42 AM
Let me check the support page more carefully and then produce all the updated files.


Viewed 2 files
Viewed 2 files
The terms.html seems truncated — the footer div isn't closed. Let me check the full end:


Ran 2 commands
Ran 2 commands
The terms.html file is literally cut off — it ends mid-tag at <div class="footer with no closing tags. The privacy.html likely has the same issue. Let me check:


Check if privacy.html is also truncated
Check if privacy.html is also truncated
Good — privacy.html is complete. Terms.html is the one that's truncated. Now let me also check the actual email in privacy.html (it showed obfuscated in the viewer but might be fine in the raw file):


Ran 2 commands
Ran 2 commands
Interesting — the file has a mix. The first three email references (in sections 1, 10, and 11) use Cloudflare's obfuscation, but the final contact section (section 14) has the real email. This confirms the file was saved from a Cloudflare-served page. The emails in the obfuscated links are privacy@guidera.app based on context.

Let me check terms and support too:


Ran 2 commands
Ran 2 commands
So support.html only has the obfuscated email — no real one visible. The email address in support.html is supposed to be support@guidera.app based on the display text in the document.

Now let me read the full privacy.html to get the real email used there:


Find all email references in privacy
Find all email references in privacy
Now I have the full picture. The privacy page uses privacy@guidera.app in the body sections (obfuscated by Cloudflare) but mehmetselim692@icloud.com in the final contact section. Let me now produce all three updated files.


Viewed 2 files
Viewed 2 files
Now I have everything. Let me also note: line 223 in privacy.html has a truncated CCPA section — it reads "the right to app." which is clearly cut off. The original CCPA text we had in the view tool showed the full version. Let me now produce all three corrected files.


Read the SKILL.md for guidance
Read the SKILL.md for guidance
Since these are legal documents, not creative frontends, I'll keep the existing design style and just fix the content issues. Let me produce all three files:


Created 3 files, ran a command, read a file
Created 3 files, ran a command, read a file
Here are all three updated files. Here's a summary of what changed in each:

privacy.html:

Added section 2.5 "Analytics Data" — explains Firebase Analytics & Crashlytics (what's collected, what's not, app instance IDs, event types)
Added section 4.4 "Firebase Analytics & Crashlytics" as a third-party service with link to Firebase privacy docs
Added analytics row to the "How We Use Your Data" table (legitimate interest basis)
Updated section 5 (Data Transfers) to mention analytics alongside AI/ads
Updated section 8 (Data Retention) to mention Firebase retention
Fixed the truncated CCPA paragraph (was cut off at "the right to app.")
Replaced all Cloudflare-obfuscated emails with real mailto:mehmetselim692@icloud.com links
Updated the summary callout to mention analytics
Renumbered subsections (2.5→2.6 Locally Stored Data, 2.6→2.7 Data We Do Not Collect, 4.4→4.5 Apple Frameworks)
terms.html:

Added "Google Firebase (anonymous analytics and crash reporting)" to the section 9 third-party services list
Fixed the truncated file — the original was cut off mid-tag at <div class="footer; now has proper closing tags
Replaced the Cloudflare-obfuscated email with real mailto link
Added matching footer with copyright and disclaimer (consistent with privacy.html)
support.html:

Restyled entirely to match the light editorial theme of privacy/terms (was dark theme before)
Uses same fonts (Source Serif 4 + DM Sans), colors, and layout patterns
Updated footer from "© 2026 Selim" to "© 2026 Mehmet Selim Çetin"
Fixed the obfuscated email to real mailto link
Updated "How do I delete my data?" FAQ to acknowledge Firebase analytics instead of claiming "No account or server-side data exists"
Footer link now says "Terms of Use" (matching the terms.html title) instead of "Terms & Conditions"
Privacy
Code · HTML 
Terms
Code · HTML 
Support
Code · HTML 
readme md text would be good for this guidera-legal repo. It should have the links of these three and a brief description

https://msc35.github.io/guidera-legal/privacy
https://msc35.github.io/guidera-legal/support
https://msc35.github.io/guidera-legal/terms

1:52 AM

Created a file, read a file
Created a file, read a file
Short and clean — has the three links, a one-liner on each, and your contact. Ready to drop into the repo root.

Readme
Document · MD 

You've used 90% of your session limit
Get more usage




Claude is AI and can make mistakes. Please double-check responses.
Readme · MD
Copy

# Guidera — Legal Documents
 
Legal and support pages for [Guidera](https://apps.apple.com/app/guidera), an AI-powered walking tour and place discovery app for iOS.
 
Hosted via GitHub Pages at `msc35.github.io/guidera-legal`.
 
## Pages
 
- **[Privacy Policy](https://msc35.github.io/guidera-legal/privacy)** — What data the app collects, third-party services used, your rights under GDPR/KVKK/CCPA.
- **[Terms of Use](https://msc35.github.io/guidera-legal/terms)** — Usage terms, AI content disclaimers, in-app purchase policies, liability.
- **[Support](https://msc35.github.io/guidera-legal/support)** — Contact info and frequently asked questions.
 
## Contact
 
Mehmet Selim Çetin — mehmetselim692@icloud.com
 






