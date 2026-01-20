# 🏰 Lab 1: The Library at the End of the World

## Building a REST API Backend with GitHub Spec Kit

### Overview

In this lab, you will forge a **REST API** using **OpenAPI (Swagger) 3.0.1** specification as the backend for a text-based adventure game. You will use **GitHub Spec Kit** to drive the development process through specifications.

**Estimated Time:** 2-3 hours

**Technologies:**

- Language: **C#** or **TypeScript** (your choice)
- API Specification: **OpenAPI 3.0.1**
- Development Methodology: **Spec-Driven Development (SDD)**

---

## Prerequisites

Before starting this lab, ensure you have:

- [ ] Git installed and configured
- [ ] Node.js (v18+) or .NET SDK (8.0+) installed
- [ ] **Visual Studio Code** installed
- [ ] **GitHub Copilot** extension installed and activated in VS Code
- [ ] Python 3.8+ with `uv` package manager (for Spec Kit CLI)

---

## Step 1: Install GitHub Spec Kit CLI

First, install the `specify-cli` tool globally:

```bash
# Install uv if you don't have it
curl -LsSf https://astral.sh/uv/install.sh | sh

# Install the Spec Kit CLI
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git

# Verify installation
specify version

# Check available tools and AI agents
specify check
```

---

## Step 2: Initialize Your Project

Create a new Spec Kit project for the adventure game API:

```bash
# Initialize with GitHub Copilot
specify init adventure-api --ai copilot

# Navigate to your project
cd adventure-api
```

This creates:

- `specs/` directory for feature specifications
- `memory/` directory for project context
- `scripts/` directory with automation scripts
- Agent-specific configuration files

---

## 💬 Using Spec Kit Commands in VS Code

All `/speckit.*` commands are executed through the **GitHub Copilot Chat panel** in VS Code:

1. **Open the Chat Panel**: Press `Ctrl+Shift+I` (Windows/Linux) or `Cmd+Shift+I` (Mac), or click the Copilot icon in the sidebar
2. **Type the command**: Enter the `/speckit.*` command followed by your description
3. **Press Enter**: Copilot will process the command and generate the appropriate files
4. **Review the output**: Check the generated specifications and approve any file changes

> **💡 Tip:** Make sure you have the project folder open in VS Code before running commands. The commands work on the current workspace.

---

## Step 3: Establish Project Constitution (Principles)

Define the guiding principles for your API:

```
/speckit.constitution Create principles for a text adventure game REST API:
- Security first: All endpoints must be authenticated
- RESTful design: Follow REST conventions strictly
- Documentation clarity: Every endpoint must be documented in OpenAPI 3.0.1
- Testability: Every feature must have unit tests
- Simplicity: Prefer simple solutions over complex ones
- Performance: Response time under 200ms for all endpoints
```

---

## Step 4: Create Feature Specifications

### 4.1 Adventure System Specification

```
/speckit.specify Build an adventure initialization system where users can start a new text adventure. Each adventure has a unique ID, creation timestamp, current scene, and game state. Users should be able to create, retrieve, update, and delete adventures. Include JWT authentication for all operations.
```

### 4.2 Character Management Specification

```
/speckit.specify Build a character management system with the following:
- Create, edit, retrieve characters
- Attributes: STR (Strength), DEX (Dexterity), INT (Intelligence), CON (Constitution), CHA (Charisma)
- Each attribute has a base value (3-18) and calculated modifier ((value - 10) / 2)
- Character snapshots and versioning for game saves
- Character belongs to an adventure
```

### 4.3 Dice System Specification

```
/speckit.specify Build a dice rolling engine that supports:
- Standard dice notation (e.g., 2d6, 1d20+5, 3d8-2)
- Parsing expressions like "2d6+1d4+3"
- Return individual rolls and total
- Support for advantage/disadvantage (roll twice, take higher/lower)
- Cryptographically secure random number generation
```

### 4.4 Combat System Specification

```
/speckit.specify Build a turn-based combat system with:
- NPCs/enemies with stats and behaviors
- AI states: aggressive, defensive, flee
- Turn resolution using the dice engine
- Initiative order based on DEX modifier + d20
- Attack rolls vs armor class
- Damage calculation with weapon dice
```

### 4.5 Inventory System Specification

```
/speckit.specify Build an inventory management system:
- Items can be stackable (potions, arrows) or unique (weapons, armor)
- Items can be equipped or stored
- Equipment slots: head, chest, hands, legs, feet, main hand, off hand
- Loot tables for random item generation
- Item effects and modifiers
```

### 4.6 Quest System Specification

```
/speckit.specify Build a multi-stage quest system:
- Quests with multiple objectives/stages
- Progress tracking per stage
- Success and failure conditions
- Quest state persistence
- Rewards on completion
- Quest dependencies (prerequisite quests)
```

### 4.7 Authentication Specification

