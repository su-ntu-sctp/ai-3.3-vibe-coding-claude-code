# Vibe Coding with Claude Code

## Part 1: Introduction

### What is Vibe Coding?

**Vibe Coding** is a modern development approach where you build software through natural conversation with AI, rather than writing code line-by-line yourself. Instead of focusing on syntax and implementation details, you describe what you want to build, and the AI handles the technical execution.

**The Philosophy:**
- Describe outcomes, not implementations
- Iterate through conversation
- Focus on "what" instead of "how"
- Think in features, not in functions

**Traditional Coding vs Vibe Coding:**

| Traditional Coding | Vibe Coding |
|-------------------|-------------|
| Write every line manually | Describe what you need |
| Remember syntax details | Focus on business logic |
| Bottom-up (code → feature) | Top-down (idea → code) |
| Hours on boilerplate | Seconds on structure |
| Debug line by line | Iterate conversationally |

**Example Comparison:**

Traditional Approach:
```java
// You manually type this
public class UserService {
    private UserRepository repo;
    
    public UserService(UserRepository repo) {
        this.repo = repo;
    }
    
    public User findById(Long id) {
        return repo.findById(id)
            .orElseThrow(() -> new UserNotFoundException(id));
    }
    // ... continues for many lines
}
```

Vibe Coding Approach:
```
You: "Create a UserService class with dependency injection, 
     CRUD operations, and proper exception handling"

AI: [Generates complete, working code]

You: "Add caching for the findById method"

AI: [Updates the code with @Cacheable annotation]
```

### What is Claude Code?

Claude Code is the **tool** that enables vibe coding. It's a command-line application and VS Code extension created by Anthropic that brings AI assistance directly into your development workflow.

**What Claude Code Does:**
- Write code based on natural language descriptions
- Debug existing code
- Explain complex concepts
- Refactor and improve your codebase
- Create entire projects from scratch
- Understand your project context

### Key Features

1. **Terminal Integration** - Works directly in your command line
2. **File Awareness** - Can read and modify files in your project
3. **Multi-Language Support** - Works with any programming language
4. **Interactive Mode** - Have back-and-forth conversations about your code
5. **Context Understanding** - Understands your entire project structure
6. **Multiple Chat Modes** - Different modes for different tasks

### Advantages

- **Speed**: Get boilerplate code written in seconds
- **Learning Tool**: Great for understanding new frameworks or languages
- **Debugging Help**: Quickly identify and fix bugs
- **Best Practices**: Claude suggests modern, clean code patterns
- **Reduced Cognitive Load**: Focus on problem-solving, not syntax
- **Faster Prototyping**: Build MVPs and demos quickly

---

## Part 2: Understanding Development Approaches

### No-Code Platforms

**Definition:** Visual tools that let you build applications without writing any code. Everything is done through drag-and-drop interfaces.

**Examples:** Webflow, Bubble, Zapier, Airtable

**Example Use Case:**
```
Task: Create a contact form
No-Code: Drag form widget, connect fields, add email action
Time: 10 minutes
Code Written: 0 lines
```

**Best for:** Simple websites, workflows, business users with no coding experience

**Limitations:** Limited customization, vendor lock-in, can't handle complex logic

### Low-Code Platforms

**Definition:** Development platforms that minimize hand-coding but still allow custom code when needed.

**Examples:** OutSystems, Mendix, Microsoft Power Apps, Retool

**Example Use Case:**
```
Task: Build a customer dashboard with custom processing
Low-Code: Use visual builder for UI (80%), write custom code for logic (20%)
Time: 2 hours
Code Written: ~200 lines of custom logic
```

**Best for:** Internal business tools, rapid development with some customization

**Limitations:** Platform lock-in, can be expensive, may hit platform limitations

### Vibe Coding (AI-Assisted Development)

**Definition:** Full coding flexibility with AI assistance. You have complete control but leverage AI to write code through natural language.

**Tools:** Claude Code, GitHub Copilot, Cursor

**Example Use Case:**
```
Task: Build a customer dashboard with custom processing
Vibe Coding: Describe needs, AI generates code, you review and iterate
Time: 1 hour
Code Written: 0 lines (by you), ~800 lines (by AI)
Full Control: Yes, modify anything
```

