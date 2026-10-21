# Repolex Knowledge Graph of glue-viz/glue-vaex

RDF knowledge graph data for [glue-viz/glue-vaex](https://github.com/glue-viz/glue-vaex), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download glue-viz/glue-vaex
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 6451a93419bfed28346b6dd0cfe5de11f22380b3
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 6451a93419bfed28346b6dd0cfe5de11f22380b3
│           └── chunk-001.nq.gz
├── blob
│   ├── 0f42bc57ca444400830ed228c2a64a00d454674d.nq.gz
│   ├── 2c4fc82ccf1332a085e4c73ec99da29bbd221d09.nq.gz
│   ├── 6853c367b2591ed0b8415b0bc1b3a9feec44e50b.nq.gz
│   ├── 8ae0f66bb52e5dd338f8859f14f512500be74236.nq.gz
│   ├── 993bb51da42a95cf087081679b395c31c8320f7d.nq.gz
│   ├── 9d5d250d095009403f66851f48866f5cfe39703b.nq.gz
│   ├── a40dba2f81f19ff4f5c41f4fdc92f64302c6452e.nq.gz
│   ├── bcbbe69adf7afff64550994695792ba292e766bf.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── fb46bc2c88da2c26f4397536df34efe4726e8277.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 6451a93419bfed28346b6dd0cfe5de11f22380b3.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 16 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[glue-viz/glue-vaex](https://github.com/glue-viz/glue-vaex)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
