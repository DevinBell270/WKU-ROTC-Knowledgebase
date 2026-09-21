# WKU ROTC Knowledgebase

Compiled, agent-maintained wiki for the Western Kentucky University Department of Military Science and Leadership (Hilltopper Army ROTC). Built as a [Karpathy LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f): raw sources stay immutable; the wiki is the layer AI agents read and update.

## Start here

- **[wiki/index.md](wiki/index.md)** — catalog of every compiled page
- **[wiki/overview.md](wiki/overview.md)** — program synthesis
- **[AGENTS.md](AGENTS.md)** — schema, authority ranking, ingest/query/lint workflows

Humans drop sources into `raw/` and ask questions. Agents compile `wiki/`.

## Current override

The 2026–2027 undergraduate catalog still lists LTC Anthony Struzik as department chair. **Lieutenant Colonel David Schnaak** is the Professor of Military Science and department chair. See `[[ltc-david-schnaak]]` and `[[source-conflicts]]`.

## Layout

```
raw/     snapshots of catalog, department site, news, housing, social, recruiting decks, and human corrections
wiki/    compiled entity, program, concept, and analysis pages
```
