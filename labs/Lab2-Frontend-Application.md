# 🗣️ Lab 2: The Voice of the Narrator

## Building a Text Adventure Frontend with GitHub Spec Kit

### Overview

With your REST API forged and running, it's time to practice the arts of invocation. In this lab, you will build a **frontend application** that connects to your adventure API and provides an interactive text-based adventure experience.

**Estimated Time:** 1.5-2 hours

**Technologies:**

- Frontend framework of your choice (React, Vue, Svelte, or Vanilla JS)
- HTTP client for API communication
- Development Methodology: **Spec-Driven Development (SDD)**

---

## Prerequisites

Before starting this lab, ensure you have:

- [ ] Completed Lab 1 with a running REST API
- [ ] Node.js (v18+) installed
- [ ] **Visual Studio Code** installed
- [ ] **GitHub Copilot** extension installed and activated in VS Code
- [ ] The Spec Kit CLI installed (`specify version` to verify)
- [ ] Your API endpoint URL available

---

## Step 1: Initialize Your Frontend Project

Create a new Spec Kit project for the frontend:

```bash
# Initialize with GitHub Copilot
specify init adventure-frontend --ai copilot

# Navigate to your project
cd adventure-frontend

# Verify project structure
ls -la
```

---

## 💬 Using Spec Kit Commands in VS Code

All `/speckit.*` commands are executed through the **GitHub Copilot Chat panel** in VS Code:

1. **Open the Chat Panel**: Press `Ctrl+Shift+I` (Windows/Linux) or `Cmd+Shift+I` (Mac), or click the Copilot icon in the sidebar
2. **Type the command**: Enter the `/speckit.*` command followed by your description
3. **Press Enter**: Copilot will process the command and generate the appropriate files
4. **Review the output**: Check the generated specifications and approve any file changes

> **💡 Tip:** Make sure you have the project folder open in VS Code before running commands. The commands work on the current workspace.

---

## Step 2: Establish Project Constitution

Define the guiding principles for your frontend:

```
/speckit.constitution Create principles for a text adventure frontend:
- Accessibility: Interface must be keyboard navigable and screen-reader friendly
- Simplicity: Focus on functionality over visual complexity
- Responsiveness: Interface must work on mobile and desktop
- Error handling: All API errors must be displayed gracefully to users
- Documentation: All components and functions must be documented
```

---

## Step 3: Implement Features Using Spec Kit Workflow

For each feature, follow the complete Spec Kit workflow:

1. **Specify** → Create the feature specification
2. **Plan** → Generate implementation plan
3. **Tasks** → Break down into actionable tasks
4. **Implement** → Execute the implementation

> **⚠️ Important:** Complete the full workflow for each feature before moving to the next one.

---

### 📋 Recommended Implementation Order

| Order | Feature                 | Reason                |
| ----- | ----------------------- | --------------------- |
| 1     | Adventure Dashboard     | Core navigation       |
| 2     | Character Management UI | Depends on adventures |
| 3     | Game Interface          | Main gameplay         |
| 4     | Inventory UI            | Enhances gameplay     |
| 5     | Quest Log               | Complete experience   |

---

### Feature 1: Adventure Dashboard

#### Step 3.1.1 - Specify

```
/speckit.specify Build an adventure dashboard where users can:
- View list of their existing adventures
- Create a new adventure with a name
- Select an adventure to continue playing
- Delete an adventure with confirmation
- Display adventure metadata (creation date, current scene, progress)
- Show loading skeleton while fetching data
```

> **📝 Review:** Check the generated specification in `specs/` folder. Verify it captures all dashboard requirements and user interactions.

#### Step 3.1.2 - Plan

**For React:**

```
/speckit.plan Use React 18 with TypeScript. Use Vite for build tooling. Use React Router for navigation. Use TanStack Query (React Query) for API state management. Use Tailwind CSS for styling. Store API URL in environment variables. Create dashboard components with adventure list.
```

**For Vue:**

```
/speckit.plan Use Vue 3 with TypeScript and Composition API. Use Vite for build tooling. Use Vue Router for navigation. Use Pinia for state management. Use Tailwind CSS for styling. Store API URL in environment variables. Create dashboard components with adventure list.
```

