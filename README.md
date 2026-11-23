# ShipIt Sprint: DevOps Warriors 🚀

> **DevOps Bootcamp · Team Activity**
>
> Build, ship, monitor, and maintain a website together using Git, GitHub Actions, AWS EC2, Nginx, Linux, and shell scripting.

**Team Name:** DevOps Warriors  
**Technical Name:** `falcon`  
**Jira Project Key:** `DEVOPS`

---

## 📌 Project Overview

ShipIt Falcon is a collaborative DevOps engineering project developed as part of a DevOps Bootcamp team activity.

The project demonstrates a complete website delivery lifecycle, from collaborative development and version control to automated deployment, monitoring, rollback, and incident management.

It brings together essential DevOps practices, including:

- Linux server administration and access management
- AWS EC2 infrastructure and server deployment
- Nginx configuration and web hosting
- Git and GitHub collaborative workflows
- GitHub Actions CI/CD automation
- Automated deployment and rollback strategies
- Bash scripting and scheduled cron jobs
- Server monitoring and traffic reporting
- Incident response and troubleshooting

### My Role: Team Lead

**Nahal Binte Imran — Team Lead**

My responsibilities include:

- Coordinating team activities and project execution.
- Managing the Jira board, tasks, and team workflow.
- Overseeing GitHub collaboration and branching strategies.
- Reviewing and merging pull requests.
- Coordinating development and deployment activities.
- Ensuring that project phases and deliverables are completed.
- Facilitating communication and resolving workflow issues.

---

## 👥 Team Members

