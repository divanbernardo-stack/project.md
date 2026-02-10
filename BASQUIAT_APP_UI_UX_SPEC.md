# Basquiat-Class: UI/UX + Frontend Product Spec

## 1) Creative Brief

**Product vision:** Build a premium marketplace where artists teach and students learn, in-person or online, wrapped in a visual language inspired by Jean-Michel Basquiat’s energy—translated into a clean, high-performing, accessible product.

**Creative direction:**
- **Mood:** “Living sketchbook meets high-end booking platform.”
- **Visual thesis:** Structured layouts + expressive overlays (crowns, arrows, rough frames, scribble annotations, crossed-out labels used sparingly).
- **UX thesis:** Frictionless booking and schedule management are sacred. Expression never blocks clarity.
- **Brand voice:** Punchy, cultured, urban-gallery confident; short lines with meaning.

**Success criteria:**
- Student can find + book a relevant class in under 2 minutes.
- Artist can publish a class in under 6 minutes.
- WCAG AA contrast and keyboard-friendly controls throughout.
- Visual identity feels distinctive and premium, not chaotic.

---

## 2) IA + User Flows

### 2.1 Site Map

```text
Root
├── Landing / Discovery
│   ├── Featured Collections
│   ├── Trending Classes
│   ├── Featured Artists
│   └── City / Remote Switch
├── Search
│   ├── Results (List/Map)
│   ├── Filters Drawer
│   └── Sort
├── Class Detail
│   ├── Overview
│   ├── Schedule + Availability
│   ├── Reviews
│   ├── Artist Snapshot
│   └── Book CTA
├── Booking
│   ├── Participant Details
│   ├── Payment
│   ├── Confirmation
│   └── Add to Calendar
├── Artists
│   ├── Artist Directory
│   └── Artist Profile
├── Community
│   ├── Saved
│   ├── Following
│   └── Shared Links
├── Messages
│   └── Thread Detail
├── Reviews
│   ├── Write Review
│   └── My Reviews
├── Trust & Safety
│   ├── Verification
│   ├── Policies
│   └── Report Issue
└── Account
    ├── Profile
    ├── Payments
    ├── Notifications
    ├── Privacy
    └── Role Switch (Student/Artist)

Artist Mode
├── Dashboard
├── Create/Edit Class
├── Availability & Calendar
├── Booking Management
├── Messages
├── Portfolio Manager
├── Payouts
└── Settings
```

### 2.2 Navigation Patterns

#### Mobile (Tab Bar)
- **Tabs:** Home, Search, Saved, Messages, Account
- **Floating action (Artist mode):** “+ Class” scribble-framed FAB.
- **Top utility row (contextual):** city selector, role switch, notifications.

#### Web (Header + Optional Left Rail)
- **Header:** logo, search bar, collections, artists, messages, account menu.
- **Left rail (authenticated):** Dashboard links + quick filters.
- **Sticky right rail (detail pages):** booking card + quick facts.

### 2.3 Core User Flows

#### Flow A: Onboarding (Student/Artist)
1. Welcome → choose role card (Student / Artist).
2. Personalize interests (art type, goals, level, location).
3. Enable notification + calendar permissions.
4. Land in role-specific home.

#### Flow B: Student Book
1. Discover/search class.
2. Apply filters (type/price/date/location/format/language).
3. Open class detail.
4. Select timeslot and seats.
5. Checkout + payment.
6. Confirmation → add to calendar → optional message artist.

#### Flow C: Artist Publish + Manage
1. Complete profile + verification.
2. Create class listing.
3. Set schedule, capacity, price, format, location/link.
4. Publish.
5. Manage bookings/messages/payouts.

### 2.4 Personas + JTBD

#### Persona 1: Student — “Maya, 26, Product Designer, Toronto”
- **Motivation:** Wants creative practice after work, low friction booking.
- **Pain points:** Too many low-quality listings; unclear skill levels.
- **JTBD:** “When I feel creatively blocked, help me quickly find a class that matches my level and schedule so I can book confidently.”

#### Persona 2: Artist — “Andre, 34, Music Producer + Educator”
- **Motivation:** Monetize teaching while building reputation and community.
- **Pain points:** Admin overhead, no-show risk, payout ambiguity.
- **JTBD:** “When I publish a workshop, help me manage scheduling, payments, and communication in one place so I can focus on teaching.”

---

## 3) Design System (Basquiat-Translated)

### 3.1 Color Palette (WCAG-aware)