**Best for:** Custom applications, production code, learning, maximum flexibility

**Advantages:** No vendor lock-in, unlimited customization, production-ready code

### Comparison Table

| Aspect | No-Code | Low-Code | Vibe Coding |
|--------|---------|----------|-------------|
| **Technical Skills** | None required | Basic coding | Some coding knowledge |
| **Flexibility** | Very limited | Moderate | Complete |
| **Customization** | Template-based | Partial | Unlimited |
| **Scalability** | Limited | Moderate | High |
| **Vendor Lock-in** | High | High | None |
| **Code Ownership** | No access | Partial | Full |

---

## Part 3: Product Requirements Document (PRD)

### What is a PRD?

A **Product Requirements Document (PRD)** is a detailed description of what you want to build. When you have a clear PRD, you can feed it to Claude Code and build your entire application through conversation.

### PRD Template

```
# Product Requirements Document

## 1. Product Overview
Product Name: [Name]
Purpose: [What problem does it solve?]
Target Users: [Who will use this?]

## 2. User Stories
- As a [user type], I want to [action] so that [benefit]
- As a [user type], I want to [action] so that [benefit]

## 3. Core Features
Feature 1: [Name]
- Description: [What it does]
- Priority: High/Medium/Low

Feature 2: [Name]
- Description: [What it does]
- Priority: High/Medium/Low

## 4. Technical Requirements
- Backend: [Technology]
- Frontend: [Technology]
- Database: [Type]
- APIs: [External services needed]

## 5. Data Model
Entity 1:
- Field 1: [Type]
- Field 2: [Type]

Entity 2:
- Field 1: [Type]
- Field 2: [Type]

## 6. Out of Scope (V1)
- [Feature that won't be in first version]
```

### Generating PRDs with AI (Google Gemini)

**Step 1:** Go to https://gemini.google.com and sign in

**Step 2:** Use this prompt template:

```
I need a detailed Product Requirements Document (PRD) for my application.

Product Idea: [Describe your idea in 2-3 sentences]

Target Users: [Who will use this?]

Main Goal: [What problem does it solve?]

Key Features:
1. [Feature idea]
2. [Feature idea]
3. [Feature idea]

Tech Stack: [e.g., Java Spring Boot + React]

Please generate a comprehensive PRD that includes product overview, 
user stories, detailed features, technical specs, and data model.
```

**Step 3:** Refine with follow-up questions:
```
"Can you add more details to the authentication feature?"
"What database schema would you recommend?"
"Add API endpoint specifications"
```

**Step 4:** Copy the PRD and use it with Claude Code

### Using PRD with Claude Code

```bash
claude-code
```

Then:
```
I have a PRD for an expense tracking app. Here are the core features:
[Paste relevant sections]

Let's start by creating the backend with Spring Boot and the data models 
for User, Expense, and Category based on this PRD.
```

---

## Part 4: Model Context Protocol (MCP)

### What is MCP?

**Model Context Protocol (MCP)** is an open standard created by Anthropic that allows AI assistants like Claude to securely connect to external data sources and tools.

**Simple Analogy:** MCP is like USB-C for AI - a standardized way for AI to plug into different systems.

### Why MCP Matters

**Without MCP:**
- AI only works with data you manually provide
- No real-time access to databases or APIs
- Limited context

**With MCP:**
- AI can query your database directly
- Access live APIs and services
- Read from your file systems
- Much more context-aware assistance

### How MCP Works

```
┌─────────────┐
│   Claude    │
│  (AI Model) │
└──────┬──────┘
       │
       │ MCP Protocol
       │
┌──────┴──────┐
│ MCP Server  │
├─────────────┤
│ • Database  │
│ • Files     │
│ • APIs      │
└─────────────┘
```

### Common MCP Use Cases

**1. Database Access**
```
You: "Show me all customers who haven't made a purchase in 30 days"

Claude: [Queries your database via MCP]
"Here are 47 customers matching that criteria..."
```

**2. File System Access**
```
You: "Find all Java files that use deprecated APIs"

Claude: [Scans your codebase via MCP]
"Found 3 files with deprecated code..."
```

**3. API Integration**
```
You: "Get the latest order status from our API"

Claude: [Calls API via MCP]
"Order #12345 is in transit, expected delivery: Tomorrow"
```