| Member | GitHub Username | Role |
|---|---|---|
| Nahal Binte Imran | [@nahalmalik](https://github.com/nahalmalik) | Team Lead |
| Ather Ullah | [@atherullah](https://github.com/atherullah) | Server Admin |
| Zahoor Ahmed | [@zahoorahmad334](https://github.com/zahoorahmad334) | Pipeline Engineer |
| Safyan Talha | [@safyantahir03-collab](https://github.com/safyantahir03-collab) | Scripter |

### Team Responsibilities

| Role | Responsibilities |
|---|---|
| Team Lead | Jira board management, repository coordination, pull request reviews, merging, and project delivery |
| Server Admin | Server users, permissions, Nginx, SSH access, and server configuration |
| Pipeline Engineer | GitHub Actions workflows, CI/CD automation, and Slack notifications |
| Scripter | Shell scripts, automation, scheduled tasks, and cron jobs |

Each member leads a specific technical area while collaborating throughout all project phases.

---

## 🛠️ Technology Stack

| Category | Technologies |
|---|---|
| Cloud Infrastructure | AWS EC2 |
| Operating System | Ubuntu Linux |
| Web Server | Nginx |
| Version Control | Git, GitHub |
| CI/CD | GitHub Actions |
| Scripting | Bash, Shell |
| Automation | Cron Jobs |
| Secure Access | SSH |
| Collaboration | Jira, Slack |
| Frontend | HTML, CSS, JavaScript |
| Deployment | Linux deployment scripts, SSH |

---

## 🔗 Project Links

| Resource | Link |
|---|---|
| Live Website | [devopwarriors.duckdns.org](http://devopwarriors.duckdns.org) |
| Original Team Repository | [atherullah/shipit-falcon](https://github.com/atherullah/shipit-falcon) |
| My GitHub Fork | [nahalmalik/shipit-falcon](https://github.com/nahalmalik/shipit-falcon) |
| Jira Board | [DEVOPS Project Board](https://nahalsworkspace-39376139.atlassian.net/jira/software/projects/DEVOPS/boards/2?filter=&groupBy=none) |
| Slack Workspace | [DevOps Warriors](https://app.slack.com/client/T0CJBT87XA6/C0CJA8Z3QVC) |

**Slack Channels:** `#falcon`, `#falcon-dev`, `#falcon-alerts`

---

## 📂 Repository Structure

```text
.
├── site/
│   ├── index.html
│   ├── style.css
│   └── members/
│       └── *.html
│
├── scripts/
│   ├── team.conf
│   ├── check-site.sh
│   ├── deploy.sh
│   ├── rollback.sh
│   ├── status.sh
│   └── traffic-report.sh
│
└── .github/
    └── workflows/
        ├── check.yml
        ├── deploy.yml
        └── rollback.yml
```

### Directory Description

| Directory/File | Purpose |
|---|---|
| `site/` | Website source files |
| `site/members/` | Individual team member pages |
| `scripts/` | Deployment, validation, monitoring, and automation scripts |
| `team.conf` | Team configuration and domain information |
| `check-site.sh` | Website validation |
| `deploy.sh` | Deployment and release management |
| `rollback.sh` | Previous release restoration |
| `status.sh` | Server status generation |
| `traffic-report.sh` | Website traffic reporting |
| `.github/workflows/` | GitHub Actions CI/CD workflows |

---

## 🔄 Git Collaboration Workflow

The project follows a structured Git collaboration process.

### Development Rules

- All team communication takes place through Slack.
- Every task must have an assigned Jira issue.
- Work progresses through To Do → In Progress → In Review → Done.
- Direct pushes to `main` are not permitted.
- All changes must be submitted through pull requests.
- Every pull request requires at least one approval from another team member.
- Branch names and pull request titles must begin with their Jira issue key.
- Website changes must be made locally and pushed through Git, not edited directly on the server.
- Passwords, private keys, and webhook URLs must never be committed or shared.

### Branch Naming Convention

```text
DEVOPS-<issue-number>-<short-description>
```

Example:

```text
DEVOPS-4-ali-page
```

### Pull Request Naming Convention

```text
DEVOPS-4 Add Ali's page
```

---

## ☁️ Server Infrastructure

The project website is hosted on an Ubuntu server using Nginx.

### Server Configuration

- Each team member has an individual Linux user.
- SSH key authentication is used for server access.
- Password-based SSH login is disabled.
- A shared `team` group manages team permissions.
- A dedicated `deploy` user handles deployments.
- Only ports 22 (SSH) and 80 (HTTP) are open.

### Nginx Configuration

Nginx serves the website from:

```text
/var/www/falcon/current
```

The live website is available at:

[http://devopwarriors.duckdns.org](http://devopwarriors.duckdns.org)

The monitoring pages are served from:

```text
/var/www/falcon/live/
```

Access logs:

```text
/var/log/nginx/falcon.access.log
```

### Deployment Directory Structure

```text
/var/www/falcon/
│
├── current -> releases/<timestamp>-<commit>
├── releases/
├── upload/
├── live/
├── bin/
└── deploys.log
```

| Directory/File | Purpose |
|---|---|
| `current` | Symlink pointing to the active release |
| `releases/` | Stores deployment releases |
| `upload/` | Holds files uploaded by GitHub Actions |
| `live/` | Contains status and traffic report pages |
| `bin/` | Stores deployed automation scripts |
| `deploys.log` | Records deployments and rollbacks |

The last five releases are retained to support rollback operations.

---

## ⚙️ CI/CD Pipeline

GitHub Actions automates website validation, deployment, and rollback.

### 1. Continuous Integration — `check.yml`

Runs automatically on every pull request.

The workflow executes:

```bash
scripts/check-site.sh
```

It validates:

- HTML pages contain a `<title>` element.
- Internal website links point to existing files.
- No website file exceeds 1 MB.
- External links, anchor links, and `/live/` links are skipped.

A failed validation check prevents the pull request from being merged.

### 2. Continuous Deployment — `deploy.yml`

Runs on every push to `main` and can also be triggered manually.

Deployment workflow:

1. Uploads `site/` and `scripts/` to the server through SSH.
2. Creates a new release directory.
3. Replaces `__VERSION__` placeholders with deployment information.
4. Updates the `current` symlink to the new release.
5. Records the deployment in `deploys.log`.
6. Retains only the five newest releases.
7. Copies scripts into the server's `bin/` directory.
8. Installs the deployment user's crontab.
9. Performs a health check from the GitHub Actions runner.
10. Sends deployment results to `#falcon-alerts`.

The health check verifies that the website responds and displays the newly deployed commit.

**Deployment safety:** Two deployments cannot run simultaneously.

### 3. Rollback — `rollback.yml`

The rollback workflow can be triggered manually from the GitHub Actions tab.

It:

- Identifies the previous release.
- Updates the `current` symlink.
- Records the rollback in `deploys.log`.
- Sends a notification to `#falcon-alerts`.

If no previous release exists, the workflow reports the issue and fails.

---

## 🔐 GitHub Actions Configuration

The CI/CD pipeline uses GitHub repository secrets and variables.

### Repository Secrets

| Secret | Purpose |
|---|---|
| `DEPLOY_SSH_KEY` | Private SSH key for deployment |
| `SSH_KNOWN_HOSTS` | Server host key for SSH verification |
| `SLACK_WEBHOOK_URL` | Slack deployment notification webhook |

### Repository Variables

| Variable | Purpose |
|---|---|
| `DEPLOY_HOST` | Server address |

Secrets are stored securely in GitHub Actions and are not included in repository files.

---

## 📊 Automated Monitoring & Scheduled Scripts

The project includes shell scripts that generate monitoring reports automatically.

### 1. Server Status — `status.sh`

Generates:

```text
/live/status.html
```

Displays:

- Server hostname
- System uptime
- CPU load
- Memory usage
- Disk usage
- Nginx service status
- Active release
- Last five deployments

A warning is displayed if disk usage exceeds 80% or Nginx is unavailable.

**Execution frequency:** Every minute.

### 2. Traffic Report — `traffic-report.sh`

Generates:

```text
/live/report.html
```

Displays:

- Total website requests
- Number of 404 responses
- Top five requested pages
- Top five visitors
- Top five missing pages

Requests to `/live/` are excluded from traffic reporting.

**Execution frequency:** Every five minutes.

---

## 🚀 Getting Started

### Prerequisites

- Git installed on your local machine.
- A GitHub account.
- Access to the project repository.
- Basic familiarity with Linux and the terminal.

### Clone the Original Team Repository

```bash
git clone https://github.com/atherullah/shipit-falcon.git
cd shipit-falcon
```

### Create a Feature Branch

```bash
git checkout -b DEVOPS-<number>-<short-name>
```

### Make Changes and Commit

```bash
git add .
git commit -m "DEVOPS-<number> Describe your changes"
```

### Push Your Branch

```bash
git push origin DEVOPS-<number>-<short-name>
```

### Submit a Pull Request

1. Open the repository on GitHub.
2. Select your pushed branch.
3. Create a pull request targeting `main`.
4. Include the relevant Jira issue.
5. Request a review from another team member.
6. Wait for automated checks and approval before merging.

---

## 🚨 Incident Management Process

When the trainer announces **"Incident time"** in `#falcon`, the team follows a structured incident response process.

### Step 1 — Detection

Identify the issue using:

- `#falcon-alerts`
- Live website
- Server status page
- Traffic report
- GitHub Actions
- Nginx and server logs

### Step 2 — Communication

Start a Slack thread in `#falcon` beginning with:

```text
INCIDENT:
```

Describe the observed issue and keep incident-related communication in that thread.

### Step 3 — Issue Tracking

Create a Jira Bug with:

- The same incident title.
- A link to the Slack discussion.
- Assignment to the responsible team member.
- Placement in the Phase 4 epic.

### Step 4 — Resolution

- Website-related changes must go through pull requests.
- Server-related issues must be resolved on the server.
- Verify the fix after implementation.

### Step 5 — Documentation

Document the following in the Jira issue:

1. What we observed
2. Root cause
3. Fix implemented
4. Prevention measures
5. Time taken

---

## 📅 Project Timeline

| Phase | Duration | Focus |
|---|---:|---|
| Phase 0 | 25 min | Slack, Jira, team server, repository (A0–A2) |
| Phase 1 | 35 min | Git collaboration: pages, conflicts, reviews, undo (A3–A6) |
| Phase 2 | 35 min | Automated deployment: SSH, checks, deploy, rollback (A7–A10) |
| Phase 3 | 30 min | Shell scripts: status page, traffic report, self-deploying scripts (A11–A13) |
| Phase 4 | 25 min | Incident response |
| Phase 5 | 15 min | Team demonstration |

---

## 🏆 Project Scoring

| Evaluation Criteria | Points |
|---|---:|
| Each activity A0–A13 completed and demonstrated | 14 |
| Jira board maintained properly | 2 |
| Team communication conducted through Slack | 2 |
| Each incident fixed and documented | 2 each |
| Every member opens a PR in every phase | 2 |
| Each direct push to `main` | −1 |
| Each hint during incident round | −1 |
| Any secret exposed in Slack, Jira, or repository | −2 |

---

## 🎯 Learning Outcomes

Through this project, the team gains practical experience in:

- Managing collaborative software development workflows.
- Working with Git branches, commits, and pull requests.
- Managing Linux users, groups, permissions, and SSH access.
- Configuring and maintaining Nginx.
- Deploying websites on AWS EC2.
- Building automated CI/CD pipelines with GitHub Actions.
- Writing and executing Bash automation scripts.
- Implementing deployment releases and rollback strategies.
- Monitoring server health and website traffic.
- Handling incidents and documenting technical resolutions.

---

## 🙌 Acknowledgements

This activity was created by **Haroon Khan, CTO, AntonX Private Limited**, as part of the DevOps Bootcamp.

Special thanks to all DevOps Warriors team members for their collaboration and contributions.

---

**Built collaboratively by Team DevOps Warriors.**

*Learn together. Build together. Ship together.* 🚀
