# Changelog

Human-readable log of what changed in the onboarding prototype, for product review. Updated at each local commit — most recent first.

## 2026-09-18 — Cosmix build: the current prototype, filled with Cosmix

This fork now runs on the same code as the main (Urban Performance) prototype, with every piece of brand content swapped for Cosmix. Nothing in the flow, the layout or the interactions differs from main; only what the cards, stories and setup say.

**What is the same as main (new to this fork)**
- The first screen's three paths: enter a URL, "See ShopOS in action" (7 demo brands), "I don't have a Brand" (3-question wizard).
- The loading state's Brand Memory column (editable cards, discard on edit, the Shopify connect row) and the one-line status under each column title.
- The single feed and the Pro deck show the same set of cards, interleaved automatically, with the Meta and Shopify connect prompts anchored to specific cards.
- Card menu and dock copy: "Copy link to share", "Tune Feed", "Jam with Team". Finish screen reads "Your brand's feed is ready".

**What is Cosmix**
- Build My Team with an empty field opens cosmix.in; the setup rail shows cosmix.in and reads the real catalog size (80 products).
- Brand Memory is written from cosmix.in: About the brand, Brand guidelines (the real wordmark, the theme's green / terracotta / cream, Recoleta headings with Manrope body), Voice and tone, Company (founded 2019 by Vibha Harish and Soorya Jagdish, Bengaluru, in-house manufacturing, Marico's 60% stake at a ₹375 cr valuation), Product catalog, Product information, Audience, Industry leaders (The Whole Truth, OZiva, Kapiva, Wellbeing Nutrition). Any other host still gets the generic placeholder set.
- All 22 feed and deck cards, the four stories, History, the CRM drawer copy and the column status streams carry the Cosmix copy and imagery from the previous Cosmix build, unchanged.
- The Cosmix spiral mark sits in the deck sidebar; the workspace badge reads C / Cosmix.

**Media rules kept from the previous Cosmix build**
- Every post image renders as a square, cropped from the top, including landscape art. A card can ask for its image to be fitted rather than filled (the nutrition-panel card), and a chart card can carry supporting images as a carousel (the discovery-prompts card).

**Housekeeping**
- Cosmix pack shots that still sat under Point Taken filenames (ptup-*, pt-*) are renamed cx-*; the unused Urban Performance photography is not carried over.
- Known gap: the feed cards say "5 of 40" products (copy from the earlier Cosmix build) while the store, and the setup rail, count 80.

## 2026-09-18 — Ring card: drop the "Health" tag, center the score

The number in the middle of the Apple-Health-style ring card had a small "Health" label above it. Removed it and let the score sit centered in the rings on its own.


## 2026-09-18 — Drop the dial-variant brand-health card; fix the connect-card anchors it broke

