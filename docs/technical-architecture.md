# Technical Architecture

## Recommended V1 Stack

Use a browser-first stack:

- Vite
- React
- TypeScript
- React Three Fiber
- Drei
- Zustand or Jotai for client state
- Tailwind CSS for DOM UI
- FastAPI, Hono, or Next.js API routes for agent and world endpoints
- Postgres or SQLite for early persistence
- OpenClaw integration for agent runtime and workflow execution

Why React Three Fiber:

- The game needs heavy DOM UI: inventory, quest log, chat, settings, vault.
- The 3D world should integrate with React state for projects, inventory, skills, and conversations.
- It is faster for a hackathon-style MVP than building every UI bridge manually.

If the project later needs more engine control, vanilla Three.js can replace the renderer while keeping the simulation and agent modules separate.

## Architecture Rule

Do not make the renderer the source of truth.

Separate:

- Simulation state
- Renderer state
- UI state
- Agent runtime
- Persistence
- Project/workspace data
- OpenClaw integration

## High-Level Modules

```text
src/
  game/
    simulation/
      entities.ts
      quests.ts
      inventory.ts
      player.ts
      projects.ts
      skills.ts
    world/
      WorldScene.tsx
      Npc.tsx
      Player.tsx
      CameraRig.tsx
      ProjectRoom.tsx
      WorldObject.tsx
    input/
      actionMap.ts
      useKeyboardMovement.ts
  agents/
    dwarfRegistry.ts
    conversationClient.ts
    outputContracts.ts
    openClawClient.ts
  ui/
    hud/
    inventory/
    quest-log/
    conversation/
    project-board/
    skill-books/
    vault/
  data/
    starterQuests.ts
    starterItems.ts
    starterProjects.ts
    starterSkills.ts
    worldMap.ts
```

## Runtime Boundaries

Simulation owns:

- Player position
- NPC availability
- Quest state
- Inventory state
- Skill progression
- Project state
- World object ownership
- Save data

Renderer owns:

- Meshes
- Animations
- Camera
- Lighting
- Effects
- Hit detection helpers

DOM UI owns:

- Inventory panel
- Quest log
- Conversation panel
- Settings
- Vault view
- Export actions
- Project board
- Skill book reader

Agent service owns:

- Prompt assembly
- Model calls
- Tool calls
- Output validation
- Memory access

OpenClaw owns:

- Canonical agent definitions
- Backend workflow execution
- Long-running tool calls
- Agent memory services
- External integrations

## Agent Conversation Flow

```text
Player interacts with NPC
-> UI opens conversation panel
-> Client sends player context, project context, dwarf id, active quest, and inventory references
-> Agent service or OpenClaw adapter builds prompt and calls model/tools
-> Agent returns structured response
-> Client renders dialogue
-> If output is useful, save it as inventory item
-> If linked to a project, attach item to project room
-> Quest state updates
```

## Data Models

### Dwarf

```ts
type DwarfAgent = {
  id: string;
  name: string;
  role: string;
  locationId: string;
  capabilities: string[];
  starterQuestIds: string[];
};
```

### Quest

```ts
type Quest = {
  id: string;
  title: string;
  offeredBy: string;
  status: "locked" | "available" | "active" | "completed";
  objective: string;
  requiredInputs: string[];
  rewardItemTypes: string[];
};
```

### Inventory Item

```ts
type InventoryItem = {
  id: string;
  type: string;
  title: string;
  createdBy: string;
  sourceQuest?: string;
  projectId?: string;
  content: string;
  tags: string[];
  version: number;
  createdAt: string;
};
```

### Project

```ts
type Project = {
  id: string;
  title: string;
  kind: "hackathon" | "saas" | "automation" | "content" | "investment" | "community" | "other";
  status: "idea" | "active" | "paused" | "launched" | "archived";
  summary: string;
  activeQuestIds: string[];
  inventoryItemIds: string[];
  worldLocationId?: string;
  nextAction?: string;
};
```

### Skill Book

```ts
type SkillBook = {
  id: string;
  title: string;
  skill: string;
  level: number;
  unlockedQuestIds: string[];
  relatedItemIds: string[];
};
```

### World Object

```ts
type WorldObject = {
  id: string;
  kind: "npc" | "project_room" | "project_board" | "skill_book" | "workflow_machine" | "vault_shelf";
  locationId: string;
  linkedEntityId?: string;
  interactionType: "talk" | "inspect" | "open" | "place_item" | "start_quest";
};
```

## Persistence Strategy

Prototype:

- Local storage for player state.
- JSON starter data for dwarfs, quests, items, projects, and skills.
- Markdown export for generated assets.

Alpha:

- User accounts.
- Database-backed inventory.
- Database-backed projects and project rooms.
- Server-side agent memory.
- Vault entries.
- OpenClaw-backed agent calls.

Production:

- Project workspaces.
- Team inventories.
- Team project rooms.
- Permissioned community vault.
- Search and retrieval over saved assets.

## Asset Strategy

Use low-poly or stylized 3D assets first.

Prioritize:

- Readable silhouettes
- Small file sizes
- Fast loading
- Consistent art direction
- Simple animations

Avoid:

- Large realistic assets
- High-poly environments
- Huge open worlds
- Asset packs with inconsistent style

## Performance Budget

V1 should run smoothly on ordinary laptops.

Targets:

- Initial load under 5 seconds on a normal connection.
- Main scene under 10 MB of compressed assets if possible.
- Stable 60 FPS on desktop.
- Functional fallback on mobile, even if controls are simplified.
