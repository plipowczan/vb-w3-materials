# Week 3 — od PRD do działającego MVP. Podsumowanie + instrukcja samodzielnego przejścia

> **Dla:** kohorta AI Startup Builders #2 · **Moduł:** MVP & vibe coding (Paweł)
> **Spotkania:** poniedziałek 08.06 (teoria + demo) i środa 10.06 (praktyka / live build)
> **Przykład przewodni:** ClearTable PL — cap table dla polskiej sp. z o.o. (dane z W1 Bartka + W2 Damiana)

Na obu spotkaniach przeszliśmy ten sam łańcuch — od artefaktów z W1/W2 do działającej aplikacji pod publicznym linkiem — **na dwóch ścieżkach równolegle**. Poniżej masz: co dokładnie zrobiliśmy (ze znacznikami czasu z nagrań), co faktycznie powstało, **czego na żywo zabrakło lub się wysypało** (z uzupełnieniem), i **instrukcję, żeby przejść to samemu** krok po kroku.

---

## Linki referencyjne (oba tracki, ClearTable)

| | Repozytorium | Wersja live |
|---|---|---|
| **Track Builder (Lovable)** | https://github.com/plipowczan/cleartable-blank-canvas | https://clear-table-start.lovable.app/login |
| **Track Tech (Claude Code)** | https://github.com/plipowczan/cleartable-demo | https://cleartable-demo.vercel.app/ |
| **Szablon startowy (oba tracki)** | https://github.com/plipowczan/vb-mvp-template — *Use this template* | — |

> 🎥 **Nagrania obu spotkań** (z hasłami) — w zamkniętym Skool kohorty: https://www.skool.com/ai-startup-builders-2-6756/classroom/05ac1dc0?md=3659342d97154d76b8a2fd9c9570b683
>
> Znaczniki w tekście typu **[S1 · 24:30]** = Spotkanie 1, ~24 min 30 s od początku nagrania (czasy przybliżone). **[S2 · …]** = Spotkanie 2. Zoom pozwala przewinąć do znacznika ręcznie.

---

## Część 1 — Co przeszliśmy na Spotkaniu 1 (teoria + demo)

### 1.1 Po co PRD i mapa tygodnia [S1 · ~08:00–18:00]
- **Cel W3:** zbudować coś, co da się **udostępnić użytkownikom** pod publicznym URL-em, żeby w **W4 (Wojtek)** zebrać feedback i analitykę.
- **Mapa tygodnia (Fazy 0–5):** Input lock + `brand.md` → `prd.md` → reguły projektu → milestones → build → deploy.
- **Brand powstaje PRZED PRD** — ukierunkowany pod konkretną grupę odbiorczą (kolory, typografia pod target).

### 1.2 Anatomia PRD [S1 · ~20:00–24:00]
Omówione sekcje: problem-solution fit + value proposition + ICP/persona (z W1/W2), data model (co zapisujemy w bazie), branding, braki danych / pytania otwarte, **kryteria walidacji**, biblioteka komponentów.

### 1.3 Dlaczego PRD przed jakąkolwiek linią kodu [S1 · ~24:00–30:00]
- PRD = **jedyne źródło prawdy** (single source of truth). Kontekst dla agenta w każdej nowej sesji → nie zmyśla, nie halucynuje, idzie najkrótszą drogą.
- **Pamięć projektu.** Okno kontekstowe ma ~**200 000 tokenów** (modele Sonnet 4.x: do **1M** w trybie rozszerzonym); powyżej **50–60%** zapełnienia jakość pracy agenta spada. PRD pozwala odtworzyć kontekst w świeżej sesji.
- Kryteria walidacji + liczba iteracji → komenda **/goal** (Claude Code / Codex): agent iteruje, aż kryteria są spełnione.