### Setting Up MCP

**Example: PostgreSQL Database**

Create `mcp-config.json`:
```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": {
        "POSTGRES_CONNECTION_STRING": "postgresql://user:password@localhost:5432/mydb"
      }
    }
  }
}
```

Use it:
```bash
claude-code --mcp-config mcp-config.json
```

Now Claude can see your database schema and query data!

### Available MCP Servers

**Official:**
- PostgreSQL, SQLite databases
- Local file systems
- GitHub repositories
- Slack, Google Drive

**Community:**
- MongoDB, MySQL, Redis
- AWS services
- Notion, Jira

### MCP Security

- Read-only by default
- You control what data is accessible
- Runs locally on your machine
- No data sent to Anthropic

---

## Part 5: Installation & Setup

### Prerequisites

- Python 3.8 or higher
- An Anthropic API key from https://console.anthropic.com
- Basic command line knowledge

### Installation

1. **Install Claude Code:**
```bash
pip install claude-code
```

2. **Set up API key:**
```bash
export ANTHROPIC_API_KEY='your-api-key-here'
```

For permanent setup:
```bash
echo 'export ANTHROPIC_API_KEY="your-api-key-here"' >> ~/.bashrc
source ~/.bashrc
```

3. **Verify:**
```bash
claude-code --version
```

---

## Part 6: Using Claude Code in CLI

### Basic Commands

**Start interactive session:**
```bash
claude-code
```

**One-time question:**
```bash
claude-code "How do I read CSV in Java using Apache Commons?"
```

**Work on specific file:**
```bash
claude-code "Add error handling" src/main/java/Service.java
```

### Interactive Mode Example

```bash
$ claude-code

You: Create a Java method for factorial using recursion

Claude: [Generates code]

You: Add input validation for negative numbers

Claude: [Updates code]

You: Write JUnit tests

Claude: [Generates tests]

You: Convert to use iteration instead

Claude: [Refactors code]
```

### Common Prompts

```bash
claude-code "Create a Spring Boot controller for user management"

claude-code "Refactor this class to follow SOLID principles" UserService.java

claude-code "Add SLF4J logging to all methods in this class"
```

---

## Part 7: Using Claude Code in VS Code

### Chat Modes

**1. Normal Mode (Default)**
- General questions and code generation
- Example: "Explain Spring Boot dependency injection"

**2. Edit Mode**
- Direct file editing with suggestions
- Example: "Add input validation to this method"

**3. Code Mode**
- Code execution and testing
- Example: "Run this method and show output"

**4. Plan Mode**
- Creates structured plan before implementing
- Example: "Build user authentication with JWT"

### Installing the Extension

1. Open VS Code
2. Go to Extensions (Ctrl+Shift+X)
3. Search for "Claude Code"
4. Click Install
5. Sign in with Anthropic account (no API key needed!)

### Using the Extension

- Click Claude icon in sidebar
- Choose mode (Normal/Edit/Code/Plan)
- Type request or right-click code → "Ask Claude Code"
- Review changes in diff view
- Accept or modify

### Extension Features

- Inline suggestions
- Chat interface
- File context awareness
- Multi-file editing
- Git integration
- All four modes

### CLI in VS Code Terminal

