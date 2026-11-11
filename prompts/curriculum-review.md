# Curriculum review prompt

Paste everything below the line into an LLM agent that can read this repository and browse the live web (fetch pages and run web searches). A model without web access cannot do this task and is told to say so and stop.

---

I maintain a fork of the Open Source Society University (OSSU) computer science curriculum at https://github.com/nathan-middleton/computer-science. It is a complete self-taught path through an undergraduate CS degree, built almost entirely out of links to free online courses, lecture playlists, textbooks, and course websites. People follow it for roughly two years of study, so a dead link, a course that has quietly gone behind a paywall, or a recommendation that points somewhere wrong costs a learner real time. I want you to audit every resource the curriculum links to and, where one is broken or out of date, find a replacement I can trust.

The standard for this work is that every factual statement in your report is something you confirmed during this session by opening the page yourself. I will act on your report without re-checking most of it, so a confident wrong statement is far worse than an honest "I could not verify this." Nothing in the report may come from memory: not a URL, not a course title, not an instructor name, not a price, not a claim that a course is free or still running. If you did not see it on a page you loaded in this session, it either stays out of the report or is labelled as unverified. If you do not have tools to fetch web pages and search the web, tell me that immediately and do nothing else, because an audit done from memory would be worse than no audit.

## What the repository contains

The curriculum lives in Markdown files. `README.md` is the main sequence: Intro CS, Core CS (programming, math, tools, systems, theory, security, applications, ethics), Advanced CS electives, and a final project. `coursepages/` holds detailed study guides for a few courses (intro-cs, intro-programming, spd, class-based, ostep), and these contain many deep links to individual lectures and assignments. `extras/` holds further courses, readings, other curricula, and practice sites. `FAQ.md`, `HELP.md`, `CONTRIBUTING.md`, and `CURRICULAR_GUIDELINES.md` contain supporting links. Altogether there are about 500 distinct URLs. The heaviest concentrations are university course sites (course.ccs.neu.edu, cs50.harvard.edu, ocw.mit.edu, pages.cs.wisc.edu), Coursera, edX, YouTube playlists, GitHub, Amazon book listings, and Discord invites.

The README states the criteria a course must meet to be in the curriculum: open for enrollment, running regularly (ideally self-paced), high quality in teaching materials and pedagogy, and aligned with the ACM/IEEE CS2013 curriculum guidelines. All or nearly all material is meant to be free to study, even if graded assignments or certificates cost money. Use those same criteria when you judge an existing resource or propose a replacement.

## How to do the audit

Start by building a complete inventory: every URL in every Markdown file, with the file, the line, the link text, and the role the link plays (a main curriculum course, an "alternative" link, a prerequisite, a lecture or assignment deep link, a book, a community link). Extract the inventory mechanically if you can run code, so that nothing is missed by skimming. The inventory is how I will know the audit was complete, so the number of URLs you report on at the end must equal the number you found at the start.

Then check each URL by loading it. A URL passing an HTTP check is not enough, because the common failures here are quiet ones. A retired course page often redirects to the provider's catalog or homepage and returns a normal success code. A course site may load but now belong to a different term with different content. A playlist may exist but have videos removed. A course may still be listed but closed for enrollment, archived, or available only with a paid subscription. So for each link, read what actually came back and confirm it is the specific thing the curriculum says it is: the title matches, the content is reachable, and for courses, a learner arriving today can actually start studying.