### 1.4 Test GIGO — dlaczego dane z W1/W2 mają znaczenie [S1 · ~29:00–32:00]
Porównaliśmy PRD wygenerowany z **realnych danych** (wywiady Bartka/Damiana, ClearTable) z PRD z **jednego zdania opisu** (podejście generyczne). Wersja generyczna zgaduje value proposition i **wycina Core Flow z deklarowanym WTP** (udostępnianie linka inwestorowi). Wniosek: *garbage in → garbage out*. Im lepszy input z W1/W2, tym lepszy MVP.

### 1.5 Demo szablonu repo [S1 · ~32:00–41:00]
- Szablon (`vb-mvp-template`) daje **dwa puste katalogi** `context/w1/` i `context/w2/`. Wypełniasz je swoimi artefaktami z poprzednich tygodni (może być 1 plik w każdym — nie musi być rozbicia).
- W repo cały **playbook** krok po kroku (fazy, cele, kroki) + 4 prompty/komendy.

### 1.6 Dwie ścieżki i kiedy którą [S1 · ~53:00–01:04:00]
- **Track Builder** (Lovable / v0) — gotowe komponenty, ~30 min do pierwszego ekranu, krok PRD opcjonalny ale **warto go nie pomijać**.
- **Track Tech** (Claude Code + Next.js + Supabase + Vercel) — pełna kontrola nad kodem, push do GitHub, brak limitów narzędzia.
- Rekomendujemy **Track Tech** (eksport kodu, łatwiejsza migracja później). Zmiana ścieżki w środku tygodnia = restart.

### 1.7 Milestones, /goal i realne czasy [S1 · ~01:14:00–01:22:00]
- Core Flow rozbijasz na **5 milestonów (M1–M5)**, każdy z binarnym „zrobione".
- Skill **prepare-goal** zamienia milestony na gotowe komendy **/goal** (G1→G5, gdzie **G5 = deploy**). /goal przyjmuje: zadanie + kryterium walidacji + liczbę iteracji.
- Realny build na pilotażu: ~**1 h planowania + ~7 h pracy agenta w tle** (Ty wracasz tylko na bramkach). Output ~95% poprawny.

### 1.8 Brand + design (impeccable) [S1 · ~01:23:00–01:30:00]
- Skill **impeccable** robi audyt designu po wygenerowaniu PRD; renderuje i sprawdza HTML (web). Działa na stronach webowych — **nie na Flutterze** (inna kompilacja).

### 1.9 Vibe engineering, nie vibe coding (SDD) [S1 · ~01:30:00–01:40:00]
- 95% pracy to **praca na specyfikacji** (decyzje), nie na kodzie. Framework SDD: eksploracja → proposal → design → spec → tasks.
- Testy: jednostkowe (agent pisze sam) + manualne + Playwright na edge cases.

### 1.10 Logistyka [S1 · ~01:58:00–02:00:00]
- **Demo Day: sobota 20.06.2026, Gdańsk** (offline; nie trzeba być, by zaliczyć, ale warto).
- Zostają 3 tygodnie: W3 (teraz) → W4 (analityka, Wojtek) → W5.

---

## Część 2 — Co zbudowaliśmy na żywo na Spotkaniu 2 (praktyka)

> ⚠️ Tego dnia był **globalny outage GitHub/Claude Code** [S2 · ~01:30–02:30] — część integracji nie działała, robiliśmy obejścia (build lokalny). To nie był błąd projektu. Frekwencja niska — wyszło prawie indywidualne mentoring.

### 2.1 Track Builder na żywo — Lovable [S2 · ~13:00–24:00]
Kolejność i 5 briefów (po jednym ekranie/funkcji na raz):
1. **Pusta aplikacja.** W Lovable **nie ma „utwórz projekt"** — zaczynasz od **pierwszego briefa**, dopiero potem uzupełniasz Knowledge. [S2 · ~13:30]
2. **Logowanie** od strony użytkownika — wybraliśmy **Magic Link** (najprostsza bariera wejścia). W Lovable na prompt „add login" domyślnie powstaje logowanie e-mail+hasło — magic link prosisz promptem. [S2 · ~16:30]
3. **Schemat bazy** (spółka, liczba udziałów) — Lovable robi pod spodem na **Lovable Cloud** (zarządzane Supabase, zero kluczy). [S2 · ~17:00]
4. **Core Flow** — udostępnianie linka do cap table; użytkownik z linkiem widzi dane read-only. [S2 · ~19:00]
5. **Wstęp do analityki** — eventy dla przycisków (śledzenie kliknięć). Granica z W4. [S2 · ~20:00]

