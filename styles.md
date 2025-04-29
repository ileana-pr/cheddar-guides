# 🎨 CheddarGuides Styling Guidelines

<div align="center">
  <i>Guidelines for creating consistent, visually appealing developer documentation</i>
</div>

---

## 📝 Document Structure

Every guide should follow this basic structure:

```markdown
# 🚀 Title of the Guide

<div align="center">
  <i>Brief description of what this guide covers</i>
</div>

---

## 📋 Table of Contents
- [Section One](#section-one)
- [Section Two](#section-two)
- [Section Three](#section-three)

---

## 🔍 Section One

Content...

---

## 🛠️ Section Two

Content...

---

## 💡 Section Three

Content...

---

<div align="center">
  <p><strong>Happy coding!</strong></p>
</div>
```

## 🎯 Visual Elements

### Emojis

Use emojis to enhance section headings and make content more visually appealing:

| Topic | Suggested Emoji |
|-------|----------------|
| Processes | 🔍 |
| Files | 📁 |
| Text | 📝 |
| Network | 🌐 |
| Packages | 📦 |
| Git/Version Control | 🔄 |
| System | 💻 |
| Compression | 🗜️ |
| Docker | 🐳 |
| Environment/Config | 🔧 |
| Users | 👤 |
| Time/Process | ⏱️ |
| Security | 🔒 |
| Tips | 💡 |
| Code | 💻 |
| CLI | 🖥️ |
| Database | 🗃️ |
| Web | 🌍 |
| API | 🔌 |
| Testing | 🧪 |

### Tables

Use tables for organized, scannable content:

```markdown
| Command | Description |
|---------|-------------|
| `command` | What it does |
| `another` | Another description |
```

### Code Blocks

Format code examples consistently:

````markdown
```language
// Code example here
const example = "This is code";
console.log(example);
```
````

### Horizontal Rules

Use horizontal rules (`---`) to separate major sections.

### Text Formatting

- **Bold** for emphasis: `**bold text**`
- *Italic* for secondary emphasis: `*italic text*`
- `Inline code` for commands, variables: `` `code` ``
- > Blockquotes for notable information: `> blockquote`

## 🔗 Linking

### Internal Links

Use anchor links to reference other sections within the document:

```markdown
[Link to Section](#section-name)
```

Note: Section names in anchors should be lowercase with hyphens instead of spaces.

### External Links

Format external links with descriptive text:

```markdown
[Description of the external resource](https://example.com)
```

## 📚 Guide Organization

- Group related commands/concepts together
- Use consistent header levels (h1 for title, h2 for main sections, h3 for subsections)
- Include examples for complex concepts
- Keep individual guides focused on a single topic

## 🌈 Color Guidance

When embedding HTML is supported, consider these color values for consistency:

- Primary Blue: `#3498db`
- Success Green: `#2ecc71`
- Warning Yellow: `#f1c40f`
- Error Red: `#e74c3c`
- Neutral Gray: `#95a5a6`

Example HTML color usage:

```html
<span style="color: #3498db;">Blue text for emphasis</span>
```

---

<div align="center">
  <p><strong>These guidelines will help maintain visual consistency across all CheddarGuides!</strong></p>
</div> 