**For Vanilla JavaScript:**

```
/speckit.plan Use vanilla HTML, CSS, and JavaScript. Use Vite for build tooling. Use native fetch API for HTTP requests. Use CSS custom properties for theming. Create modular JavaScript with ES modules. Store API URL in environment variables. Create dashboard components with adventure list.
```

> **📝 Review:** Verify the plan matches your chosen framework and includes component structure, API integration approach, and state management.

#### Step 3.1.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover component creation, API hooks/services, loading states, and error handling.

#### Step 3.1.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Check generated components for proper API integration, loading states, and user feedback.

#### ✅ Checkpoint: Verify Adventure Dashboard

> **⚠️ Before testing:** Make sure both servers are running!

```bash
# Terminal 1: Start the backend API (from Lab 1 project)
cd ../adventure-api
npm run dev   # or: dotnet run

# Terminal 2: Start the frontend dev server
cd ../adventure-frontend
npm run dev
```

Open http://localhost:5173 in your browser and verify:

- [ ] Adventures list loads from API
- [ ] Can create new adventure
- [ ] Can select adventure to play
- [ ] Delete shows confirmation

#### 🔀 Git: Commit and Merge Feature 1

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G` / `Cmd+Shift+G`)
2. Review changed files in the "Changes" section
3. Click `+` next to each file (or `+` on "Changes" header to stage all)
4. Enter commit message: `feat: implement adventure dashboard`
5. Click **Commit** button (checkmark icon)
6. Click **Sync Changes** or **Push** in the status bar

**Option B: Using Terminal**

```bash
git add .
git commit -m "feat: implement adventure dashboard

- Add adventure list with API integration
- Implement create/delete adventure flows
- Add loading skeletons and error states
- Configure environment variables"

git push origin main
```

---

### Feature 2: Character Management UI

#### Step 3.2.1 - Specify

```
/speckit.specify Build a character management interface:
- Character creation form with name input
- Attribute allocation system (STR, DEX, INT, CON, CHA)
- Point-buy or dice roll options for attributes
- Display calculated modifiers next to each attribute
- Character sheet view showing all stats
- Edit character functionality
- Character selection for adventures
```

> **📝 Review:** Check that the specification includes form validation rules and modifier calculation display.

#### Step 3.2.2 - Plan

```
/speckit.plan Continue with the existing tech stack. Create character form with attribute inputs. Implement modifier calculation display. Add dice roll integration for stat generation. Create character sheet component.
```

> **📝 Review:** Verify the plan includes form validation, dice roll API integration, and character sheet layout.

#### Step 3.2.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover form components, validation, dice integration, and character display.

#### Step 3.2.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Verify form validation, modifier calculations, and dice roll integration work correctly.

#### ✅ Checkpoint: Verify Character Management

> **⚠️ Ensure both servers are running** (see Feature 1 checkpoint for start commands)

Open http://localhost:5173 in your browser and verify:

- [ ] Character creation form works
- [ ] Attributes can be allocated
- [ ] Modifiers display correctly
- [ ] Character sheet shows all stats

#### 🔀 Git: Commit and Merge Feature 2

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `feat: implement character management UI`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "feat: implement character management UI

- Add character creation form with validation
- Implement attribute allocation system
- Display calculated modifiers
- Create character sheet view"

git push origin main
```

---

### Feature 3: Game Interface

#### Step 3.3.1 - Specify

```
/speckit.specify Build the main text adventure game interface:
- Narrative text display area with scrollable history
- Player input field for commands/choices
- Current scene description display
- Character status panel (HP, conditions, equipped items)
- Action buttons for common actions (attack, flee, use item)
- Combat mode with turn indicators
- Dice roll results display with animation
```

> **📝 Review:** Check that the specification includes all UI components and interaction patterns.

#### Step 3.3.2 - Plan

```
/speckit.plan Continue with the existing tech stack. Create game screen with narrative display. Implement command input with history. Add character status sidebar. Create combat UI with turn indicator. Add dice roll animation component.
```

> **📝 Review:** Verify the plan includes narrative scrolling, command history, and combat state management.

