# "The Boys" AI Orchestrator

> An AI orchestration system for managing workflows and task distribution across VS Code, Web, and API interfaces.


## 📚 Table of Contents
- [Overview](#-overview)
- [Goals](#-high-level-project-goals)
- [Core Components](#-core-components--architecture)
  - [AI Agents Team](#-ai-agents-the-boys-team)
  - [Model Selection](#-ai-model-selection--cost-optimization)
  - [LangGraph Integration](#-langgraph-integration)
- [Build Plan](#-step-by-step-build-plan)
- [Current Status](#-current-status)

## 🚀 Project Overview

### What is "The Boys"?

"The Boys" is an advanced AI orchestrator designed to dynamically manage AI workflows, optimize tasks, and intelligently handle coding, debugging, and multi-agent reasoning across VS Code, Web, and API interfaces.

The Boys functions as a structured AI team, handling entire workflows through specialized agents that work together on complex tasks.

This system is built to:
- Act as a multi-agent AI team that works collaboratively on coding, debugging, reasoning, and planning
- Integrate with VS Code to live inside projects, analyze multiple scripts, and ensure logical consistency across files
- Have a decision-making framework that dynamically selects AI models based on cost, complexity, and efficiency
- Use LangGraph for AI workflow orchestration and human feedback loops, ensuring real-time adjustments and quality control

## 📌 High-Level Project Goals
- **Multi-Agent AI Team**: Specialized agents working collaboratively, each with a defined role
- **Seamless VS Code Integration**: AI operates inside entire projects, analyzing and ensuring consistency between scripts
- **Web & API Interface**: Accessible via browser and Jupyter/Colab for interactions beyond VS Code
- **Cost & Model Optimization**: The system selects AI models dynamically based on complexity and budget
- **Human Feedback System (LangGraph)**: Ensures AI stops for approvals at critical decision points before executing

## 📌 Core Components & Architecture

### 1️⃣ AI Agents: "The Boys" Team

These specialized agents allow the AI system to distribute tasks intelligently rather than relying on a single model for everything.

| Agent Name | Role | Core Responsibilities | Active/On-Demand |
|------------|------|----------------------|------------------|
| Instructor (Main Coordinator) | Oversees workflow | Assigns tasks, picks AI providers, manages cost, stops if things don't make sense | Always Active |
| User Intent Clarifier | Ensures correct understanding | Asks smart clarifying questions before execution | Always Active |
| High-Level Architect | Ensures overall structure is solid | Prevents scope creep, ensures all parts work together | On-Demand |
| Performance Optimizer & Debugging Specialist | Improves efficiency | Optimizes and debugs AI-generated code | On-Demand |
| Code Implementers (2-3 agents) | Writes code | Generates, improves, and refines code | On-Demand |
| Code Validator | Checks correctness | Reviews code before final approval | On-Demand |
| Logic Checker | Prevents incorrect assumptions | Ensures the project stays on track | On-Demand |
| BS Detector & Realism Checker (Merged) | Filters out unnecessary work | One simplifies, one ensures nothing important is cut | On-Demand |
| Final Script Manager | Manages script files | Ensures scripts are formatted and structured properly | On-Demand |
| Data & Context Manager | Tracks history | Prevents AI from "forgetting" previous interactions | Always Active |

### 2️⃣ AI Model Selection & Cost Optimization

"The Boys" dynamically select AI models based on complexity, minimizing cost while maximizing efficiency.

| AI Model | Primary Strengths |
|----------|------------------|
| GPT-3.5 | Quick responses, basic code completion, simple queries |
| GPT-4o | Complex reasoning, system design, architectural decisions |
| GPT-4o-1 | Structured coding, detailed analysis, advanced problem-solving |
| GPT-4o-3 | Advanced reasoning, complex debugging, system-wide analysis |
| Claude 3.5 Sonnet | Long-form analysis, complex reasoning, detailed code review |
| DeepSeek R1 | Logical reasoning, structured thinking |
| TogetherAI Llama 3 | Local deployment option, basic code tasks |

#### Preliminary Setup – Subject to Refinement
- This model setup is an initial framework, but we will conduct further research to determine which models are best suited for specific agent roles
- During implementation, we will:
  - Test models against different agent tasks (e.g., debugging vs. planning vs. reasoning)
  - Adjust assignments dynamically based on performance, latency, and cost
  - Consider adding/removing models if a better alternative is found for a given role
  - Final model-to-role assignments will be optimized during real-world testing

#### How the Instructor decides (subject to change during refinement):
1. For small, simple tasks → Uses GPT-3.5
2. For normal reasoning & coding → Uses GPT-4o or DeepSeek R1
3. For complex debugging & structured workflows → Uses GPT-4o-3
4. If AI keeps failing at a task → Instructor escalates to a higher-end model automatically

### 3️⃣ LangGraph Integration for AI Workflow Orchestration

LangGraph is the backbone of "The Boys," enabling a multi-agent orchestration system with human feedback loops.

Parallelization for Non-Dependent Tasks:
- When multiple independent tasks (e.g., different parts of code generation, analysis, or validation) can run simultaneously, LangGraph will execute them in parallel to improve efficiency
- Example: If Code Implementers are working on different parts of a script (or even independently on the same task), their work will be done in parallel before being merged by the Final Script Manager
- Tasks that depend on previous steps (e.g., validation before execution) will still be sequential
- Decision Nodes: The system pauses at critical decision points, requiring human input before continuing
- Feedback Loop: If human feedback is negative, the AI adjusts and reassigns agents before execution

## 📌 Step-by-Step Build Plan

### Why this is included:
- This serves as our guide throughout the project to track our progress
- Later, we can decide whether to keep it as documentation or remove it

### 🛠 PHASE 1: Build the Basic System (Single-Agent API)

**Goal**: Deploy a basic API on AWS that allows sending requests and receiving AI-generated responses.

#### Step 1: Set Up AWS API ("Ask The Boys")
- ✅ Launch an EC2 instance on AWS (Linux-based, running 24/7)
- ✅ Install Python, FastAPI, and dependencies
- ✅ Expose API to the internet:
  - Configure AWS Security Groups (allow traffic on port 8000)
  - Set up a public IP or domain for easy access
- ✅ Verify external access:
  - Call the API from a browser, phone, and VS Code

#### Step 2: Connect API to VS Code & Web App
- ✅ VS Code Extension (Ask The Boys):
  - AI lives inside projects and understands multiple scripts together
  - Can analyze dependencies across files, not just respond to isolated queries
- ✅ Web App (Ask The Boys):
  - Allows structured interactions for reviewing AI decisions, workflows, and logs
- ✅ Verify connections work from all interfaces

### 🛠 PHASE 2: Expand to Multi-Agent System ("The Boys" Team)

**Goal**: Implement specialized AI agents that distribute tasks intelligently.

- ✅ Introduce "The Boys" as specialized AI agents
- ✅ Integrate LangGraph for AI Workflow Orchestration
- ✅ Ensure Instructor dynamically assigns agents based on the request
- ✅ Verify multi-agent system by testing coding/debugging workflows

### 🛠 PHASE 3: Add API Cost Awareness & Model Selection

**Goal**: The system chooses models dynamically based on complexity and budget.

- ✅ Implement model selection logic (Instructor AI assigns the best model for the task)
- ✅ Introduce cost tracking dashboard to optimize API usage
- ✅ Verify by testing tasks at different complexity levels

### 🛠 PHASE 4: Full Integration & Scaling

**Goal**: Make the system fully functional, scalable, and ready for use.

- ✅ Enable AI to edit files in VS Code, not just suggest changes
- ✅ Improve Web UI to support workflow approvals
- ✅ Optimize LangGraph feedback loop to improve AI reasoning
- ✅ Conduct full system tests across all interfaces

