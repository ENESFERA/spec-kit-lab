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
- Security: Never store sensitive tokens in localStorage; use httpOnly cookies or secure session management
- Simplicity: Focus on functionality over visual complexity
- Responsiveness: Interface must work on mobile and desktop
- Error handling: All API errors must be displayed gracefully to users
- Documentation: All components and functions must be documented
```

---

## Step 3: Create Feature Specifications

### 3.1 Authentication UI Specification

```
/speckit.specify Build an authentication interface with:
- Login form with username and password fields
- Registration form for new users
- Form validation with clear error messages
- Secure token handling (store JWT securely)
- Logout functionality
- Protected routes that redirect to login when unauthenticated
- Loading states during API calls
```

### 3.2 Adventure Dashboard Specification

```
/speckit.specify Build an adventure dashboard where users can:
- View list of their existing adventures
- Create a new adventure with a name
- Select an adventure to continue playing
- Delete an adventure with confirmation
- Display adventure metadata (creation date, current scene, progress)
- Show loading skeleton while fetching data
```

### 3.3 Character Management UI Specification

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

### 3.4 Game Interface Specification

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

### 3.5 Inventory UI Specification

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

### 3.6 Quest Log Specification

```
/speckit.specify Build a quest tracking interface:
- List of active quests
- Quest details view with objectives
- Progress indicators for each stage
- Completed quests history
- Quest rewards display
- Filter by quest status (active, completed, failed)
```

---

## Step 4: Create Implementation Plan

Generate the technical implementation plan:

### For React:

```
/speckit.plan Use React 18 with TypeScript. Use Vite for build tooling. Use React Router for navigation. Use TanStack Query (React Query) for API state management. Use Tailwind CSS for styling. Use Zustand for global state (auth tokens). Create reusable components in src/components. Use custom hooks for API calls. Store API URL in environment variables.
```

### For Vue:

```
/speckit.plan Use Vue 3 with TypeScript and Composition API. Use Vite for build tooling. Use Vue Router for navigation. Use Pinia for state management. Use Tailwind CSS for styling. Create reusable components in src/components. Use composables for API interactions. Store API URL in environment variables.
```

### For Vanilla JavaScript:

```
/speckit.plan Use vanilla HTML, CSS, and JavaScript. Use Vite for build tooling and hot reload. Use native fetch API for HTTP requests. Use CSS custom properties for theming. Create modular JavaScript with ES modules. Use Web Components for reusable UI elements. Store API URL in environment variables. Focus on progressive enhancement.
```

---

## Step 5: Analyze Consistency

Validate your plan against the specifications:

```
/speckit.analyze
```

Review any issues and refine your plan if needed.

---

## Step 6: Generate Task Breakdown

Create actionable tasks:

```
/speckit.tasks
```

Review the generated `tasks.md` to understand:

- Implementation phases
- Component dependencies
- Testing requirements

---

## Step 7: Execute Implementation

Build the frontend:

```
/speckit.implement
```

The AI will implement:

1. Project setup and configuration
2. Authentication flow
3. API integration layer
4. UI components
5. Page routing and navigation
6. State management

---

## Step 8: Connect to Your API

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

### Verify API Integration

1. Register a new account
2. Log in with credentials
3. Create a new adventure
4. Create a character
5. Start playing!

---

## Step 9: Security Checklist

Ensure your frontend implements:

- [ ] **Token Security**
  - [ ] Tokens not stored in localStorage (if possible)
  - [ ] Tokens cleared on logout
  - [ ] Automatic redirect on 401 responses

- [ ] **Input Validation**
  - [ ] Client-side form validation
  - [ ] Sanitized user input display
  - [ ] XSS prevention

- [ ] **Secure Communication**
  - [ ] HTTPS in production
  - [ ] CORS properly configured
  - [ ] No sensitive data in URLs

- [ ] **Error Handling**
  - [ ] API errors don't expose sensitive info
  - [ ] Graceful degradation
  - [ ] User-friendly error messages

---

## Minimum Functional Requirements Checklist

Ensure your frontend implements:

- [ ] **Authentication**
  - [ ] Login form
  - [ ] Registration form
  - [ ] Logout functionality
  - [ ] Protected routes

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

| Criteria                | Weight |
| ----------------------- | ------ |
| API Integration         | 25%    |
| Security Implementation | 25%    |
| Code Documentation      | 20%    |
| User Experience         | 15%    |
| Code Quality            | 15%    |

---

## Tips for Success

1. **Start with Authentication** - Get login/logout working first
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
