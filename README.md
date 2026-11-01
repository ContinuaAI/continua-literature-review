# Continua Literature Review

Literature review skills for **researchers, PhD students, R&D and medical affairs teams, and policy analysts**, built on Continua Project Rooms.

Put your papers in a Project Room once. Continua compiles each PDF to line-numbered text and reads every paper with up to **1B tokens of working context**, so screening decisions, extracted numbers, and synthesized claims all cite the paper and page they came from. Protocols, decision logs, evidence tables, and drafts are versioned files with recoverable history, which keeps a review auditable and easy to update.

## Requirements

This plugin depends on the **Continua Project Room** MCP server and requires a Continua account. Access and usage follow your account permissions and plan.

```text
https://app.askcontinua.com/mcp?subset=mini
```

The plugin declares this server in [`.mcp.json`](.mcp.json) (Streamable HTTP with OAuth), so installing the plugin adds the connection:

1. Install the plugin. In Claude Code:

   ```text
   /plugin marketplace add ContinuaAI/continua-literature-review
   /plugin install continua-literature-review@continua-literature-review
   ```

2. Sign in to **Continua Project Room**: in Claude, **Settings → Connectors**; in Claude Code, run `/mcp` and select `continua-project-room`. Users who already added Continua Project Room from the [Claude directory](https://claude.ai/directory/continua) are connected to the same server.

The skills call these Continua Project Room tools: `list_project_rooms`, `get_project_room`, `create_project_room`, `upload_project_files`, `search_project_room`, `read_project_file`, `research_project_room`, `get_project_research`, `list_project_file_history`, `restore_project_file`.

The skills work on papers you supply (PDFs and reference exports such as RIS, BibTeX, or CSV from PubMed, Scopus, Web of Science, Google Scholar, or a reference manager). They do not search bibliographic databases.

## Skills

| Skill | Use it for | What you get |
| --- | --- | --- |
| [`/continua-literature-review:lit-screening`](skills/lit-screening/SKILL.md) | Systematic, scoping, and rapid reviews | Protocol, deduplication, title/abstract and full-text decisions with reasons, PRISMA 2020 flow counts |
| [`/continua-literature-review:evidence-table`](skills/evidence-table/SKILL.md) | Data extraction | Evidence table with every value cited to its page, flagged inconsistencies, meta-analysis input sheet |
| [`/continua-literature-review:evidence-synthesis`](skills/evidence-synthesis/SKILL.md) | Review drafts, related work, gap analysis | Cited narrative synthesis: themes, agreement and disagreement, certainty, research gaps |
| [`/continua-literature-review:claim-check`](skills/claim-check/SKILL.md) | Manuscripts, theses, grants before submission | Every claim checked against its cited paper: supported, overstated, misattributed, or unsupported, with source quotes and fixes |
| [`/continua-literature-review:living-review`](skills/living-review/SKILL.md) | Keeping a review current | New papers screened with the same protocol and a "what changed" report against the last update |

## Example requests

- "Set up a systematic review on exercise for depression in adults over 65 and screen these 800 abstracts."
- "Extract sample sizes, effect sizes, and risk of bias from the 34 included trials."
- "Write the related work section for my paper on retrieval-augmented generation, using the papers in this Room."
- "Check every citation in my thesis chapter 2 against the PDFs."
- "Here are this quarter's new papers; has anything changed the conclusion?"

## Layout

```text
continua-literature-review/
├── .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json
├── .mcp.json              # Continua Project Room MCP (subset=mini)
├── skills/
│   ├── lit-screening/SKILL.md
│   ├── evidence-table/SKILL.md
│   ├── evidence-synthesis/SKILL.md
│   ├── claim-check/SKILL.md
│   └── living-review/SKILL.md
├── .gitignore
├── LICENSE
└── README.md
```

## Local development

```bash
claude --plugin-dir .
claude plugin validate .
```

## Support and policies

- Product and documentation: [Continua Project Room](https://askcontinua.com/project-room) · [Help Center](https://askcontinua.com/help#projects)
- Support: [askcontinua.com/help](https://askcontinua.com/help)
- [Privacy policy](https://app.askcontinua.com/privacy-policy) · [Terms of service](https://app.askcontinua.com/terms-of-service) · [Trust & Security](https://askcontinua.com/trust)

Outputs support researchers and do not replace their judgment. Systematic reviews normally require independent human screening and extraction; review cited evidence before relying on any result. Respect publisher licences when uploading full texts.

[Continua AI](https://askcontinua.com)
