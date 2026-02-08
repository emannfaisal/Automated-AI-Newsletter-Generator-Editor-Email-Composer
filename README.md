Autonomous Newsletter Engine
Multi-Agent Research, Synthesis, and Editorial Pipeline
This repository contains a high-level Agentic Workflow built in n8n that functions as a fully autonomous newsroom. It researches trending AI topics, plans an editorial strategy, drafts cited content in parallel, and assembles a professional HTML newsletter.

🔄 The Architecture (Multi-Stage Pipeline)
The system uses a "Fan-Out/Fan-In" pattern to handle multiple topics simultaneously without losing quality.

1. Strategy & Planning (The Planner)
Discovery: A Tavily AI node searches for the latest developments in AI adoption for small businesses.

Brainstorming: A Google Gemini agent (Planner) analyzes the search results to propose a catchy title and 3 distinct, high-value topics.

Strict Schema: A Structured Output Parser ensures the Planner provides valid JSON, which is essential for the downstream nodes to function.

2. Deep Research & Drafting (The Researchers)
Parallel Execution: The Split Out node creates three parallel branches—one for each topic.

Targeted Search: A second Tavily search fetches raw content specifically for each sub-topic.

Fact-Grounded Writing: An AI Agent writes a 350-500 word section per topic. It is strictly constrained to use only provided sources and must include inline citations [1], [2].

3. Assembly & Layout (The Editor)
Re-aggregation: The Aggregate node waits for all three researchers to finish and combines their work.

Editorial Polish: The Editor Agent takes the raw Markdown and converts it into a responsive HTML email body with inline CSS for cross-client compatibility.

Final Delivery: The workflow connects to the Gmail API to save the final product as a ready-to-send draft.

🛠️ Advanced AI Engineering Skills
Agentic Workflows: Moving beyond simple "Prompt -> Response" to a system that plans and executes.

Structured Output Parsing: Utilizing JSON schemas to maintain data integrity across different LLM calls.

Parallel Processing: Implementing a "Fan-Out" strategy to scale content generation efficiency.

Retrieval-Augmented Generation (RAG): Using live web search (Tavily) to ground Gemini’s responses in real-time facts, preventing hallucinations.
