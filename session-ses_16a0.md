# Preprod to prod promotion with package tagging

**Session ID:** ses_16a03c420ffePgAqgb7Pl3MCJO
**Created:** 6/5/2026, 9:43:16 AM
**Updated:** 6/5/2026, 10:04:04 AM

---

## User

hey i want the promotion strategy on github for from preprod to prod with package tagging how can i do that?

---

## Assistant (Plan · DeepSeek V4 Flash · 3.9s)

_Thinking:_

The user is asking about a promotion strategy on GitHub for moving from preprod to prod with package tagging. This sounds like they want to set up a CI/CD pipeline or GitHub Actions workflow that:

1. Promotes code from preprod to prod
2. Tags packages as part of the process

Let me first understand their current setup - they're in their home directory `/Users/vishal.kumar`. Let me check if this is a GitHub repository or what kind of project they have.

Since I'm in plan mode (read-only), I should ask clarifying questions and explore their current setup to provide a good plan.

Let me look at what's in their current directory first.

**Tool: read**

**Input:**
```json
{
  "filePath": "/Users/vishal.kumar"
}
```

**Output:**
```
<path>/Users/vishal.kumar</path>
<type>directory</type>
<entries>
.bash_history
.bash_profile
.bash_sessions/
.cache/
.cagent/
.CFUserTextEncoding
.config/
.copilot/
.docker/
.DS_Store
.gitconfig
.local/
.npm/
.nvm/
.Trash/
.vscode-shared/
.vscode/
Applications/
Desktop/
Documents/
Downloads/
go/
Library/
Movies/
Music/
Pictures/
Postman/
Projects/
Public/

(29 entries)
</entries>
```

**Tool: bash**

**Input:**
```json
{
  "command": "git status 2>/dev/null && echo \"---GIT REPO---\" && git remote -v 2>/dev/null; ls -la *.yml *.yaml 2>/dev/null; ls -la .github/workflows/ 2>/dev/null || echo \"No .github/workflows found\"",
  "description": "Check git status and workflows"
}
```

**Output:**
```
No .github/workflows found

```

---

## Assistant (Plan · DeepSeek V4 Flash · 2.8s)

_Thinking:_

This is their home directory, not a specific project directory. Let me look around for their projects to understand what kind of project they're working on. But since I'm in plan mode, I should ask clarifying questions about what exactly they want.

Let me check if they have any projects directory with relevant work.

**Tool: bash**

**Input:**
```json
{
  "description": "Check for project directories",
  "command": "ls -la ~/Projects/ 2>/dev/null || echo \"No Projects dir\"; ls -la ~/go/ 2>/dev/null || echo \"No go dir\""
}
```

**Output:**
```
total 16
drwxr-xr-x   7 vishal.kumar  ONDC\Domain Users   224  4 Jun 09:30 .
drwxr-x---+ 31 vishal.kumar  ONDC\Domain Users   992  4 Jun 10:15 ..
-rw-r--r--@  1 vishal.kumar  ONDC\Domain Users  6148  4 Jun 09:44 .DS_Store
drwxr-xr-x   3 vishal.kumar  ONDC\Domain Users    96  3 Jun 22:02 mcr
drwxr-xr-x@ 28 vishal.kumar  ONDC\Domain Users   896  3 Jun 10:07 mcr-platform
drwxr-xr-x   3 vishal.kumar  ONDC\Domain Users    96  4 Jun 09:30 mcr-prompt-eval
drwxr-xr-x@ 30 vishal.kumar  ONDC\Domain Users   960  3 Jun 13:54 mcr-ui
total 0
drwxr-xr-x@  3 vishal.kumar  ONDC\Domain Users   96  3 Jun 10:58 .
drwxr-x---+ 31 vishal.kumar  ONDC\Domain Users  992  4 Jun 10:15 ..
drwxr-xr-x@  3 vishal.kumar  ONDC\Domain Users   96  3 Jun 10:58 pkg

```

---

## Assistant (Plan · DeepSeek V4 Flash · 104.1s)

_Thinking:_

I see they have project directories. Let me ask some clarifying questions to understand what they need before I can produce a good plan. Since I'm in plan mode, I need to gather requirements.

I see you have some project directories (`mcr`, `mcr-platform`, `mcr-ui`, etc.). To give you the right plan, I need a few more details:

**Tool: question**

