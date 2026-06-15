# Game Design

## Fantasy

The player enters the Kingdom of Prompt Alchemist Labs, an open dwarven command world built around craft, prompts, automation, projects, and execution.

The dwarfs are not decoration. They are specialist agents who help players convert messy ideas into useful assets, then place those assets into projects, rooms, bookshelves, workflow machines, and vaults.

## Player Verbs

V1 verbs:

- Explore
- Talk
- Accept quests
- Manage inventory
- Read skill books
- Visualize projects
- Forge outputs
- Save assets
- Place assets into project spaces
- Upgrade assets
- Return to specialists

Later verbs:

- Trade
- Craft
- Build rooms
- Invite party members
- Run agent workflows
- Host live events
- Publish assets to the community vault

## Core Loop

1. Player enters the kingdom.
2. Player chooses or creates a project.
3. Player explores the world and finds a dwarf NPC, project board, skill book, or workflow station.
4. Dwarf offers a practical quest or service.
5. Player gives context, goal, or raw material.
6. Agent generates a useful output.
7. Output becomes an inventory item.
8. Player attaches the item to a project, vault, workflow, or skill book.
9. Completed quests unlock new dwarfs, districts, tools, templates, or project views.

## World Structure

V1 should feel open but stay compact. Build one dense district first, not a huge map.

Suggested hub: The Foundry Court

Areas:

- The Forge: prompt and workflow crafting.
- The Ledger Hall: business models, pricing, ROI, finance.
- The Clocktower: execution planning, deadlines, focus.
- The Market Gate: positioning, distribution, offers.
- The Workshop: automations, tooling, implementation plans.
- The Grove: sustainability, systems, long-term compounding.
- The Archive: summaries, lessons, stories, knowledge vault.
- The Project Board: current projects, ideas, hackathons, and ventures.
- The Skill Library: skill books, learning paths, and capability unlocks.

## Project Visualization

Projects are physical places in the kingdom.

Examples:

- Prompt Alchemist Labs becomes the central kingdom.
- OpenClaw becomes an engineering forge or machine room.
- A hackathon project becomes a quest tent.
- A SaaS idea becomes a workshop.
- A content series becomes a library shelf.
- A revenue stream becomes a market stall.
- An investment thesis becomes a map table.

Each project place should show:

- Current objective
- Related dwarf agents
- Active quests
- Saved inventory items
- Workflows
- Notes
- Status
- Next action

## Camera And Movement

Recommended v1 feel:

- 2.5D or low-poly 3D world.
- Isometric or angled third-person camera.
- Keyboard movement as default.
- Click-to-move can come later if pathfinding is ready.
- NPC interaction by proximity plus a button prompt.

Avoid first-person Minecraft-like controls for v1 unless there is a strong reason. A RuneScape-like camera better supports NPC discovery, UI panels, and inventory.

## Inventory

Inventory is not just game loot. It is a personal asset system for skills, workflows, project artifacts, and generated outputs.

Item categories:

- Prompt Scrolls
- Skill Books
- Workflow Blueprints
- Quest Notes
- Project Maps
- Market Maps
- Forge Tokens
- Automation Components
- Story Fragments
- Vault Artifacts

Each useful agent output should become an item.

Example:

```json
{
  "id": "item_prompt_scroll_001",
  "type": "prompt_scroll",
  "title": "Hackathon Pitch Refiner",
  "createdBy": "Orin Forgekeeper",
  "sourceQuest": "Forge a Raw Idea",
  "projectId": "project_kingdom_of_pal",
  "content": "...",
  "tags": ["prompt", "hackathon", "pitch"],
  "version": 1
}
```

## Quests

Quests should be practical, short, and output-driven.

Good v1 quest examples:

- Forge a rough idea into a clear prompt.
- Turn a hackathon project into a product thesis.
- Create a 7-day execution plan.
- Map a SaaS idea to customer pain, offer, and pricing.
- Summarize a community discussion into reusable notes.
- Convert a manual workflow into an automation blueprint.
- Create a founder story fragment from a hackathon lesson.

Bad v1 quest examples:

- Kill 10 monsters.
- Collect 20 random stones.
- Walk across a giant map with no meaningful decision.
- Do fantasy errands that do not create useful assets.

## Skills And Progression

Use practical founder/operator skills instead of generic RPG stats.

Possible skills:

- Prompting
- Automation
- Positioning
- Distribution
- Monetization
- Execution
- Systems Thinking
- Storytelling

Progression should unlock:

- New skill books
- Better agent tools
- More advanced quest templates
- Larger asset vault capacity
- Better project views
- New districts
- Export formats
- Community publishing

## Session Length

Design for short repeat visits:

- 3 minutes: talk to one dwarf and get a quick output.
- 10 minutes: complete one quest.
- 30 minutes: complete a multi-step workflow.

## Multiplayer

Do not build multiplayer first.

Fake aliveness before real multiplayer:

- NPCs walking around.
- Community announcements.
- Public vault highlights.
- Ghost records of popular quests.
- Weekly kingdom events.

Real multiplayer can come later if the single-player agent loop retains users.