| Role | Token | Hex | Usage |
|---|---|---:|---|
| Background | `--bg-canvas` | `#F7F3EB` | Main app background (“gallery wall”) |
| Surface | `--bg-surface` | `#FFFDF9` | Cards, modals, sheets |
| Surface Alt | `--bg-panel` | `#EFE7DA` | Filter rails, secondary zones |
| Text Primary | `--text-ink` | `#111111` | Main text |
| Text Secondary | `--text-charcoal` | `#2F2A24` | Subtext |
| Primary | `--brand-black` | `#0D0D0D` | CTAs, nav emphasis |
| Accent Red | `--accent-red` | `#D72638` | Highlights, urgency |
| Accent Yellow | `--accent-yellow` | `#F2C94C` | Crown motif, featured |
| Accent Blue | `--accent-blue` | `#2D6CDF` | Links, online states |
| Success | `--state-success` | `#1F9D55` | Confirmed states |
| Warning | `--state-warning` | `#D9822B` | Reschedule, caution |
| Error | `--state-error` | `#B42318` | Validation errors |
| Border | `--line-raw` | `#1F1A17` | Rough frame lines |

**Contrast targets:**
- Body text minimum 4.5:1.
- CTA text minimum 4.5:1.
- Large headline 3:1+.

### 3.2 Typography

**Fonts (Google/Web-safe):**
1. **Space Grotesk** — headings, large numerals, pricing.
2. **Inter** — body text, forms, dense UI.
3. **Caveat** (or fallback “Bradley Hand, cursive”) — annotation micro-details only.

**Usage rules:**
- H1/H2: Space Grotesk, uppercase optional, slight negative tracking.
- Body: Inter 16/24 desktop, 15/22 mobile.
- Labels/buttons: Inter 13–14 semi-bold.
- Annotation style: Caveat at 12–13 for non-critical notes (“2 seats left”, “new drop”). Never use for essential controls.

### 3.3 Motif Rules (Basquiat as System)
- **Crown highlight:** Reserved for featured artists/classes and badges.
- **Crossed-out text:** Metadata only (e.g., old price), never core instructions.
- **Scribble arrows:** Guide attention to CTAs or critical status updates.
- **Rough frames:** 1–2px imperfect SVG stroke around cards/buttons.
- **Stamped texture:** subtle (`opacity 0.04–0.08`) grain overlays, never under input text.

### 3.4 Core Components

1. **Buttons**
   - Primary: black background, off-white text, hover reveals yellow underline stroke.
   - Secondary: transparent with raw border.
   - Ghost: text + arrow icon.
   - Disabled: reduced contrast but still readable.

2. **Inputs**
   - 44px min height, thick focus ring (`2px accent-blue + 1px black`).
   - Optional annotation hint below field.

3. **Tags/Chips**
   - Rounded-rectangle with imperfect border.
   - Active chip gets marker-stroke background.

4. **Cards (Class/Artist)**
   - Collage layout: media + layered info block + pricing pill.
   - Hover: slight lift + corner crown flash for featured items.

5. **Modal/Sheet**
   - “Paper stack” edge shadow.
   - Sticky bottom action area on mobile.

6. **Calendar Picker**
   - Week rows with availability dots.
   - Selected date indicated by hand-drawn ring + strong fill.

7. **Map/List Toggle**
   - Segmented control, icon + label.
   - Map pin style matches icon set with hand-drawn micro-stroke.

8. **Rating**
   - Star icons clean outline; optional scribble underline for highlighted reviews.

9. **Avatar + Artist Badge**
   - Circular avatar with optional “Verified” stamp and tiny crown for featured mentors.

10. **Pricing Pill**
    - Strong contrast capsule; optional crossed-out old price.

### 3.5 Iconography
- Base: clean outline icon set (24px).
- Overlay: occasional 1px hand-drawn strokes (SVG path) for emphasis states only.
- Do not decorate every icon—target <20% of icon instances.

### 3.6 Motion
- **Hover:** 120–180ms translateY(-2) + shadow + marker swipe.
- **Tap:** 90ms compress + rebound.
- **Loading:** skeleton with brush-stroke shimmer.
- **Page transitions:** subtle collage reveal (fade + clip-path), <220ms.
- **Reduced motion mode:** remove transform/clip animations, keep opacity transitions only.

### 3.7 Accessibility Rules
- WCAG AA contrast in all states.
- Visible keyboard focus on every interactive element.
- Form errors include text + icon + ARIA live region.
- Hit area min 44x44 on touch.
- Support reduced motion and high zoom (200%).

### 3.8 Design Tokens (CSS Variables)

```css
:root {
  --bg-canvas: #F7F3EB;
  --bg-surface: #FFFDF9;
  --bg-panel: #EFE7DA;
  --text-ink: #111111;
  --text-charcoal: #2F2A24;
  --brand-black: #0D0D0D;
  --accent-red: #D72638;
  --accent-yellow: #F2C94C;
  --accent-blue: #2D6CDF;
  --state-success: #1F9D55;
  --state-warning: #D9822B;
  --state-error: #B42318;
  --line-raw: #1F1A17;

  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 24px;
  --space-6: 32px;
  --space-7: 48px;

  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 18px;

  --shadow-raw: 0 2px 0 #1F1A17, 0 8px 24px rgba(17, 17, 17, 0.08);
}
```

