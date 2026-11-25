# Waitlist mailer

**Practice project. Not for production use. All data is fake.**

A small local app for announcing a jewelry drop to people who joined your waitlist. Each person gets their own email through [Amazon SES](https://aws.amazon.com/ses/), so customers never see one another’s addresses.

## One-time AWS setup

1. In the SES console, verify the email address or domain you will send from. While the account is in the SES sandbox, you can only deliver to other verified addresses. Request production access before mailing a real waitlist.
2. Create an IAM user or role that can call `ses:SendEmail` (and `ses:SendBulkEmail` is not required). The default AWS credential chain works: environment variables, `~/.aws/credentials`, or a role.
3. Copy `.env.example` to `.env`. Set `AWS_REGION`, `SES_FROM_EMAIL`, and `COMPANY_NAME`. Add access keys only if you are not using a shared AWS profile.

## Run

```bash
npm install
npm start
```

Open http://127.0.0.1:3789.

Add the customers who opted in, write the drop note, preview it, send yourself a test, then send to the waitlist. The list is stored in `data/waitlist.json` on this computer.

Set `DRY_RUN=true` in `.env` to exercise the app without calling AWS.
