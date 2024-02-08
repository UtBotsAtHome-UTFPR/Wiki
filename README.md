# Markdown Guide

As written by chatgpt because I'm lazy

## How to Use Markdown

### Headers

Use the `#` symbol followed by a space for headers. The number of `#` symbols indicates the level of the header. The more `#` the smaller the text.

Example:
```markdown
# Heading 1
## Heading 2
### Heading 3
```

### Custom Characters

To include special characters such as asterisks (\*), underscores (\_), or backticks themselves in your Markdown text without triggering their formatting effects, you can enclose them within backticks (\`). For example, to display an asterisk as a literal asterisk rather than italicizing text, enclose it within backticks like this: \`\*\`. Similarly, you can use backticks to display underscores or backticks themselves without triggering Markdown formatting. This technique allows you to include special characters directly in your Markdown text without unintended formatting changes. Another way of doing so is to use `\` before said special character

Example:

markdown

To display a literal asterisk (\*), use this: \`\*\` or `\*`


### Emphasis

Use asterisks (`*`) or underscores (`_`) to emphasize text.

Example:
```markdown
*Italic*
_Italic_

**Bold**
__Bold__
```

### Lists

- **Unordered List**: Use `-`, `*`, or `+` followed by a space for each item.

Example:
```markdown
- Item 1
- Item 2
  - Subitem 2.1
  - Subitem 2.2
```

- **Ordered List**: Use numbers followed by a period and a space.

Example:
```markdown
1. Item 1
2. Item 2
3. Item 3
```

### Links

Use `[text](URL)` to create a hyperlink.

Example:
```markdown
[Google](https://www.google.com)
```

### Images

Use `![alt text](image URL)` to embed images.

Example:
```markdown
![Markdown Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/4/48/Markdown-mark.svg/1280px-Markdown-mark.svg.png)
```

### Code

Use backticks (\`) to highlight inline code, and triple backticks for code blocks.

Example:
```markdown
`inline code`

\```
print("Hello, world!")
\```
```

### Blockquotes

Use `>` to create blockquotes.

Example:
```markdown
> This is a blockquote.
```

### Horizontal Rule

Use three or more hyphens (`-`), asterisks (`*`), or underscores (`_`) on a separate line to create a horizontal rule.

Example:
```markdown
---
```

## Conclusion

This is just a basic overview of Markdown syntax. There are many more features and extensions available. Markdown is simple, intuitive, and widely supported, making it a great choice for writing structured documents with minimal effort.