---

## 4) Screen-by-Screen Specs

### Grid standards
- **Mobile:** 4-column grid, 16px margins, 12px gutters.
- **Tablet:** 8-column, 24px margins.
- **Web:** 12-column, max width 1280px, 32px margins.

### 4.1 Landing / Home Discovery
- **Hierarchy:** hero search → collections carousel → featured classes → top artists.
- **Components:** sticky top search, city/online toggle, collection chips, class cards, artist row.
- **Copy tone:** “Find your next session.” / “Tonight in Toronto.”
- **Empty state:** “No drops in this area yet. Expand radius or go online.”
- **Error state:** location failure banner with retry.

### 4.2 Search + Filters
- **Layout:** left filter rail (web) / bottom sheet (mobile), right results pane, map toggle top-right.
- **Filters:** art type, level, price, distance, date/time, format, language.
- **States:** active chip count, clear-all, saved filter set.
- **Empty state:** suggest alternative dates and nearby online classes.
- **Error state:** results fetch fail → inline retry card.

### 4.3 Class Detail
- **Layout:** media gallery top, details left, booking card right (sticky desktop).
- **Blocks:** overview, what-you’ll-learn, requirements, schedule, location/map or join link, reviews.
- **Trust row:** verified badge, cancellation terms, report link.
- **CTA:** “Book this class”.
- **Empty state:** no reviews yet → prompt “Be the first voice.”

### 4.4 Booking & Checkout
- **Steps:** slot → attendee info → payment → confirm.
- **Layout:** stepper top, form center, order summary card.
- **Payment options:** card, wallet, promo code.
- **Post-confirmation:** calendar add, message artist, share link.
- **Errors:** inline field + top summary; preserve entered data.

### 4.5 Artist Profile (Portfolio-First)
- **Layout:** hero with avatar/name/tags + masonry portfolio + classes + reviews.
- **Primary actions:** follow, message, book class.
- **Trust markers:** verified stamp, response time, class count.
- **Empty state (new artist):** featured intro card + “First class dropping soon.”

### 4.6 Create Class (Artist)
- **Layout:** progressive form sections with autosave.
- **Sections:** basics, format/location, media, schedule, pricing/capacity, policies.
- **Assistive copy:** pricing guidance, cancellation templates, required fields.
- **Validation:** immediate checks, conflict warnings for schedule overlaps.

### 4.7 Schedule/Calendar
- **Views:** month/week/day + list of bookings.
- **Color coding:** booked, waitlist, cancelled.
- **Interactions:** drag to reschedule (web), tap-edit (mobile).
- **Empty:** “No sessions here yet—drop a class to start.”

### 4.8 Messages
- **Layout:** thread list + chat pane (web), stacked on mobile.
- **Features:** quick replies, attachments (reference image/audio), booking context card.
- **Safety:** report/block from overflow menu.
- **Empty:** “Start the conversation. Ask goals, gear, and level.”

### 4.9 Reviews
- **Layout:** rating summary, filter by class type, review cards.
- **Write review:** stars + prompts (clarity, vibe, pacing, value).
- **Artist response:** inline threaded response block.
- **Moderation:** report CTA and policy link.

### 4.10 Account + Settings
- **Sections:** profile, preferences, payment methods, notifications, privacy, role mode, logout.
- **Security:** 2FA, login activity list.
- **Accessibility:** text size slider + reduced motion toggle.
- **Danger zone:** account delete with multi-step confirmation.

---

## 5) Copy Bank (Microcopy)

### Buttons
- “Book this class”
- “Hold my spot”
- “Go live online”
- “Publish the drop”
- “Save for later”
- “Follow this artist”

### Labels
- “Art form”
- “Skill level”
- “Studio or screen”
- “Distance radius”
- “Cancellation window”

### Tooltips
- “Verified = identity and payout checks completed.”
- “Featured classes are curator picks with strong reviews.”
- “Online class? We’ll send your join link after payment.”

### Empty states
- “No classes match this filter set. Loosen one line, find new energy.”
- “No saved classes yet. Build your roster.”
- “No messages yet. Say hello before class day.”

### Error states
- “Payment didn’t clear. Try again or switch method.”
- “That timeslot just filled. Pick another and keep moving.”
- “Upload failed. Your draft is safe.”

### Notification examples
- “You’re in. Class confirmed for Thu 7:00 PM.”
- “Price drop: your saved class just moved.”
- “Reminder: session starts in 2 hours.”

---

## 6) Frontend Plan + Example Code