**5 briefów wystarczyło, bez dopromptowywania.** Powstała: nowa spółka → zapis → udostępnij → kopiuj link.
> Wątek z sali: na Replicie agenci wpadali w **pętle błędów** (error goni error) i trzeba było wgrywać backup. [S2 · ~06:00] Lekcja: małe briefy + test po każdym = mniejsze ryzyko pętli.

### 2.2 Track Tech na żywo — Claude Code [S2 · ~29:00–01:42:00]
- **CLAUDE.md** = reguły projektu czytane w każdej sesji (działa też z Cursor / Codex — przez `AGENTS.md`). Katalogi `context/w1/`, `context/w2/`. [S2 · ~39:00]
- **/goal** uruchamiany z kryteriami walidacji, agent zostawiony w tle aż spełni warunki. [S2 · ~30:00]
- **Supabase:** klucze z **1Password** przez CLI; projekt + 2 klucze do `.env.local`. Uwaga: Claude Code potrafi wstawić **klucz starszej konwencji** — patrz Część 4. [S2 · ~34:00–41:00]
- **M1 (login + dashboard):** lokalnie działało, **publikacja na Vercel padła** — bo **brak zmiennych środowiskowych** na Vercel (nie wina agenta). [S2 · ~38:00–47:00]
- **M2 (migracja bazy):** agent stworzył pliki migracji, ale **nie zaaplikował od razu**; po wklejeniu treści błędu sam zrobił `push`. [S2 · ~01:08:00–01:18:00]
- **Tryb auto / bypass permissions** żeby nie akceptować każdej komendy — wciąż bezpieczny (nie usunie bazy). [S2 · ~01:10:00]

### 2.3 SDD / OpenSpec — jak dokładać kolejne funkcje [S2 · ~01:02:00–01:33:00]
Pętla: **eksploracja** (brainstorming) → **proposal** (opcjonalny) → **design** → **spec** (scenariusze testowe pisane *przed* kodem) → **tasks**. `/opsx:apply` przechodzi przez nią; synchronizacja zapisuje wiedzę o projekcie do folderu `specs/`.
- **Wdrażanie do istniejącego projektu:** najpierw **core flow** zwykłym promptem, potem każdą kolejną funkcję przez SDD. [S2 · ~01:28:00]
- Pytanie Jędrzeja (3 funkcje — 1 agent czy wielu?): buduj **1 core flow**, potem dokładaj featury. U ClearTable core = **udostępnienie linka**, nie dodawanie danych. [S2 · ~01:00:00]

### 2.4 Code review [S2 · ~01:34:00–01:38:00]
- PR → **Copilot Review** wstawia komentarze → fix → pętla. Skill **review-loop** automatyzuje pętlę Claude Code ↔ Copilot.
- **/code-review ultra** — review wysyłany do chmury; koszt ~**5–20 $** kredytów (3 darmowe na start).

### 2.5 Publikacja + handoff do W4 [S2 · ~01:42:00–01:56:00]
- Deploy: `git push` → auto-deploy na Vercel (gdy repo podpięte); produkcja przez brancha; Vercel CLI.
- **Analityka — w W3 robisz tylko minimum:** **Vercel Web Analytics + Speed Insights** (darmowe; Speed Insights = Core Web Vitals, ważne pod SEO, odpowiednik Google PageSpeed Insight). [S2 · ~01:43:00]
- **Cała reszta — zdarzenia, lejki, PostHog — to W4 z Wojtkiem.** Nic więcej nie konfigurujesz, niczego nie musisz zostawiać. [S2 · ~01:52:00]
- W4: podpięcie domeny (Vercel, automatycznie), ruch użytkowników, wersja półprodukcyjna.

