# Cursor Integration Examples

## Introduction

This document provides concrete examples and best practices for integrating the Generic Agentic Development AI-KIT with the Cursor IDE. By following these patterns, you'll maximize the effectiveness of AI-assisted development, ensure consistent context, and build a sustainable workflow that improves over time.

## Setup Instructions

### 1. Workspace Configuration

1. **Add the Kit to Your Workspace**
   ```bash
   # Clone the kit repository (if using Git)
   git clone https://github.com/your-org/generic-agentic-kit.git
   
   # Or simply copy the kit folder to your workspace
   cp -r /path/to/generic-agentic-kit /path/to/your/workspace/
   ```

2. **Verify Directory Structure**
   
   Ensure your workspace contains:
   ```
   your-workspace/
   ├── generic-agentic-kit/
   │   ├── agent_rules/
   │   ├── doc_templates/
   │   ├── guidelines/
   │   ├── principles/
   │   ├── specifications/
   │   ├── strategies/
   │   └── README.md
   ├── your-project-files/
   └── .cursor/
   ```

### 2. Cursor Rules Configuration

1. **Create Cursor Rules Directory** (if it doesn't exist)
   ```bash
   mkdir -p .cursor/rules
   ```

2. **Add User Rules**
   
   Copy and customize the USER_RULES template:
   ```bash
   cp generic-agentic-kit/agent_rules/USER_RULES.md .cursor/rules/user_context.md
   ```
   
   Then edit `.cursor/rules/user_context.md` to reflect your role, project context, and interaction preferences.

3. **Add Project-Specific Rules** (optional)
   
   Create additional rule files for project-specific guidelines:
   ```bash
   touch .cursor/rules/project_standards.md
   ```

### 3. MCPs (Managed Clipboard Processes) Setup

If you're using Cursor's MCP feature for external tool integration:

1. **Create MCP Configuration File**
   ```bash
   mkdir -p .cursor/mcps
   touch .cursor/mcps/config.json
   ```

2. **Define Relevant MCPs**
   
   Edit `.cursor/mcps/config.json` to include useful integrations:
   ```json
   {
     "mcps": [
       {
         "name": "Generate Log Analysis",
         "command": "node scripts/analyze-logs.js",
         "input_type": "text",
         "output_type": "text"
       },
       {
         "name": "Extract Requirements",
         "command": "python scripts/extract_requirements.py",
         "input_type": "text",
         "output_type": "text"
       }
     ]
   }
   ```

## Effective Prompt Patterns

### 1. Role-Based Prompts

#### Template:
```
Adopt the role of [AGENT ROLE] as defined in generic-agentic-kit/agent_rules/[ROLE_TEMPLATE].md and [TASK DESCRIPTION] for [TARGET].
```

#### Examples:

**Code Review:**
```
Adopt the role of Code Quality Guardian as defined in generic-agentic-kit/agent_rules/code_quality_guardian_template.md and review the following code against our standards in generic-agentic-kit/guidelines/CODING_STANDARDS_template.md:

[CODE SNIPPET OR FILE REFERENCE]
```

**Documentation:**
```
Adopt the role of Documentation Manager as defined in generic-agentic-kit/agent_rules/documentation_manager_template.md and create API documentation for the endpoints in src/api/users.js following the template in generic-agentic-kit/doc_templates/API_DOC_template.md.
```

**Log Analysis:**
```
Adopt the role of Operations Analyst as defined in generic-agentic-kit/agent_rules/operations_analyst_template.md and analyze these application logs to identify performance bottlenecks, following the structure in generic-agentic-kit/doc_templates/LOG_ANALYSIS_TEMPLATE.md:

[LOG CONTENT]
```

### 2. Template-Based Prompts

#### Template:
```
Generate a [DOCUMENT TYPE] for [SUBJECT] following the structure in generic-agentic-kit/doc_templates/[TEMPLATE_NAME].md, focusing on [SPECIFIC ASPECTS].
```

#### Examples:

**README Generation:**
```
Generate a README for our user authentication service following the structure in generic-agentic-kit/doc_templates/README_template.md, focusing on the OAuth implementation and security considerations.
```

**Architecture Documentation:**
```
Generate an architecture overview for our payment processing pipeline following the structure in generic-agentic-kit/doc_templates/ARCHITECTURE_template.md, focusing on the transaction flow and error handling mechanisms.
```

**Requirements Specification:**
```
Generate a requirements specification for the new notification system following the structure in generic-agentic-kit/specifications/REQUIREMENTS_SPEC_template.md, focusing on delivery guarantees and user preferences.
```

### 3. Guideline-Based Prompts

#### Template:
```
Evaluate [TARGET] against the guidelines in generic-agentic-kit/guidelines/[GUIDELINE_NAME].md and suggest improvements.
```

#### Examples:

**Security Review:**
```
Evaluate the authentication implementation in src/auth/ against the guidelines in generic-agentic-kit/guidelines/SECURITY_CHECKLIST_template.md and suggest improvements.
```

**Performance Analysis:**
```
Evaluate the database query patterns in src/db/queries.js against the guidelines in generic-agentic-kit/guidelines/PERFORMANCE_GUIDELINES_template.md and suggest improvements.
```

**UX Review:**
```
Evaluate this signup form implementation against the guidelines in generic-agentic-kit/guidelines/ACCESSIBILITY_STANDARDS_template.md and suggest improvements.
```

### 4. Multi-Modal Analysis Prompts

#### Template:
```
Using the framework in generic-agentic-kit/guidelines/VISUAL_ANALYSIS_GUIDE.md, analyze [VISUAL ARTIFACT TYPE] in relation to [TEXTUAL REFERENCE] and provide insights on [SPECIFIC ASPECT].
```

#### Examples:

**UI-Log Correlation:**
```
Using the framework in generic-agentic-kit/guidelines/VISUAL_ANALYSIS_GUIDE.md, analyze these error screen screenshots in relation to the error logs I've attached and provide insights on how we can improve error communication to users.
```

**Architecture-Performance Correlation:**
```
Using the framework in generic-agentic-kit/guidelines/VISUAL_ANALYSIS_GUIDE.md, analyze our system architecture diagram in relation to these performance metrics and provide insights on potential bottlenecks and optimization opportunities.
```

**Design-Implementation Gap:**
```
Using the framework in generic-agentic-kit/guidelines/VISUAL_ANALYSIS_GUIDE.md, analyze these UI mockups in relation to the implemented screens and provide insights on implementation discrepancies and their potential impact.
```

## Advanced Integration Techniques

### 1. Context Chaining

Build context progressively across related prompts:

```
# First prompt - Analysis
Adopt the role of Code Quality Guardian as defined in generic-agentic-kit/agent_rules/code_quality_guardian_template.md and analyze the authentication flow in src/auth/*.js.

# Second prompt - Building on previous analysis
Based on your analysis, refactor the authentication code to address the identified issues, following the patterns in generic-agentic-kit/guidelines/CODING_STANDARDS_template.md.

# Third prompt - Documentation
Now, as the Documentation Manager defined in generic-agentic-kit/agent_rules/documentation_manager_template.md, update the authentication API documentation to reflect these changes.
```

### 2. Workflow Integration

Combine the kit with specific development workflows:

**Bug Investigation Workflow:**
```
1. Adopt the role of Operations Analyst as defined in generic-agentic-kit/agent_rules/operations_analyst_template.md and analyze these error logs.

2. Based on your analysis, review the potentially problematic code in [identified files].

3. Generate a bug report following generic-agentic-kit/doc_templates/BUG_REPORT_template.md.

4. Propose a fix that adheres to our coding standards in generic-agentic-kit/guidelines/CODING_STANDARDS_template.md.
```

**Feature Development Workflow:**
```
1. Create a requirements specification for the new feature following generic-agentic-kit/specifications/REQUIREMENTS_SPEC_template.md.

2. Design the API contract following generic-agentic-kit/doc_templates/API_DOC_template.md.

3. Implement the feature according to our coding standards in generic-agentic-kit/guidelines/CODING_STANDARDS_template.md.

4. Generate unit tests that ensure compliance with the requirements.

5. Update the project documentation to include the new feature.
```

### 3. Tool Integration via MCPs

Combine Cursor's MCP feature with the kit for powerful workflows:

**Log Analysis Pipeline:**
```
1. Collect application logs using your logging tool.

2. Use the "Generate Log Analysis" MCP to process raw logs.

3. Ask Cursor (with Operations Analyst role) to analyze the processed logs:

   "Adopt the role of Operations Analyst as defined in generic-agentic-kit/agent_rules/operations_analyst_template.md and analyze these processed logs to identify performance trends and anomalies."
```

**Requirements Extraction:**
```
1. Use the "Extract Requirements" MCP to process a client email or meeting notes.

2. Ask Cursor to formalize the requirements:

   "Based on these extracted requirements, generate a formal requirements specification following generic-agentic-kit/specifications/REQUIREMENTS_SPEC_template.md."
```

## Best Practices

### 1. Consistency Is Key

- Use the same reference patterns consistently
- Maintain identical file paths in your references
- Stick to established terminology from your templates

### 2. Evolve Your Context Repository

- Update templates as you discover gaps
- Add new examples to guidelines based on real issues
- Refine agent roles based on actual interactions

### 3. Balance Reference Depth

- Include enough context for AI to understand, but not so much that it's overwhelming
- When referencing documents, specify relevant sections if the document is large
- Start with a broader context, then narrow down in follow-up prompts

### 4. Maintain File Organization

- Keep the kit directory structure clean and organized
- Use consistent naming conventions
- Document any custom additions or modifications

### 5. Measure and Improve

- Track which prompts and patterns are most effective
- Note which templates need frequent updates
- Identify which agent roles provide the most value

## Troubleshooting

### Common Issues and Solutions

**Issue: AI isn't following the referenced template properly**
- Solution: Ensure the template path is correct
- Solution: Check if the template is too complex; consider simplifying
- Solution: Provide a clearer task description

**Issue: Context seems lost between related prompts**
- Solution: Briefly summarize previous context in follow-up prompts
- Solution: Use more explicit references to previous outputs
- Solution: Reduce time between related interactions

**Issue: Agent role behavior isn't as expected**
- Solution: Review and possibly simplify the role definition
- Solution: Ensure the role is appropriate for the task
- Solution: Provide more specific instructions alongside the role reference

## Conclusion

Effective integration of the Generic Agentic Development AI-KIT with Cursor creates a powerful development environment that leverages AI assistance while maintaining consistency and quality. By following these patterns and examples, you'll build a workflow that becomes more efficient and effective over time as your context repository grows and evolves with your project. 