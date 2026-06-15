# Talent Angels — Original Project Proposal

> Preserved here as the source of truth for the project's scope and intent.
> Submitted as the LFDT / Learning Tokens Lab mentorship proposal. Do not edit the
> historical content; add revisions as new dated files.

## Primary Focus

Coding

## Description

Develop a suite of AI Graph Agents that empower humans to navigate the landscape
of skills, tasks, and occupations for lifelong learning in the age of AI.

**Why?**

Skills are the currency of talent. In the age of AI, skill demand shifts faster
than any individual, educator, or employer can track, making it critical for
humans and AI systems alike to know what to learn, how to develop it, and when it
becomes relevant.

**How?**

In AI systems, skills encode domain expertise, reusable workflows, and context,
providing a powerful abstraction for how work gets done. In the human world,
however, skills, tasks, and occupations remain scattered across incompatible
taxonomies with no shared semantic framework, widening the gap between human
talent development and the rapidly evolving demands of an AI-driven work
ecosystem.

Similar work already exists within the domain of AI tools, such as Anthropic
Skills within the Claude platform; however, efforts of this nature for human use,
or interfaces and tools to browse through skill databases that empower humans,
are less frequent, which is also a motivation for this project.

By querying these taxonomies through AI Graph Agents that build and traverse
knowledge graphs, we crowdsource a living ontology of talent that bridges human
skills development and AI-driven work.

**What?**

Talent Angels is a suite of AI Graph Agents that queries and reasons over the
following global taxonomies of skills, tasks, and occupations through a natural
language chat interface:

1. ESCO, with knowledge, skill, and competencies relevant to the European Union
   labor market, education, and training.
2. O*NET, with all occupations by the U.S. Department of Labor.
3. SFIA, a global framework for digital skills and competencies.
4. BLS, Occupational Outlook Handbook for career guidance.
5. Lightcast, a crowd-sourced common skills language.

We envision three kinds of agents:

1. **Locator** identifies and pinpoints the exact positions of skills, tasks, and
   occupations within the taxonomies.
2. **Connector** determines and lists the sequence of nodes directly preceding
   and succeeding each specified location, enabling users to view related tasks
   or skills.
3. **Pathfinder** traces and maps all possible routes connecting two locations
   through combinations of Connector paths, enabling users to discover learning
   journeys between any two skills, tasks, or occupations.

The manner in which the architecture is designed supports the implementation of a
fourth agent in future iterations: the **Evaluator**. This agent would be able to
assess and rank paths between two nodes based on relevance, distance, and
alignment with individual skill profiles.

## Learning Objectives

- Learn to collaborate in an open-source project.
- Learn about an ontology of Talent.
- Learn to apply Knowledge Graphs.
- Learn the foundational concepts of AI agents.
- Learn to build, evaluate, and deploy AI-powered agents in a production
  open-source environment.
- Understand the relationships between occupations, tasks and skills.
- Contribute standard descriptions of skills, tasks, and occupations.
- Apply Learning Tokens to granular skill acquisition processes.

## Expected Outcome and Deliverables

An Agentic AI with Graph-based Retrieval-Augmented Generation, GraphRAG, that
enables a unified reasoning layer about skills, tasks, and occupations.

Our Skill AI Agents are a set of building blocks to crowdsource the mapping of
relationships between tasks and skills.

Our approach models two dynamic functions: a skill function that defines the
minimum skills needed for each task, and a task function that reveals the
opportunities unlocked by each skill set.

The expected outcome is a living, data-driven ontology that enables AI systems,
educators, learners, and employers to identify, develop, and match talent with
unprecedented precision.

Our 2025 Mentorship successfully applied the sprints of Agile Methodology. We
propose to follow the same approach along these guidelines for AI Agent
development: https://www.linkedin.com/in/sharathrbhat/

**Deliverables**

1. Understand Knowledge Graphs, 2 weeks.
2. Define purpose and scope, 4 weeks.
   - Use Case
   - User needs
   - Success criteria
   - Constraints
3. System Prompt Design, 2 weeks.
   - Goals
   - Role / Persona
   - Instructions
   - Guardrails
4. Choose LLM, 2 weeks.
   - Base model
   - Parameters
   - Context window
   - Cost / latency
5. Tools & Integrations, 3 weeks.
   - Simple (local)
   - API (web, apps, data)
   - AI agent as a tool
   - Custom functions
6. Memory System, 3 weeks.
   - Episodic (conversation)
   - Working memory
   - Vector database
   - SQL / Structured DB
   - File storage
7. Orchestration, 3 weeks.
   - Routes / workflows
   - Triggers
   - Parameters
   - Message queues
   - Agent2Agent
   - Error handling
8. User Interface, 3 weeks.
   - Chat interface
   - Webapp
   - API endpoint
   - Slack / Discord Bot
9. Testing & Events, 3 weeks.
   - Unit tests
   - Latency testing
   - Quality metrics
   - Iterate & improve

There shall be three Virtual Meetups to present advances:

- First Virtual Meetup at the end of the 10th week.
- Second Virtual Meetup at the end of the 19th week.
- Third Virtual Meetup at the end of the 26th week.