**Input:**
```json
{
  "questions": [
    {
      "question": "Which project does this promotion strategy apply to?",
      "header": "Project",
      "options": [
        {
          "label": "mcr-platform",
          "description": "~/Projects/mcr-platform"
        },
        {
          "label": "mcr-ui",
          "description": "~/Projects/mcr-ui"
        },
        {
          "label": "mcr",
          "description": "~/Projects/mcr"
        },
        {
          "label": "mcr-prompt-eval",
          "description": "~/Projects/mcr-prompt-eval"
        },
        {
          "label": "A new project",
          "description": "Not listed, starting fresh"
        }
      ]
    },
    {
      "question": "What type of packages are you tagging/releasing?",
      "header": "Package type",
      "options": [
        {
          "label": "Docker images",
          "description": "Container images pushed to a registry"
        },
        {
          "label": "npm packages",
          "description": "JavaScript/TypeScript packages"
        },
        {
          "label": "Git tags only",
          "description": "Semantic versioning git tags (v1.2.3)"
        },
        {
          "label": "Multiple artifacts",
          "description": "Combination of above"
        },
        {
          "label": "Other",
          "description": "Different package format"
        }
      ]
    },
    {
      "question": "What does 'promotion' mean in your workflow?",
      "header": "Promotion meaning",
      "options": [
        {
          "label": "Merge PR preprod->main",
          "description": "GitHub PR from preprod branch to main/prod branch"
        },
        {
          "label": "Promote Docker tag",
          "description": "Re-tag an existing Docker image (e.g. :staging -> :latest)"
        },
        {
          "label": "Both",
          "description": "Merge code + promote package tags"
        },
        {
          "label": "Other",
          "description": "Custom promotion flow"
        }
      ]
    },
    {
      "question": "What's your current branching strategy?",
      "header": "Branching",
      "options": [
        {
          "label": "GitFlow",
          "description": "develop / release / main branches"
        },
        {
          "label": "Trunk-based",
          "description": "Short-lived branches off main"
        },
        {
          "label": "GitHub Flow",
          "description": "feature branches -> main"
        },
        {
          "label": "Preprod branch",
          "description": "Separate preprod and prod branches"
        }
      ]
    }
  ]
}
```

**Output:**
```
User has answered your questions: "Which project does this promotion strategy apply to?"="A new project", "What type of packages are you tagging/releasing?"="Docker images", "What does 'promotion' mean in your workflow?"="Promote Docker tag", "What's your current branching strategy?"="so i have staging branch and preprod there is no prod i will promote the preprod image to production environment". You can now continue with the user's answers in mind.
```

---

## Assistant (Plan · DeepSeek V4 Flash · 46.0s)

_Thinking:_

Based on the user's responses:
- New project (no existing repo yet)
- Docker images
- Promote Docker tag (re-tag existing Docker image)
- Branching: staging branch, preprod branch, no prod branch - promote preprod image to prod environment

So the workflow is:
1. Build and push Docker image from staging branch with a staging tag
2. When code goes from staging -> preprod, tag the image with preprod tag
3. When promoting preprod -> prod, re-tag the existing preprod Docker image with prod tag

Let me think about what a good GitHub Actions workflow would look like:

Typical strategy:
- **Branch-based tagging**: Images built from `staging` branch get `:staging-{sha}` or `:staging` tag
- Images built from `preprod` branch get `:preprod-{sha}` or `:preprod` tag
- **Promotion**: Manually or via workflow_dispatch, take the current `:preprod` image digest and push it as `:production` (or `:latest`)

Alternatively, a simpler approach:
- Use Git tags for promotion triggers
- `git tag v1.2.3-staging` triggers build + push with staging tag
- `git tag v1.2.3-preprod` triggers promote staging->preprod
- `git tag v1.2.3-prod` triggers promote preprod->prod

Let me ask some more questions to narrow down the plan.

Got it. So the flow is:

1. **Build** Docker images from **staging** branch
2. **Promote** to preprod (e.g., on merge to preprod branch or manual trigger)
3. **Promote** from preprod → production (re-tag existing image, no rebuild)

A few more questions to shape the plan:

**Tool: question**