---

## Część 3 — Co faktycznie powstało (ClearTable, oba tracki)

Oba MVP to **ten sam produkt** z PRD ClearTable: founder loguje się magic linkiem, wpisuje strukturę udziałową sp. z o.o., generuje **read-only link**, pod którym inwestor widzi aktualny cap table bez zakładania konta.

**Core Flow (4 ekrany):** A Dashboard (lista + stan pusty) → B Edytor (dodaj wspólników, % liczone na żywo) → C Modal „Udostępnij" (token + kopiuj link) → D Publiczny widok read-only.

| | **Track Tech** (`cleartable-demo`) | **Track Builder** (`cleartable-blank-canvas`) |
|---|---|---|
| Stack | Next.js 15 + React 19 + TS + Tailwind v4 + shadcn/ui + Supabase + Vercel | React + TanStack Router + Vite + shadcn/ui + Lovable Cloud (Supabase) |
| Logowanie | Magic link (Supabase Auth) | Magic link (Lovable Cloud) |
| Baza + RLS | `cap_tables` + `shareholders`, RLS owner-only + anon read po tokenie | analogicznie, na Lovable Cloud |
| Publiczny widok | `/share/[token]` | `/widok/$token` |
| Status | **5/5 milestonów done**, prod live, smoke test incognito @375px ✅ | Pełny Core Flow zbudowany w sesji, live ✅ |

