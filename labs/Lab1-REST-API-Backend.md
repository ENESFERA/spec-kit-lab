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
- [ ] Node.js (v18+) or .NET SDK (10.0+) installed
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
- RESTful design: Follow REST conventions strictly
- Documentation clarity: Every endpoint must be documented in OpenAPI 3.0.1
- Testability: Every feature must have unit tests
- Simplicity: Prefer simple solutions over complex ones
- Performance: Response time under 200ms for all endpoints
```

---

## Step 4: Implement Features Using Spec Kit Workflow

For each feature, follow the complete Spec Kit workflow:

1. **Specify** → Create the feature specification
2. **Plan** → Generate implementation plan
3. **Tasks** → Break down into actionable tasks
4. **Implement** → Execute the implementation

> **⚠️ Important:** Complete the full workflow for each feature before moving to the next one. This ensures each feature is fully implemented and tested before building dependent features.

---

### 📋 Recommended Implementation Order

| Order | Feature              | Reason                          |
| ----- | -------------------- | ------------------------------- |
| 1     | Dice System          | Foundation for combat mechanics |
| 2     | Adventure System     | Core game structure             |
| 3     | Character Management | Depends on adventures           |
| 4     | Inventory System     | Depends on characters           |
| 5     | Combat System        | Depends on dice, characters     |
| 6     | Quest System         | Depends on all previous         |

---

### Feature 1: Dice System

#### Step 4.1.1 - Specify

```
/speckit.specify Build a dice rolling engine that supports:
- Standard dice notation (e.g., 2d6, 1d20+5, 3d8-2)
- Parsing expressions like "2d6+1d4+3"
- Return individual rolls and total
- Support for advantage/disadvantage (roll twice, take higher/lower)
- Cryptographically secure random number generation
```

> **📝 Review:** Check the generated specification in `specs/` folder. Verify it captures all dice notation requirements and edge cases.

#### Step 4.1.2 - Plan

**For TypeScript:**

```
/speckit.plan Use TypeScript with Express.js framework. Use Prisma ORM with PostgreSQL database. Use Jest for unit testing. Structure code with controllers, services, and repositories pattern. Create a DiceService with parser and roller. Implement regex-based expression parsing. Use crypto library for secure random.
```

**For C#:**

```
/speckit.plan Use C# with ASP.NET Core 10 Web API. Use Entity Framework Core with PostgreSQL database. Use xUnit for unit testing. Follow Clean Architecture pattern. Create a DiceService with parser and roller. Implement regex-based expression parsing.
```

> **📝 Review:** Check the generated plan document. Verify the architecture decisions, file structure, and dependencies match your chosen tech stack.

#### Step 4.1.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Review the task breakdown. Ensure tasks are atomic, properly ordered, and cover all specification requirements.

#### Step 4.1.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Review all generated code files. Check that the implementation follows the plan, includes proper error handling, and has unit tests.

#### ✅ Checkpoint: Verify Dice System

> **⚠️ Before testing:** Make sure your server is running!

```bash
# Start the server first (in a separate terminal)
npm run dev   # TypeScript
# OR
dotnet run    # C#
```

```bash
# Test dice roll
curl -X POST http://localhost:3000/api/dice/roll \
  -H "Content-Type: application/json" \
  -d '{"expression": "2d6+3"}'
```

#### 🔀 Git: Commit and Merge Feature 1

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G` / `Cmd+Shift+G`)
2. Review changed files in the "Changes" section
3. Click `+` next to each file (or `+` on "Changes" header to stage all)
4. Enter commit message: `feat: implement dice rolling system`
5. Click **Commit** button (checkmark icon)
6. Click **Sync Changes** or **Push** in the status bar

**Option B: Using Terminal**

```bash
git add .
git commit -m "feat: implement dice rolling system

- Add dice notation parser (2d6, 1d20+5, etc.)
- Implement advantage/disadvantage rolls
- Add cryptographically secure random generation
- Include unit tests for dice mechanics"

git push origin main
```

---

### Feature 2: Adventure System

#### Step 4.2.1 - Specify

```
/speckit.specify Build an adventure initialization system where users can start a new text adventure. Each adventure has a unique ID, creation timestamp, current scene, and game state. Users should be able to create, retrieve, update, and delete adventures.
```

> **📝 Review:** Check the generated specification. Verify CRUD operations are defined and game state structure is clear.

#### Step 4.2.2 - Plan

```
/speckit.plan Continue with the existing tech stack. Create Adventure entity with relationships. Implement CRUD operations. Add scene management and game state persistence. Generate OpenAPI documentation for all endpoints.
```

> **📝 Review:** Verify the plan includes database schema design, API endpoints, and OpenAPI documentation approach.

#### Step 4.2.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover entity creation, repository, service, controller, and tests.

