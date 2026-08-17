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
