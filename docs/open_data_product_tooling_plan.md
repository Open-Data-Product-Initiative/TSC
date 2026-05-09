# AI-First Tooling Plan for the Open Data Product Standards Family

## Purpose

The Open Data Product standards family now includes three specifications and one shared vocabulary:

- Open Data Product Specification, ODPS
- Open Data Product Catalogs, ODPC
- Open Data Product Graphs, ODPG
- Open Data Product Vocabulary, ODPV

Together, these define a broader foundation for data product management. ODPS defines the data product. ODPC defines catalogs and reusable portfolio-level objects. ODPG defines relationships between products, use cases, objectives, KPIs, signals, domains, owners, and dependencies. ODPV defines the shared language used across the standards family.

The next step is tooling.

The tooling should be designed AI-first. The goal is not only to support documentation, validation, and publishing. The goal is to make the standards executable, machine-readable, and useful for AI agents that generate, validate, connect, explain, and improve data product ecosystems.

## Strategic Direction

The tooling should turn the standards family into an operating layer for data product portfolios.

This means the tools should help users move from static metadata files into active portfolio intelligence. Users should be able to create compliant YAML and JSON files, validate them, connect them into graphs, publish them, and ask AI agents questions about the portfolio.

The core idea is simple:

- ODPS makes data products machine-readable.
- ODPC makes catalogs and portfolio objects machine-readable.
- ODPG makes relationships machine-readable.
- ODPV makes meaning machine-readable.

Together, they create the foundation for AI-native data product management.

## Phase 1: Core Tooling MVP

Phase 1 should focus on the minimum set of tools needed to make the standards usable, testable, and demonstrable. The goal is to create a working core that proves the value of the standards family and supports early adoption.

### 1. Validation Core

The first priority is validation. Users need confidence that their ODPS, ODPC, ODPG, and ODPV files follow the expected structure.

The core validator should support:

- ODPS validation
- ODPC validation
- ODPG validation
- ODPV validation
- YAML validation
- JSON validation
- JSON Schema validation
- Required field checks
- ID uniqueness checks
- Broken reference checks
- Basic vocabulary alignment checks

The validator should work as a command-line tool first. This keeps the first implementation simple and makes it easy to use in GitHub Actions, CI pipelines, and local development.

Example commands:

```bash
odp validate product.yaml
odp validate catalog.yaml
odp validate graph.json
odp vocab check product.yaml
```

### 2. AI-Assisted Object Generation

The second priority is generation. Users should not be expected to write all YAML manually.

The MVP should include AI-assisted generation for the most important objects:

- Generate ODPS product YAML from a short description or requirement document
- Generate ODPC catalog YAML from a portfolio description
- Generate ODPC use case objects from text
- Generate ODPC business objective objects from text
- Generate ODPG relationships from existing ODPS and ODPC files
- Suggest ODPV terms based on user input

The first version should focus on assisted generation, not full automation. The user provides text, the tool produces draft YAML or JSON, and the user reviews the output.

Example commands:

```bash
odp generate odps requirements.md
odp generate odpc catalog-description.md
odp generate use-case use-case.md
odp generate graph ./examples/catalog/
```

### 3. Graph Builder

The third priority is graph construction. The value of ODPC and ODPG becomes clearer when relationships can be visualized and queried.

The graph builder should read ODPS, ODPC, and ODPG files and produce a standard graph output.

The MVP should support:

- Reading ODPS product files
- Reading ODPC catalog files
- Reading ODPG relationship files
- Resolving references between objects
- Creating graph.json
- Creating a simple HTML graph viewer
- Showing products, use cases, objectives, KPIs, signals, and relationships

Example commands:

```bash
odp graph build ./examples/mobility-catalog/
odp graph view graph.json
```

### 4. Portfolio Q&A Prototype

The fourth priority is an AI question-answering prototype over the generated graph and source files.

