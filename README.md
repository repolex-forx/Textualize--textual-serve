# Repolex Knowledge Graph of Textualize/textual-serve

RDF knowledge graph data for [Textualize/textual-serve](https://github.com/Textualize/textual-serve), parsed by [repolex](https://repolex.ai).

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
rlex download Textualize/textual-serve
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── fa5cf5f5b4273c97ed286a55747106701ddc9917
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── fa5cf5f5b4273c97ed286a55747106701ddc9917
│           └── chunk-001.nq.gz
├── blob
│   ├── 03510f2d51369f292a204a4d960473379eca7414.nq.gz
│   ├── 076ca022d2f1a6c346dc207c8dc5c2ca8257ba26.nq.gz
│   ├── 08fecbaf07f041f19fcdec1a786facc1c76ecf77.nq.gz
│   ├── 0dac734008a1b5540634ae854757ec9fb4e3f4b1.nq.gz
│   ├── 1a4d6948d68a5049624d9cd1124041afed10e130.nq.gz
│   ├── 2be5544a5bec02b37b7659701ef1b955653f1814.nq.gz
│   ├── 3481e50e8f71a10883082af7e9955e4d7a5510fb.nq.gz
│   ├── 371cfe355dd3e241cbd73707957e299ddef5bc4c.nq.gz
│   ├── 62b680485d11eaf2f7756f16c99b4677f8c30c86.nq.gz
│   ├── 665718d9b2f98b68f26b06111e0aafb8e9ec7669.nq.gz
│   ├── 79d78514904fe28a52233946a92b35ac439a3f77.nq.gz
│   ├── 7f597dfc60f183798b419b1f5960fc44b430b750.nq.gz
│   ├── 9d5fac207c80bfce14c816d2f7d71531d44f57a7.nq.gz
│   ├── a28d433dabea06224e8e4ceda513ea5e6b28131d.nq.gz
│   ├── acc4e0cd92cfa2c2b8fc2d585668e2f9557bb643.nq.gz
│   ├── b461fb17c179e0aab8b00cf4b617a3135b73683b.nq.gz
│   ├── b991350d7a8f7d3ee8ebc761b7b5ecf2f8688653.nq.gz
│   ├── c85f6d8a1ab82119141e7406bc63a19ed60141ae.nq.gz
│   ├── ce42ad4b573b2200c104bd593b47e7ad384d4ce1.nq.gz
│   ├── df61f714ce6bf49b8815d4576dbf6376d204b09a.nq.gz
│   ├── e0a73538f2e05f31b8f447d856a8e301ff5d1d47.nq.gz
│   ├── e15b007bd7fe38aa607b5afacaa3ec5e62643f5d.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── eb815b7c604cef0b3c53096bbb0c7019ecc19d62.nq.gz
│   └── fc02de43ec4a896bc5eca47399b17bbb47eaca5c.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── fa5cf5f5b4273c97ed286a55747106701ddc9917.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 33 files
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

[Textualize/textual-serve](https://github.com/Textualize/textual-serve)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