#### Step 4.2.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Check generated code for proper REST conventions, error handling, and OpenAPI annotations.

#### ✅ Checkpoint: Verify Adventure System

> **⚠️ Ensure server is running** (see Feature 1 checkpoint for start commands)

```bash
# Create adventure
curl -X POST http://localhost:3000/api/adventures \
  -H "Content-Type: application/json" \
  -d '{"name": "The Dark Cave"}'

# List adventures
curl -X GET http://localhost:3000/api/adventures
```

#### 🔀 Git: Commit and Merge Feature 2

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `feat: implement adventure system`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "feat: implement adventure system

- Add Adventure entity with CRUD operations
- Implement scene management
- Add game state persistence
- Generate OpenAPI documentation"

git push origin main
```

---

### Feature 3: Character Management

#### Step 4.3.1 - Specify

```
/speckit.specify Build a character management system with the following:
- Create, edit, retrieve characters
- Attributes: STR (Strength), DEX (Dexterity), INT (Intelligence), CON (Constitution), CHA (Charisma)
- Each attribute has a base value (3-18) and calculated modifier ((value - 10) / 2)
- Character snapshots and versioning for game saves
- Character belongs to an adventure
```

> **📝 Review:** Check that the specification includes attribute validation rules and modifier calculation formula.

#### Step 4.3.2 - Plan

```
/speckit.plan Continue with the existing tech stack. Create Character entity linked to Adventure. Implement attribute system with automatic modifier calculation. Add snapshot/versioning system for character history. Create unit tests for modifier calculations.
```

> **📝 Review:** Verify the plan includes proper entity relationships and versioning strategy.

#### Step 4.3.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks include database migrations and unit tests for modifier calculations.

#### Step 4.3.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Verify attribute validation, modifier calculations, and character-adventure relationships.

#### ✅ Checkpoint: Verify Character System

> **⚠️ Ensure server is running** (see Feature 1 checkpoint for start commands)

```bash
# Create character (replace {adventureId} with actual ID from previous step)
curl -X POST http://localhost:3000/api/adventures/{adventureId}/characters \
  -H "Content-Type: application/json" \
  -d '{"name": "Aldric", "str": 16, "dex": 14, "int": 10, "con": 15, "cha": 12}'
```

#### 🔀 Git: Commit and Merge Feature 3

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `feat: implement character management system`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "feat: implement character management system

- Add Character entity with attributes (STR, DEX, INT, CON, CHA)
- Implement modifier calculation
- Add character versioning/snapshots
- Link characters to adventures"

git push origin main
```

---

### Feature 4: Inventory System

#### Step 4.4.1 - Specify

```
/speckit.specify Build an inventory management system:
- Items can be stackable (potions, arrows) or unique (weapons, armor)
- Items can be equipped or stored
- Equipment slots: head, chest, hands, legs, feet, main hand, off hand
- Loot tables for random item generation
- Item effects and modifiers
```

> **📝 Review:** Check that the specification covers item stacking logic and equipment slot constraints.

#### Step 4.4.2 - Plan

```
/speckit.plan Continue with the existing tech stack. Create Item and Inventory entities. Implement equipment slot system. Create loot table with weighted random selection using dice system. Add item effect modifiers to character stats.
```

> **📝 Review:** Verify the plan includes loot table integration with dice system and stat modifier calculations.

#### Step 4.4.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover item CRUD, equip/unequip logic, and loot table seeding.

#### Step 4.4.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Verify slot validation, stacking logic, and stat modifier application.

#### ✅ Checkpoint: Verify Inventory System

> **⚠️ Ensure server is running** (see Feature 1 checkpoint for start commands)

```bash
# Add item to inventory (replace {characterId} with actual ID)
curl -X POST http://localhost:3000/api/characters/{characterId}/inventory \
  -H "Content-Type: application/json" \
  -d '{"itemId": "sword-01", "quantity": 1}'

# Equip item
curl -X POST http://localhost:3000/api/characters/{characterId}/equip \
  -H "Content-Type: application/json" \
  -d '{"itemId": "sword-01", "slot": "main_hand"}'
```

#### 🔀 Git: Commit and Merge Feature 4

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `feat: implement inventory system`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "feat: implement inventory system

- Add Item and Inventory entities
- Implement equipment slots (head, chest, hands, etc.)
- Add stackable/unique item logic
- Create loot tables with dice integration"

