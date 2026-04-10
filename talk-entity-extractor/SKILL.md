---
name: talk-entity-extractor
description: Analyze talk transcripts to identify and link entities (people, books, places, etc.) in a structured _meta directory and update site navigation.
---

# Talk Entity Extractor

This skill automates the process of extracting, organizing, and linking entities mentioned in talk transcripts for a Jekyll-based site.

## Workflow

### 1. Entity Extraction
Analyze the transcript to identify the following entity types:
- **People**: Authors, lecturers, historical figures.
- **Works**: Books, talk, paintings, musical pieces.
- **Places**: Countries, cities, specific venues.
- **Organizations**: Projects, foundations, groups, platforms.
- **Concepts**: Significant philosophical or mythological entities.

### 2. Directory Structure
Create or update Markdown files in the `_meta/` directory using this structure:
- `_meta/people/{Name}.md`
- **Works**: `_meta/works/{Author}/{Title}.md`
- `_meta/organizations/{Name}.md`
- `_meta/concepts/{Name}.md`
- **Geographical Entities**: `_meta/places/{Country}/{City-or-Region}/{Entity}.md`

File names should all be snake case.

Each file should contain at least a Level 1 header with the entity's name: `# {Name}`. The language of the header should be of what the language of the talk being analyzed. When an english name is available, it should be added in parenthesis.

Append the entity file with a short snippet from the talk where the entity was mentioned and give a backlink to the paragraph where the entity was mentioned. The link should include the talk title and paragraph number. The text of the snippet should be formatted as a quote.

Each directory and sub-directory under the `_meta` folder should contain an index file with the list of all child folders linking to the corresponding child index file.

### 3. Transcript Linking
Update the talk transcript file to include links to the relevant `_meta` files.
- Use Jekyll syntax: `[Entity Name]({{ site.baseurl }}/path/to/file.md)`
- Ensure links are not duplicated and handle Cyrillic/Latin characters accurately.

### 4. Index Update
Ensure the `index.md` file has an "Дослідник" section that points to the main directories:
- **People**: `[Люди]({{ site.baseurl }}/_meta/people/)`
- **Works**: `[Твори]({{ site.baseurl }}/_meta/works/)`
- **Places**: `[Місця]({{ site.baseurl }}/_meta/places/)`
- **Organizations**: `[Заснування]({{ site.baseurl }}/_meta/organizations/)`
- **Concepts**: `[Поняття]({{ site.baseurl }}/_meta/concepts/)`

## Best Practices
- **Priority**: Link longer entity names first to prevent partial matches.
- **Consistency**: Maintain a uniform naming convention for files (e.g., matching the entity name).
- **Automation**: Use sub-agents for large batch file operations to maintain session efficiency.
- **Interation**: The process should be interactive to avoid making too many mistakes. For every new entity encontered, ask one-by-one whether it's ok to add or update the `_meta` folder, suggest if you think there's already an existing entity to choose from to avoid duplication, or give an option to skip any edits