Keep "broken" and "could not verify" strictly apart. Several of these sites block automated requests or hide their content behind a login or JavaScript, and a 403, a CAPTCHA, a login wall, or an empty shell page tells you about your access, not about the resource. When that happens, try another route to the same evidence (a web search for the exact page, the provider's public catalog listing, an official syllabus page), and if you still cannot see the content, record the link as unverified and say what blocked you. Never mark a link dead, or alive, on a guess.

For courses, check the things a learner depends on and record what the page itself says: whether enrollment is open now, whether it is self-paced or on a schedule, and whether the lectures and assignments can be accessed without paying. Free access is the claim most likely to have changed and the easiest to get wrong, since providers change their audit and free-tier policies over time, so only state that something is free when the page you loaded says so in terms you can quote. If the page is ambiguous, report it as ambiguous.

## Deciding what counts as out of date

Age alone is not a reason to replace something. Calculus, discrete math, algorithms, and operating systems concepts have not changed, and a well-taught lecture series from many years ago can still be the best resource available. Much of this curriculum deliberately pins a specific past offering of a university course (for example a particular semester's course website) because that term published complete materials. Replacing those for the sake of recency would make the curriculum worse.

Treat a resource as needing replacement when it is unreachable or gone; when it is no longer free to study or no longer open for enrollment; when the same provider has published a newer edition or offering that fully supersedes it with complete public materials; or when it teaches tools, language versions, or practices that are obsolete enough that a learner would be unable to follow along or would learn something wrong. Where a link has simply moved, the fix is the new address of the same resource, not a different resource. If something works and still meets the curriculum's criteria, the correct finding is "keep", and I expect that to be the finding for most links.

## Finding replacements

When a resource does need replacing, look for the closest equivalent first: the same course at a new address, then a newer offering from the same instructor or institution, then a different course covering the same topics at the same level. A replacement has to fit the slot it fills. Compare its syllabus against the "topics covered" list for that section of the README and against what later courses assume as prerequisites, and tell me about any topic the replacement drops or adds.

Prefer primary sources: the university's own course site, the instructor's own page or channel, the publisher's own page for a book, the official platform listing. Avoid third-party reuploads, mirrors of uncertain legality, and aggregator pages. For books, link the author's or publisher's page and note the current edition as stated there.

Every replacement URL you propose must be one you loaded in this session and read closely enough to confirm that it is what you say it is, that it is complete (the lectures, notes, or assignments are actually there, not just a landing page), and that it is free and open in the sense above. Models readily produce URLs that look right and do not exist, so do not construct or recall a URL; only report addresses you arrived at and opened. If you cannot find a replacement that you were able to verify, say that no verified replacement was found and describe what you looked at. A gap I know about is useful to me, and a plausible unverified suggestion is not.

Judgments about quality are welcome, but keep them visibly separate from facts. "The course site lists 24 lectures with video and problem sets with solutions" is a fact you can verify. "This is a better introduction than the current course" is your opinion, and it should be labelled as such along with your reasoning.

## What to give me back

Write the report as a Markdown file. Open with a short summary: how many URLs were inventoried, how many fall into each status, and the handful of findings that matter most to a learner (broken or paywalled main-sequence courses come first). Then give the detail, organised in the same order as the curriculum so I can work through it section by section.

For every URL, give its location (file and line), its link text, and one status: working as described, moved (with the new address), degraded (reachable but with a problem such as closed enrollment, paywalled content, or missing materials), dead, or unverified. For each one, include the evidence: what you loaded, what you saw, quoted briefly where the wording matters, and the date you checked. Links that are working as described can be listed compactly in a table; anything else deserves a short written explanation.

For each proposed replacement, give the exact URL, the title and provider as shown on the page, the evidence for its availability and cost, how its coverage compares with the resource it replaces, and the exact replacement Markdown line so I can apply the change directly. Mark each recommendation with how confident you are and why.

Keep a separate section listing everything you could not verify and what stopped you, so I can check those by hand.

Do not edit the curriculum files. I will review the report and apply changes myself.

## Before you hand it over

When the report is drafted, go back through it as a sceptical reviewer would. Re-open every replacement URL and every "moved" address one more time and confirm it still loads and still says what your report claims. Check that each quoted phrase appears on the page you attribute it to. Check that the status counts in the summary add up to the size of the inventory. Remove or downgrade anything that does not survive that pass.

This is a large audit and you may not be able to complete it in one sitting. If so, do not thin out the checking to cover more ground. Work through the files in curriculum order, starting with the main sequence in `README.md`, check each link properly, and tell me exactly which files and links remain unchecked so the work can be resumed from that point.