**Input:**
```json
{
  "questions": [
    {
      "question": "How do you want to trigger preprod→prod promotion?",
      "options": [
        {
          "label": "Manual (workflow_dispatch)",
          "description": "Click a button in GitHub Actions UI with environment confirmation"
        },
        {
          "label": "Git tag push",
          "description": "Push a tag like v1.2.3-prod to trigger promotion"
        },
        {
          "label": "GitHub Release",
          "description": "Create a Release in GitHub UI"
        },
        {
          "label": "Merge to a 'prod' branch",
          "description": "PR/merge triggers it automatically"
        }
      ],
      "header": "Trigger method"
    },
    {
      "question": "Do you have a container registry in mind?",
      "options": [
        {
          "label": "GitHub Container Registry (ghcr.io)",
          "description": "ghcr.io/owner/image"
        },
        {
          "label": "Docker Hub",
          "description": "docker.io/username/image"
        },
        {
          "label": "AWS ECR",
          "description": "Amazon Elastic Container Registry"
        },
        {
          "label": "Undecided",
          "description": "Not sure yet, want a generic approach"
        }
      ],
      "header": "Container registry"
    },
    {
      "question": "Tag naming convention?",
      "options": [
        {
          "label": "Promote by digest",
          "description": "Copy the exact image digest (SHA256) from preprod tag to prod tag — deterministic"
        },
        {
          "label": "Promote by tag",
          "description": "Re-tag :preprod → :production (simpler but has a race window)"
        }
      ],
      "header": "Promotion method"
    },
    {
      "question": "Single image or multiple services?",
      "options": [
        {
          "label": "Single image",
          "description": "One Docker image (e.g., API server)"
        },
        {
          "label": "Multiple services",
          "description": "Several microservices (API, worker, UI, etc.)"
        }
      ],
      "header": "Services"
    }
  ]
}
```

**Output:**
```
User has answered your questions: "How do you want to trigger preprod→prod promotion?"="Git tag push", "Do you have a container registry in mind?"="GitHub Container Registry (ghcr.io)", "Tag naming convention?"="Promote by tag", "Single image or multiple services?"="Single image". You can now continue with the user's answers in mind.
```

---

## Assistant (Plan · DeepSeek V4 Flash · 10.6s)

_Thinking:_

Now I have a clear picture. Let me outline a plan:

**Strategy: Git Tag–Driven Docker Promotion (Single Image, ghcr.io)**

Branches:
- `staging` — development branch, builds Docker image
- `preprod` — pre-production, promotes staging→preprod
- No `prod` branch — production is just a Docker tag

Tags that trigger actions:
1. `promote/preprod/v*` — when pushed, promote the latest staging image to `:preprod`
2. `promote/prod/v*` — when pushed, promote the preprod image to `:prod` (or `:latest`)

Workflow files needed:
1. **Build & push staging** — triggered on push to `staging` branch, builds and pushes `ghcr.io/owner/image:staging` and `ghcr.io/owner/image:staging-{sha}`
2. **Promote to preprod** — triggered on push of tag `promote/preprod/v*`, pulls `:staging` and pushes as `:preprod` (also creates a GitHub Release)
3. **Promote to prod** — triggered on push of tag `promote/prod/v*`, pulls `:preprod` and pushes as `:prod` (and `:latest`)

This is a clean, Git-native approach where the promotion history is recorded in git tags.

Let me present this as a clear plan. Since I'm in plan mode, I'll outline the strategy and workflow design without making changes.

Here's the plan based on your answers:

---

## Promotion Strategy: Git Tag–Driven Docker Image Promotion

### Overview

```
┌──────────────────────────────────────────────────────┐
│  Branches               Git Tags                      │
│                                                       │
│  staging ──build──► ghcr.io/.../app:staging           │
│                                                       │
│  preprod  ─promote──► ghcr.io/.../app:preprod         │
│              ↑                                         │
│        push tag: promote/preprod/v1.2.3               │
│                                                       │
│  (no prod branch) ─promote──► ghcr.io/.../app:prod    │
│                     └──► ghcr.io/.../app:latest       │
│              ↑                                         │
│        push tag: promote/prod/v1.2.3                  │
└──────────────────────────────────────────────────────┘
```

### Workflows (3 GitHub Actions)

| Workflow | Trigger | What it does |
|---|---|---|
| **1. Build & Push Staging** | Push to `staging` branch | Builds Docker image, pushes `:staging` + `:staging-{sha}` to ghcr.io |
| **2. Promote to Preprod** | Push tag `promote/preprod/v*` | Pulls `:staging`, re-tags & pushes as `:preprod`. Creates a Git tag `v*` + GitHub Release. |
| **3. Promote to Prod** | Push tag `promote/prod/v*` | Pulls `:preprod`, re-tags & pushes as `:prod` and `:latest`. Creates GitHub Release. |

### The Promotion Flow (Day-to-day)

```bash
# 1. Work on staging, code gets built automatically
git push origin staging

# 2. When ready for preprod — push a preprod tag
git tag promote/preprod/v1.2.3
git push origin promote/preprod/v1.2.3   # promotes staging → preprod

# 3. When ready for production — push a prod tag
git tag promote/prod/v1.2.3
git push origin promote/prod/v1.2.3      # promotes preprod → prod (no rebuild)
```

