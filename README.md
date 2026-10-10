# Repolex Knowledge Graph of oven-sh/style-guide

RDF knowledge graph data for [oven-sh/style-guide](https://github.com/oven-sh/style-guide), parsed by [repolex](https://repolex.ai).

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
rlex download oven-sh/style-guide
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 26252c373df66e5d53b5239e4d67b5bc0a6ee8f1
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 26252c373df66e5d53b5239e4d67b5bc0a6ee8f1
│           └── chunk-001.nq.gz
├── blob
│   ├── 0f6c693a71c41e995f11cdb685b192993bc81965.nq.gz
│   ├── 14f7aa14755fad46558ca6c3a52cf87bb10d3a86.nq.gz
│   ├── 19df1311b9aac7682dd4691bde8106360aa924d3.nq.gz
│   ├── 43ed72ffc9ff9f341e9e06087d3c868cd24c27a9.nq.gz
│   ├── 61443ffa5ccf3450813312553d5feca8953bd38e.nq.gz
│   └── a4df5b865363a948493f3d4acd6a9f5455b8266a.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 26252c373df66e5d53b5239e4d67b5bc0a6ee8f1.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 12 files
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

[oven-sh/style-guide](https://github.com/oven-sh/style-guide)

---
*Parsed on 2026-10-10 by [repolex](https://repolex.ai)*