#### Step 3.3.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover narrative display, input handling, combat UI, and dice animations.

#### Step 3.3.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Verify narrative scrolling, command processing, combat mode, and dice roll display.

#### ✅ Checkpoint: Verify Game Interface

> **⚠️ Ensure both servers are running** (see Feature 1 checkpoint for start commands)

Open http://localhost:5173 in your browser and verify:

- [ ] Narrative text displays and scrolls
- [ ] Commands can be entered
- [ ] Character status shows correctly
- [ ] Combat mode works

#### 🔀 Git: Commit and Merge Feature 3

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `feat: implement main game interface`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "feat: implement main game interface

- Add narrative display with scrollable history
- Implement command input with history
- Create character status panel
- Add combat mode with turn indicators
- Implement dice roll animations"

git push origin main
```

---

### Feature 4: Inventory UI

#### Step 3.4.1 - Specify

```
/speckit.specify Build an inventory management interface:
- Grid or list view of inventory items
- Item details on hover/click
- Drag-and-drop or button-based equip/unequip
- Stack quantity display for stackable items
- Equipment slots visualization
- Use item functionality
- Sort and filter options
```

> **📝 Review:** Check that the specification covers all inventory interactions and display modes.

#### Step 3.4.2 - Plan

```
/speckit.plan Continue with the existing tech stack. Create inventory grid component. Implement item detail modal/tooltip. Add equipment slot visualization. Create equip/unequip functionality.
```

> **📝 Review:** Verify the plan includes grid/list toggle, item interactions, and equipment slot mapping.

#### Step 3.4.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover inventory display, item details, drag-drop/buttons, and filtering.

#### Step 3.4.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Verify item display, detail views, equip/unequip actions, and sort/filter functionality.

#### ✅ Checkpoint: Verify Inventory UI

> **⚠️ Ensure both servers are running** (see Feature 1 checkpoint for start commands)

Open http://localhost:5173 in your browser and verify:

- [ ] Items display in grid/list
- [ ] Item details show on interaction
- [ ] Equip/unequip works
- [ ] Stacks show quantities

#### 🔀 Git: Commit and Merge Feature 4

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `feat: implement inventory UI`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "feat: implement inventory UI

- Add inventory grid/list view
- Implement item details modal
- Create equipment slots visualization
- Add equip/unequip functionality
- Implement sort and filter options"

git push origin main
```

---

### Feature 5: Quest Log

#### Step 3.5.1 - Specify

```
/speckit.specify Build a quest tracking interface:
- List of active quests
- Quest details view with objectives
- Progress indicators for each stage
- Completed quests history
- Quest rewards display
- Filter by quest status (active, completed, failed)
```

> **📝 Review:** Check that the specification includes all quest states and progress tracking requirements.

#### Step 3.5.2 - Plan

```
/speckit.plan Continue with the existing tech stack. Create quest list component with filters. Implement quest detail view. Add progress indicators. Create completed quests section.
```

> **📝 Review:** Verify the plan includes filter logic, progress visualization, and quest history handling.

#### Step 3.5.3 - Tasks

```
/speckit.tasks
```

> **📝 Review:** Ensure tasks cover quest list, detail view, progress bars, and filtering.

#### Step 3.5.4 - Implement

```
/speckit.implement
```

> **📝 Review:** Verify quest list, details, progress indicators, and filters work correctly.

#### ✅ Checkpoint: Verify Quest Log

> **⚠️ Ensure both servers are running** (see Feature 1 checkpoint for start commands)

Open http://localhost:5173 in your browser and verify:

- [ ] Quest list displays
- [ ] Quest details show objectives
- [ ] Progress indicators work
- [ ] Filters function correctly

#### 🔀 Git: Commit and Merge Feature 5

**Option A: Using VS Code**

1. Open **Source Control** panel (`Ctrl+Shift+G`)
2. Stage all changes with `+`
3. Commit message: `feat: implement quest log UI`
4. Click **Commit** then **Sync Changes**

**Option B: Using Terminal**

```bash
git add .
git commit -m "feat: implement quest log UI

- Add quest list with status filters
- Implement quest detail view
- Create progress indicators
- Add completed quests history"

git push origin main
```