### Files to create

```
.github/
├── workflows/
│   ├── build-staging.yml       # On push to staging
│   ├── promote-preprod.yml     # On tag promote/preprod/*
│   └── promote-prod.yml        # On tag promote/prod/*
```

Each workflow will need:
- `secrets.GITHUB_TOKEN` for ghcr.io auth
- `ghcr.io` login step
- Docker build/pull, tag, and push steps

### Security considerations

- **Environment protection**: The `promote-prod.yml` workflow can be configured with **required reviewers** in the GitHub environment settings (even though triggered by a tag push, you can gate it with environments + approval)
- **Digest pinning**: For even safer promotion, you could pull by digest (`docker pull image@sha256:...`) instead of by tag — happy to adjust if you want

---

**Next steps**: I can implement this by creating the 3 workflow files under `.github/workflows/` in your new repository. Would you like me to proceed? Also, what's the name of your Docker image / repo (e.g., `mcr-api`, `mcr-app`)?

---

## User

so here is the catch from staging to preprod no preprod but tagging will be done when moved to preprod to prod

---

## Assistant (Plan · DeepSeek V4 Flash · 28.4s)

_Thinking:_

The user is clarifying that:
1. There's no "preprod" branch or separate environment for staging → preprod
2. The tagging/promotion only happens when going from preprod → prod

So let me re-understand their flow:
- They have a `staging` branch where development happens
- No separate preprod branch or environment
- They want to promote the image that's currently in "preprod" (somehow) to "prod" using Git tags

Wait, let me re-read: "from staging to preprod no preprod but tagging will be done when moved to preprod to prod"

I think they're saying:
- There IS a "preprod" environment/stage, but they don't need a separate branch or promotion step for staging → preprod
- The only promotion that needs tagging is preprod → prod

So perhaps the flow is:
1. Build happens from staging (or some other trigger) and deploys to staging environment
2. Some manual process moves code to preprod (no git tag needed)
3. When ready for prod, push a tag to promote (re-tag) the preprod Docker image to prod

So maybe:
- Workflow 1: On push to `staging`, build and push image with `:staging` tag
- Workflow 2: On push to a specific branch or manually, promote staging image to preprod (or maybe this is done outside of git tags)
- Workflow 3: On push of `promote/prod/*` tag, promote the `:preprod` image to `:prod`

Or maybe even simpler — they only want ONE promotion workflow: preprod → prod triggered by a Git tag, and everything before that is handled differently.

Let me ask for clarification.

Ah, I think I understand now. Let me rephrase to confirm:

- **Staging → Preprod**: happens automatically or manually without any Git tag (just build + deploy, no formal "promotion tag" needed)
- **Preprod → Prod**: the **only** promotion you want tracked with a Git tag, where the preprod Docker image gets re-tagged to prod

Is that correct? If so, the plan simplifies to:

---

## Simplified Plan

### Workflow 1: Build & Push (on push to `staging`)
Builds Docker image and pushes `:staging` + `:staging-{sha}` to ghcr.io.

### Workflow 2: Promote to Preprod (trigger: ?)
This is the gap I need to understand. How does the image go from `:staging` → `:preprod` today?
- Is it a manual `docker pull` + `docker tag` + `docker push` on your machine?
- Or should there still be a GitHub Actions workflow for this, just *without* a Git tag trigger?

### Workflow 3: Promote Preprod → Prod (trigger: Git tag)
Triggered by `promote/prod/v*` tag push. Pulls the current `:preprod` image digest and pushes it as `:prod` and `:latest`.

---

Can you clarify how the staging → preprod move happens? And to confirm — you only want one Git tag (for the prod promotion), right?

---

## User

so on github registry it will be pushed via ghcr but manually it will be promoted from preprod to prod

---

## Assistant (Plan · DeepSeek V4 Flash · 14.3s)

_Thinking:_

Now I understand the full picture:

1. **Staging → Build** — push to `staging` builds Docker image and pushes to ghcr.io with a staging tag
2. **Staging → Preprod** — happens manually (outside of GitHub Actions), someone manually promotes the staging image to preprod tag
3. **Preprod → Prod** — the user wants a Git tag (`promote/prod/v*`) that triggers a GitHub Actions workflow to promote the preprod image to prod tag, BUT they said "manually it will be promoted from preprod to prod"

Wait, I need to reconcile this. They said:
- "on github registry it will be pushed via ghcr but manually it will be promoted from preprod to prod"

So I think they're saying:
- The image is in ghcr.io
- The promotion from preprod to prod happens **manually** (not via an automated GitHub Actions workflow triggered by a git tag)

