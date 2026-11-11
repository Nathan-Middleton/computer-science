# OSSU Computer Science link audit, part 1: `README.md` and `coursepages/`

All checks: **11 November 2026**, from a cloud session (details and limits in [Method](#method-and-access-limits)). No curriculum file was edited.

## Summary

**Inventory.** I extracted links mechanically from all 22 Markdown files in the repository. That gave **542 link occurrences, 501 distinct URLs**. I cross-checked against a raw count of `http(s)://` strings: 544, where the 2 extra are a link whose text is its own URL and an archive.org URL that contains another URL. The full inventory (file, line, link text, URL, section, status, evidence) is in [`link-inventory.csv`](link-inventory.csv).

**Coverage of this pass.** I checked `README.md` and every file under `coursepages/` to the standard you set. That is **331 distinct URLs (367 occurrences)**. I have **not yet checked** the 170 distinct URLs that appear only in `extras/*`, `FAQ.md`, `HELP.md`, `CONTRIBUTING.md`, `CURRICULAR_GUIDELINES.md`, `CHANGELOG.md` and `.github/ISSUE_TEMPLATE/`. They are listed in [Not yet checked](#not-yet-checked-resume-here) so the work can resume there.

| Status (distinct URLs) | Count |
|--|--:|
| Working as described | 227 |
| Moved (old address still redirects; new address given) | 38 |
| Degraded (reachable, but paywalled / archived / pointing at the wrong thing) | 23 |
| Dead | 4 |
| Unverified (blocked, login wall, or unreachable from my session) | 39 |
| **Checked in this pass** | **331** |
| Not yet checked (remaining files) | 170 |
| **Total inventory** | **501** |

### Findings that matter most to a learner (main sequence first)

1. **F1 - Coursera courses in the main sequence are no longer free to study, according to their own pages.** This affects 10 Core CS courses:
   - Core programming: Software Architecture.
   - Core systems: Nand2Tetris Part I and Part II.
   - Core security: Principles of Secure Coding; Identifying Security Vulnerabilities; the C/C++ and Java options.
   - Core ethics: Ethics, Technology and Engineering; Introduction to Intellectual Property; Data Privacy Fundamentals.

   It also affects 3 Advanced courses (Parallel Programming, Security Governance & Compliance, Digital Forensics Concepts) and all 7 Final-project specializations.

   On every one of the 13 course pages, the FAQ "When will I have access to the lectures and assignments?" now answers:
   > "To access course materials, assignments, and earn a Certificate, you'll need to purchase the Certificate experience when you enroll in a course. Eligible learners may also have the option to start with a Free Trial. Some courses may also offer a Full Course, No Certificate option. This lets you access course materials, submit required assessments, and receive a final grade, but you won't be able to earn or purchase a Certificate."

   None of these pages mentions an audit option; no audit wording appears in the rendered text or the raw HTML. The 7 specialization pages answer "Can I take the course for free?" with "No, you cannot take this course for free." Enrolling requires an account, so I could not see whether any single course offers the "Full Course, No Certificate" option.

   For contrast, the Princeton and ENS Coursera courses in `extras/` (not part of this pass's scope) say "No. All features of this course are available for free." So the paywall is per course, not site-wide. The repository's own `FAQ.md:70` already says Coursera removed audit access in July 2025.

   **Replacement:** verified only for Nand2Tetris (see R2). For the others I did not search for replacements in this pass.
2. **F2 - Databases: Relational Databases and SQL (Core applications, README.md:279) is archived.** The edX page says "This course is archived" and shows no start date or audit option. The other Stanford database courses in the same table are running and self-paced. No verified replacement was found (see the detail entry).
3. **F3 - Computer Networking: a Top-Down Approach (Core systems, README.md:214) could not be checked at all.** gaia.cs.umass.edu is unreachable from my session (TLS error). This is the most important item to check by hand.
4. **F4 - Cybersecurity Fundamentals (Core security, README.md:248) runs on a schedule.** The page shows "Instructor-paced" and "Starts Jan 04, 2027 Ends Mar 03, 2027". The page is working, but a learner arriving now waits about 8 weeks.
5. **F5 - The three Linux Foundation "Secure Software Development" courses (Advanced information security, README.md:384-386) are dead.** All three edX addresses redirect to the LinuxFoundationX school page. **A verified replacement exists:** the Linux Foundation/OpenSSF course "Developing Secure Software (LFD121)". Its outline has the same three parts with the same names, and the course page shows "$0 ... Online, Self Paced" (R1).
6. **F6 - Web Security Fundamentals (Advanced information security, README.md:381) is archived on edX.**
7. **F7 - Wrong Discord channels on three lines.**
   - `README.md:394` (Introduction to Numerical Methods) opens #calculus-1c-coordinate-systems-infinite-series.
   - `coursepages/ostep/README.md:88` (OSTEP project problems) opens #computer-networking.
   - `coursepages/intro-programming/README.md:20` (CS50P chat) opens #missing-semester.

   Every other Discord invite occurrence in the checked files resolves to a channel matching its line, according to Discord's public invite API.
8. **F8 - Intro CS page: the edX 6.00.1x link is dead (coursepages/intro-cs/README.md:40).** It redirects to edX's generic CS catalog. MIT Learn has a 6.00.1x listing, but it says "This course is no longer active, but you can still access selected content", so it is not a clean replacement.
9. **F9 - CS50P links pinned to `/python/2022/` (31 links) now redirect to the current, unversioned edition.** Titles still match, but the 2022 version these links name is no longer what learners get.
10. **F10 - edX audit access is time-limited.** Every running edX course in the checked files shows "Audit course" plus "Audit Access Expires <date>". The dates shown today range from Nov 25, 2026 to Mar 3, 2027, roughly 2 to 16 weeks away. Graded assessments are listed only under the paid Certificate track. These still meet "free to study, pay for grading", but learners should know the free window is short.
11. **F11 - OSTEP lecture videos (coursepages/ostep/README.md:59) need a manual look.** The videos page links 54 YouTube videos. YouTube's oEmbed returned 401 for 49 of them, and watch pages were rate-limited for my session. They may simply be non-embeddable, but I could not confirm they still play.

Most other links are fine. The pinned past offerings (UW CSE341 Spring 2019, Northeastern CS3500 Fall 2019 and CS2510 Spring 2022, Wisconsin CS537 Spring 2018, MIT OCW courses) all load with their materials and should be **kept**. Their "archival" or "prior semester" banners are expected for deliberately pinned terms.

## Proposed changes

Each recommendation below was re-opened in the final review pass on 11 Nov 2026.

### R1 - Replace the three edX "Secure Software Development" rows (README.md:384-386) with LFD121

- **URL:** <https://training.linuxfoundation.org/training/developing-secure-software-lfd121/>. Title on page: "Developing Secure Software (LFD121) - Linux Foundation - Education". Provider: Linux Foundation Training & Certification, developed by OpenSSF.
- **Availability and cost (quoted):**
  - The course page says "$0 Login Using My Portal Before Enrolling Enroll Today Includes Online, Self Paced 16-20 Hours of Course Material Quizzes and Hands-on Labs".
  - OpenSSF's page (<https://openssf.org/training/courses/>) says "Both the course and certificate of completion are free. It is entirely online, takes about 14-18 hours to complete, and you can go at your own pace."
  - The two pages give different hour estimates (16-20 vs 14-18).
- **Coverage.** The LF course outline reads: "1. Introduction 2. Part 1: Requirements, Design and Reuse - Overview 3. Security Basics 4. Secure Design Principles 5. Reusing External Software 6. Part 2: Implementation - Overview 7. Input Validation 8. Processing Data Securely 9. Calling Other Programs 10. Sending Output 11. Part 3: Verification and More Specialized Topics 12. Verification 13. Threat Modeling 14. Cryptography 15. Other Topics 16. Final Exam". The three part names match the titles of the three retired edX courses. I could not compare against the old edX syllabi because those pages are gone. The course content is also published as <https://github.com/ossf/secure-sw-dev-fundamentals> (git ls-remote OK; linked from the OpenSSF page).
- **Confidence: high** that this is free, self-paced and current (two official pages agree). **Medium-high** that it covers what the three edX courses covered: same publisher and identical part titles, but no syllabus-level comparison. *Opinion:* it reads as the consolidated successor of the edX series. Enrolling requires a free Linux Foundation account ("Login Using My Portal Before Enrolling").
- **Replacement Markdown** (one row instead of three; the table header on README.md:379 is `Courses | Duration | Effort | Prerequisites`):

```markdown
[Developing Secure Software (LFD121)](https://training.linuxfoundation.org/training/developing-secure-software-lfd121/) | - | 16-20 hours total | Core Programming and Core Security
```

### R2 - Make nand2tetris.org the primary link for Nand2Tetris Part I and Part II (README.md:211-212)

- **URL:** <https://www.nand2tetris.org/course>. Title on page: "Projects | nand2tetris". It is the official site of the course and book (Nisan & Schocken), already listed as the "alternative" on README.md:211.
- **Cost (quoted from <https://www.nand2tetris.org/>):** "This website contains all the lectures, project materials and tools necessary for building a general-purpose computer system and a modern software hierarchy from the ground up... Everything is free and open-source, as long as you operate in a non-profit setting."
- **Coverage.** The Projects page lists all 12 projects: "Part I: Hardware" (projects 1-6: Boolean Logic ... Assembler) and "Part II: Software" (projects 7-12: VM I ... Operating System). It says "Each project consists of project guidelines and lecture slides. Some projects link to book chapters, mostly from the book's 1st edition." That matches the README's Core systems topics (gate logic through compilers and OS).
- **Gaps I could not verify.** I could not open the individual project pages; clicking a project title did not navigate in my browser. I also could not confirm that lecture videos are on the site; the home page's only video link I found is a single YouTube video. The Coursera version has video lectures and an autograder, and the site's materials may be slides plus guidelines only. Check one project page by hand before applying.
- **Confidence: medium.** Free status is confirmed in the site's own words. Completeness of each project page is not verified.
- **Replacement Markdown:**

```markdown
[Nand to Tetris Part I: Hardware (projects 1-6)](https://www.nand2tetris.org/course) ([Coursera version](https://www.coursera.org/learn/build-a-computer), paid) | 6 weeks | 7-13 hours/week | - | C-like programming language | [chat](https://discord.gg/vxB2DRV)
[Nand to Tetris Part II: Software (projects 7-12)](https://www.nand2tetris.org/course) ([Coursera version](https://www.coursera.org/learn/nand2tetris2), paid) | 6 weeks | 12-18 hours/week | - | one of [these programming languages](https://user-images.githubusercontent.com/2046800/35426340-f6ce6358-026a-11e8-8bbb-4e95ac36b1d7.png), Nand to Tetris Part I | [chat](https://discord.gg/AsUXcPu)
```

### R3 - Address-only fixes (same resource, new address)

Each old address below still works today through a redirect. Each new address was re-opened in the final pass, and its title is given in the detail tables. The CS50P change is the only one with a side effect: the links stop naming the 2022 edition, which the redirects already stopped serving. The `coursepages/ostep/README.md:88` change swaps the Discord invite for the OSTEP channel invite already used on README.md:213 (#operating-systems-3-easy-pieces, per Discord's invite API). It is a channel correction, not an address move.

`README.md:9` - replace with:

```markdown
    <img alt="Awesome" src="https://cdn.jsdelivr.net/gh/sindresorhus/awesome@d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg"
```

`README.md:171` - replace with:

```markdown
[Calculus 1A: Differentiation](https://openlearninglibrary.mit.edu/courses/course-v1:MITx+18.01.1x+2T2019/about) ([alternative](https://ocw.mit.edu/courses/18-01sc-single-variable-calculus-fall-2010/)) | 13 weeks | 6-10 hours/week | The alternate covers this and the following 2 courses | [high school math](https://ossu.dev/precollege-math) | [chat](https://discord.gg/mPCt45F)
```

`README.md:281` - replace with:

```markdown
[Machine Learning](https://www.deeplearning.ai/specializations/machine-learning)| 11 weeks | 9 hours/week | Basic coding | [chat](https://discord.gg/NcXHDjy)
```

`README.md:393` - replace with:

```markdown
[Linear Algebra](https://ocw.mit.edu/courses/18-06sc-linear-algebra-fall-2011/) | 14 weeks | 12 hours/week | corequisite: Essence of Linear Algebra | [chat](https://discord.gg/k7nSWJH)
```

`README.md:394` - replace with:

```markdown
[Introduction to Numerical Methods](https://ocw.mit.edu/courses/18-335j-introduction-to-numerical-methods-spring-2019/)| 14 weeks | 12 hours/week | [Linear Algebra](https://ocw.mit.edu/courses/18-06sc-linear-algebra-fall-2011/) | [chat](https://discord.gg/FNEcNNq)
```

`README.md:396` - replace with:

```markdown
[Probability](https://stat110.hsites.harvard.edu/) | 15 weeks | 5-10 hours/week | [Differentiation and Integration](https://learn.mit.edu/courses/course-v1:MITxT+18.01.2x) | [chat](https://discord.gg/UVjs9BU)
```

`coursepages/intro-programming/README.md:18` - replace with:

```markdown
 - If you want to follow along with the instructor, log in to the [CS50 "codespace"](https://cs50.dev) and watch [this video](https://cs50.harvard.edu/python/shorts/visual_studio_code_for_cs50/) to get started.
```

`coursepages/intro-programming/README.md:25` - replace with:

```markdown
0. [Functions, Variables](https://cs50.harvard.edu/python/weeks/0/) — [Notes](https://cs50.harvard.edu/python/notes/0/) — [Problem Set](https://cs50.harvard.edu/python/psets/0/)
```

`coursepages/intro-programming/README.md:26` - replace with:

```markdown
1. [Conditionals](https://cs50.harvard.edu/python/weeks/1/) — [Notes](https://cs50.harvard.edu/python/notes/1/) — [Problem Set](https://cs50.harvard.edu/python/psets/1/)
```

`coursepages/intro-programming/README.md:27` - replace with:

```markdown
2. [Loops](https://cs50.harvard.edu/python/weeks/2/) — [Notes](https://cs50.harvard.edu/python/notes/2/) — [Problem Set](https://cs50.harvard.edu/python/psets/2/)
```

`coursepages/intro-programming/README.md:28` - replace with:

```markdown
3. [Exceptions](https://cs50.harvard.edu/python/weeks/3/) — [Notes](https://cs50.harvard.edu/python/notes/3/) — [Problem Set](https://cs50.harvard.edu/python/psets/3/)
```

`coursepages/intro-programming/README.md:29` - replace with:

```markdown
4. [Libraries](https://cs50.harvard.edu/python/weeks/4/) — [Notes](https://cs50.harvard.edu/python/notes/4/) — [Problem Set](https://cs50.harvard.edu/python/psets/4/)
```

`coursepages/intro-programming/README.md:30` - replace with:

```markdown
5. [Unit Tests](https://cs50.harvard.edu/python/weeks/5/) — [Notes](https://cs50.harvard.edu/python/notes/5/) — [Problem Set](https://cs50.harvard.edu/python/psets/5/)
```

`coursepages/intro-programming/README.md:31` - replace with:

```markdown
6. [File I/O](https://cs50.harvard.edu/python/weeks/6/) — [Notes](https://cs50.harvard.edu/python/notes/6/) — [Problem Set](https://cs50.harvard.edu/python/psets/6/)
```

`coursepages/intro-programming/README.md:32` - replace with:

```markdown
7. [Regular Expressions](https://cs50.harvard.edu/python/weeks/7/) — [Notes](https://cs50.harvard.edu/python/notes/7/) — [Problem Set](https://cs50.harvard.edu/python/psets/7/)
```

`coursepages/intro-programming/README.md:33` - replace with:

```markdown
8. [Object-Oriented Programming](https://cs50.harvard.edu/python/weeks/8/) — [Notes](https://cs50.harvard.edu/python/notes/8/) — [Problem Set](https://cs50.harvard.edu/python/psets/8/)
```

`coursepages/intro-programming/README.md:34` - replace with:

```markdown
9. [Et Cetera](https://cs50.harvard.edu/python/weeks/9/) — [Notes](https://cs50.harvard.edu/python/notes/9/) — [Final Project](https://cs50.harvard.edu/python/project/)
```

`coursepages/ostep/README.md:88` - replace with:

```markdown
This course was originally taught as CS 537 at the University of Wisconsin by the author of the OSTEP textbook, which means that the homework and projects were written with those students as a target audience and designed to be run on UWisconsin lab computers with specific software versions pre-installed for students. We hope this section fixes that so you can run them on other computers, but we haven't tested this on every computer, so if you run into other issues, let us know on the [Discord channel](https://discord.gg/wZNgpep) and we'll try to help out.
```


### Problems with no verified fix

- **Coursera main-sequence courses (F1)** other than Nand2Tetris: I did not search for replacements in this pass. Per `FAQ.md:70`, the project is already reviewing them in its Issues.
- **Databases: Relational Databases and SQL (F2):** I looked at:
  - the edX databases catalog;
  - the "Introduction to SQL & Databases" XSeries page, which still lists the archived course;
  - the sibling Stanford pages (Advanced Topics in SQL, Modeling and Theory, Semistructured Data: all running);
  - the older "Introduction to Relational Databases" listing (also archived).

  None offers the SQL course itself in a current run. No verified replacement.
- **Web Security Fundamentals (F6):** not searched in this pass.
- **edX 6.00.1x (F8):** the only listing I found (MIT Learn) is inactive. *Opinion:* since the note at intro-cs:40 exists only to point certificate-seekers somewhere, the simplest fix may be to drop that sentence until a current run exists.
- **Discord channels at README.md:394 and intro-programming:20 (F7):** I don't know which channels OSSU intends for Numerical Methods and CS50P. The maintainers would need to supply those invites.
- **Anaconda link (coursepages/intro-cs/README.md:38):** it now redirects to "Anaconda Distribution vs. Miniconda", a comparison page, not an install overview. I did not look for the new install page.

## Detail, in curriculum order

Working links are tabulated per section; anything else gets a written entry above its section's table. "Line-level problem" marks a URL that works but is wrong for the line it is on.

### `README.md`


#### (top of file)

- **README.md:9** - "<src>" - <https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg>  
  **Status: MOVED.** RawGit address; redirects to https://cdn.jsdelivr.net/gh/sindresorhus/awesome@d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg, which returns image/svg+xml. The badge still renders through the redirect. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 8 | <href> | <https://github.com/sindresorhus/awesome> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/sindresorhus/awesome HEAD` succeeds and GitHub search API shows sindresorhus/awesome archived=false. |
| 11 | <href> | <https://github.com/ossu/computer-science> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/ossu/computer-science HEAD` succeeds and GitHub search API shows ossu/computer-science archived=false, last push 2026-11-09. |
| 12 | <src> | <https://img.shields.io/badge/OSSU-computer--science-blue.svg> | Returns image/svg+xml badge "OSSU: computer-science". |


#### Summary

- **README.md:54** - "this spreadsheet" - <https://docs.google.com/spreadsheets/d/1y2kMsIg9VaHMVmw35x_aH1hpty3V-ZMuV2jA13P_Cgo/copy>  
  **Status: UNVERIFIED.** A "/copy" link; redirects to Google sign-in ("Sign in to continue to Google Sheets"). The sheet cannot be seen without a Google account. *(checked 2026-11-11)*
- **README.md:59** - "Coursera" - <https://www.coursera.support/s/article/209819033-Apply-for-Financial-Aid-or-a-Scholarship?language=en_US>  
  **Status: UNVERIFIED.** Redirects to https://www.coursera.support/s/article/learner-000001455?language=en_US (title "Coursera Help Center"), but the page never rendered: the body shows only "Sorry to interrupt CSS Error Refresh". Whether the article still covers financial aid is unknown. *(checked 2026-11-11)*
- **README.md:59** - "edX" - <https://courses.edx.org/financial-assistance/>  
  **Status: UNVERIFIED.** Redirects to home.edx.org and then to the login page authn.edx.org/login; the financial assistance information is not visible without logging in. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 56 | OSSU CS website | <https://cs.ossu.dev> | Loads "Computer Science \| Path to a free self-taught education in Computer Science!" (the OSSU site). |
| 56 | the repo | <https://github.com/ossu/computer-science> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/ossu/computer-science HEAD` succeeds and GitHub search API shows ossu/computer-science archived=false, last push 2026-11-09. |


#### Community

- **README.md:80** - "Linkedin" - <https://www.linkedin.com/school/11272443/>  
  **Status: UNVERIFIED.** Redirects to LinkedIn login (session_redirect=/school/11272443/); the school page is not visible without logging in. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 78 | [badge] | <https://discord.gg/wuytwK5s9h> | Discord public invite API (discord.com/api/v10/invites/wuytwK5s9h) returns server "OSSU" (id 744385009028431943), channel #welcome, 36887 members, no expiry. |
| 78 | Join the OSSU Discord | <https://discord.gg/wuytwK5s9h> | Discord public invite API (discord.com/api/v10/invites/wuytwK5s9h) returns server "OSSU" (id 744385009028431943), channel #welcome, 36887 members, no expiry. |
| 78 | (nested image) | <https://img.shields.io/discord/744385009028431943.svg?label=&logo=discord&logoColor=ffffff&color=7389D8&labelColor=6A7EC2> | Returns image/svg+xml badge reading "3.3k online". |
| 82 | OSSU CS website | <https://cs.ossu.dev> | Loads "Computer Science \| Path to a free self-taught education in Computer Science!" (the OSSU site). |
| 82 | OSSU CS Github Repo | <https://github.com/ossu/computer-science> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/ossu/computer-science HEAD` succeeds and GitHub search API shows ossu/computer-science archived=false, last push 2026-11-09. |


#### Prerequisites


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 112 | high school math | <https://ossu.dev/precollege-math> | Redirects to https://ossu.dev/precollege-math/ "Pre-College Math", the OSSU pre-college math curriculum. |


#### Intro CS


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 129 | high school algebra | <https://ossu.dev/precollege-math> | Redirects to https://ossu.dev/precollege-math/ "Pre-College Math", the OSSU pre-college math curriculum. |
| 129 | chat | <https://discord.gg/jvchSm9> | Discord public invite API (discord.com/api/v10/invites/jvchSm9) returns server "OSSU" (id 744385009028431943), channel #6-100l-intro-to-computer-science, 36887 members, no expiry. |


#### Core programming

- **README.md:153** - "chat" - <https://discord.com/channels/744385009028431943/891411727294562314>  
  **Status: UNVERIFIED.** Channel deep link inside the OSSU server (guild id 744385009028431943 matches the OSSU invites). Discord shows an empty app shell without login, so the channel name could not be confirmed. *(checked 2026-11-11)*
- **README.md:155** - "chat" - <https://discord.com/channels/744385009028431943/891412022120579103>  
  **Status: UNVERIFIED.** Channel deep link inside the OSSU server (guild id 744385009028431943 matches the OSSU invites). Discord shows an empty app shell without login, so the channel name could not be confirmed. *(checked 2026-11-11)*
- **README.md:156** - "Software Architecture" - <https://www.coursera.org/learn/software-architecture>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*
- **README.md:156** - "chat" - <https://discord.com/channels/744385009028431943/891412169638432788>  
  **Status: UNVERIFIED.** Channel deep link inside the OSSU server (guild id 744385009028431943 matches the OSSU invites). Discord shows an empty app shell without login, so the channel name could not be confirmed. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 152 | part 1 | <https://discord.gg/RfqAmGJ> | Discord public invite API (discord.com/api/v10/invites/RfqAmGJ) returns server "OSSU" (id 744385009028431943), channel #spd-first-half, 36887 members, no expiry. |
| 152 | part 2 | <https://discord.gg/kczJzpm> | Discord public invite API (discord.com/api/v10/invites/kczJzpm) returns server "OSSU" (id 744385009028431943), channel #spd-second-half, 36887 members, no expiry. |
| 154 | Programming Languages | <https://courses.cs.washington.edu/courses/cse341/19sp/#lectures> | Loads "UW CSE341, Spring 2019" with banner "This page is part of an archival collection and is no longer actively maintained." Course Materials list units with slides, code and video pages; sample video file videos/unit1/uncaptioned/003-expressions-and-variables.mp4 returns HTTP 206 video/mp4. Pinned past offering, so keep. |
| 154 | chat | <https://discord.gg/8BkJtXN> | Discord public invite API (discord.com/api/v10/invites/8BkJtXN) returns server "OSSU" (id 744385009028431943), channel #program-langs, 36887 members, no expiry. |
| 155 | Object-Oriented Design | <https://course.ccs.neu.edu/cs3500f19/> | Loads "CS 3500: Object-Oriented Design" (Fall 2019) with banner "This website is for a prior semester of CS3500"; lecture list with notes pages present. Pinned past offering, so keep. |


#### Core math

- **README.md:171** - "alternative" - <https://ocw.mit.edu/courses/mathematics/18-01sc-single-variable-calculus-fall-2010/index.htm>  
  **Status: MOVED.** Old-style OCW address; redirects to https://ocw.mit.edu/courses/18-01sc-single-variable-calculus-fall-2010/ ("Single Variable Calculus \| Mathematics \| MIT OpenCourseWare"), which loads with the full course navigation. Works today through the redirect. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 171 | Calculus 1A: Differentiation | <https://openlearninglibrary.mit.edu/courses/course-v1:MITx+18.01.1x+2T2019/about> | MIT Open Learning Library about page "18.01.1x Calculus 1A: Differentiation" loads with "View Course" and "Enroll to Get Started". The page does not state a price. It adds "This course is currently available on MITx Online." |
| 171 | high school math | <https://ossu.dev/precollege-math> | Redirects to https://ossu.dev/precollege-math/ "Pre-College Math", the OSSU pre-college math curriculum. |
| 171 | chat | <https://discord.gg/mPCt45F> | Discord public invite API (discord.com/api/v10/invites/mPCt45F) returns server "OSSU" (id 744385009028431943), channel #calculus-1a-differentiation, 36887 members, no expiry. |
| 172 | Calculus 1B: Integration | <https://openlearninglibrary.mit.edu/courses/course-v1:MITx+18.01.2x+3T2019/about> | MIT Open Learning Library about page "18.01.2x Calculus 1B: Integration" loads with "View Course" and "Enroll to Get Started". The page does not state a price. It adds "This course is currently available on MITx Online." |
| 172 | chat | <https://discord.gg/sddAsZg> | Discord public invite API (discord.com/api/v10/invites/sddAsZg) returns server "OSSU" (id 744385009028431943), channel #calculus-1b-integration, 36887 members, no expiry. |
| 173 | Calculus 1C: Coordinate Systems & Infinite Series | <https://openlearninglibrary.mit.edu/courses/course-v1:MITx+18.01.3x+1T2020/about> | MIT Open Learning Library about page "18.01.3x Calculus 1C" loads with "View Course" and "Enroll to Get Started". The page does not state a price. It adds "This course is currently open for enrollment on MITx Online with certificates available." |
| 173 | chat | <https://discord.gg/FNEcNNq> | Discord public invite API (discord.com/api/v10/invites/FNEcNNq) returns server "OSSU" (id 744385009028431943), channel #calculus-1c-coordinate-systems-infinite-series, 36887 members, no expiry. |
| 174 | Mathematics for Computer Science | <https://openlearninglibrary.mit.edu/courses/course-v1:OCW+6.042J+2T2019/about> | MIT Open Learning Library about page "6.042J Mathematics for Computer Science" loads with "View Course" and "Enroll to Get Started". The page does not state a price. |
| 174 | alternative | <https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-fall-2010/> | MIT OCW page "Mathematics for Computer Science \| Electrical Engineering and Computer Science \| MIT OpenCourseWare" loads with syllabus/course navigation and course description. |
| 174 | 2015/2019 solutions | <https://github.com/spamegg1/Math-for-CS-solutions> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/spamegg1/Math-for-CS-solutions HEAD` succeeds and GitHub search API shows spamegg1/Math-for-CS-solutions archived=false; repo contains exams/, inclass-questions/, psets/. |
| 174 | 2010 solutions | <https://github.com/frevib/mit-cs-math-6042-fall-2010-problems> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/frevib/mit-cs-math-6042-fall-2010-problems HEAD` succeeds and GitHub search API shows frevib/mit-cs-math-6042-fall-2010-problems archived=false, description "MIT CS 6.042 opencourseware Fall 2010 problems + solutions". |
| 174 | 2005 solutions | <https://ocw.mit.edu/courses/6-042j-mathematics-for-computer-science-fall-2005/pages/assignments/> | MIT OCW page "Assignments \| Mathematics for Computer Science \| Electrical Engineering and Computer Science \| MIT OpenCourseWare" loads with syllabus/course navigation and course description. Table lists Problem Sets 1-8+ each with a solutions PDF. |
| 174 | chat | <https://discord.gg/EuTzNbF> | Discord public invite API (discord.com/api/v10/invites/EuTzNbF) returns server "OSSU" (id 744385009028431943), channel #math-for-cs, 36887 members, no expiry. |


#### CS Tools


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 189 | The Missing Semester of Your CS Education | <https://missing.csail.mit.edu/> | Loads "The Missing Semester of Your CS Education"; the home page is now headed "2026" with lectures and past editions linked. |
| 189 | chat | <https://discord.gg/5FvKycS> | Discord public invite API (discord.com/api/v10/invites/5FvKycS) returns server "OSSU" (id 744385009028431943), channel #missing-semester, 36887 members, no expiry. |


#### Core systems

- **README.md:211** - "Build a Modern Computer from First Principles: From Nand to Tetris" - <https://www.coursera.org/learn/build-a-computer>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*
- **README.md:212** - "Build a Modern Computer from First Principles: Nand to Tetris Part II" - <https://www.coursera.org/learn/nand2tetris2>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*
- **README.md:214** - "Computer Networking: a Top-Down Approach" - <https://gaia.cs.umass.edu/kurose_ross/online_lectures.htm>  
  **Status: UNVERIFIED.** The proxy could not reach gaia.cs.umass.edu: curl gives a TLS error ("unable to get local issuer certificate") and the browser gets "upstream request failed". The same happened for www-net.cs.umass.edu. A web search shows this URL indexed with the title "8E Kurose & Ross header", and separate 9th-edition video pages (gaia.cs.umass.edu/kurose_ross/videos/1/ etc.). I did not load either, so I make no claim about their content. *(checked 2026-11-11)*
- **README.md:214** - "Wireshark Labs" - <https://gaia.cs.umass.edu/kurose_ross/wireshark.php>  
  **Status: UNVERIFIED.** Same access failure as the other gaia.cs.umass.edu link (TLS chain / upstream request failed). *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 211 | alternative | <https://www.nand2tetris.org/> | Official site loads: "The official website of Nand to Tetris courses And of the book The Elements of Computing Systems... This website contains all the lectures, project materials and tools... Everything is free and open-source, as long as you operate in a non-profit setting." Its Projects page (nand2tetris.org/course) lists all 12 projects in two parts: Part I Hardware (1-6) and Part II Software (7-12), "Each project consists of project guidelines and lecture slides." |
| 211 | chat | <https://discord.gg/vxB2DRV> | Discord public invite API (discord.com/api/v10/invites/vxB2DRV) returns server "OSSU" (id 744385009028431943), channel #nand2tetris-1, 36887 members, no expiry. |
| 212 | these programming languages | <https://user-images.githubusercontent.com/2046800/35426340-f6ce6358-026a-11e8-8bbb-4e95ac36b1d7.png> | Returns image/png (1005x838). |
| 212 | chat | <https://discord.gg/AsUXcPu> | Discord public invite API (discord.com/api/v10/invites/AsUXcPu) returns server "OSSU" (id 744385009028431943), channel #nand2tetris-2, 36887 members, no expiry. |
| 213 | chat | <https://discord.gg/wZNgpep> | Discord public invite API (discord.com/api/v10/invites/wZNgpep) returns server "OSSU" (id 744385009028431943), channel #operating-systems-3-easy-pieces, 36887 members, no expiry. |
| 214 | chat | <https://discord.gg/MJ9YXyV> | Discord public invite API (discord.com/api/v10/invites/MJ9YXyV) returns server "OSSU" (id 744385009028431943), channel #computer-networking, 36887 members, no expiry. |


#### Core theory


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 233 | Algorithms: Design and Analysis, Part 1 | <https://www.edx.org/learn/algorithms/stanford-university-algorithms-design-and-analysis-part-1> | edX page "StanfordOnline: Algorithms: Design and Analysis, Part 1 \| edX" loads; page shows: Self-paced; Starts Nov 11 Ends Aug 31, 2030; Certificate Premium $189 USD; Audit Access Expires Dec 23; "Audit course" button present (the Certificate track is the one listed with "Graded assessments"). |
| 233 | alternative | <https://www.algorithmsilluminated.org/> | Loads "The Algorithms Illuminated Book Series" (Tim Roughgarden); describes the Omnibus Edition (Parts 1-4), "Hardcover, 690pp, list price $60". |
| 233 | chat | <https://discord.gg/mKRS7tY> | Discord public invite API (discord.com/api/v10/invites/mKRS7tY) returns server "OSSU" (id 744385009028431943), channel #divide-conquer-algo1, 36887 members, no expiry. |
| 234 | Algorithms: Design and Analysis, Part 2 | <https://www.edx.org/learn/algorithms/stanford-university-algorithms-design-and-analysis-part-2> | edX page "StanfordOnline: Algorithms: Design and Analysis, Part 2 \| edX" loads; page shows: Self-paced; Starts Nov 11 Ends Aug 31, 2030; Certificate Premium $149 USD; Audit Access Expires Dec 23; "Audit course" button present (the Certificate track is the one listed with "Graded assessments"). |
| 234 | chat | <https://discord.gg/Qstqe4t> | Discord public invite API (discord.com/api/v10/invites/Qstqe4t) returns server "OSSU" (id 744385009028431943), channel #graph-search-algo2, 36887 members, no expiry. |


#### Core security

- **README.md:249** - "Principles of Secure Coding" - <https://www.coursera.org/learn/secure-coding-principles>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*
- **README.md:250** - "Identifying Security Vulnerabilities" - <https://www.coursera.org/learn/identifying-security-vulnerabilities>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*
- **README.md:256** - "Identifying Security Vulnerabilities in C/C++ Programming" - <https://www.coursera.org/learn/identifying-security-vulnerabilities-c-programming>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*
- **README.md:257** - "Exploiting and Securing Vulnerabilities in Java Applications" - <https://www.coursera.org/learn/exploiting-securing-vulnerabilities-java-applications>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 248 | Cybersecurity Fundamentals | <https://www.edx.org/learn/cybersecurity/rochester-institute-of-technology-cybersecurity-fundamentals> | edX page "RITx: Cybersecurity Fundamentals \| edX" loads; page shows: Instructor-paced; Starts Jan 04, 2027 Ends Mar 03, 2027; Certificate Premium $399 USD; Audit Access Expires Mar 1, 2027; "Audit course" button present (the Certificate track is the one listed with "Graded assessments"). Note: this is the only Core CS edX course on a fixed schedule; the next run starts 4 Jan 2027, and a learner arriving today waits about 8 weeks. |
| 248 | chat | <https://discord.gg/XdY3AwTFK4> | Discord public invite API (discord.com/api/v10/invites/XdY3AwTFK4) returns server "OSSU" (id 744385009028431943), channel #cybersecurity-fundamentals, 36887 members, no expiry. |
| 249 | chat | <https://discord.gg/5gMdeSK> | Discord public invite API (discord.com/api/v10/invites/5gMdeSK) returns server "OSSU" (id 744385009028431943), channel #principles-secure-coding, 36887 members, no expiry. |
| 250 | chat | <https://discord.gg/V78MjUS> | Discord public invite API (discord.com/api/v10/invites/V78MjUS) returns server "OSSU" (id 744385009028431943), channel #id-security-vulnerabilities, 36887 members, no expiry. |
| 256 | chat | <https://discord.gg/Vbxce7A> | Discord public invite API (discord.com/api/v10/invites/Vbxce7A) returns server "OSSU" (id 744385009028431943), channel #id-sec-vulnerable-c, 36887 members, no expiry. |
| 257 | chat | <https://discord.gg/QxC22rR> | Discord public invite API (discord.com/api/v10/invites/QxC22rR) returns server "OSSU" (id 744385009028431943), channel #secure-vulnerable-java, 36887 members, no expiry. |


#### Core applications

- **README.md:279** - "Databases: Relational Databases and SQL" - <https://www.edx.org/learn/relational-databases/stanford-university-databases-relational-databases-and-sql>  
  **Status: DEGRADED.** edX page "StanfordOnline: Databases: Relational Databases and SQL. \| edX" loads but says "This course is archived" and shows no start date or audit/certificate options, only a "View course materials" button (clicking it did not navigate in my browser). The related Stanford pages (Modeling and Theory, Semistructured Data, Advanced Topics in SQL) are self-paced and running, and the edX "Introduction to SQL & Databases" XSeries still lists this course. The older "Databases: Introduction to Relational Databases" listing (reached via edx.org/course/databases-1-introduction-to-relational-databases) is also "This course is archived". *(checked 2026-11-11)*
- **README.md:281** - "Machine Learning" - <https://www.deeplearning.ai/courses/machine-learning-specialization/>  
  **Status: MOVED.** Redirects to https://www.deeplearning.ai/specializations/machine-learning ("Machine Learning Specialization - DeepLearning.AI"): Andrew Ng, "Earn a certificate with PRO", "Enroll Now", "Also available on Coursera". The page does not say whether the course content is free without PRO, so cost is ambiguous. *(checked 2026-11-11)*
- **README.md:282** - "alternative" - <https://cseweb.ucsd.edu/~viscomp/classes/cse167/wi22/schedule.html>  
  **Status: UNVERIFIED.** Unreachable from this session (TLS error, "upstream request failed"); the mirror visualcomp.ucsd.edu/classes/cse167/wi22/ (found by search) also failed the same way. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 278 | Databases: Modeling and Theory | <https://www.edx.org/learn/databases/stanford-university-databases-modeling-and-theory> | edX page "StanfordOnline: Databases: Modeling and Theory \| edX" loads; page shows: Self-paced; Starts Nov 11 Ends Aug 31, 2030; Certificate Premium $69 USD; Audit Access Expires Nov 25; "Audit course" button present (the Certificate track is the one listed with "Graded assessments"). |
| 278 | chat | <https://discord.gg/pMFqNf4> | Discord public invite API (discord.com/api/v10/invites/pMFqNf4) returns server "OSSU" (id 744385009028431943), channel #dbs-modeling-theory, 36887 members, no expiry. |
| 279 | chat | <https://discord.gg/P8SPPyF> | Discord public invite API (discord.com/api/v10/invites/P8SPPyF) returns server "OSSU" (id 744385009028431943), channel #relational-dbs-sql, 36887 members, no expiry. |
| 280 | Databases: Semistructured Data | <https://www.edx.org/learn/relational-databases/stanford-university-databases-semistructured-data> | edX page "StanfordOnline: Databases: Semistructured Data \| edX" loads; page shows: Self-paced; Starts Nov 11 Ends Aug 31, 2030; Certificate Premium $69 USD; Audit Access Expires Nov 25; "Audit course" button present (the Certificate track is the one listed with "Graded assessments"). |
| 280 | chat | <https://discord.gg/duCJ3GN> | Discord public invite API (discord.com/api/v10/invites/duCJ3GN) returns server "OSSU" (id 744385009028431943), channel #dbs-semistructured-data, 36887 members, no expiry. |
| 281 | chat | <https://discord.gg/NcXHDjy> | Discord public invite API (discord.com/api/v10/invites/NcXHDjy) returns server "OSSU" (id 744385009028431943), channel #machine-learning, 36887 members, no expiry. |
| 282 | Computer Graphics | <https://www.edx.org/learn/computer-graphics/the-university-of-california-san-diego-computer-graphics> | edX page "UCSanDiegoX: Computer Graphics \| edX" loads; page shows: Self-paced; Starts Nov 11 Ends Dec 31, 2027; Certificate Premium $99 USD; Audit Access Expires Dec 23; "Audit course" button present (the Certificate track is the one listed with "Graded assessments"). |
| 282 | Basic Linear Algebra | <https://ossu.dev/precollege-math/coursepages/precalculus> | Loads "Precalculus Course \| Pre-College Math" with topics list (polynomial division, conic sections, etc.). |
| 282 | chat | <https://discord.gg/68WqMNV> | Discord public invite API (discord.com/api/v10/invites/68WqMNV) returns server "OSSU" (id 744385009028431943), channel #computer-graphics, 36887 members, no expiry. |
| 283 | Software Engineering: Introduction | <https://www.edx.org/learn/software-engineering/university-of-british-columbia-software-engineering-introduction> | edX page "UBCx: Software Engineering: Introduction \| edX" loads; page shows: Self-paced; Starts Nov 11 Ends Dec 31; Certificate Premium $125 USD; Audit Access Expires Jan 6, 2027; "Audit course" button present (the Certificate track is the one listed with "Graded assessments"). |
| 283 | alternative | <https://github.com/ubccpsc/310/blob/main/resources/README.md> | GitHub web blocked in this session (see Method); clone of ubccpsc/310 (default branch main) contains resources/README.md, headed "UBC CPSC - Software Engineering Resources", with readings and YouTube videos per module. Repo last pushed 2026-11-10. |
| 283 | chat | <https://discord.gg/5Qtcwtz> | Discord public invite API (discord.com/api/v10/invites/5Qtcwtz) returns server "OSSU" (id 744385009028431943), channel #software-engineering, 36887 members, no expiry. |


#### Core ethics

- **README.md:297** - "Ethics, Technology and Engineering" - <https://www.coursera.org/learn/ethics-technology-engineering>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*
- **README.md:298** - "Introduction to Intellectual Property" - <https://www.coursera.org/learn/introduction-intellectual-property>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*
- **README.md:299** - "Data Privacy Fundamentals" - <https://www.coursera.org/learn/northeastern-data-privacy>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 297 | chat | <https://discord.gg/6ttjPmzZbe> | Discord public invite API (discord.com/api/v10/invites/6ttjPmzZbe) returns server "OSSU" (id 744385009028431943), channel #ethics-tech-and-eng, 36887 members, no expiry. |
| 298 | chat | <https://discord.gg/YbuERswpAK> | Discord public invite API (discord.com/api/v10/invites/YbuERswpAK) returns server "OSSU" (id 744385009028431943), channel #ip-law, 36887 members, no expiry. |
| 299 | chat | <https://discord.gg/64J34ajNBd> | Discord public invite API (discord.com/api/v10/invites/64J34ajNBd) returns server "OSSU" (id 744385009028431943), channel #data-privacy, 36887 members, no expiry. |


#### Advanced programming

- **README.md:320** - "Parallel Programming" - <https://www.coursera.org/learn/scala-parallel-programming>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*
- **README.md:322** - "Introduction to Haskell" - <https://www.seas.upenn.edu/~cis194/fall16/>  
  **Status: UNVERIFIED.** Unreachable from this session (TLS error, "upstream request failed"); the mirrors www.cis.upenn.edu/~cis194/fall16 and www.engineering.upenn.edu/~cis1940/fall16/ (found by search) failed the same way. Search snippets describe the Fall 2016 page (Joachim Breitner, instructor), but I did not load it. *(checked 2026-11-11)*
- **README.md:323** - "alternative" - <https://github.com/ossu/computer-science/files/6085884/lpn.pdf>  
  **Status: UNVERIFIED.** GitHub web blocked in this session (see Method); this is an issue-attachment file; there is no git or API route to it, so it could not be checked. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 321 | Compilers | <https://www.edx.org/learn/computer-science/stanford-university-compilers> | edX page "StanfordOnline: Compilers \| edX" loads; page shows: Self-paced; Starts Nov 11 Ends Aug 31, 2030; Certificate Premium $249 USD; Audit Access Expires Jan 20, 2027; "Audit course" button present (the Certificate track is the one listed with "Graded assessments"). |
| 323 | Learn Prolog Now! | <https://www.let.rug.nl/bos/lpn//lpnpage.php?pageid=online> | Loads "Learn Prolog Now!" - "Free Online Version", chapter list from "Chapter 1 Facts, Rules, and Queries". |
| 324 | Software Debugging | <https://www.youtube.com/playlist?list=PLAwxTw4SYaPkxK63TiT88oEe-AIBhr96A> | YouTube playlist "Software Debugging" by Udacity, "265 videos"; description says the videos are part of the Udacity course cs259. No hidden/unavailable-video notice shown. |
| 325 | Software Testing | <https://www.youtube.com/playlist?list=PLAwxTw4SYaPkWVHeC_8aSIbSxE_NXI76g> | YouTube playlist "Software Testing", Udacity, "162 videos", "Last updated on Mar 27, 2015". |
| 327 | source | <https://github.com/LearnPrologNow/lpn> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/LearnPrologNow/lpn HEAD` succeeds and GitHub search API shows LearnPrologNow/lpn archived=false, description "Learn Prolog Now LaTeX sources". |
| 327 | CC license | <https://creativecommons.org/licenses/by-sa/4.0/> | Loads "Deed - Attribution-ShareAlike 4.0 International". |


#### Advanced systems

- **README.md:349** - "Computation Structures 1: Digital Circuits" - <https://learning.edx.org/course/course-v1:MITx+6.004.1x_3+3T2016>  
  **Status: UNVERIFIED.** edX learning app for an archived run; it loads with the course name ("Computation Structures 1: Digital Circuits") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. *(checked 2026-11-11)*
- **README.md:349** - "Nand2Tetris II" - <https://www.coursera.org/learn/nand2tetris2>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*
- **README.md:350** - "Computation Structures 2: Computer Architecture" - <https://learning.edx.org/course/course-v1:MITx+6.004.2x+3T2015>  
  **Status: UNVERIFIED.** edX learning app for an archived run; it loads with the course name ("Computation Structures 2") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. *(checked 2026-11-11)*
- **README.md:351** - "Computation Structures 3: Computer Organization" - <https://learning.edx.org/course/course-v1:MITx+6.004.3x_2+1T2017>  
  **Status: UNVERIFIED.** edX learning app for an archived run; it loads with the course name ("Computation Structures 3: Computer Organization") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 349 | alternative 1 | <https://ocw.mit.edu/courses/6-004-computation-structures-spring-2017/> | MIT OCW page "Computation Structures \| Electrical Engineering and Computer Science \| MIT OpenCourseWare" loads with syllabus/course navigation and course description. |
| 349 | alternative 2 | <https://ocw.mit.edu/courses/6-004-computation-structures-spring-2009/> | MIT OCW page "Computation Structures \| Electrical Engineering and Computer Science \| MIT OpenCourseWare" loads with syllabus/course navigation and course description. |


#### Advanced theory


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 373 | Theory of Computation | <https://ocw.mit.edu/courses/18-404j-theory-of-computation-fall-2020/> | MIT OCW page "Theory of Computation \| Mathematics \| MIT OpenCourseWare" loads with syllabus/course navigation and course description. |
| 373 | alternative | <https://www.youtube.com/playlist?list=PLEE7DF8F5E0203A56> | YouTube playlist "Shai Simonson in Computer Science", "153 videos". Note: the playlist owner shown is "Leonardo Silveira", not Simonson or ArsDigita, so it is a third-party compilation. |
| 373 | Mathematics for Computer Science | <https://openlearninglibrary.mit.edu/courses/course-v1:OCW+6.042J+2T2019/about> | MIT Open Learning Library about page "6.042J Mathematics for Computer Science" loads with "View Course" and "Enroll to Get Started". The page does not state a price. |
| 374 | Computational Geometry | <https://www.edx.org/learn/geometry/tsinghua-university-ji-suan-ji-he-computational-geometry> | edX page "TsinghuaX: 计算几何 \| Computational Geometry \| edX" loads; page shows: Self-paced; Starts Nov 11 Ends Feb 27, 2027; Certificate Premium $179 USD; Audit Access Expires Mar 3, 2027; "Audit course" button present (the Certificate track is the one listed with "Graded assessments"). |
| 375 | Algorithmic Game Theory | <https://timroughgarden.org/f13/f13.html> | Loads "Algorithmic Game Theory (CS364A), Fall 2013", instructor Tim Roughgarden, with the lecture list. |


#### Advanced Information Security

- **README.md:381** - "Web Security Fundamentals" - <https://www.edx.org/learn/computer-security/ku-leuven-web-security-fundamentals>  
  **Status: DEGRADED.** edX page "KULeuvenX: Web Security Fundamentals \| edX" loads but says "This course is archived"; its "View course materials" button goes to edX registration for run course-v1:KULeuvenX+WEBSECx+3T2017 (authn.edx.org/register?course_id=...). Whether the archived materials are complete after registering could not be checked without an account. *(checked 2026-11-11)*
- **README.md:382** - "Security Governance & Compliance" - <https://www.coursera.org/learn/security-governance-compliance>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*
- **README.md:383** - "Digital Forensics Concepts" - <https://www.coursera.org/learn/digital-forensics-concepts>  
  **Status: DEGRADED.** Coursera page loads with the right title and instructor. Its FAQ answer on access is the paywall wording quoted in finding F1 ("you'll need to purchase the Certificate experience"); no free or audit option is stated; enrolling needs an account, so I could not see which options this course offers. *(checked 2026-11-11)*
- **README.md:384** - "Secure Software Development: Requirements, Design, and Reuse" - <https://www.edx.org/learn/software-development/the-linux-foundation-secure-software-development-requirements-design-and-reuse>  
  **Status: DEAD.** Redirects (HTTP 200) to the edX school page https://www.edx.org/school/linuxfoundationx ("Online Courses from The Linux Foundation"). The course page no longer exists at this address; this is the quiet catalog-redirect failure. *(checked 2026-11-11)*
- **README.md:385** - "Secure Software Development: Implementation" - <https://www.edx.org/learn/software-development/the-linux-foundation-secure-software-development-implementation>  
  **Status: DEAD.** Redirects (HTTP 200) to the edX school page https://www.edx.org/school/linuxfoundationx ("Online Courses from The Linux Foundation"). The course page no longer exists at this address; this is the quiet catalog-redirect failure. *(checked 2026-11-11)*
- **README.md:386** - "Secure Software Development: Verification and More Specialized Topics" - <https://www.edx.org/learn/software-engineering/the-linux-foundation-secure-software-development-verification-and-more-specialized-topics>  
  **Status: DEAD.** Redirects (HTTP 200) to the edX school page https://www.edx.org/school/linuxfoundationx ("Online Courses from The Linux Foundation"). The course page no longer exists at this address; this is the quiet catalog-redirect failure. *(checked 2026-11-11)*


#### Advanced math

- **README.md:393** - "Linear Algebra" - <https://ocw.mit.edu/courses/mathematics/18-06sc-linear-algebra-fall-2011/>  
  **Status: MOVED.** Old-style OCW address; redirects to https://ocw.mit.edu/courses/18-06sc-linear-algebra-fall-2011/ ("Linear Algebra \| Mathematics \| MIT OpenCourseWare"), which loads with the full course navigation. Works today through the redirect. *(checked 2026-11-11)*
- **README.md:394** - "Introduction to Numerical Methods" - <https://ocw.mit.edu/courses/mathematics/18-335j-introduction-to-numerical-methods-spring-2019/index.htm>  
  **Status: MOVED.** Old-style OCW address; redirects to https://ocw.mit.edu/courses/18-335j-introduction-to-numerical-methods-spring-2019/ ("Introduction to Numerical Methods \| Mathematics \| MIT OpenCourseWare"), which loads with the full course navigation. Works today through the redirect. *(checked 2026-11-11)*
- **README.md:394** - "Linear Algebra" - <https://ocw.mit.edu/courses/mathematics/18-06sc-linear-algebra-fall-2011/>  
  **Status: MOVED.** Old-style OCW address; redirects to https://ocw.mit.edu/courses/18-06sc-linear-algebra-fall-2011/ ("Linear Algebra \| Mathematics \| MIT OpenCourseWare"), which loads with the full course navigation. Works today through the redirect. *(checked 2026-11-11)*
- **README.md:394** - "chat" - <https://discord.gg/FNEcNNq>  
  **Status: WORKING (link) / PROBLEM ON THIS LINE.** Discord public invite API (discord.com/api/v10/invites/FNEcNNq) returns server "OSSU" (id 744385009028431943), channel #calculus-1c-coordinate-systems-infinite-series, 36887 members, no expiry. **Line-level problem: this invite opens #calculus-1c-coordinate-systems-infinite-series, but the row is Introduction to Numerical Methods.** *(checked 2026-11-11)*
- **README.md:396** - "Probability" - <https://stat110.hsites.harvard.edu/>  
  **Status: UNVERIFIED.** Akamai "Access Denied" (HTTP 403) to both curl and the browser, including the /about page. The block is on my access; it says nothing about whether the site is up. *(checked 2026-11-11)*
- **README.md:396** - "Differentiation and Integration" - <https://mitxonline.mit.edu/courses/course-v1:MITxT+18.01.2x/>  
  **Status: MOVED.** Redirects to https://learn.mit.edu/courses/course-v1:MITxT+18.01.2x ("Calculus 1B: Integration \| MIT Learn"). Page shows "Format: Instructor-Paced", "Start: Oct 20, 202[6]", "Certificate Track $100" and "Learn for Free Free Audit this course Access to this course & course materials". *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 392 | Essence of Linear Algebra | <https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab> | YouTube playlist "Essence of linear algebra", 3Blue1Brown, "16 videos", "Last updated on Feb 18, 2025". |
| 392 | high school math | <https://ossu.dev/precollege-math> | Redirects to https://ossu.dev/precollege-math/ "Pre-College Math", the OSSU pre-college math curriculum. |
| 392 | chat | <https://discord.gg/m6wHbP6> | Discord public invite API (discord.com/api/v10/invites/m6wHbP6) returns server "OSSU" (id 744385009028431943), channel #essence-of-linear-algebra, 36887 members, no expiry. |
| 393 | chat | <https://discord.gg/k7nSWJH> | Discord public invite API (discord.com/api/v10/invites/k7nSWJH) returns server "OSSU" (id 744385009028431943), channel #linear-algebra, 36887 members, no expiry. |
| 395 | Introduction to Formal Logic | <https://forallx.openlogicproject.org/> | Loads "forall x: Calgary. A Free and Open Introduction to Formal Logic" - "a full-featured textbook on formal logic". |
| 395 | Set Theory | <https://www.youtube.com/playlist?list=PL5KkMZvBpo5AH_5GpxMiryJT6Dkj32H6N> | YouTube playlist "Exploring Mathematics: Set Theory", Eddie Woo, "11 videos". |
| 395 | chat | <https://discord.gg/MbM2Gg5> | Discord public invite API (discord.com/api/v10/invites/MbM2Gg5) returns server "OSSU" (id 744385009028431943), channel #intro-to-logic, 36887 members, no expiry. |
| 396 | chat | <https://discord.gg/UVjs9BU> | Discord public invite API (discord.com/api/v10/invites/UVjs9BU) returns server "OSSU" (id 744385009028431943), channel #probability, 36887 members, no expiry. |


#### Final project

- **README.md:414** - "linear ordinary differential equations" - <https://www.khanacademy.org/math/differential-equations>  
  **Status: UNVERIFIED.** Khan Academy served a bot check ("Client Challenge ... Oops, something went wrong"); content not visible. *(checked 2026-11-11)*
- **README.md:415** - "Data Mining (Specialization)" - <https://www.coursera.org/specializations/data-mining>  
  **Status: DEGRADED.** Specialization page loads with the right title. Its FAQ "Can I take the course for free?" answers "No, you cannot take this course for free." (full quote in finding F1). *(checked 2026-11-11)*
- **README.md:416** - "Big Data (Specialization)" - <https://www.coursera.org/specializations/big-data>  
  **Status: DEGRADED.** Specialization page loads with the right title. Its FAQ "Can I take the course for free?" answers "No, you cannot take this course for free." (full quote in finding F1). *(checked 2026-11-11)*
- **README.md:417** - "Internet of Things (Specialization)" - <https://www.coursera.org/specializations/internet-of-things>  
  **Status: DEGRADED.** Specialization page loads with the right title. Its FAQ "Can I take the course for free?" answers "No, you cannot take this course for free." (full quote in finding F1). *(checked 2026-11-11)*
- **README.md:418** - "Cloud Computing (Specialization)" - <https://www.coursera.org/specializations/cloud-computing>  
  **Status: DEGRADED.** Specialization page loads with the right title. Its FAQ "Can I take the course for free?" answers "No, you cannot take this course for free." (full quote in finding F1). *(checked 2026-11-11)*
- **README.md:419** - "Data Science (Specialization)" - <https://www.coursera.org/specializations/jhu-data-science>  
  **Status: DEGRADED.** Specialization page loads with the right title. Its FAQ "Can I take the course for free?" answers "No, you cannot take this course for free." (full quote in finding F1). The same FAQ also says "Yes, you can access the course for free via www.coursera.org/jhu" - the page contradicts itself, so free access is ambiguous. *(checked 2026-11-11)*
- **README.md:420** - "Functional Programming in Scala (Specialization)" - <https://www.coursera.org/specializations/scala>  
  **Status: DEGRADED.** Specialization page loads with the right title. Its FAQ "Can I take the course for free?" answers "No, you cannot take this course for free." (full quote in finding F1). *(checked 2026-11-11)*
- **README.md:421** - "Game Design and Development with Unity 2020 (Specialization)" - <https://www.coursera.org/specializations/game-design-and-development>  
  **Status: DEGRADED.** Specialization page loads with the right title. Its FAQ "Can I take the course for free?" answers "No, you cannot take this course for free." (full quote in finding F1). *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 413 | Fullstack Open | <https://fullstackopen.com/en/> | Loads "Full stack open" ("Deep Dive Into Modern Web Development ... Start course"). Banner: "A new course part has been released". |
| 414 | Modern Robotics | <https://modernrobotics.northwestern.edu> | Redirects within the site to /nu-gm-book-resource/foundations-of-robot-motion/ ("Foundations of Robot Motion - Modern Robotics"): video supplements for the Lynch & Park book with links to "Online Courses (Coursera)". I did not check the cost of those Coursera courses. |


#### Congratulations


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 433 | meetup.com | <https://www.meetup.com/> | Loads "Meetup \| Find Local Groups, Events, and Activities Near You". |
| 435 | Elixir | <https://elixir-lang.org/> | Loads "The Elixir programming language". |
| 436 | Rust | <https://www.rust-lang.org/> | Redirects to https://rust-lang.org/ "Rust Programming Language". |
| 437 | Idris | <https://www.idris-lang.org/> | Redirects to https://idris-lang.org/ "Idris: A Language for Type-Driven Development". |


#### Code of conduct


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 442 | OSSU's code of conduct | <https://github.com/ossu/code-of-conduct> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/ossu/code-of-conduct HEAD` succeeds and GitHub search API shows ossu/code-of-conduct archived=false. |


#### How to show your progress


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 446 | Fork | <https://www.freecodecamp.org/news/how-to-fork-a-github-repository/> | Loads "How to Fork a GitHub Repository - A Complete Workflow". |
| 446 | GitHub repo | <https://github.com/ossu/computer-science> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/ossu/computer-science HEAD` succeeds and GitHub search API shows ossu/computer-science archived=false, last push 2026-11-09. |
| 446 | kanban board | <https://en.wikipedia.org/wiki/Kanban_board> | Loads "Kanban board - Wikipedia". |


#### Team

- **README.md:453** - "Contributors" - <https://github.com/ossu/computer-science/graphs/contributors>  
  **Status: UNVERIFIED.** GitHub web blocked in this session (see Method); the repository exists, but the contributors graph page itself could not be loaded. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 450 | Eric Douglas | <https://github.com/ericdouglas> | GitHub web blocked in this session (see Method); GitHub search API (search/users q=user:ericdouglas) returns login ericdouglas, type User. |
| 451 | Josh Hanson | <https://github.com/joshmhanson> | GitHub web blocked in this session (see Method); GitHub search API (search/users q=user:joshmhanson) returns login joshmhanson, type User. |
| 452 | Waciuma Wanjohi | <https://github.com/waciumawanjohi> | GitHub web blocked in this session (see Method); GitHub search API (search/users q=user:waciumawanjohi) returns login waciumawanjohi, type User. |


### `coursepages/intro-cs/README.md`


#### Introduction to Computer Science and Programming using Python


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 5 | MIT's OCW | <https://ocw.mit.edu> | Loads "MIT OpenCourseWare \| Free Online Course Materials". |
| 9 | (bare) | <https://ocw.mit.edu/courses/6-100l-introduction-to-cs-and-programming-using-python-fall-2022/pages/material-by-lecture/> | MIT OCW page "Materials by Lecture \| Introduction to CS and Programming using Python \| Electrical Engineering and Computer Science \| MIT OpenCourseWare" loads with syllabus/course navigation and course description. |


#### ⚠️ Under Review


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 13 | (bare) | <https://github.com/ossu/computer-science/issues/1266> | GitHub web blocked in this session (see Method); GitHub search API returns issue #1266, state open, title "RFC: Replace 6.00.1x, PY4E, and CS50P for 6.100L Introduction to CS and Programming Using Python", 12 comments. |


#### Instructions


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 17 | course link | <https://ocw.mit.edu/courses/6-100l-introduction-to-cs-and-programming-using-python-fall-2022/pages/material-by-lecture/> | MIT OCW page "Materials by Lecture \| Introduction to CS and Programming using Python \| Electrical Engineering and Computer Science \| MIT OpenCourseWare" loads with syllabus/course navigation and course description. |
| 20 | course calendar | <https://ocw.mit.edu/courses/6-100l-introduction-to-cs-and-programming-using-python-fall-2022/pages/calendar/> | MIT OCW page "Calendar \| Introduction to CS and Programming using Python \| Electrical Engineering and Computer Science \| MIT OpenCourseWare" loads with syllabus/course navigation and course description. |
| 32 | (bare) | <https://discord.gg/jvchSm9> | Discord public invite API (discord.com/api/v10/invites/jvchSm9) returns server "OSSU" (id 744385009028431943), channel #6-100l-intro-to-computer-science, 36887 members, no expiry. |


#### Notes

- **coursepages/intro-cs/README.md:38** - "Anaconda" - <https://www.anaconda.com/docs/getting-started/anaconda/install/overview>  
  **Status: MOVED.** Redirects to https://www.anaconda.com/docs/getting-started/concepts/anaconda-or-miniconda ("Anaconda Distribution vs. Miniconda"), a comparison page rather than an install overview. Still relevant to the note, but not the page the link names. *(checked 2026-11-11)*
- **coursepages/intro-cs/README.md:38** - "here" - <https://github.com/spyder-ide/spyder/releases?q=6.0.8&expanded=true>  
  **Status: UNVERIFIED.** GitHub web blocked in this session (see Method); tag v6.0.8 exists in spyder-ide/spyder (git ls-remote --tags), but the releases page and its downloadable installers could not be viewed. *(checked 2026-11-11)*
- **coursepages/intro-cs/README.md:40** - "6.00.1x course on Edx" - <https://www.edx.org/course/introduction-to-computer-science-and-programming-7>  
  **Status: DEAD.** Redirects (HTTP 200) to the generic catalog https://www.edx.org/learn/computer-science?fbclid=... ("Online computer science courses and programs \| edX"); the 6.00.1x course page is gone at this address. *(checked 2026-11-11)*
- **coursepages/intro-cs/README.md:42** - "Introduction to Computation and Programming Using Python, third edi..." - <https://mitpress.mit.edu/9780262542364/introduction-to-computation-and-programming-using-python/>  
  **Status: UNVERIFIED.** Akamai "Access Denied" (HTTP 403) for both curl and the browser. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 41 | (bare) | <https://ocw.mit.edu/courses/6-0001-introduction-to-computer-science-and-programming-in-python-fall-2016/> | MIT OCW page "Introduction to Computer Science and Programming in Python \| Electrical Engineering and Computer Science \| MIT OpenCourseWare" loads with syllabus/course navigation and course description. |


#### Extra Practice


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 46 | https://introcomp.mit.edu/spring25/practice | <https://introcomp.mit.edu/spring25/practice> | Loads "6.100A+B" Extra Coding Practice with visible exercises ("Branching 1 ... Print \"both\" if they are both positive..."). It says "You are not logged in. Please Log In for full access" - running or checking answers appears to need an MIT login (ambiguous for outside learners). |


### `coursepages/intro-programming/README.md`


#### CS50P: Introduction to Programming with Python


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 12 | (bare) | <https://cs50.harvard.edu/python/> | Loads "CS50's Introduction to Programming with Python" (David J. Malan), OpenCourseWare. |


#### Instructions

- **coursepages/intro-programming/README.md:18** - "this video" - <https://cs50.harvard.edu/python/2022/shorts/visual_studio_code_for_cs50/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/shorts/visual_studio_code_for_cs50/ ("Visual Studio Code for CS50 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:20** - "(bare)" - <https://discord.gg/cBkssaJy5g>  
  **Status: DEGRADED.** Invite is valid (server "OSSU"), but Discord's invite API says it opens channel #missing-semester, while the line it sits on (coursepages/intro-programming/README.md:20) is "the OSSU chat for this course" for CS50P. Likely the wrong channel; OSSU maintainers would know which channel CS50P learners should use. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 18 | CS50 "codespace" | <https://cs50.dev> | Loads "Visual Studio Code for CS50 ... Log In" (GitHub login needed to use it, as the instructions say). |
| 21 | (bare) | <https://discord.gg/cs50> | Discord invite API returns server "cs50" (221,569 members), channel #rules. Line says it is not affiliated with OSSU, which is accurate as far as the server name shows. |
| 49 | sign in | <https://www.py4e.com/> | Loads PY4E home: "This web site is building a set of free materials, lectures, book and assignments". |
| 51 | this page | <https://www.py4e.com/book> | Loads PY4E book page ("The goal of this book is to provide an Informatics-oriented introduction to programming"). |
| 52 | (bare) | <https://discord.gg/syA242Z> | Discord public invite API (discord.com/api/v10/invites/syA242Z) returns server "OSSU" (id 744385009028431943), channel #python-for-everybody, 36887 members, no expiry. |


#### Course Materials

- **coursepages/intro-programming/README.md:25** - "Functions, Variables" - <https://cs50.harvard.edu/python/2022/weeks/0/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/weeks/0/ ("Week 0 Functions - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:25** - "Notes" - <https://cs50.harvard.edu/python/2022/notes/0/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/notes/0/ ("Lecture 0 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:25** - "Problem Set" - <https://cs50.harvard.edu/python/2022/psets/0/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/psets/0/ ("Problem Set 0 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:26** - "Conditionals" - <https://cs50.harvard.edu/python/2022/weeks/1/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/weeks/1/ ("Week 1 Conditionals - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:26** - "Notes" - <https://cs50.harvard.edu/python/2022/notes/1/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/notes/1/ ("Lecture 1 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:26** - "Problem Set" - <https://cs50.harvard.edu/python/2022/psets/1/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/psets/1/ ("Problem Set 1 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:27** - "Loops" - <https://cs50.harvard.edu/python/2022/weeks/2/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/weeks/2/ ("Week 2 Loops - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:27** - "Notes" - <https://cs50.harvard.edu/python/2022/notes/2/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/notes/2/ ("Lecture 2 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:27** - "Problem Set" - <https://cs50.harvard.edu/python/2022/psets/2/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/psets/2/ ("Problem Set 2 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:28** - "Exceptions" - <https://cs50.harvard.edu/python/2022/weeks/3/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/weeks/3/ ("Week 3 Exceptions - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:28** - "Notes" - <https://cs50.harvard.edu/python/2022/notes/3/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/notes/3/ ("Lecture 3 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:28** - "Problem Set" - <https://cs50.harvard.edu/python/2022/psets/3/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/psets/3/ ("Problem Set 3 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:29** - "Libraries" - <https://cs50.harvard.edu/python/2022/weeks/4/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/weeks/4/ ("Week 4 Libraries - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:29** - "Notes" - <https://cs50.harvard.edu/python/2022/notes/4/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/notes/4/ ("Lecture 4 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:29** - "Problem Set" - <https://cs50.harvard.edu/python/2022/psets/4/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/psets/4/ ("Problem Set 4 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:30** - "Unit Tests" - <https://cs50.harvard.edu/python/2022/weeks/5/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/weeks/5/ ("Week 5 Unit Tests - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:30** - "Notes" - <https://cs50.harvard.edu/python/2022/notes/5/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/notes/5/ ("Lecture 5 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:30** - "Problem Set" - <https://cs50.harvard.edu/python/2022/psets/5/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/psets/5/ ("Problem Set 5 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:31** - "File I/O" - <https://cs50.harvard.edu/python/2022/weeks/6/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/weeks/6/ ("Week 6 File I/O - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:31** - "Notes" - <https://cs50.harvard.edu/python/2022/notes/6/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/notes/6/ ("Lecture 6 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:31** - "Problem Set" - <https://cs50.harvard.edu/python/2022/psets/6/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/psets/6/ ("Problem Set 6 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:32** - "Regular Expressions" - <https://cs50.harvard.edu/python/2022/weeks/7/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/weeks/7/ ("Week 7 Regular Expressions - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:32** - "Notes" - <https://cs50.harvard.edu/python/2022/notes/7/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/notes/7/ ("Lecture 7 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:32** - "Problem Set" - <https://cs50.harvard.edu/python/2022/psets/7/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/psets/7/ ("Problem Set 7 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:33** - "Object-Oriented Programming" - <https://cs50.harvard.edu/python/2022/weeks/8/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/weeks/8/ ("Week 8 Object-Oriented Programming - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:33** - "Notes" - <https://cs50.harvard.edu/python/2022/notes/8/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/notes/8/ ("Lecture 8 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:33** - "Problem Set" - <https://cs50.harvard.edu/python/2022/psets/8/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/psets/8/ ("Problem Set 8 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:34** - "Et Cetera" - <https://cs50.harvard.edu/python/2022/weeks/9/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/weeks/9/ ("Week 9 Et Cetera - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:34** - "Notes" - <https://cs50.harvard.edu/python/2022/notes/9/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/notes/9/ ("Lecture 9 - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*
- **coursepages/intro-programming/README.md:34** - "Final Project" - <https://cs50.harvard.edu/python/2022/project/>  
  **Status: MOVED.** Redirects to https://cs50.harvard.edu/python/project/ ("Final Project - CS50's Introduction to Programming with Python"). The pinned 2022 address now serves the current unversioned edition, not the 2022 version; titles still match the link. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 57 | Installing Python | <https://www.py4e.com/lessons/install> | Loads PY4E lesson page "1: Installing Python" (1 / 17). |
| 58 | Why Program? | <https://www.py4e.com/lessons/intro> | Loads PY4E lesson page "2: Why Program?" (2 / 17). |
| 59 | Variables, expressions and statements | <https://www.py4e.com/lessons/memory> | Loads PY4E lesson page "3: Variables, expressions and statements" (3 / 17). |
| 60 | Conditional Execution | <https://www.py4e.com/lessons/logic> | Loads PY4E lesson page "4: Conditional Execution" (4 / 17). |
| 61 | Functions | <https://www.py4e.com/lessons/functions> | Loads PY4E lesson page "5: Functions" (5 / 17). |
| 62 | Loops and Iterations | <https://www.py4e.com/lessons/loops> | Loads PY4E lesson page "6: Loops and Iterations" (6 / 17). |
| 63 | Strings | <https://www.py4e.com/lessons/strings> | Loads PY4E lesson page "7: Strings" (7 / 17). |
| 64 | Files | <https://www.py4e.com/lessons/files> | Loads PY4E lesson page "8: Files" (8 / 17). |
| 65 | Lists | <https://www.py4e.com/lessons/lists> | Loads PY4E lesson page "9: Lists" (9 / 17). |
| 66 | Dictionaries | <https://www.py4e.com/lessons/dictionary> | Loads PY4E lesson page "10: Dictionaries" (10 / 17). |
| 67 | Tuples | <https://www.py4e.com/lessons/tuples> | Loads PY4E lesson page "11: Tuples" (11 / 17). |
| 68 | Regular Expressions | <https://www.py4e.com/lessons/regex> | Loads PY4E lesson page "12: Regular Expressions" (12 / 17). |
| 69 | Network Programming | <https://www.py4e.com/lessons/network> | Loads PY4E lesson page "13: Network Programming" (13 / 17). |
| 70 | Using Web Services | <https://www.py4e.com/lessons/servces> | Loads PY4E lesson page "14: Using" (14 / 17). |
| 71 | Object-Oriented Programming | <https://www.py4e.com/lessons/Objects> | Loads PY4E lesson page "15: Object-Oriented Programming" (15 / 17). |
| 72 | Databases | <https://www.py4e.com/lessons/database> | Loads PY4E lesson page "16: Databases" (16 / 17). |
| 73 | Data Visualization | <https://www.py4e.com/lessons/dataviz> | Loads PY4E lesson page "17: Data Visualization" (17 / 17). |


#### Python for Everybody

- **coursepages/intro-programming/README.md:43** - "HTML" - <https://www.py4e.com/html3>  
  **Status: UNVERIFIED.** Returns 301 to http://www.py4e.com/html3/ (a downgrade to plain HTTP), which this session cannot follow (HTTPS-only proxy). *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 41 | (bare) | <https://www.py4e.com/lessons> | Loads "PY4E - Python for Everybody" lessons index ("1: Installing Python ..."). |
| 43 | PDF | <http://do1.dr-chuck.com/pythonlearn/EN_us/pythonlearn.pdf> | http:// could not be fetched (this session's proxy is HTTPS-only); the https:// form of the same address returns application/pdf, 2,369,098 bytes. |
| 43 | EPUB | <http://do1.dr-chuck.com/pythonlearn/EN_us/pythonlearn.epub> | http:// could not be fetched (HTTPS-only proxy); the https:// form returns application/epub+zip, 4,513,517 bytes. |
| 43 | Buy hardcopy | <https://www.py4e.com/book> | Loads PY4E book page ("The goal of this book is to provide an Informatics-oriented introduction to programming"). |


### `coursepages/spd/README.md`


#### Systematic Program Design

- **coursepages/spd/README.md:9** - "(bare)" - <https://learning.edx.org/course/course-v1:UBCx+SPD1x+2T2015>  
  **Status: UNVERIFIED.** edX learning app for an archived run; it loads with the course name ("Systematic Program Design - Part 1") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. *(checked 2026-11-11)*
- **coursepages/spd/README.md:10** - "(bare)" - <https://learning.edx.org/course/course-v1:UBCx+SPD2x+2T2015>  
  **Status: UNVERIFIED.** edX learning app for an archived run; it loads with the course name ("Systematic Program Design - Part 2") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. *(checked 2026-11-11)*
- **coursepages/spd/README.md:11** - "(bare)" - <https://learning.edx.org/course/course-v1:UBCx+SPD3x+3T2015>  
  **Status: UNVERIFIED.** edX learning app for an archived run; it loads with the course name ("Systematic Program Design - Part 3") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 16 | (bare) | <https://www.edx.org/learn/coding/university-of-british-columbia-how-to-code-simple-data> | edX page "UBCx: How to Code: Simple Data \| edX" loads; page shows: Self-paced; Starts Nov 11 Ends Dec 31; Certificate Premium $125 USD; Audit Access Expires Dec 30; "Audit course" button present (the Certificate track is the one listed with "Graded assessments"). Note: the current run shows "Ends Dec 31" with no year, so I read it as this year; whether a new run follows was not shown. |
| 17 | (bare) | <https://www.edx.org/learn/coding/university-of-british-columbia-how-to-code-complex-data> | edX page "UBCx: How to Code: Complex Data \| edX" loads; page shows: Self-paced; Starts Nov 11 Ends Dec 31; Certificate Premium $125 USD; Audit Access Expires Dec 23; "Audit course" button present (the Certificate track is the one listed with "Graded assessments"). Note: the current run shows "Ends Dec 31" with no year, so I read it as this year; whether a new run follows was not shown. |


#### Instructions

- **coursepages/spd/README.md:25** - "link" - <https://learning.edx.org/course/course-v1:UBCx+SPD1x+2T2015>  
  **Status: UNVERIFIED.** edX learning app for an archived run; it loads with the course name ("Systematic Program Design - Part 1") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 29 | this playlist | <https://www.youtube.com/playlist?list=PL6NenTZG6KrqdcyTwGf09uBxjI5pbXuT7> | YouTube playlist "Extra Videos" by Systematic Program Design, "3 videos". |
| 30 | TA solver problem | <https://github.com/ossu/spd-starters/blob/main/final/ta-solver-starter.rkt> | GitHub web blocked in this session (see Method); clone of ossu/spd-starters (default branch main) contains final/ta-solver-starter.rkt. |
| 32 | this link | <https://github.com/ossu/spd-starters/archive/refs/heads/main.zip> | GitHub web blocked in this session (see Method); branch refs/heads/main exists (ls-remote), which is what this archive URL packages; the zip itself was not downloaded. |
| 32 | (bare) | <https://github.com/ossu/spd-starters> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/ossu/spd-starters HEAD` succeeds and GitHub search API shows ossu/spd-starters archived=false. |
| 37 | (bare) | <https://discord.gg/RfqAmGJ> | Discord public invite API (discord.com/api/v10/invites/RfqAmGJ) returns server "OSSU" (id 744385009028431943), channel #spd-first-half, 36887 members, no expiry. |
| 38 | (bare) | <https://discord.gg/kczJzpm> | Discord public invite API (discord.com/api/v10/invites/kczJzpm) returns server "OSSU" (id 744385009028431943), channel #spd-second-half, 36887 members, no expiry. |


#### Notes


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 54 | this youtube channel | <https://www.youtube.com/@systematicprogramdesign7962/playlists> | Channel "Systematic Program Design" (3.28K subscribers, 117 videos) with per-module playlists (01a - BSL ... 09b - Search). |


#### How do I test functions which are supposed to output random values?


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 106 | learn more about it here | <https://docs.racket-lang.org/htdp-langs/beginner-abbr.html#(form._((lib._lang%2Fhtdp-beginner-abbr..rkt> | Loads Racket docs "2 Beginning Student with List Abbreviations". |


#### Credits

- **coursepages/spd/README.md:110** - ""Systematic Program Design" on Edx" - <https://learning.edx.org/course/course-v1:UBCx+SPD1x+2T2015>  
  **Status: UNVERIFIED.** edX learning app for an archived run; it loads with the course name ("Systematic Program Design - Part 1") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 110 | CC BY-NC-SA | <https://creativecommons.org/licenses/by-nc-sa/4.0/> | Loads "Deed - Attribution-NonCommercial-ShareAlike 4.0 International". |


### `coursepages/spd/space-invaders-instructions.md`

- **coursepages/spd/space-invaders-instructions.md:13** - "Space_Invaders.webm" - <https://github.com/user-attachments/assets/a19d6e31-c931-475c-8ab5-647d2caa050f>  
  **Status: UNVERIFIED.** GitHub web blocked in this session (see Method); user-attachment asset; no git or API route to it, so it could not be checked. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 3 | Click here | <https://github.com/ossu/spd-starters/blob/main/final/space-invaders-starter.rkt> | GitHub web blocked in this session (see Method); clone of ossu/spd-starters (default branch main) contains final/space-invaders-starter.rkt. |
| 5 | here | <https://freeinvaders.org/> | Loads "Free Invaders", a playable Space Invaders page (Ruffle flash emulator, keyboard required), ad-supported. |


### `coursepages/class-based/README.md`


#### Class-Based Program Design


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 9 | (bare) | <https://course.ccs.neu.edu/cs2510sp22/index.html> | Loads "Fundamentals II Introduction to Class-based Program Design" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |


#### Schedule


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 13 | here | <https://course.ccs.neu.edu/cs2510sp22/Syllabus.html> | Loads "Syllabus" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 17 | 1 | <https://course.ccs.neu.edu/cs2510sp22/lecture1.html> | Loads "Lecture 1: Data Definitions in Java" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 17 | 2 | <https://course.ccs.neu.edu/cs2510sp22/lecture2.html> | Loads "Lecture 2: Data Definitions: Unions" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 17 | 3 | <https://course.ccs.neu.edu/cs2510sp22/lecture3.html> | Loads "Lecture 3: Methods for simple classes" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 17 | Lab 1 | <https://course.ccs.neu.edu/cs2510sp22/lab1.html> | Loads "Lab 1: Introduction to Eclipse and Simple Data Definitions" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 17 | Assignment 1 | <https://course.ccs.neu.edu/cs2510sp22/assignment1.html> | Loads "Assignment 1: Designing complex data" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 18 | 4 | <https://course.ccs.neu.edu/cs2510sp22/lecture4.html> | Loads "Lecture 4: Methods for unions" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 18 | 5 | <https://course.ccs.neu.edu/cs2510sp22/lecture5.html> | Loads "Lecture 5: Methods for self-referential lists" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 18 | 6 | <https://course.ccs.neu.edu/cs2510sp22/lecture6.html> | Loads "Lecture 6: Accumulator methods" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 18 | Lab 2 | <https://course.ccs.neu.edu/cs2510sp22/lab2.html> | Loads "Lab 2: Working with Self-Referential Data" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 18 | Assignment 2 | <https://course.ccs.neu.edu/cs2510sp22/assignment2.html> | Loads "Assignment 2: Designing methods for complex data" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 19 | 7 | <https://course.ccs.neu.edu/cs2510sp22/lecture7.html> | Loads "Lecture 7: Accumulator methods, continued" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 19 | 8 | <https://course.ccs.neu.edu/cs2510sp22/lecture8.html> | Loads "Lecture 8: Practice Design" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 19 | 9 | <https://course.ccs.neu.edu/cs2510sp22/lecture9.html> | Loads "Lecture 9: Abstract classes and inheritance" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 19 | Lab 3 | <https://course.ccs.neu.edu/cs2510sp22/lab3.html> | Loads "Lab 3: Working with the Debugger" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 19 | Assignment 3 | <https://course.ccs.neu.edu/cs2510sp22/assignment3.html> | Loads "Assignment 3: Designing methods for Complex Data, Practice with Lists and Trees, Drawing" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 20 | 10 | <https://course.ccs.neu.edu/cs2510sp22/lecture10.html> | Loads "Lecture 10: Customizing constructors for correctness and convenience" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 20 | 11 | <https://course.ccs.neu.edu/cs2510sp22/lecture11.html> | Loads "Lecture 11: Defining sameness for complex data, part 1" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 20 | 12 | <https://course.ccs.neu.edu/cs2510sp22/lecture12.html> | Loads "Lecture 12: Defining sameness for complex data, part 2" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 20 | Lab 4 | <https://course.ccs.neu.edu/cs2510sp22/lab4.html> | Loads "Lab 4: Working with Abstract Classes, Problem Solving" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 20 | Assignment 4 | <https://course.ccs.neu.edu/cs2510sp22/assignment4.html> | Loads "Assignment 4: Abstraction; Constructors" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 21 | 13 | <https://course.ccs.neu.edu/cs2510sp22/lecture13.html> | Loads "Lecture 13: Abstracting over behavior" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 21 | 14 | <https://course.ccs.neu.edu/cs2510sp22/lecture14.html> | Loads "Lecture 14: Abstractions over more than one argument" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 21 | Lab 5 | <https://course.ccs.neu.edu/cs2510sp22/lab5.html> | Loads "Lab 5: Working with the image library" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 21 | Assignment 5 | <https://course.ccs.neu.edu/cs2510sp22/assignment5.html> | Loads "Assignment 5: A Game" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 22 | 15 | <https://course.ccs.neu.edu/cs2510sp22/lecture15.html> | Loads "Lecture 15: Abstracting over types" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 22 | 16 | <https://course.ccs.neu.edu/cs2510sp22/lecture16.html> | Loads "Lecture 16: Visitors" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 22 | Lab 6 | <https://course.ccs.neu.edu/cs2510sp22/lab6.html> | Loads "Lab 6: Visitors and Generics" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 22 | Assignment 6 | <https://course.ccs.neu.edu/cs2510sp22/assignment6.html> | Loads "Assignment 6: Generic data, function objects" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 23 | 17 | <https://course.ccs.neu.edu/cs2510sp22/lecture17.html> | Loads "Lecture 17: Mutation" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 23 | 18 | <https://course.ccs.neu.edu/cs2510sp22/lecture18.html> | Loads "Lecture 18: Mutation inside structures" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 23 | 19 | <https://course.ccs.neu.edu/cs2510sp22/lecture19.html> | Loads "Lecture 19: Mutation, aliasing and testing" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 23 | Lab 7 | <https://course.ccs.neu.edu/cs2510sp22/lab7.html> | Loads "Lab 7: Working with Cyclic Data" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 23 | Assignment 7 | <https://course.ccs.neu.edu/cs2510sp22/assignment7.html> | Loads "Assignment 7: Visitors and Mutation" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 24 | 20 | <https://course.ccs.neu.edu/cs2510sp22/lecture20.html> | Loads "Lecture 20: Mutable data structures" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 24 | 21 | <https://course.ccs.neu.edu/cs2510sp22/lecture21.html> | Loads "Lecture 21: ArrayLists" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 24 | 22 | <https://course.ccs.neu.edu/cs2510sp22/lecture22.html> | Loads "Lecture 22: ArrayLists" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 24 | Lab 8 | <https://course.ccs.neu.edu/cs2510sp22/lab8.html> | Loads "Lab 8: Understanding Mutation" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 24 | Assignment 8 | <https://course.ccs.neu.edu/cs2510sp22/assignment8.html> | Loads "Assignment 8: Mutation and ArrayLists" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 25 | 23 | <https://course.ccs.neu.edu/cs2510sp22/lecture23.html> | Loads "Lecture 23: For-each loops and Counted-for loops" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 25 | 24 | <https://course.ccs.neu.edu/cs2510sp22/lecture24.html> | Loads "Lecture 24: While loops" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 25 | 25 | <https://course.ccs.neu.edu/cs2510sp22/lecture25.html> | Loads "Lecture 25: Iterator and Iterable" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 25 | Lab 9 | <https://course.ccs.neu.edu/cs2510sp22/lab9.html> | Loads "Lab 9: Imperative Worlds" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 25 | Assignment 9 Part 1 | <https://course.ccs.neu.edu/cs2510sp22/assignment9.html> | Loads "Assignment 9: Flood It" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 26 | 26 | <https://course.ccs.neu.edu/cs2510sp22/lecture26.html> | Loads "Lecture 26: Hashing and Equality" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 26 | 27 | <https://course.ccs.neu.edu/cs2510sp22/lecture27.html> | Loads "Lecture 27: Introduction to Big-O Analysis" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 26 | 30 | <https://course.ccs.neu.edu/cs2510sp22/lecture30.html> | Loads "Lecture 30: Breadth-first search and Depth-first search on graphs" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 26 | Lab 10 | <https://course.ccs.neu.edu/cs2510sp22/lab10.html> | Loads "Lab 10: Working with equals, hashCode, stacks, and iterators" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 26 | Assignment 9 Part 2 | <https://course.ccs.neu.edu/cs2510sp22/assignment9.html> | Loads "Assignment 9: Flood It" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 27 | 28 | <https://course.ccs.neu.edu/cs2510sp22/lecture28.html> | Loads "Lecture 28: Quicksort and Mergesort" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 27 | 29 | <https://course.ccs.neu.edu/cs2510sp22/lecture29.html> | Loads "Lecture 29: Priority Queues and Heapsort" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 27 | Lab 11 | <https://course.ccs.neu.edu/cs2510sp22/lab11.html> | Loads "Lab 11: An Introduction to Topological sort" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 28 | 31 | <https://course.ccs.neu.edu/cs2510sp22/lecture31.html> | Loads "Lecture 31: Dijkstra's Algorithm for single-source shortest paths" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 28 | 32 | <https://course.ccs.neu.edu/cs2510sp22/lecture32.html> | Loads "Lecture 32: Minimum Spanning Trees" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 28 | Lab 12 | <https://course.ccs.neu.edu/cs2510sp22/lab12.html> | Loads "Lab 12: An Introduction to the JUnit testing library" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 28 | Assignment 10 Part 1 | <https://course.ccs.neu.edu/cs2510sp22/assignment10.html> | Loads "Assignment 10: Maze of twisty passages" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 29 | 34 | <https://course.ccs.neu.edu/cs2510sp22/lecture34.html> | Loads "Lecture 34: Implementing Objects" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 29 | 35 | <https://course.ccs.neu.edu/cs2510sp22/lecture35.html> | Loads "Lecture 35: Dynamic Programming" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 29 | Assignment 10 Part 2 | <https://course.ccs.neu.edu/cs2510sp22/assignment10.html> | Loads "Assignment 10: Maze of twisty passages" (Northeastern CS2510 Spring 2022); the title matches the link number in the schedule table. |
| 36 | Lecture 28 | <https://youtube.com/playlist?list=PL_N7YxtCMPydJ-aBr4Ku9-q--D6vheOnp&si=XnBXaZKbBhqdUJgJ> | Redirects to the playlist "QuickSort" by LectureArchivesALIGN, "3 videos" (used for Lecture 28). |
| 37 | Lecture 30 | <https://www.youtube.com/watch?v=6WZo7sFFFlQ&list=PL_N7YxtCMPyea2YC3e-1s7SR_S3oWGjdb&index=1> | The watch page hit YouTube's rate limit (Google "unusual traffic" page). YouTube oEmbed for the video returns title "BFS DFS Review" by LectureArchivesALIGN, and the playlist page loads as "CS2510 Shortest Path" (2 videos: "BFS DFS Review", "Dijstra Cheapest Path"), which matches Lecture 30 (BFS/DFS). |


### `coursepages/ostep/README.md`


#### Operating Systems: Three Easy Pieces


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 3 | palladian | <https://github.com/palladian1> | GitHub web blocked in this session (see Method); GitHub search API (search/users q=user:palladian1) returns login palladian1, type User. |


#### Base Approach


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 15 | Github repository | <https://github.com/remzi-arpacidusseau/ostep-homework> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/remzi-arpacidusseau/ostep-homework HEAD` succeeds and GitHub search API shows remzi-arpacidusseau/ostep-homework archived=false. |


#### Course Links

- **coursepages/ostep/README.md:59** - "Lecture videos" - <https://pages.cs.wisc.edu/~remzi/Classes/537/Spring2018/Discussion/videos.html>  
  **Status: UNVERIFIED.** The page loads ("Videos ... Lecture 1: Introduction to the class ...") and links 54 distinct YouTube videos. YouTube's oEmbed endpoint returned 401 for 49 of them and 200 for 5, and watch pages were rate-limited, so I could not tell whether the 49 are merely non-embeddable or no longer public. Check one or two by hand. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 23 | Book | <https://pages.cs.wisc.edu/~remzi/OSTEP/> | Loads "Operating Systems: Three Easy Pieces" (Remzi H. and Andrea C. Arpaci-Dusseau) with the free chapter PDFs. |
| 24 | Homework | <https://pages.cs.wisc.edu/~remzi/OSTEP/Homework/homework.html> | Loads "Homework" ("Homeworks can be used to solidify your knowledge..."). |
| 25 | Homework Source Code Repo | <https://github.com/remzi-arpacidusseau/ostep-homework> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/remzi-arpacidusseau/ostep-homework HEAD` succeeds and GitHub search API shows remzi-arpacidusseau/ostep-homework archived=false. |
| 26 | Homework Solutions | <https://github.com/xxyzz/ostep-hw> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/xxyzz/ostep-hw HEAD` succeeds and GitHub search API shows xxyzz/ostep-hw archived=false, description "Operating Systems: Three Easy Pieces(OSTEP) homework and project solutions". |
| 57 | Course website | <https://pages.cs.wisc.edu/~remzi/Classes/537/Spring2018/> | Loads "CS-537: Intro to Operating Systems", UW-Madison, Spring 2018. |
| 58 | Book | <https://pages.cs.wisc.edu/~remzi/OSTEP/> | Loads "Operating Systems: Three Easy Pieces" (Remzi H. and Andrea C. Arpaci-Dusseau) with the free chapter PDFs. |
| 60 | Homework | <https://pages.cs.wisc.edu/~remzi/OSTEP/Homework/homework.html> | Loads "Homework" ("Homeworks can be used to solidify your knowledge..."). |
| 61 | Homework Source Code Repo | <https://github.com/remzi-arpacidusseau/ostep-homework> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/remzi-arpacidusseau/ostep-homework HEAD` succeeds and GitHub search API shows remzi-arpacidusseau/ostep-homework archived=false. |
| 62 | Homework Solutions | <https://github.com/xxyzz/ostep-hw> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/xxyzz/ostep-hw HEAD` succeeds and GitHub search API shows xxyzz/ostep-hw archived=false, description "Operating Systems: Three Easy Pieces(OSTEP) homework and project solutions". |
| 63 | Projects | <https://github.com/remzi-arpacidusseau/ostep-projects> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/remzi-arpacidusseau/ostep-projects HEAD` succeeds and GitHub search API shows remzi-arpacidusseau/ostep-projects archived=false. |
| 64 | xv6 | <https://github.com/mit-pdos/xv6-public> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/mit-pdos/xv6-public HEAD` succeeds and GitHub search API shows mit-pdos/xv6-public archived=false. Note: its README begins "NOTE: we have stopped maintaining the x86 version of xv6, and switched our efforts to the RISC-V version". The OSTEP projects are written against this x86 version, so it is still the right repo for them. |


#### C

- **coursepages/ostep/README.md:140** - "freely available online" - <https://inria.hal.science/hal-02383654v2/file/modernC.pdf>  
  **Status: UNVERIFIED.** HAL served a bot-check page ("Making sure you're not a bot!"), so the PDF was not retrieved. *(checked 2026-11-11)*
- **coursepages/ostep/README.md:142** - "*C Programming: A Modern Approach*" - <http://www.knking.com/books/c2/>  
  **Status: UNVERIFIED.** http:// not fetchable (HTTPS-only proxy) and the https:// form failed ("upstream request failed"). *(checked 2026-11-11)*
- **coursepages/ostep/README.md:150** - "Secure Coding Practices in C and C++" - <https://www.amazon.com/dp/0321822137>  
  **Status: UNVERIFIED.** Amazon returned "Access restricted. Continued access by an unauthorized AI agent violates Amazon's Conditions of Use"; I stopped requesting Amazon pages. *(checked 2026-11-11)*
- **coursepages/ostep/README.md:151** - "*The C Programming Language*" - <https://www.amazon.com/dp/0131103628>  
  **Status: UNVERIFIED.** Amazon returned "Access restricted. Continued access by an unauthorized AI agent violates Amazon's Conditions of Use"; I stopped requesting Amazon pages. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 32 | Dive into Systems: Chapter 1 and 2 | <https://diveintosystems.org/book/C1-C_intro/index.html> | Loads "Dive Into Systems" chapter 1 "By the C, the Beautiful C". |
| 32 | CS50 Manual pages | <https://manual.cs50.io> | Loads "CS50 Manual Pages". |
| 37 | reverse project | <https://github.com/remzi-arpacidusseau/ostep-projects/tree/master/initial-reverse> | GitHub web blocked in this session (see Method); clone of ostep-projects (default branch master) contains directory initial-reverse/. |
| 39 | here | <https://github.com/xxyzz/ostep-hw> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/xxyzz/ostep-hw HEAD` succeeds and GitHub search API shows xxyzz/ostep-hw archived=false, description "Operating Systems: Three Easy Pieces(OSTEP) homework and project solutions". |
| 147 | CS 50 Manual Pages | <https://manual.cs50.io> | Loads "CS50 Manual Pages". |
| 148 | cdecl | <https://cdecl.org> | Loads "cdecl: C gibberish <-> English". |
| 149 | C track on exercism.org | <https://exercism.org/tracks/C> | Loads "C on Exercism". |


#### Running the Projects

- **coursepages/ostep/README.md:88** - "Discord channel" - <https://discord.gg/MJ9YXyV>  
  **Status: WORKING (link) / PROBLEM ON THIS LINE.** Discord public invite API (discord.com/api/v10/invites/MJ9YXyV) returns server "OSSU" (id 744385009028431943), channel #computer-networking, 36887 members, no expiry. **Line-level problem: this invite opens #computer-networking, but the text asks OSTEP learners to report project problems; the OSTEP channel invite used in README.md:213 is https://discord.gg/wZNgpep (#operating-systems-3-easy-pieces).** *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 106 | this link | <https://pdos.csail.mit.edu/6.828/2018/tools.html> | Loads "6.828 / Fall 2018 ... Tools Used in 6.828". |
| 114 | (bare) | <https://github.com/remzi-arpacidusseau/ostep-homework/> | GitHub web blocked in this session (see Method); same as the address without the trailing slash, which exists (git ls-remote OK). |
| 115 | (bare) | <https://github.com/remzi-arpacidusseau/ostep-projects/> | GitHub web blocked in this session (see Method); same as the address without the trailing slash, which exists (git ls-remote OK). |
| 119 | the `xv6-public` repository | <https://github.com/mit-pdos/xv6-public> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/mit-pdos/xv6-public HEAD` succeeds and GitHub search API shows mit-pdos/xv6-public archived=false. Note: its README begins "NOTE: we have stopped maintaining the x86 version of xv6, and switched our efforts to the RISC-V version". The OSTEP projects are written against this x86 version, so it is still the right repo for them. |
| 123 | (bare) | <https://github.com/mit-pdos/xv6-public> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/mit-pdos/xv6-public HEAD` succeeds and GitHub search API shows mit-pdos/xv6-public archived=false. Note: its README begins "NOTE: we have stopped maintaining the x86 version of xv6, and switched our efforts to the RISC-V version". The OSTEP projects are written against this x86 version, so it is still the right repo for them. |


#### x86 Architecture and Assembly Language

- **coursepages/ostep/README.md:157** - "textbook" - <https://www.amazon.com/dp/013409266X>  
  **Status: UNVERIFIED.** Amazon returned "Access restricted. Continued access by an unauthorized AI agent violates Amazon's Conditions of Use"; I stopped requesting Amazon pages. *(checked 2026-11-11)*
- **coursepages/ostep/README.md:167** - "Writeup" - <http://csapp.cs.cmu.edu/3e/bomblab.pdf>  
  **Status: UNVERIFIED.** csapp.cs.cmu.edu is unreachable from this session (TLS "self-signed certificate in certificate chain" via curl; "upstream request failed" in the browser); http:// cannot be fetched through the HTTPS-only proxy. *(checked 2026-11-11)*
- **coursepages/ostep/README.md:167** - "self-study handout" - <https://csapp.cs.cmu.edu/3e/bomb.tar>  
  **Status: UNVERIFIED.** csapp.cs.cmu.edu is unreachable from this session (TLS "self-signed certificate in certificate chain" via curl; "upstream request failed" in the browser); http:// cannot be fetched through the HTTPS-only proxy. *(checked 2026-11-11)*
- **coursepages/ostep/README.md:169** - "Writeup" - <http://csapp.cs.cmu.edu/3e/attacklab.pdf>  
  **Status: UNVERIFIED.** csapp.cs.cmu.edu is unreachable from this session (TLS "self-signed certificate in certificate chain" via curl; "upstream request failed" in the browser); http:// cannot be fetched through the HTTPS-only proxy. *(checked 2026-11-11)*
- **coursepages/ostep/README.md:169** - "self-study handout" - <https://csapp.cs.cmu.edu/3e/target1.tar>  
  **Status: UNVERIFIED.** csapp.cs.cmu.edu is unreachable from this session (TLS "self-signed certificate in certificate chain" via curl; "upstream request failed" in the browser); http:// cannot be fetched through the HTTPS-only proxy. *(checked 2026-11-11)*
- **coursepages/ostep/README.md:173** - "CPU Registers x86" - <https://wiki.osdev.org/CPU_Registers_x86>  
  **Status: UNVERIFIED.** Cloudflare challenge ("Just a moment... Performing security verification"), HTTP 403. *(checked 2026-11-11)*
- **coursepages/ostep/README.md:175** - "GCC Inline Assembly HOWTO" - <https://www.ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html>  
  **Status: UNVERIFIED.** Unreachable from this session (TLS error, "upstream request failed"). *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 159 | Machine-Level Programming I: Basics | <https://scs.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=6e410255-3858-4e85-89c7-812c5845d197> | Loads Panopto viewer "Lecture 05: Machine-Level Programming I: Basics" with the table of contents (slide timestamps) visible without signing in; playback itself was not tested. |
| 160 | Machine-Level Programming II: Control | <https://scs.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=fc93c499-8fc9-4652-9a99-711058054afb> | Loads Panopto viewer "Lecture 06: Machine-Level Programming II: Control" with the table of contents (slide timestamps) visible without signing in; playback itself was not tested. |
| 161 | Machine-Level Programming III: Procedures | <https://scs.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=2994255f-923b-4ad4-8fb4-5def7fd802cd> | Loads Panopto viewer "Lecture 07: Machine-Level Programming III: Procedures" with the table of contents (slide timestamps) visible without signing in; playback itself was not tested. |
| 162 | Machine-Level Programming IV: Data | <https://scs.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=03308c94-fc20-40d8-8978-1a9b81c344ed> | Loads Panopto viewer "Lecture 08: Machine-Level Programming IV: Data" with the table of contents (slide timestamps) visible without signing in; playback itself was not tested. |
| 163 | Machine-Level Programming V: Advanced Topics | <https://scs.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=3f0bf9ca-d640-4798-b91a-73aed656a10a> | Loads Panopto viewer "Lecture 09: Machine-Level Programming V: Advanced Topics" with the table of contents (slide timestamps) visible without signing in; playback itself was not tested. |
| 164 | Linking | <https://scs.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=0aef84fc-a53b-49c6-bb43-14cb2b175249> | Loads Panopto viewer "Lecture 13: Linking" with the table of contents (slide timestamps) visible without signing in; playback itself was not tested. |
| 174 | *PC Assembly Language* | <https://pdos.csail.mit.edu/6.828/2018/readings/pcasm-book.pdf> | application/pdf, 846,920 bytes; first page reads "PC Assembly Language Paul A. Carter". |
| 176 | *Intel 80386 Programmer's Reference Manual* | <https://pdos.csail.mit.edu/6.828/2018/readings/i386.pdf> | application/pdf, 1,096,291 bytes; first page reads "INTEL 80386 PROGRAMMER'S REFERENCE MANUAL 1986". |


#### xv6


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 182 | book | <https://pdos.csail.mit.edu/6.828/2018/xv6/book-rev11.pdf> | application/pdf; first page reads "xv6 a simple, Unix-like teaching operating system Russ Cox Frans Kaashoek Robert Morris ... Draft as of September 4, [2018]". |
| 182 | PDF version | <https://pdos.csail.mit.edu/6.828/2018/xv6/xv6-rev11.pdf> | application/pdf; xv6 source listing ("Sep 4 06:29 2018 README Page 1 ... table of contents"). |
| 184 | annotated guide to xv6 | <https://github.com/palladian1/xv6-annotated> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/palladian1/xv6-annotated HEAD` succeeds and GitHub search API shows palladian1/xv6-annotated archived=false. |
| 186 | Here | <https://github.com/YehudaShapira/xv6-explained> | GitHub web blocked in this session (see Method); `git ls-remote https://github.com/YehudaShapira/xv6-explained HEAD` succeeds and GitHub search API shows YehudaShapira/xv6-explained archived=false. |
| 188 | here | <https://www.youtube.com/playlist?list=PLbtzT1TYeoMhTPzyTZboW_j7TPAnjv9XB> | YouTube playlist "The xv6 Kernel (Previous Version)" by hhp3, "38 videos". |


#### Miscellaneous

- **coursepages/ostep/README.md:197** - "OSDev Wiki" - <https://wiki.osdev.org>  
  **Status: UNVERIFIED.** Cloudflare challenge ("Just a moment... Performing security verification"), HTTP 403. *(checked 2026-11-11)*
- **coursepages/ostep/README.md:198** - "*Linux Kernel Development*" - <https://www.amazon.com/dp/0672329468>  
  **Status: UNVERIFIED.** Amazon returned "Access restricted. Continued access by an unauthorized AI agent violates Amazon's Conditions of Use"; I stopped requesting Amazon pages. *(checked 2026-11-11)*

| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 192 | This tutorial | <https://makefiletutorial.com> | Loads "Makefile Tutorial By Example". |
| 195 | GCC Command Options | <https://gcc.gnu.org/onlinedocs/gcc-11.1.0/gcc/Invoking-GCC.html#Invoking-GCC> | Loads "Invoking GCC" (3 GCC Command Options) for GCC 11.1.0, an older manual version but still valid for the flags discussed. |
| 196 | Linker Scripts | <https://sourceware.org/binutils/docs/ld/Scripts.html#Scripts> | Loads "Scripts (LD)" - "3 Linker Scripts". |


### `coursepages/ostep/Reading-order.md`


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 1 | palladian | <https://github.com/palladian1> | GitHub web blocked in this session (see Method); GitHub search API (search/users q=user:palladian1) returns login palladian1, type User. |


### `coursepages/ostep/Project-1B-initial-xv6.md`


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 3 | palladian | <https://github.com/palladian1> | GitHub web blocked in this session (see Method); GitHub search API (search/users q=user:palladian1) returns login palladian1, type User. |


### `coursepages/ostep/Project-2A-processes-shell.md`


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 2 | Palladian | <https://github.com/palladian1/> | GitHub web blocked in this session (see Method); same as the address without the trailing slash, which is a real user (search API: login palladian1, type User). |


### `coursepages/ostep/Scheduling-xv6-lottery.md`


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 1 | palladian | <https://github.com/palladian1> | GitHub web blocked in this session (see Method); GitHub search API (search/users q=user:palladian1) returns login palladian1, type User. |


### `coursepages/ostep/vm-xv6-intro.md`


#### (top of file)


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 1 | palladian | <https://github.com/palladian1> | GitHub web blocked in this session (see Method); GitHub search API (search/users q=user:palladian1) returns login palladian1, type User. |


#### WARNING:


| Line | Link text | URL | Evidence (all checked 2026-11-11) |
|--:|--|--|--|
| 9 | palladian | <https://github.com/palladian1> | GitHub web blocked in this session (see Method); GitHub search API (search/users q=user:palladian1) returns login palladian1, type User. |
| 11 | `start.zip` | <https://github.com/spamegg1/reviews/raw/master/courses/OSTEP/ostep-projects/vm-xv6-intro/start.zip> | GitHub web blocked in this session (see Method); clone of spamegg1/reviews (default branch master) contains courses/OSTEP/ostep-projects/vm-xv6-intro/start.zip. |

## Could not verify (check by hand)

These 39 URLs (from the checked files) are **not** reported as broken or as working. Each failure tells you about my access, not about the resource, unless stated otherwise. Highest priority: the two Kurose & Ross links (Core systems main course), then Stat 110 (Advanced math), the Haskell and Computer Graphics alternative sites, the six edX archived-run links (SPD's recommended runs and Computation Structures 1-3), and the OSTEP lecture videos.

| URL | Where used | What stopped me |
|--|--|--|
| <http://csapp.cs.cmu.edu/3e/attacklab.pdf> | coursepages/ostep/README.md:169 | csapp.cs.cmu.edu is unreachable from this session (TLS "self-signed certificate in certificate chain" via curl; "upstream request failed" in the browser); http:// cannot be fetched through the HTTPS-only proxy. |
| <http://csapp.cs.cmu.edu/3e/bomblab.pdf> | coursepages/ostep/README.md:167 | csapp.cs.cmu.edu is unreachable from this session (TLS "self-signed certificate in certificate chain" via curl; "upstream request failed" in the browser); http:// cannot be fetched through the HTTPS-only proxy. |
| <http://www.knking.com/books/c2/> | coursepages/ostep/README.md:142 | http:// not fetchable (HTTPS-only proxy) and the https:// form failed ("upstream request failed"). |
| <https://courses.edx.org/financial-assistance/> | README.md:59 | Redirects to home.edx.org and then to the login page authn.edx.org/login; the financial assistance information is not visible without logging in. |
| <https://csapp.cs.cmu.edu/3e/bomb.tar> | coursepages/ostep/README.md:167 | csapp.cs.cmu.edu is unreachable from this session (TLS "self-signed certificate in certificate chain" via curl; "upstream request failed" in the browser); http:// cannot be fetched through the HTTPS-only proxy. |
| <https://csapp.cs.cmu.edu/3e/target1.tar> | coursepages/ostep/README.md:169 | csapp.cs.cmu.edu is unreachable from this session (TLS "self-signed certificate in certificate chain" via curl; "upstream request failed" in the browser); http:// cannot be fetched through the HTTPS-only proxy. |
| <https://cseweb.ucsd.edu/~viscomp/classes/cse167/wi22/schedule.html> | README.md:282 | Unreachable from this session (TLS error, "upstream request failed"); the mirror visualcomp.ucsd.edu/classes/cse167/wi22/ (found by search) also failed the same way. |
| <https://discord.com/channels/744385009028431943/891411727294562314> | README.md:153 | Channel deep link inside the OSSU server (guild id 744385009028431943 matches the OSSU invites). Discord shows an empty app shell without login, so the channel name could not be confirmed. |
| <https://discord.com/channels/744385009028431943/891412022120579103> | README.md:155 | Channel deep link inside the OSSU server (guild id 744385009028431943 matches the OSSU invites). Discord shows an empty app shell without login, so the channel name could not be confirmed. |
| <https://discord.com/channels/744385009028431943/891412169638432788> | README.md:156 | Channel deep link inside the OSSU server (guild id 744385009028431943 matches the OSSU invites). Discord shows an empty app shell without login, so the channel name could not be confirmed. |
| <https://docs.google.com/spreadsheets/d/1y2kMsIg9VaHMVmw35x_aH1hpty3V-ZMuV2jA13P_Cgo/copy> | README.md:54 | A "/copy" link; redirects to Google sign-in ("Sign in to continue to Google Sheets"). The sheet cannot be seen without a Google account. |
| <https://gaia.cs.umass.edu/kurose_ross/online_lectures.htm> | README.md:214 | The proxy could not reach gaia.cs.umass.edu: curl gives a TLS error ("unable to get local issuer certificate") and the browser gets "upstream request failed". The same happened for www-net.cs.umass.edu. A web search shows this URL indexed with the title "8E Kurose & Ross header", and separate 9th-edition video pages (gaia.cs.umass.edu/kurose_ross/videos/1/ etc.). I did not load either, so I make no claim about their content. |
| <https://gaia.cs.umass.edu/kurose_ross/wireshark.php> | README.md:214 | Same access failure as the other gaia.cs.umass.edu link (TLS chain / upstream request failed). |
| <https://github.com/ossu/computer-science/files/6085884/lpn.pdf> | README.md:323 | GitHub web blocked in this session (see Method); this is an issue-attachment file; there is no git or API route to it, so it could not be checked. |
| <https://github.com/ossu/computer-science/graphs/contributors> | README.md:453 | GitHub web blocked in this session (see Method); the repository exists, but the contributors graph page itself could not be loaded. |
| <https://github.com/spyder-ide/spyder/releases?q=6.0.8&expanded=true> | coursepages/intro-cs/README.md:38 | GitHub web blocked in this session (see Method); tag v6.0.8 exists in spyder-ide/spyder (git ls-remote --tags), but the releases page and its downloadable installers could not be viewed. |
| <https://github.com/user-attachments/assets/a19d6e31-c931-475c-8ab5-647d2caa050f> | coursepages/spd/space-invaders-instructions.md:13 | GitHub web blocked in this session (see Method); user-attachment asset; no git or API route to it, so it could not be checked. |
| <https://inria.hal.science/hal-02383654v2/file/modernC.pdf> | coursepages/ostep/README.md:140 | HAL served a bot-check page ("Making sure you're not a bot!"), so the PDF was not retrieved. |
| <https://learning.edx.org/course/course-v1:MITx+6.004.1x_3+3T2016> | README.md:349 | edX learning app for an archived run; it loads with the course name ("Computation Structures 1: Digital Circuits") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. |
| <https://learning.edx.org/course/course-v1:MITx+6.004.2x+3T2015> | README.md:350 | edX learning app for an archived run; it loads with the course name ("Computation Structures 2") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. |
| <https://learning.edx.org/course/course-v1:MITx+6.004.3x_2+1T2017> | README.md:351 | edX learning app for an archived run; it loads with the course name ("Computation Structures 3: Computer Organization") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. |
| <https://learning.edx.org/course/course-v1:UBCx+SPD1x+2T2015> | coursepages/spd/README.md:9, coursepages/spd/README.md:25, coursepages/spd/README.md:110 | edX learning app for an archived run; it loads with the course name ("Systematic Program Design - Part 1") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. |
| <https://learning.edx.org/course/course-v1:UBCx+SPD2x+2T2015> | coursepages/spd/README.md:10 | edX learning app for an archived run; it loads with the course name ("Systematic Program Design - Part 2") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. |
| <https://learning.edx.org/course/course-v1:UBCx+SPD3x+3T2015> | coursepages/spd/README.md:11 | edX learning app for an archived run; it loads with the course name ("Systematic Program Design - Part 3") but says "To see course content, sign in or register" / "You must be enrolled in the course to see course content." Without an account I could not confirm that enrollment is still accepted or that content is complete. |
| <https://mitpress.mit.edu/9780262542364/introduction-to-computation-and-programming-using-python/> | coursepages/intro-cs/README.md:42 | Akamai "Access Denied" (HTTP 403) for both curl and the browser. |
| <https://pages.cs.wisc.edu/~remzi/Classes/537/Spring2018/Discussion/videos.html> | coursepages/ostep/README.md:59 | The page loads ("Videos ... Lecture 1: Introduction to the class ...") and links 54 distinct YouTube videos. YouTube's oEmbed endpoint returned 401 for 49 of them and 200 for 5, and watch pages were rate-limited, so I could not tell whether the 49 are merely non-embeddable or no longer public. Check one or two by hand. |
| <https://stat110.hsites.harvard.edu/> | README.md:396 | Akamai "Access Denied" (HTTP 403) to both curl and the browser, including the /about page. The block is on my access; it says nothing about whether the site is up. |
| <https://wiki.osdev.org> | coursepages/ostep/README.md:197 | Cloudflare challenge ("Just a moment... Performing security verification"), HTTP 403. |
| <https://wiki.osdev.org/CPU_Registers_x86> | coursepages/ostep/README.md:173 | Cloudflare challenge ("Just a moment... Performing security verification"), HTTP 403. |
| <https://www.amazon.com/dp/0131103628> | coursepages/ostep/README.md:151 | Amazon returned "Access restricted. Continued access by an unauthorized AI agent violates Amazon's Conditions of Use"; I stopped requesting Amazon pages. |
| <https://www.amazon.com/dp/013409266X> | coursepages/ostep/README.md:157 | Amazon returned "Access restricted. Continued access by an unauthorized AI agent violates Amazon's Conditions of Use"; I stopped requesting Amazon pages. |
| <https://www.amazon.com/dp/0321822137> | coursepages/ostep/README.md:150 | Amazon returned "Access restricted. Continued access by an unauthorized AI agent violates Amazon's Conditions of Use"; I stopped requesting Amazon pages. |
| <https://www.amazon.com/dp/0672329468> | coursepages/ostep/README.md:198 | Amazon returned "Access restricted. Continued access by an unauthorized AI agent violates Amazon's Conditions of Use"; I stopped requesting Amazon pages. |
| <https://www.coursera.support/s/article/209819033-Apply-for-Financial-Aid-or-a-Scholarship?language=en_US> | README.md:59 | Redirects to https://www.coursera.support/s/article/learner-000001455?language=en_US (title "Coursera Help Center"), but the page never rendered: the body shows only "Sorry to interrupt CSS Error Refresh". Whether the article still covers financial aid is unknown. |
| <https://www.ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html> | coursepages/ostep/README.md:175 | Unreachable from this session (TLS error, "upstream request failed"). |
| <https://www.khanacademy.org/math/differential-equations> | README.md:414 | Khan Academy served a bot check ("Client Challenge ... Oops, something went wrong"); content not visible. |
| <https://www.linkedin.com/school/11272443/> | README.md:80 | Redirects to LinkedIn login (session_redirect=/school/11272443/); the school page is not visible without logging in. |
| <https://www.py4e.com/html3> | coursepages/intro-programming/README.md:43 | Returns 301 to http://www.py4e.com/html3/ (a downgrade to plain HTTP), which this session cannot follow (HTTPS-only proxy). |
| <https://www.seas.upenn.edu/~cis194/fall16/> | README.md:322, extras/courses.md:26 | Unreachable from this session (TLS error, "upstream request failed"); the mirrors www.cis.upenn.edu/~cis194/fall16 and www.engineering.upenn.edu/~cis1940/fall16/ (found by search) failed the same way. Search snippets describe the Fall 2016 page (Joachim Breitner, instructor), but I did not load it. |

## Not yet checked (resume here)

The following files were **not checked** in this pass, in curriculum order: `extras/courses.md`, `extras/readings.md`, `extras/other_curricula.md`, `extras/puzzles-practice-plods.md`, `FAQ.md`, `HELP.md`, `CONTRIBUTING.md`, `CURRICULAR_GUIDELINES.md`, `CHANGELOG.md`, `.github/ISSUE_TEMPLATE/request-for-comment-template.md`. Together they hold 175 link occurrences: 170 distinct URLs not seen anywhere in the checked files, plus a few URLs that also appear in checked files (marked in the Note column; re-check those lines in their own context).

The first automated fetch did load every one of these URLs. I have deliberately **not** turned that into statuses, because I have not read each page against its link text. A few plain observations from those page loads are worth having when the work resumes. They are facts about what came back, not reviewed findings:

- `extras/courses.md:23` (Delft "Introduction to Functional Programming", edX): HTTP 404.
- `extras/courses.md:11` (MIT 6.00.2x on edX): redirects to the generic edX computer-science catalog.
- `extras/courses.md:42` (MIT Probability on edX): redirects to "MIT related data science courses".
- `extras/courses.md:50` (Udacity cs344): HTTP 404. Its "alt" YouTube playlist (`PLGvfHSgImk4aweyWlhBXNF6XISY3um82_`) shows "The playlist does not exist."
- `extras/courses.md:20` (IITBombayX Programming Basics) and `extras/courses.md:102` (Power Searching with Google): edX says "This course is archived".
- Coursera courses in `extras/courses.md`: the Princeton and ENS courses (Algorithms I/II, Analysis of Algorithms, Computer Architecture, Approximation Algorithms I/II, Statistical Mechanics) have an FAQ answering "Do I need to pay for this course?" with "No... all features of this course are available for free." The other Coursera course pages there (`/learn/...`) carry the same paywall wording as F1.
- Amazon book listings in `extras/readings.md`: Amazon asks AI agents not to access its pages (see Method). These will need checking by hand or via publisher pages.


#### `extras/courses.md` (70 occurrences)

| Line | Link text | URL | Note |
|--:|--|--|--|
| 11 | Introduction to Computational Thinking and Data Science | <https://www.edx.org/learn/computer-science/massachusetts-institute-of-technology-introduction-to-computational-thinking-and-data-science#!> | not checked |
| 11 | alt | <https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-0002-introduction-to-computational-thinking-and-data-science-fall-2016/> | not checked |
| 12 | Introduction to Computer Science - CS50 | <https://www.edx.org/learn/computer-science/harvard-university-cs50-s-introduction-to-computer-science#!> | not checked |
| 12 | alt | <https://cs50.harvard.edu/x/> | not checked |
| 13 | Introduction to Computer Science (Udacity) | <https://www.udacity.com/course/intro-to-computer-science--cs101> | not checked |
| 14 | An Introduction to Interactive Programming in Python (Part 1) | <https://www.coursera.org/learn/interactive-python-1> | not checked |
| 15 | An Introduction to Interactive Programming in Python (Part 2) | <https://www.coursera.org/learn/interactive-python-2> | not checked |
| 16 | Computing In Python, Part I: Fundamentals and Procedural Programming | <https://www.edx.org/learn/python/the-georgia-institute-of-technology-computing-in-python-i-fundamentals-and-procedural-programming> | not checked |
| 17 | Computing In Python, Part II: Control Structures | <https://www.edx.org/learn/python/the-georgia-institute-of-technology-computing-in-python-ii-control-structures> | not checked |
| 18 | Computing In Python, Part III: Data Structures | <https://www.edx.org/learn/python/the-georgia-institute-of-technology-computing-in-python-iii-data-structures> | not checked |
| 19 | Computing In Python, Part IV: Objects & Algorithms | <https://www.edx.org/learn/python/the-georgia-institute-of-technology-computing-in-python-iv-objects-algorithms> | not checked |
| 20 | Programming Basics | <https://www.edx.org/learn/computer-programming/iitbombay-programming-basics> | not checked |
| 21 | Object-Oriented Programming with Java | <https://java-programming.mooc.fi/> | not checked |
| 22 | Introduction to Programming with MATLAB | <https://www.coursera.org/learn/matlab> | not checked |
| 23 | Introduction to Functional Programming | <https://www.edx.org/learn/computer-programming/delft-university-of-technology-introduction-to-functional-programming> | not checked |
| 24 | The Structure and Interpretation of Computer Programs (2022, Python) | <http://cs61a.org/> | not checked |
| 25 | The Structure and Interpretation of Computer Programs (2011, Scheme) | <https://romanbird.github.io/sicp/> | not checked |
| 26 | Introduction to Haskell | <https://www.seas.upenn.edu/~cis194/fall16/> | URL also used in a checked file; status there: unverified (re-check this line in its own context) |
| 32 | Effective Thinking Through Mathematics | <https://www.edx.org/learn/math/the-university-of-texas-at-austin-effective-thinking-through-mathematics-2> | not checked |
| 33 | Introduction to Mathematical Thinking | <https://www.coursera.org/learn/mathematical-thinking> | not checked |
| 34 | High School Math | <https://www.khanacademy.org/math/high-school-math> | not checked |
| 35 | Precalculus | <https://www.futurelearn.com/courses/precalculus> | not checked |
| 36 | Advanced Precalculus | <https://www.futurelearn.com/courses/advanced-precalculus> | not checked |
| 37 | Calculus Applied! | <https://www.edx.org/learn/calculus/harvard-university-calculus-applied> | not checked |
| 38 | Introduction to Probability and Data | <https://www.coursera.org/learn/probability-intro> | not checked |
| 39 | Linear Algebra (Strang) | <https://ocw.mit.edu/courses/mathematics/18-06-linear-algebra-spring-2010/index.htm> | not checked |
| 40 | Introduction to Computational Thinking | <https://computationalthinking.mit.edu/Spring21/#introduction_to_computational_thinking> | not checked |
| 41 | Multivariable Calculus | <https://ocw.mit.edu/courses/mathematics/18-02sc-multivariable-calculus-fall-2010/index.htm> | not checked |
| 42 | Introduction to Probability - The Science of Uncertainty | <https://www.edx.org/learn/probability/massachusetts-institute-of-technology-probability-the-science-of-uncertainty-and-data> | not checked |
| 43 | Matrix Methods In Data Analysis, Signal Processing, And Machine Lea... | <https://ocw.mit.edu/courses/18-065-matrix-methods-in-data-analysis-signal-processing-and-machine-learning-spring-2018/> | not checked |
| 49 | Cloud Computing / Distributed Programming | <https://www.coursera.org/learn/cloud-computing> | not checked |
| 50 | Introduction to Parallel Programming | <https://www.udacity.com/course/--cs344> | not checked |
| 50 | alt | <https://www.youtube.com/playlist?list=PLGvfHSgImk4aweyWlhBXNF6XISY3um82_> | not checked |
| 50 | HW | <https://colab.research.google.com/github/depctg/udacity-cs344-colab> | not checked |
| 51 | Intro to Computer Systems | <http://www.cs.cmu.edu/afs/cs.cmu.edu/academic/class/15213-f15/www/> | not checked |
| 51 | Labs | <http://csapp.cs.cmu.edu/3e/labs.html> | not checked |
| 52 | Great Ideas in Computer Architecture (Machine Structures) | <https://web.archive.org/web/20190919235114/https://inst.eecs.berkeley.edu/~cs61c/fa14/> | not checked |
| 52 | Lectures | <https://archive.org/details/ucberkeley_webcast_itunesu_915550404> | not checked |
| 53 | Computer Architecture | <https://www.coursera.org/learn/comparch> | not checked |
| 54 | Operating System Engineering | <http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-828-operating-system-engineering-fall-2012/> | not checked |
| 55 | Introduction to Operating Systems | <https://www.udacity.com/course/operating-systems--ud923> | not checked |
| 56 | Advanced Operating Systems | <https://www.udacity.com/course/ai-deep-learning--ud189> | not checked |
| 57 | Networking for Web Developers | <https://www.udacity.com/course/computer-networking--ud436> | not checked |
| 58 | Playlist | <https://www.youtube.com/playlist?list=PLrw6a1wE39_tb2fErI4-WkMbsvGQk9_UB> | not checked |
| 58 | Course site | <http://nil.csail.mit.edu/6.824/2020/schedule.html> | not checked |
| 58 | Self-studying 6.824 | <https://lieuzhenghong.com/mit_6.824_self_study/> | not checked |
| 58 | 6.824 Discord group for further help | <https://discord.gg/KbhkEqpBqC> | not checked |
| 64 | Algorithms, Part I | <https://www.coursera.org/learn/algorithms-part1> | not checked |
| 65 | Algorithms, Part II | <https://www.coursera.org/learn/algorithms-part2> | not checked |
| 66 | Analysis of Algorithms (Sedgewick) | <https://www.coursera.org/learn/analysis-of-algorithms> | not checked |
| 67 | Analysis of Algorithms (Skiena) | <http://www3.cs.stonybrook.edu/~skiena/373/> | not checked |
| 68 | Programming Challenges (Skiena) | <http://www3.cs.stonybrook.edu/~skiena/392/> | not checked |
| 69 | Data Structures and Algorithms (Specialization) | <https://www.coursera.org/specializations/data-structures-algorithms> | not checked |
| 70 | Algorithmic Thinking (Part 1) | <https://www.coursera.org/learn/algorithmic-thinking-1/> | not checked |
| 71 | Algorithmic Thinking (Part 2) | <https://www.coursera.org/learn/algorithmic-thinking-2/> | not checked |
| 72 | Statistical Mechanics: Algorithms and Computations | <https://www.coursera.org/learn/statistical-mechanics/> | not checked |
| 73 | Approximation Algorithms Part I | <https://www.coursera.org/learn/approximation-algorithms-part-1/> | not checked |
| 74 | Approximation Algorithms Part II | <https://www.coursera.org/learn/approximation-algorithms-part-2/> | not checked |
| 75 | Design And Analysis Of Algorithms | <https://ocw.mit.edu/courses/6-046j-design-and-analysis-of-algorithms-spring-2015/> | not checked |
| 81 | Using Databases with Python | <https://www.coursera.org/learn/python-databases> | not checked |
| 82 | Database Systems | <https://15721.courses.cs.cmu.edu/spring2016/> | not checked |
| 83 | Database Management Essentials | <https://www.coursera.org/learn/database-management> | not checked |
| 84 | Intro to Artificial Intelligence | <https://www.udacity.com/course/intro-to-artificial-intelligence--cs271> | not checked |
| 85 | Intro to Machine Learning | <https://www.udacity.com/course/intro-to-machine-learning--ud120> | not checked |
| 86 | Big Data Science with the BD2K-LINCS Data Coordination and Integrat... | <https://www.coursera.org/course/bd2klincs> | not checked |
| 92 | How to Use Git and GitHub | <https://www.udacity.com/blog/2015/06/a-beginners-git-github-tutorial.html> | not checked |
| 93 | Kubernetes Certified Application Developer | <https://www.udemy.com/course/certified-kubernetes-application-developer/> | not checked |
| 100 | Learning How to Learn | <https://www.coursera.org/learn/learning-how-to-learn> | not checked |
| 101 | Mindshift | <https://www.coursera.org/learn/mindshift> | not checked |
| 102 | Powersearching with Google | <https://www.edx.org/learn/google-power-searching/google-power-searching-with-google> | not checked |

#### `extras/readings.md` (66 occurrences)

| Line | Link text | URL | Note |
|--:|--|--|--|
| 14 | Introduction to Computation and Programming Using Python 3e | <https://mitpress.mit.edu/books/introduction-computation-and-programming-using-python-third-edition> | not checked |
| 15 | Think Python 2e | <http://greenteapress.com/wp/think-python-2e/> | not checked |
| 16 | How to Design Programs 2e | <https://www.htdp.org/> | not checked |
| 17 | Structure and Interpretation of Computer Programs 2e | <https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book.html> | not checked |
| 18 | The Structure and Interpretation of Computer Programs (2021, JavaSc... | <https://sourceacademy.org/sicpjs/index> | not checked |
| 19 | Concepts, Techniques, and Models of Computer Programming | <https://www.amazon.com/gp/product/0262220695> | not checked |
| 20 | Design Patterns: Elements of Reusable Object-Oriented Software | <https://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612> | not checked |
| 21 | Refactoring | <https://www.refactoring.com/> | not checked |
| 22 | Clean Code | <https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882> | not checked |
| 23 | Code Complete 2e | <https://www.amazon.com/Code-Complete-Practical-Handbook-Construction/dp/0735619670> | not checked |
| 24 | The Pragmatic Programmer 2e | <https://pragprog.com/titles/tpp20/the-pragmatic-programmer-20th-anniversary-edition/> | not checked |
| 25 | Programming Languages: Application and Interpretation | <http://cs.brown.edu/~sk/Publications/Books/ProgLangs/> | not checked |
| 26 | Programming and Programming Languages | <https://papl.cs.brown.edu/2018/> | not checked |
| 27 | Competitive Programming | <https://cpbook.net/> | not checked |
| 28 | Introduction to computing in Java | <https://introcs.cs.princeton.edu/java/home/> | not checked |
| 34 | Calculus Made Easy | <http://www.gutenberg.org/ebooks/33283> | not checked |
| 35 | Ximera: Interactive Calculus Textbooks | <https://ximera.osu.edu/> | not checked |
| 35 | Ximera team | <https://ximera.osu.edu/about/team> | not checked |
| 36 | Discrete Mathematics with Applications (4th Edition) | <http://www.amazon.com/Discrete-Mathematics-Applications-Susanna-Epp/dp/0495391328/> | not checked |
| 37 | Discrete Mathematics: An Open Introduction | <https://discrete.openmathbooks.org/dmoi4/frontmatter.html> | not checked |
| 38 | Applied Discrete Structures | <http://faculty.uml.edu/klevasseur/ads2/> | not checked |
| 39 | Grinstead and Snell’s Introduction to Probability | <https://math.dartmouth.edu/~prob/prob/prob.pdf> | not checked |
| 40 | Linear Algebra for Everyone | <https://math.mit.edu/~gs/everyone/> | not checked |
| 41 | The Art of Linear Algebra | <https://github.com/kenjihiranabe/The-Art-of-Linear-Algebra> | not checked |
| 47 | But How Do It Know? | <http://www.buthowdoitknow.com/> | not checked |
| 48 | Computer Systems: A Programmer's Perspective (3rd Edition) | <http://csapp.cs.cmu.edu/> | not checked |
| 49 | Modern Operating Systems (4th Edition) | <http://www.amazon.com/Modern-Operating-Systems-Andrew-Tanenbaum/dp/013359162X/> | not checked |
| 50 | Computer Organization and Design: The Hardware/Software Interface (... | <https://www.amazon.com/Computer-Organization-Design-MIPS-Architecture/dp/0128201096/> | not checked |
| 51 | Computer Networks (5th Edition) | <http://www.amazon.com/Computer-Networks-5th-Andrew-Tanenbaum/dp/0132126958/> | not checked |
| 52 | Computer Networking: A Top-Down Approach (8th Edition) | <https://gaia.cs.umass.edu/kurose_ross/index.html> | not checked |
| 53 | Computer Networks: A Systems Approach | <https://book.systemsapproach.org/> | not checked |
| 54 | Distributed Systems: Principles and Paradigms | <https://www.amazon.com/Distributed-Systems-Principles-Andrew-Tanenbaum/dp/153028175X> | not checked |
| 55 | Operating Systems Design and Implementation | <https://www.amazon.com/Operating-Systems-Design-Implementation-3rd/dp/0131429388> | not checked |
| 56 | Crafting Interpreters | <https://www.craftinginterpreters.com/contents.html> | not checked |
| 57 | Principles of Compiler Design | <https://www.amazon.com/Principles-Compiler-Addison-Wesley-information-processing/dp/0201000229> | not checked |
| 58 | Distributed Systems Reading Group | <http://dsrg.pdos.csail.mit.edu/papers/> | not checked |
| 59 | System Design: Design large-scale systems | <https://github.com/donnemartin/system-design-primer> | not checked |
| 60 | Code: The Hidden Language of Computer Hardware and Software | <https://codehiddenlanguage.com/Chapter00/> | not checked |
| 66 | Introduction to Computing: Explorations in Language, Logic, and Mac... | <http://www.computingbook.org/> | not checked |
| 67 | Introduction to the Theory of Computation (3rd Edition) | <https://www.amazon.com/Introduction-Theory-Computation-Michael-Sipser/dp/113318779X> | not checked |
| 68 | Introduction to Algorithms (3rd Edition) | <http://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844/> | not checked |
| 69 | The Algorithm Design Manual (3rd Edition) | <https://www.algorist.com/> | not checked |
| 70 | Algorithms (4th Edition) | <https://algs4.cs.princeton.edu/home/> | not checked |
| 71 | Algorithms Illuminated | <https://algorithmsilluminated.org/> | not checked |
| 72 | Introducing Category Theory | <https://www.logicmatters.net/categories/SmithCat.pdf> | not checked |
| 73 | Category Theory for Programmers: The Preface | <https://bartoszmilewski.com/2014/10/28/category-theory-for-programmers-the-preface/> | not checked |
| 74 | An Introduction to Information Retrieval | <https://nlp.stanford.edu/IR-book/pdf/irbookonlinereading.pdf> | not checked |
| 75 | Computer Science: An interdisciplinary approach | <https://introcs.cs.princeton.edu/java/cs/> | not checked |
| 76 | DSA CS3: Data Structures & Algorithms | <https://opendsa-server.cs.vt.edu/OpenDSA/Books/CS3/html/> | not checked |
| 76 | Coursenotes | <https://opendsa-server.cs.vt.edu/OpenDSA/Books/CS3notes/html/> | not checked |
| 76 | Slides | <https://opendsa-server.cs.vt.edu/OpenDSA/Books/CS3slides/html/> | not checked |
| 82 | Architecture of a Database System | <http://db.cs.berkeley.edu/papers/fntdb07-architecture.pdf> | not checked |
| 83 | Readings in Database Systems (5th Edition) | <http://www.redbook.io/> | not checked |
| 84 | Database Management Systems (3rd Edition) | <https://www.amazon.com/gp/product/0072465638> | not checked |
| 85 | Transaction Processing: Concepts and Techniques | <https://www.amazon.com/Transaction-Processing-Concepts-Techniques-Management/dp/1558601902> | not checked |
| 86 | Data and Reality: A Timeless Perspective on Perceiving and Managing... | <https://www.amazon.com/Data-Reality-Perspective-Perceiving-Information/dp/1935504215> | not checked |
| 87 | The Architecture of Open Source Applications | <http://aosabook.org/en/> | not checked |
| 88 | An Introduction to Statistical Learning | <https://www-bcf.usc.edu/~gareth/ISL/> | not checked |
| 89 | Deep Learning | <http://www.deeplearningbook.org/> | not checked |
| 90 | Bayesian Reasoning and Machine Learning | <http://web4.cs.ucl.ac.uk/staff/D.Barber/pmwiki/pmwiki.php?n=Brml.HomePage> | not checked |
| 91 | Language Implementation Patterns | <https://www.amazon.com/gp/product/193435645X> | not checked |
| 92 | Compilers: Principles, Techniques, and Tools (2nd Edition) | <http://www.amazon.com/Compilers-Principles-Techniques-Tools-2nd/dp/0321486811/> | not checked |
| 93 | Compiler Construction | <https://inf.ethz.ch/personal/wirth/CompilerConstruction/index.html> | not checked |
| 94 | The Mythical Man-Month | <https://www.amazon.com/Mythical-Man-Month-Software-Engineering-Anniversary/dp/0201835959/> | not checked |
| 95 | Physically Based Rendering: From Theory To Implementation | <http://www.pbr-book.org/> | not checked |
| 102 | The Linux Command Line | <https://linuxcommand.org/tlcl.php> | not checked |

#### `extras/other_curricula.md` (5 occurrences)

| Line | Link text | URL | Note |
|--:|--|--|--|
| 5 | Google - Guide for Technical Development | <https://www.google.com/about/careers/students/guide-to-technical-development.html> | not checked |
| 6 | Teach Yourself Computer Science | <https://teachyourselfcs.com/> | not checked |
| 7 | Obtaining a Thorough CS Background Online | <http://spin.atomicobject.com/2015/05/15/obtaining-thorough-cs-background-online/> | not checked |
| 8 | P1xt | <https://github.com/P1xt/p1xt-guides> | not checked |
| 9 | Functional CS | <https://functionalcs.github.io/curriculum/> | not checked |

#### `extras/puzzles-practice-plods.md` (11 occurrences)

| Line | Link text | URL | Note |
|--:|--|--|--|
| 7 | link | <https://github.com/ossu/computer-science/issues/783#issuecomment-694187743> | not checked |
| 11 | link | <https://github.com/ossu/computer-science/issues/783#issuecomment-694176898> | not checked |
| 39 | link | <https://github.com/ossu/computer-science/issues/783#issuecomment-690023645> | not checked |
| 42 | Exercism | <https://exercism.io/> | not checked |
| 43 | LeetCode | <https://leetcode.com/> | not checked |
| 44 | HackerRank | <https://www.hackerrank.com/> | not checked |
| 45 | CodeWars | <https://www.codewars.com/> | not checked |
| 46 | 100+ Python Coding Problems with Solutions | <https://github.com/ProgrammingHero1/100-plus-python-coding-problems-with-solutions> | not checked |
| 47 | Rosalind | <http://rosalind.info/problems/locations/> | not checked |
| 48 | Advent of Code | <https://adventofcode.com/> | not checked |
| 49 | GitHub projects for beginners | <https://github.com/MunGell/awesome-for-beginners> | not checked |

#### `FAQ.md` (10 occurrences)

| Line | Link text | URL | Note |
|--:|--|--|--|
| 32 | Pre-College Math | <https://ossu.dev/precollege-math> | URL also used in a checked file; status there: working (re-check this line in its own context) |
| 36 | Hackr.io | <https://hackr.io/tutorials/> | not checked |
| 37 | /r/python | <https://old.reddit.com/r/Python> | not checked |
| 70 | July of 2025, Coursera removed audit access | <https://www.classcentral.com/report/coursera-preview-mode-paywall/> | not checked |
| 74 | Issues tab | <https://github.com/ossu/computer-science/issues> | not checked |
| 76 | Discord channel | <https://discord.gg/wuytwK5s9h> | URL also used in a checked file; status there: working (re-check this line in its own context) |
| 107 | Class Central | <https://www.classcentral.com/> | not checked |
| 109 | awesome-courses | <https://github.com/prakhar1989/awesome-courses> | not checked |
| 110 | cs-video-courses | <https://github.com/Developer-Y/cs-video-courses> | not checked |
| 111 | Goodreads | <https://www.goodreads.com/genres/computer-science> | not checked |

#### `HELP.md` (3 occurrences)

| Line | Link text | URL | Note |
|--:|--|--|--|
| 5 | [badge] | <https://discord.gg/5pUhfpX> | not checked |
| 5 | Discord server | <https://discord.gg/5pUhfpX> | not checked |
| 5 | (nested image) | <https://img.shields.io/discord/744385009028431943.svg?label=&logo=discord&logoColor=ffffff&color=7389D8&labelColor=6A7EC2> | URL also used in a checked file; status there: working (re-check this line in its own context) |

#### `CONTRIBUTING.md` (4 occurrences)

| Line | Link text | URL | Note |
|--:|--|--|--|
| 4 | pull request | <https://www.freecodecamp.org/news/how-to-make-your-first-pull-request-on-github-3/> | not checked |
| 6 | open an issue | <https://help.github.com/articles/creating-an-issue/> | not checked |
| 15 | emoji reactions | <https://github.blog/2016-03-10-add-reactions-to-pull-requests-issues-and-comments/> | not checked |
| 19 | fork this project | <https://help.github.com/articles/fork-a-repo/> | not checked |

#### `CURRICULAR_GUIDELINES.md` (2 occurrences)

| Line | Link text | URL | Note |
|--:|--|--|--|
| 3 | Curriculum Guidelines for Undergraduate Programs in Computer Science | <https://www.acm.org/binaries/content/assets/education/cs2013_web_final.pdf> | not checked |
| 7 | here | <https://csed.acm.org/> | not checked |

#### `CHANGELOG.md` (3 occurrences)

| Line | Link text | URL | Note |
|--:|--|--|--|
| 6 | Semantic Versioning | <http://semver.org/> | not checked |
| 229 | web app | <https://ossu.firebaseapp.com> | not checked |
| 260 | extras | <https://github.com/ossu/computer-science/tree/master/extras> | not checked |

#### `.github/ISSUE_TEMPLATE/request-for-comment-template.md` (1 occurrences)

| Line | Link text | URL | Note |
|--:|--|--|--|
| 11 | our curricular guidelines | <https://github.com/ossu/computer-science/blob/master/CURRICULAR_GUIDELINES.md> | not checked |

## Method and access limits

- **Inventory.** A Python script parsed Markdown links (including image links nested inside link text), HTML `href`/`src` attributes and bare URLs. Its counts were reconciled line by line against a raw count of `http(s)://` occurrences. Roles were assigned from the table column or section each link sits in.
- **Loading.** Every URL was fetched with curl (following redirects) and rendered in headless Chromium with a 4-second settle time. The rendered text was saved and read. For course platforms I extracted the enrollment, pacing, price and access wording, and expanded Coursera's FAQ accordions to read the answers. Status was assigned only after reading what came back, not from HTTP codes.
- **GitHub.** This session's proxy blocks github.com web pages and the REST API for repositories not attached to the session ("GitHub access to this repository is not enabled for this session"). For GitHub links I used:
  - anonymous `git ls-remote` and shallow clones, which confirm repositories, branches, tags and file paths;
  - GitHub's search API (repository archived flag, users, issue titles and states).

  Pages with no git or API route (issue-comment anchors, attachments, release pages, the contributors graph) are marked unverified.
- **Discord.** Invites were checked through Discord's public invite endpoint, which returns the server and channel name without logging in. Channel deep links (`discord.com/channels/...`) need a login and are unverified.
- **HTTP-only links.** The session proxy carries HTTPS only. For `http://` links I loaded the `https://` form of the same address and say so where it matters.
- **Blocked sites.** Some hosts refused or could not be reached:
  - TLS failures: gaia.cs.umass.edu, cseweb.ucsd.edu, seas.upenn.edu, csapp.cs.cmu.edu, ibiblio.org, knking.com.
  - Bot protection: Akamai (stat110.hsites.harvard.edu, mitpress.mit.edu), Cloudflare (wiki.osdev.org), HAL (bot check), Khan Academy (client challenge).
  - Rate limiting: YouTube watch pages.

  For these I tried alternate hosts found by web search and the platform's own catalog. Where that also failed, the link is unverified.
- **Amazon.** Amazon pages returned "Access restricted. Continued access by an unauthorized AI agent violates Amazon's Conditions of Use". I stopped requesting Amazon after that, so every Amazon book link is unverified.
- **Not used as evidence.** Web search snippets were used only to find alternate addresses. No status or quoted claim in this report rests on a search snippet.
- **Final review pass (11 Nov 2026).** I re-opened every proposed replacement and every "moved" target (42 URLs; all returned 200 with the expected titles). I re-confirmed the key quoted phrases on their pages. I re-added the status counts: 227 + 38 + 23 + 4 + 39 = 331 checked, plus 170 not yet checked = 501 = size of the inventory.
