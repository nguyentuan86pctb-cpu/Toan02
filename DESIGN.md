# Design System Specification: The Enchanted Ledger

## 1. Overview & Creative North Star: "The Living Storybook"
This design system rejects the clinical, grid-locked nature of traditional educational software. Our Creative North Star is **The Living Storybook**. We are not building a calculator; we are crafting an immersive, tactile world where numbers are magical ingredients and the UI is the parchment upon which a child’s journey is written.

To move beyond the "template" look, this system utilizes **Organic Asymmetry**. Elements should never feel perfectly centered or mechanically aligned. By using overlapping surfaces, floating "magical" motifs, and extreme typographic contrast, we create a sense of wonder. The interface should feel like it was hand-assembled by the lead character (the Bunny or Unicorn), not rendered by a machine.

---

## 2. Color & Atmospheric Depth
Our palette is a sophisticated take on childhood whimsy, moving away from garish saturation toward a "frosted-pastels" editorial aesthetic.

### The "No-Line" Rule
**Explicit Instruction:** Traditional 1px solid borders are strictly prohibited for sectioning or containment. Boundaries must be defined through background color shifts. Use `surface-container-low` for large section backgrounds sitting on a `surface` base. If a separation is needed, use a transition of tone, not a stroke.

### Surface Hierarchy & Nesting
Treat the UI as physical layers of "Magic Paper."
*   **Base Layer:** `surface` (#fbf5f8) – The foundation.
*   **Secondary Sections:** `surface-container-low` (#f5eff2) – Use for sidebars or secondary content areas.
*   **Interactive Containers:** `surface-container-lowest` (#ffffff) – Use for white "paper cards" that hold math problems. This creates a natural "pop" against the pinkish background without needing shadows.

### The "Glass & Gradient" Rule
To achieve the "Fairy-Tale" shimmer, use **Glassmorphism** for floating toolbars or achievement badges. 
*   **Token Application:** Use `primary-container` (#fdb5cc) at 60% opacity with a `20px` backdrop-blur. 
*   **Signature Textures:** Apply a linear gradient from `primary` (#824a5e) to `secondary` (#6f5174) at a 45-degree angle for Hero CTAs to provide a "velvet" depth.

---

## 3. Typography: Editorial Whimsy
We utilize a dual-font strategy to balance character with legibility for early readers.

*   **The Hero (Plus Jakarta Sans):** Used for `display` and `headline` tiers. Despite its name, when scaled up (e.g., `display-lg` at 3.5rem), its rounded terminals feel friendly yet premium. Use it for big numbers and celebratory feedback.
*   **The Narrator (Be Vietnam Pro):** Used for `title` and `body` tiers. It offers high legibility for 1st-grade reading levels while maintaining the soft, open counters that mirror the "rounded" brand identity.

**Typography Scale Note:** 
Always prioritize `headline-lg` for math questions. The high contrast between a `headline-lg` question and `body-md` helper text creates a clear "Editorial Hierarchy" that guides a child's eye.

---

## 4. Elevation & Depth
We eschew "Material Design" style heavy shadows in favor of **Ambient Luminance.**

*   **The Layering Principle:** Place a `surface-container-lowest` (#ffffff) card on a `surface-container-low` (#f5eff2) section. This 2-point hex shift is enough to define depth naturally.
*   **Ambient Shadows:** For "floating" elements like the Bunny character or modal pop-ups, use a "Bloom Shadow": 
    *   `box-shadow: 0 10px 40px rgba(130, 74, 94, 0.08);` (A tinted shadow using the `primary` token rather than black).
*   **Ghost Borders:** If a field needs a container (like a text input), use the `outline-variant` (#b0acaf) at 20% opacity. It should be a suggestion of a shape, not a cage.

---

## 5. Components

### The "Sparkle" Button (Primary)
*   **Visuals:** `surface-tint` (#824a5e) background, `on_primary` (#ffeff2) text.
*   **Shape:** `rounded-xl` (3rem). 
*   **State:** On hover, apply a "Sparkle Filter" (a CSS mask-image of small stars) and scale the button by 1.05x.

### Enchanted Chips (Selection)
*   **Visuals:** `secondary-container` (#fad3fd) for unselected; `primary` (#824a5e) with `on-primary` text for selected.
*   **Rule:** No dividers. Use `1.5rem` horizontal spacing (`md`) to let the elements breathe.

### Math Input Fields
*   **Visuals:** `surface-container-highest` (#e1dbdf) background, `rounded-md` (1.5rem).
*   **Animation:** On focus, the background shifts to `tertiary-container` (mint green #b4f5bd) to signal "Green means go/safe."

### Progression Rainbow (Special Component)
*   Instead of a flat progress bar, use a segmented arc. Each segment is a `tertiary-fixed` (#b4f5bd) block that glows when the child completes a math problem.

### The Character "Guide"
*   The Bunny/Unicorn should never be boxed. Use **Absolute Positioning** to let the character overlap two different surface containers (e.g., half on the white card, half on the pink background) to break the "webpage" feel.

---

## 6. Do’s and Don’ts

### Do:
*   **Use Intentional Asymmetry:** Tilt images or cards by 1-2 degrees to make the UI feel "hand-placed."
*   **Prioritize Negative Space:** 1st graders get overwhelmed. If a screen feels full, remove a container, don't shrink the text.
*   **Use Tonal Transitions:** Use the `tertiary` (mint) tokens exclusively for "Success" and "Correct" states to build a positive emotional association.

### Don’t:
*   **Don't use 100% black text:** Use `on-surface` (#302e30). It is softer on the eyes and feels more "editorial."
*   **Don't use sharp corners:** Nothing in the world of magic is sharp. Minimum radius is `sm` (0.5rem), but `xl` is preferred for interactive elements.
*   **Don't use Divider Lines:** If you need to separate content, use a `2rem` gap or a subtle shift from `surface` to `surface-container-low`.