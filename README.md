# GTD Execution System Template

Welcome! This is a complete Getting Things Done (GTD) execution system template with AI automation built in. It provides the folder structure, templates, and AI assistance to help you capture, clarify, organize, and execute on everything in your life.

**This template assumes you're familiar with GTD and the Horizons of Focus model.** If you're new to GTD, we recommend reading David Allen's "Getting Things Done" first. This README explains how to set up and use *this specific implementation* of GTD with AI automation.

## System Overview

### GTD Horizons of Focus

This system is organized using the six horizons of focus, from highest (50k) to lowest (00k):

**`execution-system/50k-purpose-and-principles/`** - Your "why" and core values
- `purpose.md` - Why you do what you do
- `principles.md` - How you operate and make decisions

**`execution-system/40k-vision/`** - 3-5 year aspirations
- `vision-summary.md` - What success looks like across life areas

**`execution-system/30k-goals/`** - 1-2 year objectives
- `active/` - Goals you're actively working toward
- `incubator/` - Goals you're considering but not ready to commit to

**`execution-system/20k-areas/`** - Ongoing responsibilities
- `areas-of-focus.md` - Key life roles (health, career, relationships, etc.)
- `dunbar-connections.md` - Relationship tracking across intimacy levels

**`execution-system/10k-projects/`** - Multi-step outcomes
- `active/` - Projects you're working on now (organized by area)
- `incubator/` - Projects you might do someday
- `completed/` - Finished projects
- `descoped/` - Projects you've decided not to do

**`execution-system/00k-next-actions/`** - Concrete next steps
- `contexts/` - Actions by where/how you do them (@laptop, @phone, @home, @errands)
- `@waiting.md` - Things you're waiting on from others
- `@deferred.md` - Actions scheduled for a specific future date
- `@incubating.md` - Ideas that might become actions someday
- `agendas/` - Topics to discuss with specific people
- `someday/` - Someday/maybe lists
- `completed.md` - Log of completed actions

**`execution-system/00-inbox.md`** - Capture everything here for processing

### Reviews

**`reviews/weekly/`** - Weekly review templates
**`reviews/quarterly/`** - Quarterly review templates

### Active vs Incubator

Many horizons (goals, projects) have two folders:
- **Active** - You're working on this now. It has your attention and commitment.
- **Incubator** - You might do this someday, but you're not ready yet. It's in "maybe" status.

This separation helps you focus on what matters now while preserving ideas for later.

## Prerequisites