git push origin main
```

---

### Feature 5: Combat System

#### Step 4.5.1 - Specify

```
/speckit.specify Build a turn-based combat system with:
- NPCs/enemies with stats and behaviors
- AI states: aggressive, defensive, flee
- Turn resolution using the dice engine
- Initiative order based on DEX modifier + d20
- Attack rolls vs armor class
- Damage calculation with weapon dice
```

> **📝 Review:** Verify the specification includes AI behavior definitions and combat formula details.

#### Step 4.5.2 - Plan

```
/speckit.plan Continue with the existing tech stack. Create NPC/Enemy entities with AI state machine. Implement initiative system using dice service. Create combat resolver with attack rolls and damage calculation. Add unit tests for combat scenarios.
```

> **📝 Review:** Check the plan includes state machine design and dice service integration.

#### Step 4.5.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover enemy creation, AI logic, and combat resolution tests.

#### Step 4.5.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Verify initiative ordering, attack/damage calculations, and AI state transitions.

#### ✅ Checkpoint: Verify Combat System

> **⚠️ Ensure server is running** (see Feature 1 checkpoint for start commands)

```bash
# Start combat (replace {adventureId} with actual ID)
curl -X POST http://localhost:3000/api/adventures/{adventureId}/combat/start \
  -H "Content-Type: application/json" \
  -d '{"enemies": ["goblin-01", "goblin-02"]}'

# Execute turn
curl -X POST http://localhost:3000/api/adventures/{adventureId}/combat/turn \
  -H "Content-Type: application/json" \
  -d '{"action": "attack", "targetId": "goblin-01"}'
```

#### 🔀 Git: Commit and Merge Feature 5

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `feat: implement turn-based combat system`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "feat: implement turn-based combat system

- Add NPC/Enemy entities with AI states
- Implement initiative system using dice
- Add attack rolls and damage calculation
- Create combat resolver with turn management"

git push origin main
```

---

### Feature 6: Quest System

#### Step 4.6.1 - Specify

```
/speckit.specify Build a multi-stage quest system:
- Quests with multiple objectives/stages
- Progress tracking per stage
- Success and failure conditions
- Quest state persistence
- Rewards on completion
- Quest dependencies (prerequisite quests)
```

> **📝 Review:** Check that the specification defines stage transitions, conditions, and reward structures.

#### Step 4.6.2 - Plan

```
/speckit.plan Continue with the existing tech stack. Create Quest and QuestStage entities. Implement progress tracking system. Add condition evaluation for success/failure. Integrate with inventory for rewards. Create quest dependency graph.
```

> **📝 Review:** Verify the plan includes dependency graph handling and reward distribution logic.

#### Step 4.6.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover quest CRUD, stage progression, and reward integration.

#### Step 4.6.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Verify quest dependencies, stage transitions, and reward distribution.

#### ✅ Checkpoint: Verify Quest System

> **⚠️ Ensure server is running** (see Feature 1 checkpoint for start commands)

```bash
# Get available quests (replace {adventureId} with actual ID)
curl -X GET http://localhost:3000/api/adventures/{adventureId}/quests

# Accept quest (replace {questId} with actual ID)
curl -X POST http://localhost:3000/api/adventures/{adventureId}/quests/{questId}/accept
```

#### 🔀 Git: Commit and Merge Feature 6

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `feat: implement quest system`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "feat: implement quest system

- Add Quest and QuestStage entities
- Implement multi-stage progress tracking
- Add quest dependencies graph
- Integrate rewards with inventory system"

git push origin main
```

---

## Step 5: Generate OpenAPI Documentation

After all features are implemented, ensure your OpenAPI specification is complete:

```bash
# For TypeScript with tsoa
npm run swagger

# For C# - Swagger is auto-generated at runtime
# Access at: http://localhost:5000/swagger
```

---

## Step 6: Verify Your Implementation

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

### Test API Endpoints

```bash
# Start your server
npm run dev  # TypeScript
dotnet run   # C#

# Test with curl or use the Swagger UI
curl -X POST http://localhost:3000/api/dice/roll \
  -H "Content-Type: application/json" \
  -d '{"expression": "2d6+3"}'
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

- [ ] **Documentation**
  - [ ] OpenAPI 3.0.1 specification
  - [ ] All endpoints documented
  - [ ] Unit tests for core systems

---

## Evaluation Criteria

Your implementation will be evaluated on:

| Criteria                      | Weight |
| ----------------------------- | ------ |
| Text Adventure Enjoyability   | 25%    |
| API Documentation (OpenAPI)   | 25%    |
| Best Practices & Code Quality | 30%    |
| Test Coverage                 | 20%    |

---

## Tips for Success

1. **Start with the Dice Engine** - It's foundational for combat
2. **Design your OpenAPI spec early** - Let it guide implementation
3. **Test as you go** - Don't leave testing until the end
4. **Document clearly** - Good API docs help everyone

---

## Resources

- [GitHub Spec Kit Documentation](https://speckit.org/)
- [OpenAPI 3.0.1 Specification](https://swagger.io/specification/)
- [REST API Best Practices](https://restfulapi.net/)

---

**Good luck, adventurers! May your APIs be robust and your specifications clear! 🎲⚔️**
