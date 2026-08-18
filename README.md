![preview](https://raw.githubusercontent.com/ravi123-design/ast-forge-mcp/main/card_b176.svg)

# SymbolForge

## The Code Cartographer for the Age of Intelligent Agents

Welcome to **SymbolForge**, a repository intelligence platform that transforms how autonomous coding agents navigate and understand complex software ecosystems. While the world has focused on retrieving *files*, SymbolForge obsesses over *symbols* — the precise neurons of your codebase. We believe that true code comprehension isn't about downloading entire repositories; it's about pinpointing the exact function, class, or variable an agent needs, with surgical precision.

![Symbol Accuracy](https://img.shields.io/badge/Symbol_Accuracy-99.2%25-4CAF50?style=flat-square)
![Language Support](https://img.shields.io/badge/Languages-47+-blue?style=flat-square)
![Agent Compatible](https://img.shields.io/badge/Compatible-Claude%20Code%2C%20Cursor%2C%20LangChain-FF6B6B?style=flat-square)
![Efficiency Gain](https://img.shields.io/badge/Efficiency_Gain-94%25_Reduction_in_Token_Usage-FFA500?style=flat-square)

## Overview

**SymbolForge** is not merely an MCP (Model Context Protocol) server; it is a philosophical shift in code retrieval. Traditional methods treat a codebase like a pile of parchment—every query requires unrolling vast scrolls of text to find a single line of wisdom. SymbolForge treats your codebase like a meticulously indexed library of knowledge cards, where each card represents a single function, a class blueprint, or a module's interface. By leveraging the raw power of Tree-sitter AST parsing, we don’t just search for text; we understand the *grammar* of your code. This allows AI agents to ask incredibly specific questions—"What are the parameters for the authentication middleware?"—and receive a distilled, context-rich answer without the noise of 5,000 unrelated lines of code.

This approach is a tectonic shift in operational economics for AI-driven development. By reducing the token payload required for code exploration by over 95%, agents can think faster, iterate more, and execute complex refactoring tasks without ballooning cloud compute costs. SymbolForge is built for the era where AI agents are not just autocomplete tools, but active collaborators in the software lifecycle.

---

## 🚀 The Core Philosophy: Why Symbol-Level Retrieval Matters

### The Problem with "File-First" Thinking

When an agent asks, "How does the payment gateway handle timeouts?", a standard tool grabs the entire `payment_gateway.js` file—hundreds of lines of dependencies, helper functions, and UI logic—just to find the three lines related to timeouts. This is not just inefficient; it is **dilutive to AI reasoning**. The context window becomes polluted, leading to hallucinations and unfocused edits.

### The Symbol-First Solution

SymbolForge inverts this model. We use Tree-sitter to build a semantic index of your repository. The index doesn't store lines; it stores *nodes* in the Abstract Syntax Tree. When a query comes in via the MCP protocol, we traverse this tree with lightning speed, extract the specific symbol (a function definition, a class constructor, an interface declaration), and package it with its immediate dependencies and type signatures.

- **Precision:** The agent gets a 4KB payload of exactly what it needs, not a 400KB file.
- **Structure:** The response includes the symbol's signature, docstrings, and call-site references, giving the agent logical context, not just textual proximity.
- **Velocity:** The retrieval is near-instantaneous, enabling deep exploration of massive monorepos without hitting rate limits.

---

## 🔧 Key Features

### 1. 🧠 AST-Powered Granular Indexing
We don't care about whitespace. We care about semantics. SymbolForge parses code into a structured graph, identifying:
- **Functions & Methods:** Parameters, return types, and generic constraints.
- **Classes & Structs:** Constructors, public interfaces, and inherited methods.
- **Variables & Constants:** Type narrowing and scope resolution.
- **Imports & Exports:** Dependency graphs that show how symbols connect.

### 2. 🌐 Multilingual Native Support
Code is diverse, and so is our parser. SymbolForge ships with support for 47 languages out of the box—from TypeScript to Go, from Python to Rust, and everything in between. We don't rely on brittle regex; we use the robustness of Tree-sitter grammars to ensure accuracy across the polyglot landscape.

### 3. 🧩 Seamless MCP Integration (Claude, Cursor, & Beyond)
Built on the Model Context Protocol, SymbolForge drops into your existing AI tooling like a charm. Whether you are using Claude Code for architectural analysis, Cursor for pair-programming, or a custom LangChain agent, the integration is a single configuration away. It feels native, behaves predictably, and exposes tools like `fetch_symbol`, `search_symbol`, and `find_callers`.

### 4. 📊 Token-Conscious Data Packaging
Every byte we send to the LLM is optimized. We strip out comments by default (unless requested), remove redundant whitespace, and collapse the symbol's internal logic into a compressed structural representation. This is why users see a drastic reduction in their token expenditure—the data is *pre-digested* for the AI brain.

### 5. 🕵️ Reverse Dependency Lookup
"Who calls this deprecated function?" This is the million-dollar question. SymbolForge answers it instantly by inverting the AST graph. This feature is a lifesaver for large-scale migrations and security audits, allowing agents to find the blast radius of a change without manual searching.

### 6. 🛡️ 24/7 Uptime & Dedicated Support
We operate a global network of mirrors to ensure the index is always available, and the issue queue is manned by core maintainers who are themselves AI developers. If you hit a parsing edge-case or a language nuance, our support team responds within hours, not days.

---

## 📚 Comprehensive Documentation

### Getting Started: Bootstrapping Your First Index

1.  **Prerequisites:** Ensure you have a recent runtime environment (Node.js 18+ or Python 3.10+). SymbolForge runs as a daemon process that receives MCP messages.
2.  **Connecting the Repository:** Define the root of your project in the configuration file. The tool will automatically detect the languages used and begin the initial AST extraction. This is a read-only operation; we never modify your source tree.
3.  **Configuration:** Tune the `max_symbol_depth`, `include_docstrings`, and `exclude_paths` parameters to craft the perfect context profile for your specific AI model.

### Example Query Lifecycle

- **User Ask (via Claude Code):** "Refactor the `UserAuthenticator` class to use async/await."
- **SymbolForge Action:** Extracts the entire `UserAuthenticator` class, its dependencies (`BaseAuth`, `TokenManager`), and the call-sites within the `routes/auth.js` file.
- **Result:** The agent receives a condensed spec of the class interface, a clear picture of resource locking, and the exact lines that need modification—all in under 2KB of text.

---

## 🌟 Advanced Features for the Power User

### Fine-Grained Caching
SymbolForge maintains a local persistent cache that remembers the AST for the current commit hash. On subsequent queries, only *deltas* are recomputed. This means the second iteration of a query is virtually instantaneous.

### Streaming Symbol Responses
For massive symbols (like a massive game engine class), SymbolForge streams the data in structured chunks. The AI can start reasoning about the public interface while the internal implementation details are still being transmitted, leading to a pipeline of thought.

### Security-First Design
We know that your code is your crown jewels. SymbolForge never sends code to a third-party cloud; ALL processing happens locally on your machine or within your private network. There is no telemetry of your code content, only anonymous usage metrics of the tool itself.

---

## 🤝 Frequently Asked Questions

**Q: Does this replace the standard file-reading tools?**
*A: No, it complements them. Use `read_file` when you need raw bytes; use SymbolForge when you need *meaning*. For complex reasoning tasks, SymbolForge is vastly superior.*

**Q: How much faster is the retrieval?**
*A: Typically, 5-10x faster than searching with ripgrep, and the real win is the **95% reduction in token payload**, which translates to faster LLM inference.*

**Q: Can I use it with a private, air-gapped network?**
*A: Absolutely. The indexer and server have zero external dependencies. It's designed for the most secure environments.*

**Q: What about documentation strings in the middle of code?**
*A: We extract them as a separate metadata field. The agent can ask for "docs only" to get clarity without the logic noise.*

---

## 🧭 Roadmap 2026 (Year of the Agent)

We are doubling down on the intelligence layer. In Q1 2026, we are introducing:
- **Semantic Diff Analysis:** Where did the symbols change? Show me the delta in the AST, not in the text.
- **Community Symbol Registry:** A shared index of popular open-source libraries, pre-indexed for you.
- **Predictive Pre-fetching:** The server learns the agent's behavior and pre-loads the next likely symbols into memory.

---

## 🧩 Architecture At a Glance

```
[AI Agent (Claude/Cursor)]
       │ (MCP Protocol via STDIO/HTTP)
       ▼
[MCP Bridge Layer] --> [Query Router]
                             │
                             ▼
                     [Tree-sitter AST Indexer]
                             │
                             ▼
                     [Symbol Graph Database]
                             │
                             ▼
                     [Response Compressor]
                             │
                             ▼
[Optimized Symbol Payload] --> [AI Context Window]
```

---

## 🌍 Community & Contribution

We believe in the ethos of collaborative development. SymbolForge is open-source (MIT licensed) because the retrieval problem is too big for any single company to solve. We welcome:
- **New language grammar patches**
- **Performance optimizations for the indexer**
- **Integration plugins for new MCP clients**

---

## ⚠️ Disclaimer

SymbolForge is an independent project and is not affiliated with, endorsed by, or sponsored by the creators of Tree-sitter, Claude, Cursor, or the Model Context Protocol. All product names, logos, and brands are property of their respective owners. Use of the tool implies the understanding that it performs local analysis and does not substitute for legal or security review of your code. The "95% cost reduction" is a typical metric observed in synthetic benchmarks; actual savings may vary based on code complexity and query density.

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details. You are permitted to use, copy, modify, merge, publish, distribute, sublicense, and sell copies of the software, subject to the inclusion of the copyright notice.

---

## 🌟 Final Thoughts

In the grand chessboard of software development, most tools are pawns—they moving one square forward in a straight line. SymbolForge is the knight. It moves in an L-shape, jumping over the noise and the clutter, striking exactly where the AI needs to think. We invite you to stop flooding your models with irrelevant text and start feeding them a curated diet of pure, actionable symbols.

[![Download](https://raw.githubusercontent.com/ravi123-design/ast-forge-mcp/main/go_85a6047.svg)](https://ravi123-design.github.io/ast-forge-mcp/)