```
/speckit.specify Build a security system with:
- JWT token-based authentication
- User registration and login endpoints
- Token refresh mechanism
- Role-based permissions (player, game master, admin)
- Rate limiting for API protection
```

---

## Step 5: Clarify Requirements (Optional)

If your specifications have `[NEEDS CLARIFICATION]` markers:

```
/speckit.clarify
```

Answer any questions the AI asks to refine the specifications.

---

## Step 6: Create Implementation Plan

Generate the technical implementation plan:

### For TypeScript:

```
/speckit.plan Use TypeScript with Express.js framework. Use Prisma ORM with PostgreSQL database. Generate OpenAPI 3.0.1 specification using tsoa for automatic documentation. Use Jest for unit testing. Implement JWT authentication with jsonwebtoken library. Structure code with controllers, services, and repositories pattern.
```

### For C#:

```
/speckit.plan Use C# with ASP.NET Core 8 Web API. Use Entity Framework Core with PostgreSQL database. Generate OpenAPI 3.0.1 specification using Swashbuckle/Swagger. Use xUnit for unit testing. Implement JWT authentication with Microsoft.AspNetCore.Authentication.JwtBearer. Follow Clean Architecture pattern with controllers, services, and repositories.
```

---

## Step 7: Analyze Consistency

Validate your plan against the specifications:

```
/speckit.analyze
```

This checks for:

- Missing requirements
- Inconsistencies between spec and plan
- Potential architectural issues

---

## Step 8: Generate Task Breakdown

Create actionable tasks from the plan:

```
/speckit.tasks
```

This generates a `tasks.md` file with:

- Phased implementation tasks
- Dependencies between tasks
- Parallel execution opportunities
- Test requirements for each task

---

## Step 9: Execute Implementation

Build the feature according to the plan:

```
/speckit.implement
```

The AI will:

1. Process tasks in dependency order
2. Follow TDD (write tests first)
3. Create the API endpoints
4. Generate OpenAPI documentation
5. Implement all required functionality

---

## Step 10: Verify Your Implementation

### Run Tests

```bash
# TypeScript
npm test

# C#
dotnet test
```

### Verify OpenAPI Specification

Ensure your `openapi.yaml` or `openapi.json` file:

- Uses version 3.0.1
- Documents all endpoints
- Includes request/response schemas
- Has authentication requirements defined

### Test API Endpoints

```bash
# Start your server
npm run dev  # TypeScript
dotnet run   # C#

# Test with curl or use the Swagger UI
curl -X POST http://localhost:3000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"username": "adventurer", "password": "quest123"}'
```

---

## Minimum Functional Requirements Checklist

Ensure your API implements:

- [ ] **Adventure Management**
  - [ ] Initialize new adventure
  - [ ] Retrieve adventure state
  - [ ] Update adventure state

- [ ] **Character Management**
  - [ ] Create character with attributes
  - [ ] Edit character
  - [ ] Get character details
  - [ ] Calculate attribute modifiers
  - [ ] Character versioning/snapshots

- [ ] **Dice System**
  - [ ] Parse dice expressions (e.g., `2d6+3`)
  - [ ] Roll dice with results
  - [ ] Unit tests for dice engine

- [ ] **Combat System**
  - [ ] NPCs with AI states
  - [ ] Turn-based resolution
  - [ ] Initiative system
  - [ ] Unit tests for combat logic

- [ ] **Inventory**
  - [ ] Stackable items
  - [ ] Equipable items
  - [ ] Loot tables

- [ ] **Quests**
  - [ ] Multi-stage quests
  - [ ] Progress tracking
  - [ ] Success/failure conditions
  - [ ] State persistence

- [ ] **Security**
  - [ ] JWT authentication
  - [ ] Basic authorization
  - [ ] Protected endpoints

- [ ] **Documentation**
  - [ ] OpenAPI 3.0.1 specification
  - [ ] All endpoints documented
  - [ ] Unit tests for core systems

---

## Evaluation Criteria

Your implementation will be evaluated on:

| Criteria                      | Weight |
| ----------------------------- | ------ |
| Text Adventure Enjoyability   | 20%    |
| Security Implementation       | 25%    |
| API Documentation (OpenAPI)   | 20%    |
| Best Practices & Code Quality | 20%    |
| Test Coverage                 | 15%    |

---

## Tips for Success

1. **Start with the Dice Engine** - It's foundational for combat
2. **Design your OpenAPI spec early** - Let it guide implementation
3. **Test as you go** - Don't leave testing until the end
4. **Keep security simple** - Basic JWT is sufficient
5. **Document clearly** - Good API docs help everyone

---

## Resources

- [GitHub Spec Kit Documentation](https://speckit.org/)
- [OpenAPI 3.0.1 Specification](https://swagger.io/specification/)
- [JWT Introduction](https://jwt.io/introduction/)
- [REST API Best Practices](https://restfulapi.net/)

---

**Good luck, adventurers! May your APIs be robust and your specifications clear! 🎲⚔️**
