# lectures

A collection of lecture transcripts and metadata.

## Skills

### lecture-entity-extractor
This skill automates the extraction, organization, and linking of entities (people, books, places, etc.) from lecture transcripts.

**Trigger Prompt:**
> "Analyze the lecture transcript in the md file and list all mentioned entities, grouped by type. For every entity identified, create (or find an existing) an md file in the \"_meta\" directory. The structure of the _meta directory should be \"_meta/{entity-type}/{entity-name}\". Geographical entities should be nested like this: \"_meta/places/{country}/{city-or-region}/{entity}\". Update the lecture file with links to entity entries. Update the index file to point to the tree of entities."

To install this skill:
```bash
gemini skills install lecture-entity-extractor.skill --scope workspace
```
After installation, run `/skills reload` in your interactive session.
