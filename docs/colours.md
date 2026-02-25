# ClimbingTracker – Design System (v1)

Primary Brand Colour: #38BDF8

------------------------------------------------------------
COLOUR SYSTEM
------------------------------------------------------------

### Primary (Brand)

primary-500 → #38BDF8   (Main CTA, active states)
primary-600 → #0EA5E9   (Hover / pressed)
primary-400 → #7DD3FC   (Light background accents)
primary-100 → #E0F2FE   (Subtle surface highlight)

Usage Rules:
- primary-500 = Primary buttons
- primary-600 = Button hover
- primary-100 = Tag background or highlight surface
- primary-400 = Selected state backgrounds

------------------------------------------------------------

### Neutral Scale

neutral-900 → #0F172A   (Main text)
neutral-700 → #334155   (Secondary headings)
neutral-600 → #475569   (Secondary text)
neutral-300 → #CBD5E1   (Borders)
neutral-200 → #E2E8F0   (Dividers)
neutral-100 → #F1F5F9   (Card background)
background  → #F8FAFC   (App background)

Usage Rules:
- neutral-900 = Primary text
- neutral-600 = Subtext
- neutral-300 = Borders
- neutral-100 = Card fill
- background = Main app background

------------------------------------------------------------

### Status Colours

success-500 → #16A34A
success-100 → #DCFCE7

warning-500 → #F59E0B
warning-100 → #FEF3C7

danger-500 → #DC2626
danger-100 → #FEE2E2

Usage:
- Completed sessions → success
- In Progress → primary
- Skipped → neutral or danger
- Delete → danger

------------------------------------------------------------
TYPOGRAPHY
------------------------------------------------------------

Font Family: Inter

H1
- 24px
- SemiBold
- Line height 120%

H2
- 20px
- SemiBold

Body
- 16px
- Regular

Small
- 14px
- Regular

Label
- 12–14px
- Medium

Rule:
No more than 5 text styles.

------------------------------------------------------------
SPACING SYSTEM
------------------------------------------------------------

8px scale:

4
8
12
16
24
32
48
64

Rules:
- Card padding = 16px
- Section spacing = 24px
- Button padding vertical = 12px
- Button padding horizontal = 16px

------------------------------------------------------------
ELEVATION
------------------------------------------------------------

Card Shadow:
0px 1px 3px rgba(0,0,0,0.06)

Modal Shadow:
0px 8px 24px rgba(0,0,0,0.12)

Do not create more than 2 shadow levels.

------------------------------------------------------------
COMPONENTS
------------------------------------------------------------

Button
- Primary (primary-500 background, white text)
- Secondary (white background, neutral-300 border)
- Disabled (neutral-200 background)

Tag
- Default (neutral-100 background)
- Primary (primary-100 background, primary-600 text)
- Success (success-100 background, success-500 text)
- Warning (warning-100 background, warning-500 text)

Card Base
- background: neutral-100
- border: neutral-300
- radius: 12px
- padding: 16px

PlannedSessionCard
Contains:
- Title (H2)
- Training focus tag
- Duration (Small)
- Status indicator
- CTA button

Bottom Navigation
- White background
- Active tab icon = primary-500
- Inactive = neutral-600

------------------------------------------------------------
DESIGN PRINCIPLES
------------------------------------------------------------

- Use colour sparingly.
- Primary colour = action only.
- Most UI = neutral.
- No gradients.
- No glassmorphism.
- No more than 2 corner radius values (12px cards, 8px buttons).

------------------------------------------------------------
END STATE
------------------------------------------------------------

The app should feel:
- Clean
- Athletic
- Focused
- Calm but energetic
- Not playful
- Not corporate
- Not overdesigned
