# Generic Agentic Development AI-KIT

This repository contains a comprehensive, framework-agnostic toolkit for establishing effective agentic development workflows in software projects. The AI-KIT provides templates, guidelines, and best practices for integrating AI agents (like those in Cursor) into your development lifecycle, serving as a foundation for building your team's **Context Repository**.

## Overview & Philosophy

The Generic Agentic Development AI-KIT provides a foundational structure for:

1. **Defining specialized AI agent roles** with clear responsibilities and workflows (see `agent_rules/`).
2. **Establishing standard document templates** for consistent project documentation (see `doc_templates/`).
3. **Implementing coding and operational guidelines** for maintainable and efficient systems (see `guidelines/`).
4. **Defining core principles** for effective context management and agent interaction (see `principles/`).
5. **Outlining integration strategies** for connecting agent workflows with development tools (see `strategies/`).

**Philosophy:** This kit is designed to be a **flexible starting point**, not a rigid prescription. Its purpose is to provide reusable, generic assets that you can adapt to your specific project needs, technology stack, team roles, and development methodology. It encourages structured interaction with AI agents, promoting consistency and leveraging AI capabilities more effectively across the software development lifecycle.

### The Context Repository Concept

The AI-KIT functions as more than just a collection of templates—it serves as the foundation for your team's **Context Repository**: a living, evolving knowledge base that grows in value over time. As you customize templates, define guidelines, and establish workflows, you're building a centralized source of truth for:

- How your team interfaces with AI assistants
- Your project's documentation standards
- Your code quality expectations
- Your operational procedures
- Your architectural patterns

This Context Repository becomes increasingly valuable as it evolves, capturing institutional knowledge and reducing the need to repeatedly explain the same concepts to AI assistants. For a deeper exploration of this concept, see `principles/CONTEXT_REPOSITORY_GUIDE.md`.

## Repository Structure

```
generic-agentic-kit/
├── agent_rules/                # Templates for defining agent roles (Orchestrator, Analyst, etc.) and User interaction rules.
│   ├── master_orchestrator_template.md
│   ├── code_quality_guardian_template.md
│   ├── documentation_manager_template.md
│   ├── operations_analyst_template.md
│   └── USER_RULES.md
├── doc_templates/              # Templates for project documentation (Architecture, APIs, Reports, Overviews, Tasks).
│   ├── ARCHITECTURE_template.md
│   ├── API_DOC_template.md
│   ├── PROJECT_OVERVIEW_template.md
│   ├── OPERATIONAL_REPORT_template.md
│   ├── TASK_TRACKER_template.md
│   └── LOG_ANALYSIS_TEMPLATE.md
├── guidelines/                 # Development guidelines (Coding Standards, Security, Deployment, Logging).
│   ├── CODING_STANDARDS_template.md
│   ├── SECURITY_CHECKLIST_template.md
│   ├── DEPLOYMENT_template.md
│   ├── LOGGING_GUIDELINES.md
│   └── VISUAL_ANALYSIS_GUIDE.md
├── principles/                 # Core principles for effective agent workflows (e.g., Context Management).
│   ├── CONTEXT_MANAGEMENT.md
│   ├── CONTEXT_REPOSITORY_GUIDE.md
│   └── KIT_EVOLUTION_STRATEGY.md
├── specifications/             # Templates for requirements and specifications (Requirements, Use Cases, User Stories).
│   ├── REQUIREMENTS_template.md
│   ├── USE_CASE_template.md
│   └── USER_STORY_template.md
├── strategies/                 # Strategies for integrating agent workflows with tools and processes.
│   ├── INTEGRATION_STRATEGIES.md
│   └── CURSOR_INTEGRATION_EXAMPLES.md
├── ARCHITECHTURE.md            # High-level architecture overview of the kit
├── TECH-FLOWCHART.md           # Technical flowcharts visualizing kit components and interactions
└── README.md                   # This file
```

## Core Agent Role Examples

*(Note: The templates in `agent_rules/` provide examples. Adapt or create roles specific to your project needs.)*

*   **Master Orchestrator:** Central coordinator for agent activities, managing task lifecycles and enforcing project standards.
*   **Operations Analyst:** Monitors system health, analyzes logs/metrics, provides insights for optimization. Performs multi-modal analysis using logs, metrics, and visual artifacts.
*   **Documentation Manager:** Creates and maintains technical documentation, diagrams, and API references.
*   **Code Quality Guardian:** Enforces coding standards, identifies potential issues, suggests improvements.

## Getting Started: Setup & Integration with Cursor

This section guides you through setting up the `generic-agentic-kit` alongside your primary project within Cursor.

### Prerequisites

