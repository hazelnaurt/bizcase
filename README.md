# Business Case Development System

An iterative, human-in-the-loop workflow powered by a custom **Claude Code Skill**. This system transforms Claude from a generic document generator into an analytical Business Analyst. Instead of outputting an entire business case at once, it generates **one stage at a time**, pausing for human review, feedback, and explicit approval.

---

## 📁 Folder Structure

```text
.
├── .claude/
│   └── skills/
│       └── bizcase/
│           └── SKILL.md            # Execution protocol & stage-gating state engine
│
├── .business-case/
│   ├── templates/                  # Independent stage templates
│   │   ├── 01_problem.md           # Problem definition & selection frameworks
│   │   ├── 02_current_state.md     # Current state analysis & baseline cost
│   │   ├── 03_options.md           # Options analysis (enforces "Do Nothing" option)
│   │   ├── 04_cba.md               # Cost-Benefit Analysis (CapEx, OpEx, ROI)
│   │   └── 05_recommendation.md    # Strategic decision synthesis
│   │
│   └── cases/                      # Active working directories
│       └── <case-name>/
│           ├── state.json          # Workflow state tracking
│           ├── 01_problem_draft.md # Active working draft
│           └── 01_problem_approved.md
└── README.md
```
# 🚀 Setup Instructions

1. Clone/Ensure Project Structure:
   
   Verify that .claude/skills/bizcase/SKILL.md and .business-case/templates/ exist in your workspace root.

2. Initialize a Case Folder:
   
   Create a new case directory under .business-case/cases/:

    ```Bash
    mkdir -p .business-case/cases/drought-mitigation
    ```
3. Set the Initial State:

   Create a state.json file inside your new case folder:

   ```
   {
    "active_stage": "01_problem"
   }
   ```

# 📖 Step-by-Step Usage Guide

## Step 1: Launch Claude Code

Open your terminal at the root of your workspace and start Claude Code:

```
claude
```

## Step 2: Trigger the Business Case Skill

Invoke the custom skill by typing /bizcase or initiating a request:

```
/bizcase Let's work on the drought-mitigation case. Here are my raw notes on recent water bills...
```

## Step 3: Review the Generated Draft (Human-in-the-Loop)

Claude will process your inputs, generate only the active stage artifact (e.g., 01_problem_draft.md), write it to your case folder, and pause execution.

- Review the file: Open
  
  `.business-case/cases/drought-mitigation/01_problem_draft.md` in your text editor (VS Code, Cursor, Neovim, etc.).

## Step 4: Approve or Refine

- If changes are needed: Tell Claude what to adjust directly in your CLI session:

  ```
  Please rephrase using the SCQA framework and highlight the municipal fine risk.
  ```

  Claude will edit `01_problem_draft.md` and pause again.

- If you approve: Type `Approve`:

  ```
  Approve
  ```

  Claude will automatically:

  1. Rename `01_problem_draft.md` to `01_problem_approved.md`.

  2. Update `state.json` to `"active_stage"`: `"02_current_state"`.

  3. Prompt you for any additional data needed for the next stage.
 
## Step 5: Final Assembly

Repeat the workflow through `05_recommendation`. Once the final stage is approved, instruct Claude to generate the Executive Summary and combine all approved artifacts into a single output:

```
Assemble the final business case.
```

Claude will compile all `*_approved.md` files into `Final_Business_Case.md`.

# 🛡️ Best Practices & Rules

- Loose Context Coupling: Each stage template only reads approved outputs from previous stages (`*_approved.md`). Drafts in progress are never fed forward.
- No Synthetic Metrics: Do not let the AI invent financial numbers during the Cost-Benefit stage. If exact figures are missing, instruct Claude during review to insert variables (e.g., `[Insert Expected Maintenance Cost]`).
- Git Version Control: Keep `.business-case/templates/` committed to Git. You may choose to add `.business-case/cases/` to `.gitignore` if cases contain private operational data.
