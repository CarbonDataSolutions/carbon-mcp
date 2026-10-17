# Registry republish v1.0.4 (commands for Danie — do not run until GO)

Prereq: this PR is merged to `main`, and you are an owner of the GitHub org **CarbonDataSolutions**.

Install and publish docs: https://modelcontextprotocol.io/registry/quickstart

```bash
# 1) Clone / update
git clone https://github.com/CarbonDataSolutions/carbon-mcp.git
cd carbon-mcp
git checkout main && git pull

# 2) Install the official publisher (once)
# macOS / Linux — pre-built binary (from the quickstart):
curl -L "https://github.com/modelcontextprotocol/registry/releases/latest/download/mcp-publisher_$(uname -s | tr '[:upper:]' '[:lower:]')_$(uname -m | sed 's/x86_64/amd64/;s/aarch64/arm64/').tar.gz" | tar xz mcp-publisher && sudo mv mcp-publisher /usr/local/bin/

# Or with Homebrew:
# brew install mcp-publisher

mcp-publisher --help

# 3) Device login as the org owner (required for io.github.CarbonDataSolutions/*)
mcp-publisher login github

# Follow the device-code prompt in the browser while signed into GitHub as an
# owner of CarbonDataSolutions (not only danie-carbondatasolutions personal).

# 4) Publish from the repo root (reads server.json)
mcp-publisher publish

# 5) Confirm
# Registry entry io.github.CarbonDataSolutions/carbon should show version 1.0.4
# with title carbon.talent and the new ≤100 description.
```

Optional after publish (also needs GO; not done in this PR):
```bash
# GitHub topics (proposed — apply in the GitHub UI or via gh):
gh repo edit CarbonDataSolutions/carbon-mcp \
  --add-topic mcp \
  --add-topic mcp-server \
  --add-topic remote-mcp \
  --add-topic model-context-protocol \
  --add-topic gemini-cli-extension \
  --add-topic hiring \
  --add-topic recruiting \
  --add-topic data-engineering \
  --add-topic ai-talent

# Release tag (proposed — create after merge):
git tag -a v1.0.4 -m "carbon.talent MCP connector v1.0.4"
git push origin v1.0.4
gh release create v1.0.4 --title "v1.0.4" --notes "Directory kit: gemini-extension, Cursor plugin, skill, registry description."
```

DNS domain namespace `com.carbondatasolutions/carbon` is **out of scope** here (needs a DNS TXT GO).
