# cypher-shell

Neo4j Cypher Shell skill for AI coding agents. Connect once, query fast, inspect schemas.

Works on **Claude Code, Copilot, Gemini CLI, Codex, Cline** and 30+ more agents.

---

## Step 1: Install cypher-shell

### macOS
```bash
brew install cypher-shell
```

### Linux (Debian/Ubuntu)
```bash
curl -fsSL https://debian.neo4j.com/neotechnology.gpg.key | sudo gpg --dearmor -o /usr/share/keyrings/neo4j.gpg
echo 'deb [signed-by=/usr/share/keyrings/neo4j.gpg] https://debian.neo4j.com stable latest' | sudo tee /etc/apt/sources.list.d/neo4j.list
sudo apt-get update && sudo apt-get install -y cypher-shell
```

### Windows
```powershell
# Download from https://neo4j.com/deployment-center/ (Cypher Shell section)
# Or use Chocolatey:
choco install neo4j-community
# cypher-shell is included in the bin/ folder
```

### Verify
```bash
cypher-shell --version   # should print version
java -version            # needs Java 21+
```

---

## Step 2: Install the skill

```bash
npx skills add octaviopavon/cypher-shell -g -y
```

Done. One command.

---

## Step 3: Open your agent and connect

Open Claude Code (or any supported agent):

```bash
claude
```

Connect to your Neo4j instance:

```
/cypher-shell connect neo4j://localhost:7687
```

It will ask for username and password (defaults: `neo4j` / `neo4j`).

For **Neo4j Aura** (cloud):
```
/cypher-shell connect neo4j+s://xxxx.databases.neo4j.io
```

---

## Step 4: Use it

```
/cypher-shell schema                              # see full graph structure
/cypher-shell schema Person                        # deep-dive a label
/cypher-shell query MATCH (n) RETURN n LIMIT 10    # any Cypher query
/cypher-shell query count                          # quick node/rel counts
/cypher-shell query orphans                        # find disconnected nodes
/cypher-shell query indexes                        # list all indexes
/cypher-shell query constraints                    # list all constraints
/cypher-shell test                                 # verify connection
```

---

## Query Shortcuts

| Command | What it does |
|---------|-------------|
| `query count` | Node and relationship counts by label/type |
| `query orphans` | Disconnected nodes |
| `query indexes` | All indexes |
| `query constraints` | All constraints |
| `query wipe` | Delete all data (asks confirmation first) |

---

## How it Works

1. `connect` saves credentials to `~/.neo4j-connection`
2. All commands source that file — connect once, query forever
3. Uses native cypher-shell env vars (`NEO4J_URI`, `NEO4J_USERNAME`, `NEO4J_PASSWORD`, `NEO4J_DATABASE`)

## License

MIT
