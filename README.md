# cypher-shell

Neo4j Cypher Shell skill for [Claude Code](https://claude.com/claude-code). Connect once, query fast, inspect schemas.

## Install

```bash
npx skills add octaviopavon/cypher-shell
```

## Usage

```bash
/cypher-shell connect neo4j://localhost:7687   # connect to instance
/cypher-shell query MATCH (n) RETURN n LIMIT 5 # run any Cypher
/cypher-shell query count                       # node/rel counts
/cypher-shell schema                            # full graph schema
/cypher-shell schema Function                   # deep-dive a label
/cypher-shell test                              # test connection
/cypher-shell install                           # show install instructions
```

## Quick Start

```bash
# 1. Install the skill
npx skills add octaviopavon/cypher-shell

# 2. Open Claude Code
claude

# 3. Connect to your Neo4j instance
/cypher-shell connect neo4j://localhost:7687

# 4. Explore your graph
/cypher-shell schema

# 5. Run queries
/cypher-shell query MATCH (n) RETURN labels(n), count(n) ORDER BY count(n) DESC
```

## Prerequisites

- [cypher-shell](https://neo4j.com/docs/operations-manual/current/tools/cypher-shell/) installed (`brew install cypher-shell`)
- Java 21+ (`java -version`)
- A running Neo4j instance

## Query Shortcuts

| Shortcut | What it runs |
|----------|-------------|
| `query count` | Node and relationship counts by label/type |
| `query orphans` | Disconnected nodes |
| `query indexes` | All indexes |
| `query constraints` | All constraints |
| `query wipe` | Delete all data (with confirmation) |

## How it Works

1. `connect` saves credentials to `~/.neo4j-connection`
2. All other commands source that file before running
3. Uses native cypher-shell env vars: `NEO4J_URI`, `NEO4J_USERNAME`, `NEO4J_PASSWORD`, `NEO4J_DATABASE`

## License

MIT
