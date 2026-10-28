# Repolex Knowledge Graph of dask/dask-pyspy

RDF knowledge graph data for [dask/dask-pyspy](https://github.com/dask/dask-pyspy), parsed by [repolex](https://repolex.ai).

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
rlex download dask/dask-pyspy
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── e75b2377ea267bb20ac3b163f128a54c40d9f0c3
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── e75b2377ea267bb20ac3b163f128a54c40d9f0c3
│           └── chunk-001.nq.gz
├── blob
│   ├── 07f2f7986f07e33ddb3be28f2c3a3503fc4bd9ca.nq.gz
│   ├── 1933f7099beb10dd7e94bd0321e292503dae372e.nq.gz
│   ├── 3c8e723e37ac266e2ac2041222fb13f924b6c56a.nq.gz
│   ├── 754fb8b2860a8c04e5081be99aacac41d3bee1d5.nq.gz
│   ├── 786e5658ffd3c9cb563b44af4bd26c2f422460e8.nq.gz
│   ├── 8332de349fb740af44a3de304dba51d670ff609e.nq.gz
│   ├── 89e00acc0d13a526a29d24f8af9949ab38ec32e7.nq.gz
│   ├── a87319006a7dadd79fc0922108d0abd6a2002013.nq.gz
│   ├── b324f1dc0a6af24c842a098f4ecd0cd598a4447a.nq.gz
│   ├── bf8ce24753c3488646816459d4e99bd89388b531.nq.gz
│   ├── e58bbfccae963834c7f895f780f74b00416e4ab9.nq.gz
│   ├── ed5cdada8ea154535f3feb01a53a5caada55aa04.nq.gz
│   └── fdbd759157975b50bcad9075b4978791e837d78a.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── e75b2377ea267bb20ac3b163f128a54c40d9f0c3.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 21 files
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

[dask/dask-pyspy](https://github.com/dask/dask-pyspy)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
