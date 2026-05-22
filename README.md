# SkillForge — Modular AI Marketplace Platform

![Version](https://img.shields.io/badge/version-1.0.0-7F77DD?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-1D9E75?style=flat-square)
![Status](https://img.shields.io/badge/status-active-1D9E75?style=flat-square)
![Built With](https://img.shields.io/badge/built%20with-HTML%20%7C%20CSS%20%7C%20JavaScript-378ADD?style=flat-square)

> A modular marketplace where developers publish specialized AI Skills and Intents — and users install them to extend their AI assistant for any domain.

---

## What is SkillForge?

SkillForge is a modular marketplace platform where developers can publish, discover, and install specialized AI **Skills** and **Intents** — purpose-built plugins that extend an AI assistant's capabilities for specific domains like medical research, financial tracking, legal analysis, code security, and more.

Users browse a curated storefront of Skills organized by category, rating, and pricing. Developers list and monetize their own domain expertise as installable plugins — no infrastructure needed.

---

## Features

### For Users
- **Skill & Intent marketplace** — browse 40+ skills across Medical, Finance, Code, Data, Legal, and Design categories
- **Live search & filtering** — filter by category, price tier, or keyword in real time
- **Detail panels** — per-skill pages with star rating breakdowns, user reviews, install counts, and changelogs
- **Bundle packs** — curated multi-skill bundles at discounted prices (e.g. Medical Suite, Dev Essentials)
- **Premium theme store** — 8+ UI skins with real-time preview and one-click activation
- **Personal library** — manage all installed skills from a single dashboard

### For Developers
- **Publish portal** — list and monetize skills with pricing tiers (free, one-time, subscription)
- **Category tagging** — tag skills by domain, use case, and compatible platforms
- **Analytics dashboard** — track installs, ratings, and revenue
- **Bundle creation** — group your skills into discounted packs

---

## Project Structure

```
skillforge/
├── index.html              # Main entry point
├── assets/
│   ├── css/
│   │   ├── main.css        # Core styles and design tokens
│   │   └── themes/         # Premium theme skin files
│   │       ├── midnight.css
│   │       ├── solar.css
│   │       ├── forest.css
│   │       └── ...
│   └── js/
│       ├── marketplace.js  # Skill browsing, filtering, search
│       ├── themes.js       # Theme switching logic
│       ├── panel.js        # Skill detail panel
│       └── api.js          # Anthropic API integration
├── pages/
│   ├── browse.html         # Main skills storefront
│   ├── bundles.html        # Bundle packs page
│   ├── themes.html         # Theme store
│   ├── library.html        # Installed skills / user library
│   └── publish.html        # Developer publish portal
├── data/
│   ├── skills.json         # Skills catalog (mock / seed data)
│   ├── themes.json         # Theme metadata
│   └── bundles.json        # Bundle definitions
└── README.md
```

---

## Getting Started

### Prerequisites

- A modern browser (Chrome, Firefox, Safari, Edge)
- Node.js `v18+` (optional, for local dev server)
- An [Anthropic API key](https://console.anthropic.com/) (required for AI-powered features)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/your-username/skillforge.git
cd skillforge

# 2. Install dependencies (if using Node)
npm install

# 3. Add your API key
cp .env.example .env
# Edit .env and set: ANTHROPIC_API_KEY=your_key_here

# 4. Start the dev server
npm run dev
```

Or open `index.html` directly in your browser for a static preview (no API features).

### Deploy to GitHub Pages

```bash
# Build for production
npm run build

# Push to gh-pages branch
npm run deploy
```

Then enable GitHub Pages in your repo settings → Pages → Source: `gh-pages` branch.

Your site will be live at: `https://your-username.github.io/skillforge`

---

## Skill Categories

| Category | Description | Example Skills |
|----------|-------------|----------------|
| 🩺 Medical | Clinical research, notes, diagnostics | MedResearch Pro, ClinicalNotes |
| 📈 Finance | Portfolio tracking, tax, market data | PortfolioIQ, TaxIntent |
| 💻 Code | Security, APIs, testing, DevOps | CodeGuardian, APIWeaver |
| 📊 Data | SQL, visualization, anomaly detection | DataSculpt |
| ⚖️ Legal | Contracts, jurisdiction, precedent | LexAI |
| 🎨 Design | Tokens, specs, accessibility audits | DesignBrief |

---

## API Integration

SkillForge uses the Anthropic API to power skill execution. API calls are made server-side — never expose your key in frontend code.

```javascript
// Example: calling a skill via the Anthropic API
const response = await fetch("https://api.anthropic.com/v1/messages", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    // API key is injected server-side only
  },
  body: JSON.stringify({
    model: "claude-sonnet-4-20250514",
    max_tokens: 1000,
    system: skillSystemPrompt,   // loaded from installed skill definition
    messages: [{ role: "user", content: userInput }]
  })
});
```

Each installed skill ships with a `skill.json` definition:

```json
{
  "id": "medresearch-pro",
  "name": "MedResearch Pro",
  "version": "2.1.0",
  "author": "HealthAI Labs",
  "category": "medical",
  "price": { "type": "subscription", "amount": 9, "currency": "USD" },
  "systemPrompt": "You are a medical research assistant...",
  "tags": ["PubMed", "FDA", "Clinical Trials"]
}
```

---

## Themes

SkillForge ships with 8 UI themes beyond the default. Premium themes are available in the marketplace.

| Theme | Type | Preview |
|-------|------|---------|
| Default | Free | Purple + teal |
| Midnight | Premium ($4) | Deep navy |
| Solar | Premium ($4) | Warm amber |
| Forest | Premium ($4) | Earthy green |
| Rose | Premium ($4) | Soft pink |
| Arctic | Premium ($3) | Cool blue |
| Neon Dusk | Community ($2) | Deep violet |
| Terracotta | Community ($2) | Warm coral |

---

## Roadmap

- [ ] Developer analytics dashboard
- [ ] Skill versioning and auto-update
- [ ] OAuth login and user accounts
- [ ] Stripe integration for paid skills
- [ ] Skill review and moderation system
- [ ] CLI tool for publishing skills
- [ ] Mobile app (iOS / Android)
- [ ] Multi-language support

---

## Contributing

Contributions are welcome! To add a new skill to the catalog:

1. Fork this repository
2. Add your skill definition to `data/skills.json`
3. Follow the [skill schema](docs/skill-schema.md)
4. Open a pull request with a short description

Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## Acknowledgements

- Built with the [Anthropic API](https://www.anthropic.com)
- Icons by [Tabler Icons](https://tabler.io/icons)
- Inspired by the VS Code Extensions Marketplace and npm registry

---

<p align="center">Made with ♥ by the SkillForge team</p>