Open terminal (Ctrl + \`) and run:
```bash
claude-code "Create a Java service class"
```

**Switch modes:**
```bash
claude-code --mode edit
claude-code --mode plan
```

---

## Part 8: Demo - Building a CRM

### Project Overview

We'll build a Customer Relationship Management system with:
- Backend: Java Spring Boot
- Frontend: React
- Features: CRUD operations, search, notes

### Step 1: Initialize Project

```bash
mkdir crm-app
cd crm-app
claude-code
```

**Prompt:**
```
Create a Spring Boot project for a CRM application.
Include Customer entity with: id, name, email, phone, company, notes.
Create REST controller with CRUD endpoints.
Use in-memory storage with ArrayList.
Add CORS for localhost:3000.
Include pom.xml.
```

**Review:** Check generated files match requirements

### Step 2: Enhance Backend

**Prompt:**
```
Add validation to Customer entity.
Name and email are required.
Email must be valid format.
Add error handling in controller.
```

**Then:**
```
Add search endpoint to filter customers by name or company.
Make it case-insensitive.
```

### Step 3: Build Frontend

**Prompt:**
```
Create React application for the CRM.
Setup App.js as main component.
Include api.js for API calls to localhost:8080.
Use fetch for HTTP requests.
```

**Then:**
```
Create CustomerList component that:
- Fetches and displays customers in a table
- Shows name, email, phone, company columns
- Has delete button for each customer
- Has "Add Customer" button at top
- Includes search bar
Style with clean, modern CSS.
```

### Step 4: Add Form

**Prompt:**
```
Create CustomerForm component with:
- Input fields for name, email, phone, company, notes
- Form validation with error messages
- Save and Cancel buttons
- Works for both add and edit
- Modal or card design
Add professional CSS.
```

**Connect:**
```
Update App.js to:
- Toggle between list and form views
- Pass customer data for editing
- Refresh list after add/update
- Show success messages
```

### Step 5: Polish UI

**Prompt:**
```
Enhance UI with:
- Header with "CRM System" title
- Professional color scheme
- Hover effects on buttons and rows
- Loading state when fetching
- Empty state message
Make responsive for mobile.
```

**Add:**
```
Add confirmation dialog for delete.
Add toast notifications for all operations.
```

### Step 6: Run Application

**Backend Terminal:**
```bash
cd backend
mvn spring-boot:run
```

**Frontend Terminal:**
```bash
cd frontend
npm install
npm start
```

Visit: http://localhost:3000

### Iteration Examples

Continue improving:
```
"Add more spacing to the table"
"Change color scheme to blue and white"
"Add notes preview showing first 50 characters"
"Format phone as (XXX) XXX-XXXX"
"Add last contacted date field"
```

---

## Part 9: Advanced - Using MCP with CRM

### Connect Real Database

Create `mcp-config.json`:
```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": {
        "POSTGRES_CONNECTION_STRING": "postgresql://localhost:5432/crm_db"
      }
    }
  }
}
```

Start with MCP:
```bash
claude-code --mcp-config mcp-config.json
```

### Vibe Code with Real Data

```
You: "What's my database structure?"

Claude: [Queries via MCP]
"Your database has:
- customers table (id, name, email, phone...)
- interactions table (id, customer_id, notes...)
"

You: "Update CustomerController to use JPA with my existing schema"

Claude: [Sees actual schema via MCP]
[Generates matching JPA entities]
[Creates repositories]
[Updates controller]

You: "Show customers not contacted in 30 days"

Claude: [Queries real data via MCP]
"Found 12 customers:
1. Acme Corp - 45 days ago
2. Tech Solutions - 33 days ago
..."
```

---

## Part 10: Best Practices

### Do's

- Be specific in requests
- Review generated code
- Ask for explanations
- Iterate on solutions
- Start with PRD for complex projects
- Use MCP for context
- Test thoroughly

### Don'ts

- Don't blindly copy code
- Don't skip code review
- Don't forget testing
- Don't share API keys
- Don't skip learning fundamentals

### Pro Tips

1. Break complex tasks into steps
2. Provide error messages and context
3. Ask "Explain how this works"
4. Request specific styles/patterns
5. Use Plan Mode for architecture
6. Leverage MCP for accuracy
7. Review diffs carefully
8. Document as you go

---

## Part 11: Practice Exercises

### Beginner
1. Add status field (active/inactive) to customers
2. Generate calculator class with tests
3. Add pagination (10 per page)

### Intermediate
4. Export customers to CSV with filters
5. Add JWT authentication
6. Create dashboard with charts

### Advanced
7. Set up MCP with real database
8. Build email notification system
9. Create multi-tenant SaaS version

---

## Part 12: Resources

### Documentation
- Claude Code: https://docs.claude.com/claude-code
- MCP: https://modelcontextprotocol.io
- Anthropic Console: https://console.anthropic.com

### Learning
- Spring Boot: https://spring.io/projects/spring-boot
- React: https://react.dev

### AI Tools
- Google Gemini: https://gemini.google.com
- Claude: https://claude.ai

### Community
- MCP Servers: https://github.com/modelcontextprotocol/servers

---



