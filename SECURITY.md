# Security policy

## Supported versions

Only the latest commit on `main` is supported. The skill has no releases or version branches, so fixes land on `main`.

## Reporting a vulnerability

Please report security problems privately through GitHub: open the **Security** tab of this repository and choose **Report a vulnerability**. Don't open a public issue for anything that could be exploited.

Include what you found, the file or step involved, and how to reproduce it. I aim to reply within 7 days and to fix confirmed problems within 30.

## What counts

This repository is an agent skill: Markdown instructions plus reference files. It has no server or install script, and it ships no runtime code of its own. It calls Apify Actors through the Apify CLI you sign in with. Useful reports include:

- Instructions that could make an agent leak your Apify token, or other secrets, into output, files or messages.
- Instructions that could be abused through prompt injection from scraped job posts or careers pages.
- Steps that could run Actors, or spend credits, well beyond the cost the skill states before it runs.
- A link or command in the repository that points to something malicious.

Bugs in the Apify Actors themselves, in Apify's platform, or in the job boards they read belong with those projects. Problems with a job board's data are out of scope.

## Handling your own credentials

The skill never asks you to paste an API token into a prompt or a file. Keep your Apify token in the Apify CLI (`apify login`) or in an environment variable, and never commit it. If you think a token was exposed, revoke it in the Apify Console under Settings > API & Integrations.
