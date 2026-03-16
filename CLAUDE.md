# vibecoded.pro

Curated community answers for vibecoding questions. Hugo + Vercel, dark monospace theme.

## Stack

- **SSG**: Hugo (no theme, inline styles in baseof.html)
- **Deploy**: Vercel (auto-deploy on push to main)
- **Font**: Fira Code
- **Accent**: #22C55E (green)

## Content Model

Curated discussion pages live in `content/q/`. Each page = one strong thread from @vibecod3rs Telegram community.

### Frontmatter fields

| Field | Required | Description |
|-------|----------|-------------|
| `title` | yes | SEO-title, question formulation |
| `description` | yes | 1-2 sentences, meta description |
| `short_answer` | yes | 2-3 sentences, featured snippet target |
| `tags` | yes | e.g. ["claude-code", "cursor"] |
| `categories` | yes | e.g. ["инструменты"] |
| `opinions_count` | yes | Number of opinions in the thread |
| `has_code` | yes | Boolean, code examples present |
| `difficulty` | yes | "начинающий" / "средний" / "продвинутый" |
| `question` | no | Original question from chat (verbatim) |
| `thread_url` | no | Link to original Telegram thread |

### Creating new pages

```sh
hugo new q/slug-name.md
```

## Architecture

| Path | Purpose |
|------|---------|
| `layouts/_default/baseof.html` | Base template with all CSS (inline) |
| `layouts/q/single.html` | Curated discussion page layout |
| `layouts/q/list.html` | Question index |
| `layouts/partials/seo.html` | OG, Twitter, JSON-LD (DiscussionForumPosting) |
| `layouts/partials/footer.html` | Cross-site links |
| `layouts/partials/card.html` | Reusable question card |
| `content/q/` | Curated pages (markdown) |
| `static/robots.txt` | AI-friendly robots.txt |
| `_archive/` | Old prototype files |

## SEO

- JSON-LD: DiscussionForumPosting for /q/ pages, WebSite for homepage
- sitemap.xml auto-generated
- robots.txt allows all crawlers including AI bots
- Git-based lastmod via enableGitInfo

## Cross-site links (footer)

sereja.tech, context.lat, vibecoding.phd, @vibecod3rs, @ris_ai