*   **Cursor Installation:** Ensure you have Cursor installed. Download it from [cursor.sh](https://cursor.sh/).

### Step 1: Add Kit to Your Workspace

This is the recommended way to use the kit, keeping its resources separate but easily accessible to the AI.

1.  **Open Your Main Project:** Ensure the project you're working on is open as a workspace folder in Cursor (`File` > `Open Folder...`).
2.  **Add Kit to Workspace:**
    *   Go to `File` > `Add Folder to Workspace...`.
    *   Navigate to and select this `generic-agentic-kit` directory.
    *   Your Cursor Explorer panel should now show both your project folder and the `generic-agentic-kit` folder.
3.  **Verify Structure:** Your workspace might look like this:

    ```
    YOUR_PROJECT/
    ├── src/
    ├── ...

    generic-agentic-kit/
    ├── agent_rules/
    ├── doc_templates/
    ├── guidelines/
    ├── principles/
    ├── specifications/
    ├── strategies/
    ├── USER_RULES.md
    └── README.md
    ```

### Step 2: Configure Cursor Settings

Access Cursor's AI settings via the chat panel (usually the gear icon or `...` menu).

1.  **Command Denylist (Optional):** Review the 'Command Denylist' section. You might add commands you never want the AI to run (e.g., specific destructive commands).
2.  **Basic Checklists (Optional):** Explore the checklist options. You can enable basic checks (like adding imports or comments) that the AI performs automatically on code generation/edits.
3.  **Model Selection:** Choose the AI models you prefer for different tasks (e.g., Code Generation, Chat). Consider factors like speed, capability, and context window size. Experiment to find what works best for your needs (e.g., GPT-4 variants for complex tasks, Claude variants for speed or larger context).

### Step 3: Set Up Your User Rule

This rule helps the AI understand *your* role and how you interact with *your* project while using this kit.

1.  **Locate the Template:** Find the `USER_RULES.md` file within the `generic-agentic-kit` folder in your workspace.
2.  **Fill in Your Details:** Open `USER_RULES.md` and fill in the bracketed placeholders (`[Your Project Name Here]`, `[Your Primary Role]`, `[Your Core Responsibilities]`, etc.) to reflect your specific situation.
3.  **Add Rule to Cursor:**
    *   Go to Cursor AI Settings > Rules.
    *   Click "Add New Rule" or similar.
    *   Choose "User Rule".
    *   Copy the *entire content* of your filled-in `USER_RULES.md` file.
    *   Paste the content into the rule editor in Cursor.
    *   Save the rule. It should now be active for your interactions.

### Step 4: Configure MCPs (Middleware Communication Protocols)

MCPs allow Cursor's AI to interact with external tools like Jira or GitHub.

1.  **Identify Needs:** Determine which external tools you want the AI to interact with (e.g., Jira for task tracking, GitHub for repository actions).
2.  **Configure `mcp.json`:**
    *   In Cursor, navigate to your configuration directory (often `~/.cursor/` or accessible via `Help > Show Configuration Folder`).
    *   Open or create the `mcp.json` file.
    *   Add configurations for the MCPs you need. Refer to Cursor documentation for specific MCP availability and setup instructions. Example structure:

      ```json
      {
        "mcpServers": {
          "context7": { // Example for enhanced context
            "command": "npx",
            "args": ["-y", "@upstash/context7-mcp@latest"]
          },
          "jira": { // Example for Jira integration
            "command": "npx",
            "args": ["-y", "jira-mcp"],
            "env": {
              "JIRA_INSTANCE_URL": "https://your-instance.atlassian.net",
              "JIRA_USER_EMAIL": "your-email@example.com",
              "JIRA_API_KEY": "YOUR_ATLASSIAN_API_TOKEN"
            }
          },
          "github": { // Example placeholder for GitHub
            // ... configuration based on GitHub MCP documentation
          }
        }
      }
      ```
    *   **Note:** You will need to generate API tokens (like the `JIRA_API_KEY`) from the respective services (Jira, GitHub, etc.). Follow their documentation for secure token generation.
    *   Restart Cursor after modifying `mcp.json` for changes to take effect.

### Step 5: Define Agent Application Strategy

Control when specific agent roles (defined in `agent_rules/` or custom project rules) are automatically applied.

1.  **Access Rule Settings:** Go to Cursor AI Settings > Rules.
2.  **Project-Specific Configuration:** You can often configure rules to apply differently per project (workspace folder).
3.  **Set Application Strategy:**
    *   **Always Apply:** Consider setting the `master_orchestrator_template.md` rule (or a custom project-specific version) to "Always Apply" for your main project folder. This ensures coordination tasks are always considered.
    *   **When Agent Requests:** For other specialized agents (like `Code Quality Guardian`, `Documentation Manager`), set their rules to "When Agent Requests". This means they will only be activated when explicitly invoked in your chat prompts (e.g., `@agent_rules use code_quality_guardian to review this file`).
    *   Adjust these settings based on your workflow preferences.

### Setup Complete!

With these steps completed, Cursor is configured to work with your project and the `generic-agentic-kit`. You can now start instructing the AI, leveraging the defined rules and templates.

## How to Use the Kit (Usage Examples)

Now that setup is complete, instruct the AI agent within Cursor to reference specific files from the kit when performing tasks:

*   **Applying Agent Rules:**
    *   `@agent_rules adopt the role described in generic-agentic-kit/agent_rules/code_quality_guardian_template.md and review my recent code changes in 'YOUR_PROJECT/...'`
    *   `Follow the error handling protocol defined in generic-agentic-kit/agent_rules/master_orchestrator_template.md.`
*   **Using Document Templates:**
    *   `Create a new architecture document for my project located at 'YOUR_PROJECT/docs/ARCHITECTURE.md' using the template generic-agentic-kit/doc_templates/ARCHITECTURE_template.md.`
    *   `Generate an API reference in 'YOUR_PROJECT/docs/api.md' based on the structure in generic-agentic-kit/doc_templates/API_DOC_template.md.`
*   **Following Guidelines:**
    *   `Refactor the file 'YOUR_PROJECT/src/utils.py' according to the standards outlined in generic-agentic-kit/guidelines/CODING_STANDARDS_template.md.`
    *   `Ensure all logging in this module follows the practices described in generic-agentic-kit/guidelines/LOGGING_GUIDELINES.md.`
*   **Consulting Principles & Strategies:**
    *   `How can I improve context management for complex tasks, based on generic-agentic-kit/principles/CONTEXT_MANAGEMENT.md?`
    *   `Suggest an integration strategy for our CI/CD pipeline using the ideas in generic-agentic-kit/strategies/INTEGRATION_STRATEGIES.md.`
*   **Multi-Modal Analysis:**
    *   `Using the framework in generic-agentic-kit/guidelines/VISUAL_ANALYSIS_GUIDE.md, analyze these error screen screenshots in relation to the error logs I've attached and provide insights on how we can improve error communication to users.`
    *   `Adopt the role of Operations Analyst as defined in generic-agentic-kit/agent_rules/operations_analyst_template.md and analyze these application logs to identify performance bottlenecks, following the structure in generic-agentic-kit/doc_templates/LOG_ANALYSIS_TEMPLATE.md.`

**(Remember to replace `YOUR_PROJECT/...` with the actual paths in your main project folder.)**

## Growing Your Context Repository

The kit is designed to evolve over time, becoming increasingly valuable as you customize and extend it:

1. **Initial Setup (1-3 months):**
   * Customize essential templates to your environment
   * Establish basic usage patterns
   * Identify immediate gaps in the kit

2. **Expansion & Refinement (3-6 months):**
   * Add domain-specific templates and examples
   * Refine agent roles based on usage patterns
   * Develop more sophisticated workflows

3. **Long-term Evolution:**
   * Regularly update templates based on emerging best practices
   * Create specialized variants for different project types
   * Document successful patterns and anti-patterns

For a comprehensive evolution strategy, see `principles/KIT_EVOLUTION_STRATEGY.md`.

## Customizing the Kit

This AI-KIT is a starting point. Adapt it to your specific needs:

1.  **Modify Templates:** Edit the `.md` files in `agent_rules/`, `doc_templates/`, `guidelines/`, and `specifications/` to match your project's technology stack, team conventions, and specific requirements. Replace placeholders like `[Project Name]` or `[Technology Specifics]`. **Remember to update your User Rule (`USER_RULES.md`) as well!**
2.  **Add New Roles/Docs:** Create new files for specialized agent roles or documentation types relevant to your domain.
3.  **Refine Principles:** Update `principles/CONTEXT_MANAGEMENT.md` or add new principle documents reflecting your team's workflow philosophies.
4.  **Extend Strategies:** Add specific tool integration details or workflow patterns to `strategies/INTEGRATION_STRATEGIES.md`.

## Core Principles (Summary)

*   **Coordination:** Establish clear inter-agent communication patterns and error handling.
*   **Context Management:** Organize project context effectively using standardized referencing and metadata.
*   **Human-Agent Interaction:** Use consistent command patterns and provide clear feedback loops.
*   **Context Repository:** Build a living knowledge base that grows in value over time.
*   **Structured Flexibility:** Maintain enough structure for consistency while allowing adaptation to specific needs.

## Contributing

Contributions to improve the Generic Agentic Development AI-KIT are welcome! Please feel free to submit issues or pull requests with enhancements, bug fixes, or additional templates/guidelines.

## License

This project is licensed under the MIT License.

## Acknowledgements

The structure and concepts within this kit are inspired by best practices observed in various agentic development workflows and AI integration patterns.