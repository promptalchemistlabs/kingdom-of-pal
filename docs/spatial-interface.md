# Spatial Interface

## Core Idea

Kingdom of PAL is a spatial interface for agents, projects, workflows, and knowledge.

The world is not just decoration. It is a memory palace and command center:

- Dwarfs are AI agents.
- Buildings are projects or domains.
- Books are skills and learning assets.
- Scrolls are prompts.
- Blueprints are workflows.
- Machines are automations.
- Quest boards are task backlogs.
- Vault shelves are saved knowledge assets.
- Districts are areas of work, such as products, hackathons, content, investments, and community.

## Relationship To OpenClaw

OpenClaw should remain the agent runtime and execution layer.

Kingdom of PAL should become the world interface above it.

```text
OpenClaw
-> agent definitions
-> tool calls
-> workflow execution
-> memory and retrieval
-> backend task orchestration

Kingdom of PAL
-> open-world navigation
-> embodied agent conversations
-> project visualization
-> inventory and skill books
-> quests and progression
-> spatial memory
```

This separation matters because the game world should not own the agent runtime. It should call it.

## Project Visualization

Projects should become physical places in the kingdom.

Examples:

- A SaaS idea becomes a workshop.
- A hackathon project becomes a quest tent.
- A content series becomes a library shelf.
- An automation system becomes a machine room.
- A revenue stream becomes a market stall.
- An investment thesis becomes a map table.

Each project place can contain:

- Project summary
- Current status
- Related agents
- Open quests
- Saved inventory items
- Workflows
- Notes and documents
- Timeline or milestones

## Inventory As Knowledge Assets

Inventory should store real reusable work assets, not random loot.

Important item types:

- Skill Book: learning asset or capability unlock
- Prompt Scroll: reusable prompt
- Workflow Blueprint: repeatable process
- Project Map: visual summary of a project
- Automation Gear: automation component or plan
- Market Map: audience, positioning, or channel artifact
- Quest Note: task context and next action
- Vault Entry: reusable knowledge-base record

The inventory should answer:

- What have I created?
- Which project does this belong to?
- Which agent helped me create it?
- Can I reuse, refine, export, or combine it?

## Skill Books

Skill books are progression and knowledge objects.

Possible skill books:

- Prompting
- Agent Building
- Automation
- Product Thinking
- Positioning
- Distribution
- Monetization
- Founder Operations
- Sustainability Systems
- Investing
- Crypto and Decentralized Systems

Skill books can unlock:

- New quests
- Better agent prompts
- New workflow templates
- Deeper project analysis
- New districts or rooms

## World Design Principle

The world should make real work easier to see, remember, and act on.

If walking through the world is slower than using a dashboard and gives no extra context, the design is failing.

The world adds value when it:

- Makes abstract work visible.
- Helps users remember where ideas live.
- Gives agents stronger context.
- Makes progress feel tangible.
- Creates a distinctive Prompt Alchemist Labs experience.

## First Spatial MVP

Build only these world objects first:

- Central plaza
- Seven dwarf agent stations
- Project board
- One project room
- Inventory bag
- Skill bookshelf
- Workflow forge
- Vault shelf

Killer demo:

```text
Player creates a project on the project board
-> walks to Orin
-> asks for help refining the project
-> receives a workflow blueprint
-> saves it in inventory
-> places it inside the project room
-> sees the project room update
```