You'll need:
- A computer with macOS, Windows, or Linux
- Internet connection
- The following software (we'll install these in the next section):
  - VS Code
  - Git
  - Claude Code
  - Python (via uv package manager)

## Step-by-Step Setup

### Part 1: Install Required Software

#### 1. Install VS Code

VS Code is the text editor you'll use to edit your execution system files.

1. Go to [https://code.visualstudio.com/](https://code.visualstudio.com/)
2. Download the installer for your operating system
3. Run the installer and follow the prompts
4. Open VS Code when installation is complete

#### 2. Install Git

Git helps you track changes to your files and sync with the skills/MCP repositories.

**Check if Git is already installed:**

Open Terminal (macOS/Linux) or Command Prompt (Windows) and run:

```bash
git --version
```

If you see a version number (e.g., `git version 2.39.0`), Git is already installed. Skip to step 3.

**If Git is not installed:**

1. Go to [https://git-scm.com/downloads](https://git-scm.com/downloads)
2. Download the installer for your operating system
3. Run the installer with default settings
4. Verify installation by running `git --version` again

#### 3. Install Claude Code

Claude Code is the AI assistant that will help you manage your execution system.

**Follow the official installation guide:** [https://docs.claude.com/en/docs/claude-code/quickstart](https://docs.claude.com/en/docs/claude-code/quickstart)

**Quick install commands:**

macOS/Linux (Homebrew):
```bash
brew install --cask claude-code
```

macOS/Linux (curl):
```bash
curl -fsSL https://claude.ai/install.sh | bash
```

Windows (PowerShell):
```powershell
irm https://claude.ai/install.ps1 | iex
```

Windows (Command Prompt):
```cmd
curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd
```

**After installation:**
1. Run `claude` in your terminal
2. Follow the prompts to log in with your Claude.ai account
3. Verify installation by typing `claude --version`

#### 4. Install Claude Code VS Code Extension

The VS Code extension integrates Claude directly into your editor.

**Installation:**
1. Open VS Code
2. Click the Extensions icon in the sidebar (or press `Cmd+Shift+X` on Mac, `Ctrl+Shift+X` on Windows)
3. Search for "Claude Code"
4. Click "Install"

**More info:** [https://docs.claude.com/en/docs/claude-code/vs-code](https://docs.claude.com/en/docs/claude-code/vs-code)

### Part 2: Clone This Repository

Now we'll get your execution system set up on your computer.

**Open Terminal (macOS/Linux) or Command Prompt (Windows)** and run these commands:

```bash
# Navigate to where you want your execution system
# Common locations: ~/Documents or ~/Desktop
cd ~/Documents

# Clone this repository
# Replace YOUR-USERNAME with the actual GitHub username
git clone https://github.com/YOUR-USERNAME/execution-system-template.git my-execution-system

# Navigate into the folder
cd my-execution-system

# Open in VS Code
code .
```

VS Code should open with your execution system folder loaded.

### Part 3: Customize the Template

Before setting up AI automation, customize the template for your life:

1. **Review example files** - Look through the sample projects, actions, goals, vision, purpose, and principles
2. **Update areas of focus** - Edit `execution-system/20k-areas/active/areas-of-focus.md` to match your life roles
3. **Personalize higher horizons**:
   - `execution-system/50k-purpose-and-principles/active/purpose.md` - Your purpose
   - `execution-system/50k-purpose-and-principles/active/principles.md` - Your values
   - `execution-system/40k-vision/active/vision-summary.md` - Your 3-5 year vision
4. **Delete or modify sample projects** - Remove example projects and create your own
5. **Set up your context lists** - Modify `@laptop.md`, `@phone.md`, etc. to match your actual contexts

**Commit your changes:**

```bash
git add .
git commit -m "Customize template for my execution system"
```

## AI Automation Setup

This is where the magic happens. You'll install two key components that let Claude Code help you manage your execution system:

1. **Claude Code Skills** - Pre-built AI workflows for inbox processing and project creation
2. **MCP Server** - Allows Claude to create projects, add actions, and query your system

### Part A: Install Claude Code Skills

Skills are reusable AI workflows. We'll install two skills:
- **process-inbox** - Guides you through GTD inbox processing
- **natural-planning-project** - Helps you create well-formed projects using David Allen's Natural Planning Model

**Step-by-step installation:**

1. **Open Terminal in VS Code**
   - In VS Code, press `Ctrl+` ` (backtick) to open the integrated terminal
   - Make sure you're in your execution system folder (`my-execution-system`)

2. **Create the `.claude` directory and clone skills**

```bash
# Create .claude directory
mkdir -p .claude
cd .claude

# Clone the skills repository as a git submodule
git submodule add https://github.com/elinsky/execution-system-skills.git skills

# Return to root folder
cd ..

# Commit the submodule
git add .gitmodules .claude
git commit -m "Add execution system skills"
```

3. **Verify installation**

Check that `.claude/skills/` exists and contains folders named `process-inbox` and `natural-planning-project`.

In VS Code, expand the `.claude` folder in the file explorer. You should see:
```
.claude/
  skills/
    process-inbox/
    natural-planning-project/
```

4. **What these skills do**

- **process-inbox** - When you say "Process my inbox" to Claude, it guides you through the GTD clarify and organize workflow, helping you decide what each inbox item is and where it belongs in your system.

- **natural-planning-project** - When you say "Create a new project for [something]", Claude guides you through defining purpose, vision, brainstorming, and creating next actions.

**More info:** [https://docs.claude.com/en/docs/claude-code/skills](https://docs.claude.com/en/docs/claude-code/skills)

### Part B: Install MCP Server

The MCP (Model Context Protocol) server gives Claude the ability to create projects, add actions, list goals, and perform other operations on your execution system.

**Step-by-step installation:**

#### 1. Install uv (Python package manager)

uv is a fast Python package manager. We'll use it to run the MCP server.

**Installation guide:** [https://docs.astral.sh/uv/getting-started/installation/](https://docs.astral.sh/uv/getting-started/installation/)

**Quick install:**

macOS/Linux:
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Windows (PowerShell):
```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**Verify installation:**
```bash
uv --version
```

You should see a version number (e.g., `uv 0.4.15`).

#### 2. Clone the MCP server repository

**Open a new terminal** and navigate to where you keep code repositories (can be different from your execution system):

```bash
# Navigate to your code folder
cd ~/Documents  # or wherever you keep code

# Clone the MCP server repository
git clone https://github.com/elinsky/execution-system-mcp.git

# Navigate into the folder
cd execution-system-mcp
```

#### 3. Install dependencies

```bash
uv sync
```

This installs all the Python packages the MCP server needs.

#### 4. Configure Claude Code to use the MCP server

Now we need to tell Claude Code where to find the MCP server and your execution system.

**In VS Code, create a new file in your execution system folder** called `.mcp.json`:

```json
{
  "mcpServers": {
    "gtd-project-creator": {
      "command": "uv",
      "args": [
        "--directory",
        "/FULL/PATH/TO/execution-system-mcp",
        "run",
        "execution-system-mcp"
      ],
      "env": {
        "GTD_BASE_DIR": "/FULL/PATH/TO/my-execution-system/execution-system"
      }
    }
  }
}
```

**IMPORTANT: Replace `/FULL/PATH/TO/` with the actual full paths on your system.**

**How to find full paths:**

macOS/Linux:
```bash
# Get the path to execution-system-mcp
cd ~/Documents/execution-system-mcp
pwd
# Copy this path

# Get the path to your execution system
cd ~/Documents/my-execution-system/execution-system
pwd
# Copy this path
```

Windows:
```cmd
# Get the path to execution-system-mcp
cd C:\Users\YourName\Documents\execution-system-mcp
cd
# Copy this path (use double backslashes in JSON: C:\\Users\\...)

# Get the path to your execution system
cd C:\Users\YourName\Documents\my-execution-system\execution-system
cd
# Copy this path
```

**Example `.mcp.json` on macOS:**
```json
{
  "mcpServers": {
    "gtd-project-creator": {
      "command": "uv",
      "args": [
        "--directory",
        "/Users/jane/Documents/execution-system-mcp",
        "run",
        "execution-system-mcp"
      ],
      "env": {
        "GTD_BASE_DIR": "/Users/jane/Documents/my-execution-system/execution-system"
      }
    }
  }
}
```

**Example `.mcp.json` on Windows:**
```json
{
  "mcpServers": {
    "gtd-project-creator": {
      "command": "uv",
      "args": [
        "--directory",
        "C:\\Users\\Jane\\Documents\\execution-system-mcp",
        "run",
        "execution-system-mcp"
      ],
      "env": {
        "GTD_BASE_DIR": "C:\\Users\\Jane\\Documents\\my-execution-system\\execution-system"
      }
    }
  }
}
```

**Save the file.**

#### 5. Verify MCP server is working

1. **In VS Code, open the Claude Code panel** (click the sparkle icon in the sidebar)
2. **Ask Claude:** "List my active projects"
3. Claude should respond with a list of your active projects using the MCP server

If it works, you're all set! If not, double-check that:
- The paths in `.mcp.json` are correct and use full absolute paths
- You used double backslashes (`\\`) on Windows
- You ran `uv sync` in the `execution-system-mcp` folder
- The `execution-system` subfolder exists in your execution system folder

**More info:** [https://docs.claude.com/en/docs/claude-code/mcp](https://docs.claude.com/en/docs/claude-code/mcp)

## Using the System

Now that everything is set up, here's how to use your GTD execution system with AI assistance.

### Daily Workflow

1. **Capture** - Throughout the day, add items to `execution-system/00-inbox.md`
   - Don't worry about organizing or clarifying yet
   - Just capture everything that has your attention

2. **Process Inbox** - When you're ready, ask Claude:
   ```
   Process my inbox
   ```
   Claude will guide you through clarifying each item and putting it in the right place.

3. **Work from context lists** - During the day, check your context lists:
   - `@laptop` - Things you can do on your computer
   - `@phone` - Calls, texts, mobile actions
   - `@home` - Things to do at home
   - `@errands` - Out-and-about tasks

4. **Check waiting/deferred** - Regularly review:
   - `@waiting.md` - What are you waiting on?
   - `@deferred.md` - What becomes actionable today?

### Creating Projects

When you identify something that requires multiple steps:

**Ask Claude:**
```
Create a new project for [your project idea]
```

Claude will guide you through:
1. Choosing planning depth (Quick/Standard/Deep)
2. Defining purpose and vision
3. Brainstorming (for deep planning)
4. Creating at least one next action

The project file is created automatically in the right area folder.

### Weekly Review

Every week, conduct a weekly review:

1. **Create this week's review file** in `reviews/weekly/YYYY-WXX.md` (copy the template)
2. **Follow the checklist:**
   - Process inbox to zero
   - Review calendar (past week + next 2 weeks)
   - Review all context lists
   - Review @waiting, @deferred, @incubating
   - Review all active projects
   - Check goals progress
   - Plan next week's key outcomes

3. **Ask Claude for help:**
   ```
   List all projects needing review
   List all actions for [project name]
   Show me my goals
   ```

### Quarterly Review

Every quarter, conduct a deeper review:

1. **Create this quarter's review file** in `reviews/quarterly/YYYY-QX.md` (copy the template)
2. **Review goals** - What progress have you made? What needs adjustment?
3. **Review areas of focus** - Are you giving appropriate attention to all life areas?
4. **Check vision alignment** - Are your daily actions aligned with your 3-5 year vision?
5. **Update higher horizons** - Revise vision, purpose, principles as you evolve

## You're Ready!

Your GTD execution system with AI automation is now set up. Start by:

1. Capturing some items in your inbox
2. Asking Claude to "Process my inbox"
3. Creating your first project with Claude's help

Over time, this system becomes your external brain - capturing everything, helping you clarify what matters, and ensuring nothing falls through the cracks.

**Happy executing!**
