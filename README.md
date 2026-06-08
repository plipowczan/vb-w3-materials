# Materiały — AI Startup Builders #2, Week 3 (MVP & vibe coding)

Komplet materiałów z mojego modułu W3. Wszystko do **czytania** w jednym miejscu. Tu **nie budujesz** — do buildu jest osobny szablon (niżej).

## Co tu jest

| Plik | Co to |
|---|---|
| **[PLAYBOOK.md](./PLAYBOOK.md)** | Pełny playbook 7-dniowego MVP: Fazy 0–5, anty-wzorce, realne czasy z pilotażu. Główny dokument. |
| **[prompts/](./prompts)** | 4 prompty do wklejenia (Lovable / v0 / dowolny czat): `01-brand` → `02-prd` → `03-reguly` → `04-milestones`. Kolejność obowiązkowa. |
| **[slides/](./slides)** | Prezentacja ze Spotkania 1 (PDF + HTML, bez notatek mówcy). |

## 🛠️ Build — osobny szablon repo

Do budowy MVP używasz **szablonu build** (czysty scaffold + komendy):
👉 **https://github.com/plipowczan/vb-mvp-template** — klikasz *Use this template*.

- **Track Tech** (Claude Code): *Use this template*, komendy `/brand` `/prd` `/reguly` `/milestones` od razu działają.
- **Track Builder** (Lovable/v0): kopiujesz prompty z [`prompts/`](./prompts) tutaj do narzędzia. Szablon możesz użyć opcjonalnie jako magazyn kontekstu.

## 🔗 Narzędzia i materiały omawiane na spotkaniu

**Stack:**
- [Lovable](https://lovable.dev) · [v0](https://v0.dev) — Track Builder
- [Claude Code](https://claude.com/claude-code) — Track Tech
- [Supabase](https://supabase.com) (baza, gdy potrzebna) · [Vercel](https://vercel.com) (deploy)

**Skille / narzędzia agentowe:**
- **impeccable** — skill designowy, który tępi „AI-design tells" (Inter wszędzie, fioletowe gradienty, karty w kartach): [github.com/pbakaus/impeccable](https://github.com/pbakaus/impeccable). Instalacja: `npx impeccable skills install` lub `/plugin marketplace add pbakaus/impeccable`.
- **shared-skills** — skille `prd` i `/prepare-goal` (Track Tech): [github.com/200iqlabs/shared-skills](https://github.com/200iqlabs/shared-skills).
- **OpenSpec / opsx** — spec-driven development, gdy projekt rośnie poza MVP: [github.com/Fission-AI/OpenSpec](https://github.com/Fission-AI/OpenSpec). Workflow `/opsx:*`.

## Kolejność pracy (skrót)

```
brand.md  →  prd.md  →  reguły projektu  →  milestones (goals.md)  →  build  →  deploy
   01          02            03                   04
```

Każdy krok konsumuje poprzedni. Pełny opis: [PLAYBOOK.md](./PLAYBOOK.md).

---

_Pytania → grupa programu. Bloker > 30 min = pisz._
