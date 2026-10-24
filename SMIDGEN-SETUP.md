# Smidgen theme setup

This theme is Shopify's Horizon plus a Smidgen brand layer. Everything we added
is prefixed `sm-` so Horizon updates can still be merged in.

## What's included

| File | What it is |
| --- | --- |
| `assets/smidgen.css` | Brand colors, fonts, outlines, hard shadows, card hover, waves. Also restyles every Horizon button purple. |
| `snippets/stylesheets.liquid` | Loads Bayon, Londrina Solid and Rubik from Google Fonts, then `smidgen.css`. |
| `snippets/sm-game-card.liquid` | Game card (no add-to-cart). Whole card links to the game. |
| `snippets/sm-divider.liquid` | Outlined wave / zigzag / scallop / straight divider. |
| `snippets/sm-doodle.liquid` | Hand-drawn squiggle, spiral, zigzag, star, loop arrow. |
| `blocks/sm-game-facts.liquid` | Buy-box block: award sticker, preorder ship date, ages / players / play time tiles. |
| `sections/sm-hero.liquid` | Hero with sticker, purple highlight word, buttons, circle art, hand-written note. |
| `sections/sm-game-grid.liquid` | Game cards from a collection or hand-picked games. |
| `sections/sm-feature-cards.liquid` | Up to 6 icon cards. |
| `sections/sm-spotlight.liquid` | One game in a big color band. |
| `sections/sm-retailer-quotes.liquid` | Featured retailer quote with photo plus smaller quotes. |
| `sections/sm-pitch.liquid` | "Pitch us a game" checklist, email button, reply-time note. |
| `sections/sm-faq.liquid` | FAQ that hides empty rows, with FAQ structured data for search. |
| `sections/sm-newsletter.liquid` | Email signup (Shopify customer list, tagged `newsletter`). |
| `sections/sm-divider.liquid` | A standalone divider you can drop between any two sections. |
| `sections/sm-learn-to-play.liquid` | Product only: how-to video, steps, rules PDF. |
| `sections/sm-in-the-box.liquid` | Product only: components list. |
| `sections/sm-reviews.liquid` | Product only: Judge.me rating summary + slot for the Judge.me review widget. |
| `templates/index.json` | Homepage: hero, game grid, feature cards, spotlight, newsletter. |
| `templates/product.json` | Horizon product page + game facts + learn to play, in the box, FAQ, reviews. |
| `templates/page.help.json` | Help page: FAQ, contact form, pitch section. Assign to your Help page. |
| `templates/page.wholesale.json` | Wholesale page: hero, why stock us, retailer quotes, FAQ. |

Every `sm-` section (except the product-only ones) can be added to any page in
**Online Store → Themes → Customize → Add section**.

## Product fields to create

Shopify admin → **Settings → Custom data → Products → Add definition**.
Use namespace `smidgen` for all of these. Anything left empty is simply hidden.

| Name | Key (`smidgen.` …) | Type | Shows up |
| --- | --- | --- | --- |
| Hook | `hook` | Single line text | Game cards, spotlight |
| Card color | `card_color` | Color | Game card background |
| Badge | `badge` | Single line text | Card badge (overrides automatic Preorder / Coming soon / Sale) |
| Award | `award` | Single line text | Orange sticker in the buy box |
| Ages | `ages` | Single line text (e.g. `8+`) | Cards, buy box |
| Players | `players` | Single line text (e.g. `2–4`) | Cards, buy box |
| Play time | `play_time` | Single line text (e.g. `15 min`) | Cards, buy box |
| Ship date | `ship_date` | Single line text (e.g. `March 2027`) | Preorder note |
| How-to video | `howto_video` | URL (YouTube links embed) | Learn to play |
| How-to steps | `howto_steps` | Metaobject, list → `smidgen_step` | Learn to play |
| Rules PDF | `rules_pdf` | File | Learn to play button |
| Components | `components` | Single line text, list | What's in the box |
| FAQs | `faqs` | Metaobject, list → `smidgen_faq` | Product FAQ |

### Metaobjects to create first

Settings → Custom data → **Metaobjects → Add definition**:

- **Smidgen FAQ**, type `smidgen_faq`, fields `question` (single line text) and
  `answer` (rich text or multi-line text). Turn on "Storefronts" access.
- **Smidgen step**, type `smidgen_step`, fields `title` (single line text) and
  `description` (multi-line text). Turn on "Storefronts" access.

Because FAQs are entries you attach to a product, a game can have 2 or 9 and
none show up blank, and one FAQ can be shared by several games.

### Tags the theme understands

- `preorder`: Preorder badge on cards and in the buy box.
- `coming-soon`: "Coming soon" badge, price replaced with "Coming soon", link says "Get notified".

## Judge.me

1. Customize → open a product → **Smidgen · Reviews** section → Add block → Judge.me **Review widget**.
2. In Judge.me: Settings → Theme integration (Widget installation) → pick this theme → Reinstall.
3. Ratings on cards and in the summary box come from Shopify's standard `reviews.rating` /
   `reviews.rating_count` fields, which Judge.me keeps in sync.

## Pages

- Help page: Online Store → Pages → your Help page → Theme template → `page.help`.
  Set the pitch email in Customize → Smidgen · Pitch us a game.
- Wholesale page: same, template `page.wholesale`. Add the Faire link to the hero's first button.