This should allow users to ask practical portfolio questions such as:

- Which products support this business objective?
- Which objectives have no linked data products?
- Which use cases depend on weak or missing products?
- Which signals suggest a need for new data products?
- Which catalog areas have strong coverage?
- Which products are most connected in the portfolio?

The MVP does not need a complex user interface. A command-line or simple local web interface is enough.

Example command:

```bash
odp ask "Which business objectives have weak data product coverage?"
```

### 5. GitHub Actions Support

The core tooling should support automated validation in GitHub.

This helps specification repositories, examples, and adopters maintain quality over time.

Phase 1 should include:

- GitHub Action for validating ODPS files
- GitHub Action for validating ODPC files
- GitHub Action for validating ODPG files
- GitHub Action for checking vocabulary alignment
- Example workflow files
- Clear error messages for failed validation

Example workflow use cases:

- Validate all examples when a pull request is opened
- Prevent broken YAML from being merged
- Detect invalid references
- Detect missing required metadata
- Detect vocabulary terms that do not match ODPV

### Phase 1 Deliverables

Phase 1 should produce a practical open-source toolkit with the following deliverables:

- Open Data Product CLI
- Core validators for ODPS, ODPC, ODPG, and ODPV
- AI-assisted YAML generation prototype
- Graph builder
- graph.json output
- Simple HTML graph viewer
- Portfolio Q&A prototype
- GitHub Actions templates
- Example files for a sample portfolio
- Basic documentation and README

### Phase 1 Success Criteria

Phase 1 is successful when a user can:

- Create or generate ODPS, ODPC, and ODPG files
- Validate the files locally
- Validate the files in GitHub Actions
- Build a graph from the files
- View the graph in HTML
- Ask AI-assisted questions about the portfolio
- Use ODPV terms to improve consistency

## Phase 2: Extended Tooling and Ecosystem Support

Phase 2 should expand the toolkit from core usability into broader ecosystem support. This phase should build on the MVP and add richer user interfaces, stronger AI support, deeper governance checks, and publishing workflows.

### 1. Agent-Native Tooling Layer

Phase 2 should focus on tooling for AI agents, not a traditional human authoring studio.

The main users of the tooling are expected to be AI agents, copilots, automation pipelines, and developer workflows. Humans should still be able to inspect, approve, and correct outputs, but the primary interface should be machine-readable and callable.

The agent-native tooling layer should support:

- Read ODPS product files
- Read ODPC catalog files
- Read ODPG graph files
- Read and search ODPV terms
- Generate draft ODPS, ODPC, and ODPG objects
- Validate generated objects
- Resolve references between files
- Suggest missing relationships
- Suggest vocabulary terms
- Explain validation errors
- Compare current and proposed versions
- Produce human-readable review summaries
- Export compliant YAML, JSON, Markdown, and graph.json

This layer should work through CLI commands, APIs, MCP tools, and automation workflows. A visual interface can be added later for review and inspection, but it should not drive the architecture.

The goal is to make the standards family usable by agents that create, validate, connect, explain, and improve data product ecosystems.

### 2. Specialized AI Agents

Phase 2 should move from simple AI assistance to more specialized agents.

Possible agents include:

- Data Product Steward Agent
- Portfolio Manager Agent
- Governance Reviewer Agent
- Vocabulary Alignment Agent
- Marketplace Publishing Agent
- Graph Analysis Agent

These agents should help users perform structured tasks, such as reviewing a catalog, identifying gaps, preparing governance notes, or suggesting new data products.

### 3. MCP Server

An MCP server should expose the standards family to AI assistants and agent frameworks.

The MCP server should provide tools for:

- Reading ODPS files
- Reading ODPC files
- Reading ODPG files
- Searching ODPV terms
- Validating files
- Building graphs
- Resolving references
- Querying portfolio relationships
- Generating draft objects
- Explaining portfolio structure

