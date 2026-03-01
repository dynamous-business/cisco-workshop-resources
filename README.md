# Cisco Agentic Engineering Workshop

**AI-Assisted Development for Enterprise Teams**

Most developers using AI coding tools are stuck in a frustrating loop: impressive demos that fall apart in real projects, inconsistent results between sessions, and hours lost cleaning up AI-generated code. The difference between developers who struggle and those who thrive isn't the AI—it's the system around it.

This workshop teaches you how to build that system. You'll create an "AI Layer" in your codebase: persistent rules, on-demand context, and reusable workflows that turn AI from an unpredictable chat tool into a reliable development partner.

## What You'll Learn

| Module | Topic |
|--------|-------|
| 01 | **The New SDLC** - Your codebase now has an AI layer (Rules, On-Demand Context, Skills) |
| 02 | **Setting the Stage** - PRDs and scoping work before implementation |
| 03 | **The PIV Loop** - Plan → Implement → Validate methodology |
| 04 | **Foundations** - Building your AI layer (Custom Instructions, Prompt Files, Skills) |
| 05 | **AI-Native Architecture** - Optimizing codebases for agents (VSA, Priming, Component Sizing) |

## Hands-On Exercises

1. **Baseline** - Apply your current AI workflow to a brownfield development task
2. **PIV Loop** - Apply planning → implementing → validating to the same task
3. **Build a Prompt** - Create your own reusable prompt file for something you do daily/weekly
4. **AI-Optimized** - Build on top of an AI-optimized codebase (Python/FastAPI)

## Contents

### Presentation

- [`cisco-workshop-slides.pptx`](./cisco-workshop-slides.pptx) - Main workshop presentation (50 slides)

### Diagrams

| File | Description |
|------|-------------|
| [`Excal-1-Workshop-Guide.png`](./diagrams/Excal-1-Workshop-Guide.png) | Workshop structure overview |
| [`Excal-2-SystemGap.png`](./diagrams/Excal-2-SystemGap.png) | The system gap problem |
| [`Excal-3-PIVLoop.png`](./diagrams/Excal-3-PIVLoop.png) | Plan → Implement → Validate loop |
| [`Excal-4-GlobalRules.png`](./diagrams/Excal-4-GlobalRules.png) | Global rules structure |
| [`Excal-5-ReusablePrompts.png`](./diagrams/Excal-5-ReusablePrompts.png) | Reusable prompts pattern |
| [`Excal-6-AI-Optimized-Codebases.png`](./diagrams/Excal-6-AI-Optimized-Codebases.png) | AI-optimized codebase structure |

### GitHub Copilot Configuration

Example configuration demonstrating the AI Layer concepts from the workshop.

#### Custom Instructions Template

- [`.github/copilot-instructions-template.md`](./.github/copilot-instructions-template.md) - Template for creating project-specific custom instructions

#### Prompt Files (Reusable Commands)

Prompt files live in `.github/prompts/` and become slash commands in Copilot Chat. Type `/` in the chat input to see available prompts.

| Prompt | Description |
|--------|-------------|
| [`/prd`](./.github/prompts/prd.prompt.md) | Create a Product Requirements Document |
| [`/plan`](./.github/prompts/plan.prompt.md) | Generate an implementation plan |
| [`/implement`](./.github/prompts/implement.prompt.md) | Execute a plan with validation loops |
| [`/validate`](./.github/prompts/validate.prompt.md) | Run linter, type checker, and tests |
| [`/review`](./.github/prompts/review.prompt.md) | Code review workflow |
| [`/create-rules`](./.github/prompts/create-rules.prompt.md) | Generate AGENTS.md from codebase analysis |
| [`/prime`](./.github/prompts/prime.prompt.md) | Load full project context |
| [`/prime-client`](./.github/prompts/prime-client.prompt.md) | Load frontend context |
| [`/prime-server`](./.github/prompts/prime-server.prompt.md) | Load backend context |
| [`/prime-components`](./.github/prompts/prime-components.prompt.md) | Learn component patterns |
| [`/prime-endpoint`](./.github/prompts/prime-endpoint.prompt.md) | Learn end-to-end endpoint patterns |
| [`/install`](./.github/prompts/install.prompt.md) | Install project dependencies |

#### Skills

| Skill | Description |
|-------|-------------|
| [`agent-browser`](./.github/skills/agent-browser/SKILL.md) | Browser automation for web testing and validation |

##### Installing agent-browser

The `agent-browser` skill requires the [Vercel agent-browser CLI](https://github.com/vercel-labs/agent-browser) to be installed:

```bash
# Install globally via npm
npm install -g agent-browser

# Download the browser (Chromium)
agent-browser install
```

**Linux users** need additional system dependencies:

```bash
agent-browser install --with-deps
```

**Verify installation:**

```bash
agent-browser --help
```

**Version pinning tip:** If using npx, keep install and run on the same version:

```bash
npx agent-browser@latest install
npx agent-browser@latest open example.com
```

## Using This AI Layer

### Setup

1. **Copy the `.github/` folder** into your project root
2. **Generate custom instructions**: Run `/create-rules` in Copilot Chat to auto-generate an `AGENTS.md` from your codebase
3. **Customize prompt files**: Edit prompts in `.github/prompts/` to match your project's build/test commands

### The PIV Loop Workflow

1. **Plan**: `/plan "feature description"` — creates a structured plan
2. **Implement**: `/implement .agents/plans/your-plan.plan.md` — executes with validation loops
3. **Validate**: `/validate` — runs all checks and reports results

### Recommended Copilot Settings

For the best agent mode experience, add to your VS Code `settings.json`:

```json
{
  "chat.agent.enabled": true,
  "chat.promptFiles": true,
  "github.copilot.chat.agent.runTasks": true
}
```

### Model Recommendations

| Phase | Recommended Model | Why |
|-------|-------------------|-----|
| Planning (`/plan`, `/prd`) | Claude Sonnet 4.6 or Opus 4.6 | Better reasoning for architecture decisions |
| Implementation (`/implement`) | Claude Sonnet 4.6 | Good balance of quality and speed (1x multiplier) |
| Quick tasks (`/validate`, `/install`) | GPT-4.1 or GPT-5 mini | Free (0x multiplier), fast responses |

## Exercise Repository

The hands-on exercises use a separate repository:

```bash
git clone https://github.com/dynamous-business/nextjs-feature-flag-exercise
cd nextjs-feature-flag-exercise
git checkout exercise-1
```

## Key Takeaways

1. **Build Your AI Layer** - Custom instructions, on-demand context, and skills compound over time
2. **PRD Then PIV** - Scope the work first, then iterate with Plan-Implement-Validate
3. **Evolve the System** - Every bug is an opportunity to improve your AI layer

---

*Cole Medin | Dynamous*
