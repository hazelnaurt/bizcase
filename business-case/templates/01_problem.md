# PURPOSE
Establish a clear and concise problem statement that defines the opportunity or issue.

# INPUTS
- Raw user request or findings from the Qualification stage.

# AI BEHAVIOR & QUESTIONS
- If the core metric failing or the specific constraint limiting the opportunity is unknown, STOP and ask the user for this data.
- Avoid pre-supposing a specific solution in the problem statement.

# EXPECTED OUTPUT
Generate the problem statement using the user's preferred framework (if not specified, default to SCQA):
- **SCQA (Situation, Complication, Question, Answer)**
  - Situation: The recognizable starting point or common basis.
  - Complication: The reason for acting now, containing threats or opportunities.
  - Question: How the hurdle can be overcome.
  - Answer: How the proposed intervention resolves the complication.
- **Root Cause, Impact, Threat**
  - Root Cause: What is fundamentally driving the issue.
  - Current Impact: Quantifiable current pain or loss.
  - Future Threat: What happens if unmitigated.
- **Problem, Evidence, Consequences**
- **Opportunity, Constraints, Risks**

# VALIDATION CHECKLIST (Do not print in output, use for internal validation)
[ ] Is the core issue quantifiable?
[ ] Does the statement avoid assuming the solution?

# NEXT WORKFLOW
Current State Analysis