Brand (oba): granat `#0F2A4A` + niebieski `#1D6FB8`, tło `#F6F8FB`; fonty Plus Jakarta Sans / Inter / **IBM Plex Mono na liczbach udziałów i %**; light-only, polskie etykiety (kierunek „instytucjonalne zaufanie").

> Track Tech ma w repo dowody: `docs/IMPLEMENTATION-SUMMARY.md`, skrypty `scripts/*_walkthrough.py`, `screenshots/`, `supabase/rls_proof.sql`. Zajrzyj — to wzór, jak udokumentować własne MVP.

---

## Część 4 — Czego na żywo zabrakło lub się wysypało (i jak to zrobić dobrze)

Na żywo kilka rzeczy się nie udało albo zostały pominięte (outage, czas, dane z szablonu już gotowe). Tu masz **uzupełnienie** — przejdź przez to u siebie.

1. **Generowanie `brand.md` / `prd.md` / reguł nie było robione na żywo w środę** — używaliśmy szablonu z już wypełnionymi plikami. **U siebie musisz je wygenerować:** Spotkanie 1 [S1 · ~24:00] pokazuje sens, a komendy/prompty masz w repo (`/brand`, `/prd`, `/reguly`, `/milestones` lub `prompts/`). Kolejność obowiązkowa — każdy krok konsumuje poprzedni.

2. **Publikacja na Vercel padła przez brak zmiennych środowiskowych** [S2 · ~38:00]. Uzupełnienie: po pierwszym deployu wejdź **Vercel → Project → Settings → Environment Variables** i dodaj `NEXT_PUBLIC_SUPABASE_URL`, `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY`, `SUPABASE_SERVICE_ROLE_KEY` dla środowiska **Production**, potem **redeploy**. Lokalny `.env.local` NIE trafia na Vercel automatycznie.

3. **Konwencja kluczy Supabase (2025+)** — Claude Code potrafi wstawić starą nazwę (`anon key`). Aktualnie: `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY` (klient) i `SUPABASE_SERVICE_ROLE_KEY` (tylko serwer, **nigdy** pod prefiksem `NEXT_PUBLIC_`). Gdy agent pyta o klucz — podaj właściwy.

4. **Migracja bazy nie zaaplikowała się sama** [S2 · ~01:08:00]. Wzorzec naprawy: **wklej treść błędu do sesji**, agent sam zrobi `supabase db push`. W demo pierwsza migracja padła, bo na zdalnym projekcie nie było rozszerzenia `pgcrypto` — token wygenerowano przez `gen_random_uuid()` (też unikalny). Jak Twoja migracja pada na rozszerzeniu — to typowe, nie blokujące.

5. **Vercel Deployment Protection (401)** — częsta pułapka, **nie pokazana na żywo**. Nowe projekty Vercel zwracają **401** na „surowych" aliasach deploymentu dla niezalogowanych; publiczny jest tylko **canonical alias** (np. `cleartable-demo.vercel.app`). Przed ogłoszeniem linka sprawdź w incognito albo wyłącz Protection (Settings → Deployment Protection).

6. **Logowanie magic link testuj OSOBIŚCIE** — agent nie ma prawdziwej skrzynki, więc tego nie sprawdzi za Ciebie. Uwaga: Supabase na darmowym planie ma **limit ~2 maile/godz.** — przy wielokrotnym re-teście logowania trafisz na rate limit (to ograniczenie, nie błąd).

7. **impeccable (audyt designu)** — wspomniany [S1 · ~01:23:00], nie zademonstrowany. Opcjonalnie: `npx impeccable skills install`, potem `/impeccable shape` przed buildem core flow i `/impeccable audit` przed deployem.

8. **Komenda „onboarding" do podpięcia obcego środowiska** — szukaliśmy na żywo i nie znaleźliśmy [S2 · ~01:58:00], możliwe że wycofana. Nie jest potrzebna do przejścia tygodnia — pomiń.

9. **Analityka produktowa (PostHog) — celowo NIE w W3.** W tym tygodniu tylko Vercel Analytics (1 linijka). PostHog, zdarzenia i lejki robisz **w W4 z Wojtkiem** — nie wyprzedzaj.

---

## Część 5 — Instrukcja samodzielnego przejścia (end-to-end)

Pełny opis każdej fazy (anty-wzorce, realne czasy) masz w **`PLAYBOOK.md`** w szablonie. Tu skrót operacyjny.

### Faza 0 — Konta + brand (pon→śr)
1. Zbierz artefakty **W1** (BHC, deep-analysis, mom-test) i **W2** (ICP, positioning, insights playbook, **landing brief**) w jedno miejsce.
2. Załóż konta (darmowe tiery): **Track Builder** → Lovable (+ Vercel opcjonalnie); **Track Tech** → GitHub + Vercel + Claude Code + Supabase (jeśli potrzebujesz bazy).
   - **Potrzebujesz bazy?** Czy ktoś poza Tobą tworzy/zapisuje dane, które przeżyją odświeżenie? TAK → baza (Tech: Supabase; Builder: Lovable Cloud włącza się samo). NIE → pomiń bazę i milestone M2.
3. Z szablonu: *Use this template* → wrzuć artefakty do `context/w1/`, `context/w2/`.
4. Wygeneruj **`brand.md`** — `/brand` (Tech) lub `PROMPT_Brand` (Builder). Ścieżka A (z opublikowanego LP) lub B (od zera z ICP). Musi mieć **konkretne HEX-y i nazwy fontów**.

### Faza 1 — PRD
5. Wygeneruj **`prd.md`** — `/prd` (czyta `context/` + `brand.md`) lub `PROMPT_PRD`. Model zrobi audyt wejścia (dopytaj — nie pozwól zgadywać), zaproponuje **cięcie do 1 Core Flow** (zaakceptuj świadomie), wygeneruje PRD ≤ 2 strony. Przeczytaj **§6 Out of scope** i **§7 Open Questions**.

### Faza 2 — Reguły projektu (~10 min)
6. Wygeneruj reguły (konstytucję) — `/reguly` → `CLAUDE.md`/`AGENTS.md` (Tech) lub `PROMPT_Reguły` → **Lovable Knowledge** (Builder). Wyprowadzane z `prd.md` + `brand.md`. **Test:** zapytaj narzędzie „jakie są reguły tego projektu?" — ma odpowiedzieć Twoją konstytucją.

### Faza 3 — Milestones (środa)
7. Wygeneruj **`goals.md`** — `/milestones` lub `PROMPT_Milestones`. Rozbicie Core Flow na **M1 Fundament → M2 Dane → M3 Core Flow UI → M4 Edge cases → M5 Deploy**, każdy z binarnym DoD.

### Faza 4 — Build (środa→sobota)
8. **Track Tech:** `/prepare-goal <opis>` → `/goal <warunek>` w **świeżej sesji** per milestone → agent pracuje w tle → review na bramce → następny. Zawsze świeża sesja per goal.
9. **Track Builder:** 1 briefing = 1 ekran/feature → Lovable generuje → **sprawdź w preview** → iteruj 2–3 razy → następny. DoD z `goals.md` wklejasz jako definicję „zrobione".
10. **Testuj między milestonami** — 15 min preview > 3 h debugowania w piątek. Bloker > 30 min → pytanie na grupie.

### Faza 5 — Deploy + handoff (sobota→niedziela)
11. **Produkcja:** Tech — merge do `main` / `vercel --prod`; Builder — Publish w Lovable. Zostań na domenie `*.vercel.app` / domenie narzędzia (custom domain = ryzyko 24 h DNS).
12. **Ustaw zmienne środowiskowe na Vercel (Production)** i zrób redeploy — patrz Część 4 pkt 2.
13. **Vercel Analytics** (1 linijka) — i **na tym kończysz analitykę w W3**.
14. **Smoke test ZAWSZE w incognito:** otwórz produkcyjny URL → przejdź cały Core Flow → sprawdź mobile (375px) → magic link przetestuj osobiście.
15. **Handoff na grupę:** URL + znane braki (uczciwie — „known issues" to profesjonalizm).

---

## Część 6 — Najczęstsze potknięcia (ściąga)

| Objaw | Przyczyna | Naprawa |
|---|---|---|
| Lokalnie działa, na Vercel biały ekran / błąd | Brak env vars na Vercel | Settings → Environment Variables (Production) + redeploy |
| Publiczny link zwraca **401** | Vercel Deployment Protection | Użyj canonical aliasu / wyłącz Protection / sprawdź w incognito |
| Agent pyta o „anon key", a Supabase go nie pokazuje | Stara konwencja kluczy | Podaj `…PUBLISHABLE_KEY`; `SERVICE_ROLE` nigdy pod `NEXT_PUBLIC_` |
| Migracja nie zastosowana / błąd rozszerzenia | Agent nie zrobił `db push` / brak `pgcrypto` | Wklej błąd do sesji → agent naprawi; token przez `gen_random_uuid()` |
| Magic link nie przychodzi przy re-testach | Rate limit ~2/h (free) | Poczekaj / użyj disposable inbox; przetestuj logowanie sam |
| Agent w pętli błędów (Lovable/Replit) | Za duży brief naraz | Mniejsze briefy, test po każdym, w razie czego cofnij do backupu |
| MVP wygląda generycznie (fiolet, Inter) | Build bez `brand.md` | Wróć do Fazy 0, wygeneruj brand, dopiero buduj |

---

## Co dalej — Week 4 (Wojtek)

Przychodzisz do W4 z **działającym publicznym URL-em**. Wojtek prowadzi **analitykę produktową od zera**: PostHog, zdarzenia, lejki, soft launch, iteracja na feedbacku userów. Zasada: drobne zmiany pod konkretny feedback, **nie** przepisywanie PRD. Jak feedback wymusza duży rewrite — wracasz do insightów W1/W2, nie do kodu.

**Demo Day: sobota 20.06, Gdańsk.** Powodzenia 🚀

_Pytania w trakcie tygodnia → grupa programu. Bloker > 30 min = pisz._
