# How AI Systems Are Built, One Layer at a Time

A single-page, ten-stage visual walkthrough of the AI stack. It starts with one LLM prompt and adds a layer at a time until it reaches a full enterprise reference architecture.

1. LLM for research and drafting
2. Prompt engineering and structured outputs
3. RAG (ingestion, hybrid search, reranking, citations)
4. Tool use, function calling, code sandbox and MCP
5. A single agent (plan, act, observe, memory, stop conditions)
6. Multi-agent systems (orchestrator, workers, shared state, human approval)
7. Evals (golden sets, LLM-as-judge, RAG and agent metrics, CI gates)
8. Guardrails and safety (input, output, action)
9. Observability and LLMOps (traces, versioning, cost, feedback loop)
10. Enterprise reference architecture (layered system view with six data paths)

Each stage has a plain-language explanation, an inline SVG diagram that grows cumulatively (new components are highlighted), a technical stack panel, and a "what can go wrong / why the next layer exists" note.

## What is in this folder

| File | Purpose |
| --- | --- |
| `index.html` | The whole site: HTML, CSS, JS and SVG in one file. No build step, no dependencies, no network calls. |
| `og-image.png` | The 1200x630 preview image shown when the link is shared on LinkedIn, Slack, X and similar. |
| `ai-stack-explained-general.pdf` / `ai-stack-explained-technical.pdf` | Printable versions, linked from the page. |
| `set-url.sh` | One-line script that fills in your GitHub username and repo name (see below). |
| `TESTING.md` | A 30-minute protocol for testing the page with real beginners, plus automated results. |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are. |
| `README.md` | This file. |

Two views: the page opens in **General** view, written for non-technical readers. Each stage is one screen: a one-line meaning with no jargon, what it gives, the main risk, an everyday comparison and a collapsed "A little more detail" section. The **Technical** toggle in the header shows the full explanations, key terms, technology lists and the complete architecture diagram. Dotted-underline words show a short definition on hover or tap. The choice is remembered in the browser.

Interactive features: a **step-through player** (Back, Play/Pause, Next, numbered steps) that builds the diagram up one layer at a time; a **request simulator** in stage 10 with three scenarios (warranty check with human approval, a board summary with an unsupported claim removed, and a suspicious uploaded document) that lights up the parts of the platform doing the work; animated data flow along new arrows; and hover or focus on any diagram box to highlight its connections and show a short explanation. All animation is switched off for visitors who prefer reduced motion.

Also on the page: a running example followed through stages 1 to 9, clickable diagram boxes (keyboard accessible) and a sources section. Features: one-screen overview of all ten stages, sticky stage navigation with a progress bar, light and dark mode (follows the system, with a toggle), keyboard navigable, ARIA labels and text descriptions on every diagram, responsive down to phone width (diagrams scroll sideways on narrow screens).

## Publish on GitHub Pages

Replace `<username>` and `<repo>` with your own values.

### Before you push: set your link

The share preview needs your final address. Run this once (it replaces `YOUR-USERNAME` and `YOUR-REPO` in `index.html`):

```bash
cd ai-stack-explained
bash set-url.sh <username> <repo>
```

On Windows, open `index.html` in any editor and use find and replace instead.

### Option A: command line

```bash
cd ai-stack-explained
git init
git add .
git commit -m "Add AI stack explainer"
git branch -M main
git remote add origin https://github.com/<username>/<repo>.git
git push -u origin main
```

Then in the browser:

1. Open `https://github.com/<username>/<repo>/settings/pages`.
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
3. Choose branch **main** and folder **/ (root)**, then click **Save**.
4. Wait about one minute and refresh the page. The live address appears at the top.

### Option B: GitHub CLI

```bash
cd ai-stack-explained
git init && git add . && git commit -m "Add AI stack explainer" && git branch -M main
gh repo create <repo> --public --source=. --push
gh api -X POST repos/<username>/<repo>/pages -f "source[branch]=main" -f "source[path]=/"
```

### Your shareable link

```
https://<username>.github.io/<repo>/
```

If you name the repository `<username>.github.io`, the link becomes `https://<username>.github.io/`.

To link straight to a stage, add an anchor, for example `https://<username>.github.io/<repo>/#s3` for RAG. Anchors `#s1` to `#s10` map to the ten stages and `#summary` to the recap table.

## Notes

- Contact details point to https://sudharsanbalaji.com (header button, byline, footer and share metadata). The byline, date and version are in the page header and footer; edit them in `index.html`. Add a licence of your choice if you want others to reuse the content.
- Product and framework names are examples of representative technology, not endorsements or a complete list. This field changes quickly, so check current documentation before choosing.
- Private repositories need a GitHub plan that includes Pages for private repos; public repositories work on the free plan.