The dial read of the brand-health card is commented out of `POSTS` (three passes at the shape, none of them right — kept, not deleted, in case it's worth another attempt). That shifted every index after it, which broke the meta/Shopify connect-card placement in the feed: it was anchored to `POSTS[1]`/`POSTS[3]` by position, and `POSTS[3]` no longer pointed at the card it was supposed to. Anchored by title instead, so it can't silently point at the wrong card again — and while fixing it, moved the Shopify prompt to follow the Cloud Soft Tee storefront post instead of the old dial card, which fits the "publish the changes" copy better anyway.


## 2026-09-18 — Feed and Pro deck now show the same cards

The single-column feed was quietly a subset of what Pro mode's columns show: it was missing one image post, one data-led post, and all eight cards that used to be deck-only, twelve cards short of the full twenty-two. The feed's card order now comes from the same three lists the deck reads (interleaved for rhythm rather than dumped in as one long block), so any card added to those lists appears in both places automatically. Signals stays deck-only, as intended — everything else is now identical either way you look at the feed.


## 2026-09-18 — Feed card copy: clearer labels

- Card menu: "Copy link" is now "Copy link to share"
- Bottom-right dock: "Tune" is now "Tune Feed", "Jam" is now "Jam with Team"


## 2026-09-18 — Onboarding: "Your brand's feed is ready"

The finish-screen headline is now "Your brand's feed is ready" (was "Your feed is ready").


## 2026-09-18 — Brand Memory: discard on edits, no scrolling, fewer and clearer cards

**Discard, not just save**
Editing a card now shows a check and a cross, not just a check. Check keeps what you typed; the cross puts the card back exactly as it was — text and any tags you removed while editing.

**Toned down the edit chrome**
No background box behind the text you're editing, and no background on the check/cross buttons — just the icons, so editing doesn't call more attention to itself than the card's content does.

**Tag crosses only take up space while the card is being edited**
A tag pill used to reserve room for its remove-cross at all times (revealed on hover). Now the cross has zero width until the card enters editing state, then the pill opens up to show it. No dead space on cards you're not touching.

**Dropped the fixed-height, scrolling cards**
Cards were pinned to one height with an internal scrollbar; nothing in them was ever long enough to need it. Cards now size to their own content — short cards are short, longer ones are taller.

**Fewer cards, clearer purpose**
Cut Pricing, Channels, Drops and collections, standalone Business landscape, Growth direction, and the "Still missing" card. Merged the two Product information cards into one. Company now carries a bit more of what Business landscape used to say, since that's where it belongs. Catalog is now "Product catalog" and says plainly what's being pulled together. Audience keeps its text, loses its (repetitive) tags. Competitors keeps its tags, loses its description — just the names. Voice and tone moved up next to the new "Brand guidelines" card (the old untitled Brand Kit card now has a name). Nine cards total, down from fifteen.

**New: a Shopify connect row**
Reuses the exact connector-row shape from the Signals column — logo, name, one line, a white Connect button — with copy written for this moment ("Connect Shopify for detailed product analytics."). It's the one card in the column that isn't a finding, so it carries no edit icon; clicking Connect gives it its own short, self-contained "Connecting → Connected" state.


## 2026-09-18 — Brand Memory: editable, scrollable cards during loading

**The first column of the loading state ("Brand Memory") is now editable**
Each card is a fixed height and scrolls inside itself if the copy runs long, so editing one card never pushes the others down the column. A pencil icon in the top-right corner opens editing — click it and the card's description becomes an input; click the checkmark (or press Enter) to save, or press Escape to cancel. A soft fade at the bottom of a card is the cue that there's more to scroll to.

**New: generic, reusable card titles**
Card titles are no longer one-off headlines specific to a single demo brand (e.g. "The Flex henley is leading the brand right now"). They're now a fixed set of category labels — "About the brand," "Product information," "Business landscape," "Growth direction" — that make sense for any brand ShopOS reads. The label stays put; only the finding underneath it (what was actually read off the store) is what gets edited.

**Only text cards are editable**
The Brand Kit card (logo, colors, typeface swatches) carries no edit icon — it isn't a text finding, so there's nothing to type into.

**Confirmed: this column only ever appears during loading**
It's built fresh each time onboarding runs and is never carried into the finished feed — nothing else needed to change here, but flagging it since it came up as a question this session.

## 2026-09-17 — Onboarding flow: two new paths, a product-first wizard, and polish

**New: two more ways to start, right on the first screen**
Below the "Enter your store URL" field, there are now two extra options: **"See ShopOS in action"** and **"I don't have a Brand"**. Typing a real URL into the field automatically hides these two options (typing anything else does not); the field also silently blocks characters that can't appear in a URL as you type.

**New: "See ShopOS in action" → pick a demo brand**
Clicking it opens a brand-picker screen with 7 sample brands (Dunder Mifflin, Los Pollos Hermanos, Chocolate Frogs, Fishwife, Miu Miu, Vacation Inc., Dorsey). Picking one and continuing runs the same setup/loading experience as a real store. Only the parts of the screen that actually change (the subtitle, the body, the button label) animate — the logo and headline never move.

**New: "I don't have a Brand" → a 3-question wizard**
Instead of jumping straight to setup with no information, this now asks three quick questions, one at a time: what's your product, who's your audience, what should we call your Brand. Answering one reveals the next; each answered question collapses to show just the answer with a pencil icon to go back and edit it. Editing an earlier answer discards whichever questions came after it, so the flow always makes sense. The brand name you type here now also shows up in the "URL" field on the loading screen, instead of a generic placeholder.

**Fixes and polish**
- The "Build My Team" button on the first screen always shows in its active white state — it no longer greys out when the input is empty.
- Clicking anywhere inside a text field (not just precisely on the text) now focuses it.
- The "Try your own Brand" button on the brand-picker screen is no longer stretched to match the width of the button next to it — it sizes to its own label.
- Fixed a background color mismatch (was pure black, should be the site's standard near-black) on both the URL screen and the brand-picker screen.
- Fixed a couple of small spacing/alignment misses in the new 3-question wizard so its icons and text line up with the rest of the screen.
- Set up version control for this prototype so changes can be tracked going forward.