### 6.1 Recommended Stack
- **Next.js (App Router) + TypeScript** for scalable SSR/ISR, strong typing, and route performance.
- **Tailwind CSS** for token-driven styling with fast iteration.
- **shadcn/ui (optional foundation)** for accessible primitives customized with Basquiat motifs.
- **React Query / TanStack Query** for booking/search data fetching and caching.
- **Zod + React Hook Form** for robust form validation in booking + class creation.

**Why this stack:** speed to build, strong DX, good SEO for discovery pages, and tight control over visual system without performance-heavy design tooling.

### 6.2 Tailwind Theme Notes
- Define token mapping in `tailwind.config.ts` via CSS variables.
- Create utility classes:
  - `.rough-frame`
  - `.marker-divider`
  - `.crown-badge`
  - `.annotation-text`

### 6.3 Example: ClassCard Component (React + Tailwind)

```tsx
import Link from "next/link";

type ClassCardProps = {
  id: string;
  title: string;
  artist: string;
  price: string;
  rating: number;
  image: string;
  featured?: boolean;
  format: "online" | "in-person";
};

export function ClassCard({
  id,
  title,
  artist,
  price,
  rating,
  image,
  featured,
  format,
}: ClassCardProps) {
  return (
    <Link
      href={`/classes/${id}`}
      className="group block rounded-[14px] bg-[var(--bg-surface)] p-2 shadow-[var(--shadow-raw)] transition duration-150 hover:-translate-y-0.5 focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-[var(--accent-blue)]"
    >
      <div className="relative overflow-hidden rounded-[10px]">
        <img src={image} alt={title} className="h-44 w-full object-cover" />
        <div className="absolute left-2 top-2 rounded-full bg-[var(--brand-black)] px-2 py-1 text-xs font-semibold text-[var(--bg-surface)]">
          {format === "online" ? "Online" : "In Person"}
        </div>
        {featured && (
          <div className="absolute right-2 top-2 rounded-full bg-[var(--accent-yellow)] px-2 py-1 text-xs font-bold text-[var(--brand-black)]">
            👑 Featured
          </div>
        )}
      </div>

      <div className="relative p-3">
        <div className="absolute -left-1 top-1 h-[2px] w-8 bg-[var(--accent-red)] opacity-80" />
        <h3 className="font-['Space_Grotesk'] text-base font-bold text-[var(--text-ink)]">
          {title}
        </h3>
        <p className="mt-1 text-sm text-[var(--text-charcoal)]">{artist}</p>

        <div className="mt-3 flex items-center justify-between">
          <span className="rounded-full border border-[var(--line-raw)] px-2 py-1 text-sm font-semibold">
            {price}
          </span>
          <span className="text-sm font-medium text-[var(--text-charcoal)]">
            ★ {rating.toFixed(1)}
          </span>
        </div>
      </div>
    </Link>
  );
}
```

### 6.4 Example: FilterChips Component

```tsx
type FilterOption = {
  key: string;
  label: string;
};

type FilterChipsProps = {
  options: FilterOption[];
  active: string[];
  onToggle: (key: string) => void;
};

export function FilterChips({ options, active, onToggle }: FilterChipsProps) {
  return (
    <div className="flex flex-wrap gap-2">
      {options.map((option) => {
        const isActive = active.includes(option.key);
        return (
          <button
            key={option.key}
            type="button"
            onClick={() => onToggle(option.key)}
            className={[
              "rounded-full border px-3 py-2 text-sm font-medium transition",
              "focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-[var(--accent-blue)]",
              isActive
                ? "border-[var(--line-raw)] bg-[var(--accent-yellow)] text-[var(--brand-black)]"
                : "border-[var(--line-raw)] bg-[var(--bg-surface)] text-[var(--text-charcoal)] hover:bg-[var(--bg-panel)]",
            ].join(" ")}
            aria-pressed={isActive}
          >
            {option.label}
          </button>
        );
      })}
    </div>
  );
}
```

### 6.5 Responsive Rules (Mobile-First)
- Start with single-column flows; elevate to split panes at `md` and `lg`.
- Booking CTA sticky bottom on mobile; sticky sidebar on desktop.
- Filters as sheet on mobile, persistent rail on desktop.
- Max 2 taps from search result to booking entry.

### 6.6 Performance Guidance
- Use optimized image pipeline (`next/image` + AVIF/WebP).
- Limit decorative SVG layers to one per section.
- Lazy-load map and heavy carousels.
- Avoid heavy raster textures; use CSS noise + lightweight SVG patterns.
- Skeleton loaders for class cards/search lists.
- Cache search/filter query results with stale-while-revalidate.

### 6.7 Trust & Safety UX Implementation Notes
- Verification badges server-driven with signed metadata.
- Cancellation terms shown before payment confirmation.
- Prominent report action in class detail, messages, and reviews.

---

## Closing Principle
**“Raw expression, precise interaction.”**
Every visual flourish must either guide attention, reinforce trust, or celebrate artists—never slow down booking.