This would make the standards family agent-ready and easier to integrate into AI-native workflows.

### 4. Advanced Graph Analytics

Phase 2 should strengthen the graph layer.

Advanced graph features could include:

- Objective coverage analysis
- Use case coverage analysis
- KPI coverage analysis
- Product dependency analysis
- Portfolio gap detection
- Impact analysis
- Critical product identification
- Signal-to-product matching
- Domain-level portfolio heatmaps
- Governance maturity mapping

This is where ODPC and ODPG become more than metadata structures. They become analytical tools for portfolio management.

### 5. Publishing Tools

Phase 2 should support richer publishing workflows.

Publishing tools could include:

- Product page generator
- Catalog page generator
- Graph HTML generator
- Vocabulary browser
- Static documentation site generator
- GitHub Pages templates
- Markdown export
- PDF export
- JSON export
- API documentation export

This helps adopters publish their data product ecosystems in a clear and consistent way.

### 6. Governance and Quality Intelligence

Phase 2 should add deeper semantic and governance checks.

Examples:

- Check whether each product links to a clear business objective
- Check whether each use case has supporting data products
- Check whether objectives have measurable KPIs
- Check whether products have ownership information
- Check whether products have SLA and data quality declarations
- Check whether catalog signals are connected to products or use cases
- Check whether vocabulary usage is consistent
- Detect duplicated or overlapping products
- Detect weak or missing portfolio coverage

This makes the tooling valuable for governance, not only technical validation.

### 7. Integrations

Phase 2 should explore integrations with common platforms and workflows.

Possible integrations:

- GitHub
- GitLab
- Data catalogs
- Open data portals
- CKAN or DKAN-based platforms
- Data marketplaces
- BI platforms
- API gateways
- Metadata repositories
- Local LLM runtimes
- Cloud AI platforms

The integrations should follow the same principle: standards first, vendor-neutral tooling, AI-ready interfaces.

### Phase 2 Deliverables

Phase 2 should produce:

- Web-based authoring studio
- MCP server
- Advanced AI agents
- Advanced graph analytics
- Static site publishing tools
- Governance intelligence checks
- Vocabulary browser
- Integration examples
- Extended documentation
- Reference implementation for a full portfolio

### Phase 2 Success Criteria

Phase 2 is successful when users can:

- Manage data product portfolios through a web interface
- Use AI agents to generate, validate, and improve objects
- Query portfolio relationships through MCP
- Publish catalogs and graphs as documentation sites
- Run semantic governance checks
- Identify gaps and improvement areas in the portfolio
- Integrate the tooling into existing metadata and data platform workflows

## Suggested Product Structure

The tooling should be organized into a small number of clear components.

### Open Data Product CLI

The command-line tool for validation, generation, graph building, and automation.

Possible name:

```bash
odp
```

### Open Data Product Studio

The web-based authoring and review interface.

### Open Data Product MCP Server

The AI agent interface for reading, validating, generating, and querying standards-based content.

### Open Data Product Graph Viewer

The visual tool for exploring portfolio relationships.

### Open Data Product GitHub Actions

Reusable workflows for validation and quality checks.

## Recommended Implementation Order

The recommended order is:

1. CLI structure
2. JSON Schema validation
3. ODPS, ODPC, ODPG, and ODPV validators
4. Reference resolver
5. Sample portfolio files
6. Graph builder
7. HTML graph viewer
8. AI-assisted generation
9. Portfolio Q&A prototype
10. GitHub Actions
11. MCP server
12. Web studio
13. Advanced governance intelligence
14. Publishing tools
15. Integrations

This order keeps the foundation stable before adding user-facing and AI-agent capabilities.

## Positioning Statement

The Open Data Product standards family defines the language for data products, catalogs, graphs, and vocabulary. The tooling makes that language executable. AI makes it usable at scale.

The result is an AI-first foundation for creating, governing, connecting, publishing, and improving data product ecosystems.