We partner with Universidad Centroamericana José Simeón Cañas in El Salvador and a
local university in Mérida, Yucatán, México, to develop and apply our Skill AI
Agents to current courses.

Accepted mentees can also partner with their own universities or workplaces to
test our results.

## Relation to LF Decentralized Trust and impact on the community

Talent Angels directly extends the Learning Tokens Lab infrastructure at LF
Decentralized Trust by delivering the skill and competency metadata layer
required for Proof of Learning, PoL, validation.

Beyond Learning Tokens, the project contributes to the broader LFDT ecosystem in
three ways:

- Standardized skill recognition for any learning activity within LFX, in
  particular LF Decentralized Trust.
- Support for the Education and Outreach Workstream of the Generative AI Commons
  at LF AI & Data Foundation.
- An open-source set of reusable building blocks for anyone developing talent
  applications within the landscape of skills, tasks, and occupations.

## Recommended Skills

**Required**

- Python
- LLMs
- REST APIs
- Git/GitHub
- AI-augmented development (proficient using AI coding agents such as Claude Code,
  Cursor, or Codex as part of daily workflow)

**Preferred**

- Neo4j or any DB graph
- Agentic design (tool use)
- Langchain or any LLM framework
- Supabase or any backend-as-a-service with vector storage
- TypeScript/Node
- Docker

**Desired Soft Skills**

- Active listening
- Collaboration
- Accountability
- Empathy
- Critical thinking
- Proactiveness
- Clear communication
- Adaptability
- Creativity

## Mentor(s) Names and Contact Info

**Alfonso Govela**
Learning Tokens Lab at LF Decentralized Trust
alfonsogovela@me.com
https://www.linkedin.com/in/alfonsogovela/

**Enmanuel Amaya**
Director of the Bachelor in Computer Science Program, Universidad Centroamericana
José Simeón Cañas, El Salvador
earaujo@uca.edu.sv
https://github.com/enxel
https://www.linkedin.com/in/enmanuel-amaya-5a988a41/

**Alberto Ceballos**
Agentic AI Developer & Founder, Danil AI
alberto@danil.ai
https://github.com/nosoypoot
https://www.linkedin.com/in/aceballosvilla/

**Noemí Muñiz**
Professional Project / Product Manager
noemi.muniz.gutierrez@gmail.com
https://www.linkedin.com/in/noemi-muniz-gutierrez-96b25357/

## Additional Information

**2025**

- GitHub Hyperledger Learning Tokens Lab: https://github.com/hyperledger-labs/learning-tokens
- Learning Tokens. Connections with Online Learning Platforms. First SDK: https://www.youtube.com/watch?v=JaWJ2sEJmXQ&t=9s
- Learning Tokens: Connections with Online Learning Platforms and LMS & API Landscape: https://www.youtube.com/watch?v=5YVtrkQsxbA&t=17s
- Learning Tokens. Connections with online learning platforms. Final SDK: https://www.youtube.com/watch?v=vypFBJAd_WA&t=4s

**2024**

- GitHub Hyperledger Learning Tokens Lab: https://github.com/hyperledger-labs/learning-tokens
- Learning Tokens for Hyperledger Community Building, 1st Public Session: https://www.youtube.com/watch?v=8C6Ddse68Xc
- Learning Tokens for Hyperledger Community Building, 3rd Public Session: https://www.youtube.com/watch?v=PgVyHM3Qjtk
- Learning Tokens presentation at Bloxberg Hub of the University of Geneva, Switzerland: https://drive.google.com/file/d/1w7nBiu3_2oTAPENWjWXxIxiB9xKotXhh/view?usp=sharing

**2023**

- GitHub Hyperledger Lab Learning Tokens 2023: https://github.com/hyperledger-labs/learning-tokens
- GitHub Token Taxonomy Framework: https://github.com/InterWorkAlliance/TokenTaxonomyFramework/tree/main/artifacts/token-templates/definitions/LearningToken1/latest
- Wiki: https://lf-hyperledger.atlassian.net/wiki/display/INTERN/Learning+Tokens+@+Hyperledger+Besu
- Webinars:
  - Learning Tokens @ Hyperledger Besu, 1st Public Session: https://www.youtube.com/watch?v=-JA4os5zv-0
  - Learning Tokens @ Hyperledger Besu, 2nd Public Session: https://www.youtube.com/watch?v=8A6fyA5WIWo
  - Learning Tokens @ Hyperledger Besu, 3rd Public Session: https://www.youtube.com/watch?v=VoNeMqHaY2M

**2022**

- GitHub Learning Tokens 2022: https://github.com/hyperledger-labs/learning-tokens/tree/fd834c18bc1267aa14065fda07ce28f366da6ef5
- Wiki: https://lf-hyperledger.atlassian.net/wiki/display/CP/Learning+Tokens
- Wiki: https://lf-hyperledger.atlassian.net/wiki/display/INTERN/Learning+Tokens
- Webinar — Learning Tokens, un nuevo laboratorio en Hyperledger: https://www.youtube.com/watch?v=RZDaX-LRP4M
