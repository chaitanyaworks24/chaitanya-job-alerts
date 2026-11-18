# Chaitanya's Job Alerts

Checks every 3 hours for **Software Engineer, Full-Stack, .NET/C#, Angular and Next.js/React** roles at junior to mid level. It skips senior, lead, mobile, Java, Python and other roles that don't match. New jobs are sent to Telegram in this order:

1. 🌍 **Remote jobs open to India** (worldwide, APAC or India-remote)
2. 📍 **Pune** (hybrid or office)
3. 📍 **Bengaluru**

## Where it looks

- **Remote job boards:** Himalayas (filtered to jobs open to India), Jobicy (APAC and Anywhere), Remotive, RemoteOK, We Work Remotely
- **Company career portals in Pune/Bengaluru (Workday):** Citi, Barclays, Mastercard, Deutsche Bank, FIS, Fiserv, Qualys, Accenture, Wolters Kluwer, Equifax, Hitachi, Workday, Zendesk, NVIDIA
- **Product companies (Greenhouse/Lever):** PubMatic, Druva, Rubrik, New Relic, Razorpay, Groww, InMobi, Okta, GitLab, Mindtickle, Hevo Data, Paytm, Meesho, CRED, Zeta, FamPay

Tune roles, exclusions and companies in `config.json`.

## Alerts

Jobs go to `TELEGRAM_CHAT_ID`. Problem reports go to `TELEGRAM_ADMIN_CHAT_ID`:

- 📊 A daily check-in (if it stops arriving, the watcher has stopped)
- ⚠️ A warning if a source or a single company fails 2 checks in a row, or if alerts couldn't be delivered, and ✅ when it recovers
- 🚨 A crash alert with a link to the logs

## Run locally

```sh
python3 job_watcher.py --dry-run   # show matching jobs, send nothing
python3 job_watcher.py             # send alerts
```

`.env` holds the Telegram settings. It is git-ignored; on GitHub they are repository secrets.

## Not covered automatically

Naukri, LinkedIn, Indeed, Wellfound and Instahyre block bots or forbid scraping. Use their own email job alerts instead.