---

## Step 4: Connect to Your API

### Configure API Endpoint

Create a `.env` file:

```bash
# .env
VITE_API_URL=http://localhost:3000/api
```

### Test the Connection

```bash
# Start the development server
npm run dev

# Open in browser
# Navigate to http://localhost:5173
```

### Verify Full Integration

1. Register a new account
2. Log in with credentials
3. Create a new adventure
4. Create a character
5. Start playing!

---

## Step 5: Quality Checklist

Ensure your frontend implements:

- [ ] **Input Validation**
  - [ ] Client-side form validation
  - [ ] Sanitized user input display
  - [ ] XSS prevention

- [ ] **Error Handling**
  - [ ] API errors handled gracefully
  - [ ] Graceful degradation
  - [ ] User-friendly error messages

- [ ] **Performance**
  - [ ] Loading states during API calls
  - [ ] Efficient re-renders
  - [ ] Responsive design

---

## Minimum Functional Requirements Checklist

Ensure your frontend implements:

- [ ] **Adventure Management**
  - [ ] List adventures
  - [ ] Create new adventure
  - [ ] Select adventure to play
  - [ ] Delete adventure

- [ ] **Character Interface**
  - [ ] Create character with attributes
  - [ ] View character sheet
  - [ ] Attribute modifiers displayed

- [ ] **Game Interface**
  - [ ] Narrative text display
  - [ ] Player input
  - [ ] Action responses
  - [ ] Dice roll display

- [ ] **Inventory** (Optional but valued)
  - [ ] View items
  - [ ] Equip/unequip

- [ ] **Quests** (Optional but valued)
  - [ ] Quest list
  - [ ] Quest progress

---

## Example Game Flow

Here's what a typical interaction might look like:

```
┌─────────────────────────────────────────────────────────────┐
│  🏰 The Adventure Begins                                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  You stand at the entrance of a dark cave. The wind        │
│  howls behind you, carrying whispers of treasure and       │
│  danger within.                                             │
│                                                             │
│  A faint glow emanates from deeper inside the cavern.      │
│                                                             │
│  What do you do?                                            │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  [Enter Cave]  [Search Outside]  [Check Inventory]         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  > Enter the cave carefully                                 │
│                                                    [Send]   │
└─────────────────────────────────────────────────────────────┘

┌──────────────────┐
│ Aldric the Brave │
│ ──────────────── │
│ HP: 24/24        │
│ STR: 16 (+3)     │
│ DEX: 14 (+2)     │
│ INT: 10 (+0)     │
│ CON: 15 (+2)     │
│ CHA: 12 (+1)     │
└──────────────────┘
```

---

## Evaluation Criteria

Your implementation will be evaluated on:

| Criteria           | Weight |
| ------------------ | ------ |
| API Integration    | 30%    |
| Code Documentation | 25%    |
| User Experience    | 25%    |
| Code Quality       | 20%    |

---

## Tips for Success

1. **Start with the Dashboard** - Get the adventure list working first
2. **Use API Types** - Generate TypeScript types from your OpenAPI spec
3. **Handle Loading States** - Show spinners during API calls
4. **Test Error Cases** - What happens when the API is down?
5. **Keep it Simple** - Functionality over fancy visuals

---

## Code Documentation Guidelines

Your code should include:

````typescript
/**
 * Fetches the current adventure state from the API.
 *
 * @param adventureId - The unique identifier of the adventure
 * @returns Promise containing the adventure data
 * @throws {ApiError} When the API request fails
 *
 * @example
 * ```ts
 * const adventure = await getAdventure('123');
 * console.log(adventure.currentScene);
 * ```
 */
async function getAdventure(adventureId: string): Promise<Adventure> {
  // Implementation
}
````

---

## Resources

- [GitHub Spec Kit Documentation](https://speckit.org/)
- [React Documentation](https://react.dev/)
- [Vue.js Documentation](https://vuejs.org/)
- [Vite Documentation](https://vitejs.dev/)
- [TanStack Query](https://tanstack.com/query)
- [Tailwind CSS](https://tailwindcss.com/)

---

**May your interface be intuitive and your API calls swift! 🎮📜**
