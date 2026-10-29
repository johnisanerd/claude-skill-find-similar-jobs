# claude-skill-find-similar-jobs

A [Claude and agent skill](https://agentskills.io/specification) that finds similar jobs from one posting you love. Paste a job URL or the job description and it returns about ten jobs similar to it that are still open, each one checked against the employer's own careers board. It chains nine Apify Actors and installs in Claude Code, Cursor, and other skills-compatible agents.

## What it does

Give it one job. Before it spends anything, it reads the posting and builds a short role signature for you to confirm: the job family, the level, up to five must-have skills, the domain, and the location rule. Then it searches in two ways.

- **Job sites:** Google Jobs, LinkedIn job search, and LinkedIn's own "similar jobs" list for your posting.
- **Employers' own boards:** Ashby, Greenhouse and JazzHR, plus Workday, Oracle and iCIMS career sites found by company. Some openings are only posted on a company's own careers site and never reach the big job sites; this is where those show up.

Every result gets a status:

- **open on the employer's board**, with that board's own job or requisition id;
- **likely closed**;
- **aggregator only**;
- **agency**, for staffing and travel-contract reposts.

A LinkedIn listing or a recent posted date never counts as proof a job is open, because LinkedIn can serve job pages up to a week old.

It does not rank jobs against your resume, analyze salaries, watch named companies' careers pages, export jobs in bulk, or apply for you. For those it points you to the awesome-skills entries that do.

## Example

> This is my dream job: https://www.linkedin.com/jobs/view/4481397960/. Find about ten similar roles that are still open in the US.

In testing, LinkedIn suggested 37 similar jobs for that posting. The skill checked their employers' own boards and confirmed 12 of them were still listed there, with the exact title.

## Install

```bash
npx skills add johnisanerd/claude-skill-find-similar-jobs
```

The skill lives in the `apify-find-similar-jobs/` folder. You can also copy that folder straight into your agent's skills directory.

New to Claude Code? Start a [free trial](https://claude.ai/referral/uIlpa7nPLg), then run the install command above. You also need an [Apify account](https://apify.com/sign-up?fpr=9n7kx3&fp_sid=skillrepo) with the Apify CLI signed in (`apify login`). A typical search costs about $0.40 on Apify's free plan, and the skill states the cost before it runs anything.

## Powered by

Job sites:

- [Google Jobs Scraper](https://apify.com/johnvc/google-jobs-scraper?fpr=9n7kx3&fp_sid=skillrepo): breadth across job boards, one bounded page per title.
- [LinkedIn Job Search](https://apify.com/johnvc/linkedin-job-search-scraper?fpr=9n7kx3&fp_sid=skillrepo): your exemplar, LinkedIn's similar jobs, and listings.

Employers' own boards:

- [Ashby Job Board API](https://apify.com/johnvc/ashby-job-board-scraper?fpr=9n7kx3&fp_sid=skillrepo): employer lookup by name, and title searches across the largest boards.
- [Greenhouse Job Board API](https://apify.com/johnvc/greenhouse-job-board-api?fpr=9n7kx3&fp_sid=skillrepo): title searches across the largest boards.
- [JazzHR Jobs API](https://apify.com/johnvc/jazzhr-jobs-api?fpr=9n7kx3&fp_sid=skillrepo): small-business, hourly and clinical roles across the platform.
- [Workday Career Sites API](https://apify.com/johnvc/workday-career-sites-api?fpr=9n7kx3&fp_sid=skillrepo) and [Workday Careers API](https://apify.com/johnvc/workday-careers-api?fpr=9n7kx3&fp_sid=skillrepo): an employer's Workday site, then a title-filtered pull.
- [Oracle and Taleo Jobs API](https://apify.com/johnvc/oracle-taleo-jobs-api?fpr=9n7kx3&fp_sid=skillrepo) and [iCIMS Careers API](https://apify.com/johnvc/icims-careers-api?fpr=9n7kx3&fp_sid=skillrepo): enterprise employers' career sites.

Disclosure: links use the author's Apify affiliate code; the `johnvc/*` Actors are built by the author.

## License

MIT
