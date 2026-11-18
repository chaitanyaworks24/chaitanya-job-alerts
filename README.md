# Chaitanya's Job Alerts

Checks every 2 hours for **Software Engineer, Full-Stack, .NET/C#, Angular and Next.js/React** roles at junior to mid level. It skips senior, lead, mobile, Java, Python and other roles that don't match. New jobs are sent to Telegram in this order:

1. 🌍 **Remote jobs open to India** (worldwide, APAC or India-remote)
2. 📍 **Pune** (hybrid or office)
3. 📍 **Bengaluru**

## Where it looks

- **Job sites (via [JobSpy](https://github.com/speedyapply/JobSpy)):** LinkedIn, Naukri and Indeed (logged out, jobs posted in the last 24 hours). Glassdoor is set up but off: it blocks GitHub's servers. The same job showing up on several sites is only sent once.
- **Indian job boards:** Hirist (searched with a 10-second gap between requests, as its robots.txt asks). It hides some of its newest jobs from logged-out visitors, so a few Hirist roles arrive a few days late. iimjobs is set up but off: it has almost no software roles.
- **Remote job boards:** Himalayas (filtered to jobs open to India), Jobicy (APAC and Anywhere), Remotive, RemoteOK, We Work Remotely
- **Company career portals in Pune/Bengaluru (Workday):** Citi, Barclays, Mastercard, Deutsche Bank, FIS, Fiserv, Qualys, Accenture, Wolters Kluwer, Equifax, Hitachi, Workday, Zendesk, NVIDIA
- **Product companies (Greenhouse/Lever):** PubMatic, Druva, Rubrik, New Relic, Razorpay, Groww, InMobi, Okta, GitLab, Mindtickle, Hevo Data, Paytm, Meesho, CRED, Zeta, FamPay

Tune roles, exclusions and companies in `config.json`.

## Alerts

Jobs go to `TELEGRAM_CHAT_ID`. After each check's jobs, one more message lists all their apply links as full URLs, one per line, ready to copy and forward (split into several messages if it's too long for one).

Problem reports go to `TELEGRAM_ADMIN_CHAT_ID`:

- 📊 A daily check-in (if it stops arriving, the watcher has stopped)
- ⚠️ A warning if a source or a single company fails 2 checks in a row, or if alerts couldn't be delivered, and ✅ when it recovers
- 🚨 A crash alert with a link to the logs

## Run locally

Needs Python 3.10+ for the JobSpy sites:

```sh
pip install -r requirements.txt
python3 job_watcher.py --dry-run   # show matching jobs, send nothing
python3 job_watcher.py             # send alerts
```

`.env` holds the Telegram settings. It is git-ignored; on GitHub they are repository secrets.

## Not covered automatically

Wellfound and Instahyre block bots. Use their own email job alerts instead.
