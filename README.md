# Repolex Knowledge Graph of simonw/llm-echo

RDF knowledge graph data for [simonw/llm-echo](https://github.com/simonw/llm-echo), parsed by [repolex](https://repolex.ai).

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
rlex download simonw/llm-echo
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 83783687993a52b307c94e9db33a850bb50d0a37
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 83783687993a52b307c94e9db33a850bb50d0a37
│           └── chunk-001.nq.gz
├── blob
│   ├── 214b1aac2adfd73108cd47ddc48f991cbc6771c2.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 61e1ff47a6ad081ca4b83aed4bcb0fc78184020d.nq.gz
│   ├── 6988965c0fff6d9070362cebbff657ddd203f62a.nq.gz
│   ├── 8eec563a4a6ad7ef438cbe23da0ce57413317943.nq.gz
│   ├── a228f9aabc26d4872e905346c763601746b6304f.nq.gz
│   ├── cc2ed04137813fe252e161e2cef7f88d6195ab10.nq.gz
│   └── d0d5ce3ee8fa6494d61b4f902ee7d8de943e1b36.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 83783687993a52b307c94e9db33a850bb50d0a37.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 16 files
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

[simonw/llm-echo](https://github.com/simonw/llm-echo)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
