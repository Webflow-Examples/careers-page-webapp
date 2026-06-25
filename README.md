# Greenhouse Careers Page

A [Webflow Cloud](https://webflow.com/cloud) example app to showcase an example careers page. Built with Next.js, this app integrates Webflow components via [**DevLink**](https://developers.webflow.com/webflow-cloud/devlink) and uses the [**Greenhouse API**](https://developers.greenhouse.io/job-board.html#introduction) to display job listings dynamically.

[![Deploy to Webflow](https://webflow.com/img/deploy-dark.svg)](https://webflow.com/dashboard/cloud/deploy?repo=https://github.com/Webflow-Examples/careers-page-webapp)

## ✨ Features

- **Dynamic Job Listings**: Fetches real-time job data from Greenhouse API on the backend
- **Webflow Integration**: Uses Webflow DevLink components for consistent design with Webflow site
- **Department Filtering**: Filter jobs by department with a dropdown

## 🛠️ Tech Stack

- **Webflow Cloud** - Infrastructure for hosting the webapp alongside a Webflow site
- **Greenhouse API** - Job data source
- **Next.js 15** - Webapp framework using React
- **Webflow DevLink** - Syncs design system components from the Webflow site to React components

## 📋 Prerequisites

Make sure you have the following before running the app locally:

- Install Node.js 18+ / npm / Git
- Webflow account (sign up for free)
- Install the Webflow CLI

## 🏗️ Getting Started

### 1. Fork and clone the repository

- [Fork this repo](https://github.com/Webflow-Examples/careers-page-webapp/fork) into your own repositories so you have a copy of this project to work with
- Clone the repo down to your local machine
- `cd careers-page-webapp`

### 2. Clone the Webflow Demo Site

This project uses Webflow UI components and styles from a demo Webflow cloneable site. Clone the demo site into your workspace:

- Open the [Astral Fund template](https://webflow.com/made-in-webflow/website/astralfund-cloud-app---careers-page)
- Click "Clone in Webflow" button to spin up your own site

### 3. Gather site details for `.env`

#### Generate a Site Token

Once your new site is created, generate a Site Token to use for syncing Webflow components with Devlink:

- Navigate to Site Settings -> Apps & Integrations
- In the "API access" section, click "Generate API token" \*
- Choose a name, and find "Sites"; select the "Read-only" scope from the dropdown
- Generate token and copy the token value (you cannot retrieve this later, so save it accordingly)

\* Only users with Site Manager access (or higher) can generate an API token.

#### Fill in the `.env` file

- In your editor, duplicate `.env.example`, rename the copy to `.env`, and paste the token you just generated into the `WEBFLOW_SITE_API_TOKEN` field.
- Set the `WEBFLOW_SITE_ID` value to the ID of your Webflow site. You can find this value in under Site Settings -> General -> Overview.
- Set `NEXT_PUBLIC_BASE_PATH` to the mount path (aka base URL segment) of this Webflow Cloud app where it will live on the Webflow site. You can default to `/careers`.

### 4. Install and run locally

```bash
npm install
```

```bash
npm run dev
```

### 5. Access the Careers Page

The development server will start and automatically show you where to navigate:

```
🚀 Starting development server...
📍 App will be available at: http://localhost:3000/careers
```

Open [http://localhost:3000/careers](http://localhost:3000/careers) in your browser to see the careers page. In the app, you can type in a Greenhouse source to pull job listings from. Try `webflow`, `anthropic`, or `greenhouse` to start.

### 6. Sync DevLink

This example repo has components already in place from the Astral Fund template site, but if you make any changes to the components on the Webflow site, you'll need to sync the changes down using the `webflow-cli` devlink tool.

Once your `.env` is set up, run `webflow devlink sync` in the terminal.

## 🚀 Deploy Webflow Cloud app

Once everything locally works OK, it's time to build and deploy the app to your Webflow site at the mounted path.

First, push up any code changes made to the project to the forked remote GitHub repo.

### Create Webflow Cloud app

> For more detailed guidance on creating a Webflow Cloud app, [see docs here](https://developers.webflow.com/webflow-cloud/bring-your-own-app) for a step-by-step.

In your Webflow site settings, navigate to the **Webflow Cloud** tab, click "Install GitHub App", and follow the prompts so Webflow can access your forked repo.

Back in the Webflow Cloud page, click the "Create New Project" button and follow the prompts accordingly to add your project name, and the location of your GitHub repo.

When you are prompted to create an **Environment**:
1. **Branch** - Select the GitHub branch you're working from (usually `main`)
2. **Mount Path** - Enter the same value you set for `NEXT_PUBLIC_BASE_PATH` variable in `.env` (`/careers` in this example).

After the project is created, click "Publish" to re-publish your Webflow site. Once publishing completes, open your Webflow Cloud project, navigate into the **Environments**, then select the `main` branch name to view **Deployments**.

### Add environment variables

On the **Deployments** page, open the "Environment Variables" tab and add all the environment variables from your `.env` file. Because the `.env` file is ignored by git, these variables and associated values must be added here - this will ensure your deployed app can access them.

### Deploy the app

Click the "Deploy latest commit" button to build and deploy the latest app from your repo.

After a few minutes, you can click the "Environment URL", which should be where the app is deployed to on your site (i.e. `https://{your-site-here}.webflow.io/careers`).

If you see the same webapp careers page from localhost, congrats! You've deployed your first Webflow Cloud app 🎉

If you make additional changes to your project, simply push them up to your repo on `main`, and Webflow will automatically kick off a new deployment with your changes. Also, if your deployment build fails for any reason, check the "Deployment History" for more logs.

## Build Locally

To check a build locally before Webflow kicks off a build and deploys the latest changes, simply run the following commands:

```bash
npm run build
```

```bash
npm start
```

## 📁 Project Structure

Below is a simplified tree of important parts for this project.

```
src/
├── app/
│   ├── api/greenhouse/   # Backend routes for Greenhouse API
│   ├── components/       # React components
│   ├── globals.css       # Global styles
│   ├── layout.tsx        # Entry-point for the app
├── devlink/              # Webflow components
webflow.json              # Config for Webflow Cloud + DevLink
```

## 🤝 Contributing
Feel free to submit issues and enhancement requests!


## 📄 License
This project is MIT licensed.
