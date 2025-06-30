# Contributing to the S1 Modding Wiki

Thank you for your interest in contributing to the S1 Modding Wiki! This document outlines the guidelines and best practices for contributing to the wiki. By following these guidelines, you help ensure the wiki remains a valuable resource for modders.

## How to Contribute

1. **Fork the Repository**: Fork the repository to your own GitHub account. This lets you make changes without affecting the main repository.
2. **Clone the Repository**: Clone your forked repository to your local machine using `git clone --recurse-submodules <your-fork-url>`.
3. **Create a Branch**: Create a new branch for your changes with `git checkout -b <branch-name>`. Use a descriptive name that reflects your changes (e.g., `add-new-mod-guide`).
4. **Make Changes**: Modify the wiki content. This includes adding new pages, updating existing content, fixing typos, or improving formatting.
5. **Commit and Push**: Commit your changes with a clear, concise message using `git commit -m "Your commit message"`, then push to your fork with `git push origin <branch-name>`.
6. **Create a Pull Request**: Go to the original repository on GitHub and open a pull request (PR) from your branch. Provide a clear description of the changes and their purpose to help reviewers understand and evaluate your contribution.

## Guidelines for Contributions

The S1 Modding Wiki uses [Hugo](https://gohugo.io/) for static site generation, [Lotus Docs](https://lotusdocs.dev/) as a template, and [Markdown](https://www.markdownguide.org/) for formatting.

Please follow these guidelines:

- Ensure your content is relevant to modding Schedule I and follows the existing wiki structure.
- Provide tested, functional code snippets where appropriate.
- Use clear and concise language.

### Content Structure

Each page must begin with a front matter section enclosed in `---` lines. It should include:

- `weight`: Determines the order of the page in navigation; lower numbers appear first.
- `title`: The title of the page.
- `description`: A brief summary of the content.
- `icon`: An icon name from the [Material Icons](https://fonts.google.com/icons) library.
- `date`: The page's creation or last modification date.
- `lastmod`: The last modification date.
- `draft`: Set to `true` if the page is a work in progress; otherwise, `false`.
- `toc`: Set to `true` to enable a table of contents.

This front matter can be generated with the Hugo CLI, e.g.:
```bash
hugo new content/docs/moddevs/new_page.md
```

The documentation is divided into `moddevs` and `modusers` sections. Place your content in the appropriate directory.

* The first page in `modusers` has a `weight` of `11100`.
* The first page in `moddevs` has a `weight` of `22200`.

Pages are sorted by their `weight`. Use unique values (preferably multiples of 100) to allow space for inserting pages later without renumbering.

Check existing pages for examples of proper `weight` usage.

For more on front matter, see the [Hugo documentation](https://gohugo.io/content-management/front-matter/).

### Content Formatting

- Use [Markdown](https://www.markdownguide.org/) for formatting.
- Use headings (`#`, `##`, `###`, etc.) to structure content.
- Use fenced code blocks with language identifiers for syntax highlighting (e.g., \`\`\`csharp\` for C#).
- Use bullet or numbered lists for clarity.
- Link to other wiki pages or external resources as needed.

#### Images

To include images that are specific to a page, use leaf bundles:

```bash
content-name/
├── index.md
└── image.png
```

Create the bundle using Hugo CLI:

```bash
hugo new content/docs/<moddevs|modusers>/<content-name>/index.md
```

Reference images in content using:

```markdown
{{< figure src="image.png" alt="alt text" >}}
```

### Alerts and Callouts

Use the `alert` shortcode to add styled notification boxes in your content.

#### Basic usage:

```markdown
{{< alert context="info" >}}
This is an informational message.
{{< /alert >}}
```

#### Context options:

* `info`
* `warning`
* `success`
* `danger`
* `default`
* `primary`

Each context changes the color and icon.

#### Example variations:

```markdown
{{< alert context="warning" >}}
Be careful when editing these files.
{{< /alert >}}

{{< alert context="success" >}}
All tasks completed!
{{< /alert >}}

{{< alert context="danger" text="Critical error occurred!" >}}
```

If you use `text=`, it overrides the body. Otherwise, the content between `{{< /alert >}}` is used.

> If neither `text` nor body content is provided, it will error.
> When using `alert`s, ensure you do not have Markdown formatting inside the alert body, as it will not render correctly. Use HTML tags if you need formatting inside an alert.

---

### Checking Your Changes

To preview your edits locally, run:

```bash
hugo server -D
```

Open your browser to `http://localhost:1313` to view the site.

Note:

- Changes to `data/landing.yml` may require restarting the server.
- Markdown files in `content/docs/` are hot-reloaded on save.