But wait, they originally asked for a promotion strategy "with package tagging". Let me re-read.

So maybe the promotion from preprod to prod is:
- Done **manually** (i.e., someone runs a command or clicks a button)
- But should still result in proper tagging

Actually, re-reading again: "on github registry it will be pushed via ghcr but manually it will be promoted from preprod to prod"

I think they mean:
1. Images are pushed to ghcr.io (the registry)
2. But the **promotion** from preprod to prod is done **manually** — not via an automated workflow

So perhaps they want a workflow that supports a manual promotion step. This could mean:
- A `workflow_dispatch` triggered workflow where someone manually runs it to promote preprod→prod
- Or they just want to know the process: manually pull the preprod image and re-tag it as prod

Let me ask to clarify. They initially said "Git tag push" for the trigger, but now saying "manually". Let me clarify what "manually" means to them.

Just to make sure I have this right — when you say **manually**, what does that look like to you?

**Tool: question**

**Input:**
```json
{
  "questions": [
    {
      "header": "Manual promotion",
      "question": "How do you want to manually trigger the preprod→prod promotion?",
      "options": [
        {
          "label": "workflow_dispatch",
          "description": "A 'Run workflow' button in GitHub Actions UI — you click it, optionally enter a version, and it promotes the image"
        },
        {
          "label": "Local docker commands",
          "description": "docker pull ghcr.io/.../app:preprod && docker tag ... && docker push ... on your local machine"
        },
        {
          "label": "Git tag push",
          "description": "Still push a git tag, but that's your 'manual' step (git tag + git push)"
        }
      ]
    }
  ]
}
```

**Output:**
```
User has answered your questions: "How do you want to manually trigger the preprod→prod promotion?"="Git tag push". You can now continue with the user's answers in mind.
```

---

## Assistant (Plan · DeepSeek V4 Flash · 7.0s)

_Thinking:_

So they want:
1. A workflow that builds and pushes Docker image to ghcr.io on push to `staging` branch
2. The staging → preprod promotion happens outside of Git/GitHub (manually via docker commands or some other mechanism)
3. The preprod → prod promotion is triggered by pushing a Git tag like `promote/prod/v*` — this triggers a GitHub Actions workflow that pulls the `:preprod` image from ghcr.io and pushes it as `:prod`

So it's still a Git tag trigger, just "manual" in the sense that they have to manually `git tag` and `git push` the tag.

Now I have a clear picture. Let me present the final plan:

**Workflows:**

1. **build-staging.yml** — On push to `staging` branch
   - Checkout code
   - Login to ghcr.io
   - Build Docker image
   - Push `:staging` and `:staging-{sha}` tags

2. **promote-prod.yml** — On push of tag `promote/prod/v*`
   - Login to ghcr.io
   - Pull `:preprod` image
   - Re-tag as `:prod` and `:latest`
   - Push tags
   - Optionally create a GitHub Release

That's it. Two workflows, clean and simple.

Let me present this final plan to the user.

Perfect, now it's crystal clear. Here's the final plan:

---

## Final Strategy

```
staging branch push ──build──► ghcr.io/.../app:staging
                                   │
                            [MANUAL: outside Git]
                                   │
                                   ▼
                               :preprod tag
                                   │
                      git tag promote/prod/v1.2.3
                      git push origin promote/prod/v1.2.3
                                   │
                                   ▼
                          ghcr.io/.../app:prod
                          ghcr.io/.../app:latest
```

### Two GitHub Actions workflows:

| File | Trigger | Action |
|---|---|---|
| `.github/workflows/build-staging.yml` | Push to `staging` branch | Build & push `:staging` + `:staging-{sha}` to ghcr.io |
| `.github/workflows/promote-prod.yml` | Tag push `promote/prod/v*` | Pull `:preprod` image → re-tag as `:prod` & `:latest` → push → create GitHub Release |

### Your daily flow:

```bash
# 1. Code on staging — auto-built
git push origin staging

# 2. Manually promote staging → preprod (outside Git — docker pull/tag/push)

# 3. When ready for prod — push a tag
git tag promote/prod/v1.2.3
git push origin promote/prod/v1.2.3   # promotes :preprod → :prod
```

### Simple and effective:
- **Single source of truth**: ghcr.io holds all tags
- **Immutable promotion**: no rebuild on prod — the exact same image digest that was tested in preprod goes to prod
- **Auditable**: every prod deployment is traceable via Git tags and GitHub Releases

---

After your confirmation (or if you want to tweak anything), I'll create both workflow files for you. Shall I proceed?

---

