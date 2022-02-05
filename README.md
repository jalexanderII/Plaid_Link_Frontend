# Plaid quickstart

This repository accompanies Plaid's [**quickstart guide**][quickstart].

Here you'll find full example integration apps using our [**client libraries**][libraries]:

![Plaid quickstart app](/assets/quickstart.jpeg)

## Table of contents

<!-- toc -->

- [1. Clone the repository](#1-clone-the-repository)
  - [Special instructions for Windows](#special-instructions-for-windows)
- [2. Set up your environment variables](#2-set-up-your-environment-variables)
- [3. Run the quickstart](#3-run-the-quickstart)
  - [Run without Docker](#run-without-docker)
    - [Pre-requisites](#pre-requisites)
    - [2. Running the frontend](#2-running-the-frontend)
- [Testing OAuth](#testing-oauth)

<!-- tocstop -->

## 1. Clone the repository

Using https:

```bash
git clone https://github.com/plaid/quickstart
cd quickstart
```

Alternatively, if you use ssh:

```bash
git clone git@github.com:plaid/quickstart.git
cd quickstart
```

#### Special instructions for Windows

Note - because this repository makes use of symbolic links, to run this on a Windows machine, make sure you have checked the "enable symbolic links" box when you download Git to your local machine. Then you can run the above commands to clone the quickstart. Otherwise, you may open your Git Bash terminal as an administrator and use the following command when cloning the project

```bash
git clone -c core.symlinks=true https://github.com/plaid/quickstart
```

## 2. Set up your environment variables

```bash
cp .env.example .env
```

Copy `.env.example` to a new file called `.env` and fill out the environment variables inside. At
minimum `PLAID_CLIENT_ID` and `PLAID_SECRET` must be filled out. Get your Client ID and secrets from
the dashboard: https://dashboard.plaid.com/account/keys

> NOTE: `.env` files are a convenient local development tool. Never run a production application
> using an environment file with secrets in it.

## 3. Run the Quickstart

There are two ways to run the various language quickstarts in this repository. You can simply choose to use Docker, or you can run the
code directly. If you would like to run the code directly, skip to the
[Run without Docker](#run-without-docker) section.

### Run without Docker

#### Pre-requisites

- The language you intend to use is installed on your machine and available at your command line.
  This repo should generally work with active LTS versions of each language such as node >= 14,
  python >= 3.8, ruby >= 2.6, etc.
- Your environment variables populated in `.env`
- [npm](https://www.npmjs.com/get-npm)
- If using Windows, a command line utility capable of running basic Unix shell commands

#### 1. Running the backend

Once started with one of the commands below, the quickstart will be running on http://localhost:8000 for the backend. Enter the additional commands in step 2 to run the frontend which will run on http://localhost:3000.

#### 2. Running the frontend

```bash
$ cd ./frontend
$ npm ci
$ npm start
```

## Testing OAuth

Some institutions (primarily in Europe, but a small number in the US) require an OAuth redirect
authentication flow, where the end user is redirected to the bank’s website or mobile app to
authenticate. For this flow, you should set `PLAID_REDIRECT_URI=http://localhost:3000/` in `.env`.
You will also need to register this localhost redirect URI in the
[Plaid dashboard under Team Settings > API > Allowed redirect URIs][dashboard-api-section].

OAuth flows are only testable in the `sandbox` environment in this Quickstart app due to an https
`redirect_uri` being required in other environments. Additionally, if you want to use the [Payment
Initiation][payment-initiation] product, you will need to [contact Sales][contact-sales] to get this
product enabled.

[quickstart]: https://plaid.com/docs/quickstart
[libraries]: https://plaid.com/docs/api/libraries
[payment-initiation]: https://plaid.com/docs/payment-initiation/
[python-example]: /python
[go-example]: /go
[docker]: https://www.docker.com
[dashboard-api-section]: https://dashboard.plaid.com/team/api
