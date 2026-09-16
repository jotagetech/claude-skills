# Shape: local-multibrand-retail-showcase

A local, single- or few-location retailer carrying a genuinely broad, multi-brand, multi-audience assortment (commonly footwear, but the pattern generalizes to any local retailer with real catalog breadth), with no digital storefront, no prices published online, and no cart or checkout. Every purchase path resolves into a human conversation, typically WhatsApp, a phone call, or an in-store visit. The reader arrives already knowing what a shop like this is; the page's job is to make the real range and the shop's local, personal character legible online, then route the reader into that conversation.

This shape sits between `ecommerce-standout` and `ecommerce-catalog` but is neither. `ecommerce-standout` assumes a narrow line, a few SKUs, and air-led minimalism; it collapses under a genuinely broad, multi-brand, multi-audience assortment, understating real breadth as if it were a single curated object. `ecommerce-catalog` assumes a priced, filterable, cart-and-checkout storefront with search, faceted filtering, stock signals, and a promotional deal surface; none of that exists for this business, and building it in would misrepresent a shop that has no digital commerce at all. Reaching for either stub by analogy alone produces a page that either hides the shop's real depth or promises transactions the shop cannot fulfill.

## Status

Reasoned default, built from a single real case (a local multi-brand footwear retailer) against the seven-dimension framework, not yet validated against a `competitor-experience-audit` for this micro-vertical. Treat the conventions below as a strong starting point to verify against the next few builds in this shape, the same way the `ecommerce-catalog` defaults were sharpened after repeated builds exposed the density gap that became convention 11 there.

## 1. Primary-task prominence

**Primary task:** starting a conversation with the business (WhatsApp, phone, or a comparable direct channel), not completing a purchase. There is no transaction to complete online.

**Build conventions:**
- The conversation CTA is the largest, earliest interactive element in the hero, exactly as a "buy" or "book" CTA would be in a shape that has one.
- The CTA is sticky to the chrome across the whole scroll, labeled (not icon-only), so a reader who has scrolled deep into the merchandising sections never loses it.
- The CTA recurs at the merchandising level: inside category or audience sections, not only in the hero and the footer. This is the direct analog of "add to cart" staying reachable on every product in a catalog shape; here the reachable action is "ask about this."
- No competing primary CTA. Newsletter signup, social-follow prompts, or a generic "contact us" form are secondary at most; a single conversation channel should read as the one path.

## 2. Layout register and density

**Register:** photo-led maximalism, denser than `ecommerce-standout`'s air-and-image minimalism, but without the transactional density (facets, spec tables, price grids, stock badges) that makes `ecommerce-catalog` read as a working storefront. The density comes from real photographic breadth and category range, not from data density.

**Build conventions:**
- The hero itself should carry more than one real photograph, or a grouped image treatment, rather than one restrained, mostly-empty hero shot. A single-hero-image, air-heavy layout understates a business whose real differentiator is breadth.
- Whitespace separates grouped photo blocks for legibility, but is not the load-bearing device the way it is in a narrow-line premium shape. The field this shape serves is closer to "a lot to show, shown with intent" than "one object, treated with reverence."
- No facets, filters, sort controls, price grids, or stock/inventory badges. Their presence would misrepresent a business with no structured, priced inventory to filter or count.
- Route the actual color, type, and aesthetic register to `creative-direction` and `design-standards`; this shape only fixes that the register should read as warm and grounded rather than either sparse-premium or dense-utilitarian.

## 3. Merchandising and category surface

**Conventions:**
- Primary cut: **by audience** where the business genuinely serves distinct audiences (women's/men's/children's is the common case; a comparable business might cut by use-case or department instead). This should mirror how the business itself talks about its own offering (its own bio, signage, or self-description), not an invented taxonomy.
- Secondary cut, inside each audience or department: **by occasion or category**, built from what the real, observed assortment actually supports (everyday, going-out, seasonal/weather-driven categories), not a generic category list assumed in advance.
- No SKU count, part count, or "X items in stock" figure. This shape has no structured inventory to count, and inventing a number would be a fabrication the `ecommerce-catalog` shape's honest inventory-depth signal is not meant to license here. Depth is signaled instead through brand or supplier diversity (a "brands carried" row) and duration in business (a founding year), both real and verifiable facts a shop like this typically has.
- If a named audience or category segment lacks real photographic material to fill it (a genuine content gap, not a design choice), do not backfill with stock photography. Either hold that segment to a shorter, text-led module that still routes to the conversation CTA, or flag the gap for real photography to be sourced before ship. Stock imagery standing in for a segment's real product photos breaks the shape's core trust proposition, which is that everything shown is real.

## 4. Navigation and search paths

**Paths this shape carries:**
- By audience or department: primary, always present, via anchor navigation and the ordered sections themselves.
- By occasion/category: secondary, expressed as in-page grouping inside each audience or department section, not as a separate nav tier or filter control.
- To the conversation channel: universal and persistent. Every other path exists to feed this one.
- Search: absent. There is no structured, priced catalog to search against.
- Account, cart, checkout: absent. Including any transactional chrome misrepresents a business that has none.

**Build conventions:**
- Anchor navigation (in-page jumps) is the typical implementation, since this shape is commonly a single, sectioned landing page rather than a multi-page catalog with its own URLs per category.
- The conversation CTA's prominence should not be diluted by treating it as one of several equal chrome-level actions; it is the one action this whole shape exists to produce.

## 5. Brand register and conviction

**Typical postures:** warm and personal (a shop that knows its regulars), grounded-local, or craft-forward, depending on the business; cross-reference `creative-direction` and `brand-archetype-system` for the controlled vocabulary rather than inventing new register language here.

**Build conventions:**
- The register set for the hero must carry into the category sections, the story module, the trust band, and the footer. A warm, personal voice that turns generic and corporate in the CTA microcopy or the footer is a composition failure, not a brand failure.
- Voice consistency matters most in the recurring conversation CTA: "ask about this" phrased warmly in the hero and phrased as a bare, generic "Contact Us" in a category section reads as two different businesses on one page.
- Imagery posture stays consistent: if the hero uses real, unstaged photography, the category sections and the story module should too. This shape does not switch to stock or illustrated imagery anywhere.

## 6. Trust and conversion signals

**Signals this shape carries:**
- Duration in business (a founding year or "since" line), when real and confirmed.
- Brands or suppliers carried, listed plainly, limited to what is actually confirmed; an unverified brand mention should not be included on the strength of a single third-party snippet.
- A real aggregate rating and review count, shown modestly, never restyled as more significant than it is, and never paired with fabricated or invented testimonial quotes.
- Physical address, phone, and hours, presented with appropriate caution where any detail (an unusual closing hour, for instance) is itself unverified beyond a single public listing; the module should not overstate confidence it does not have.
- A delivery, shipping, or service-area claim, when the business makes one, surfaced as a supporting line rather than a headline promise.
- The real, unwatermarked photography itself is a trust signal in this shape: it substitutes for the reviews-and-specification trust stack a priced catalog would otherwise need, and its absence anywhere on the page (a stock photo standing in) undercuts the whole page's credibility, not just one section.

**Explicitly excluded, categorically, not case-by-case:** fabricated urgency ("only a few left," countdown timers), invented testimonials, price or discount graphics of any kind, and stock photography of the goods. These are load-bearing exclusions for this shape's credibility, not optional polish decisions.

## 7. Recurring vertical conventions (the synthesis)

A credible local-multibrand-retail-showcase build carries these conventions:

1. A conversation CTA (not a purchase CTA) that owns the hero as the dominant, earliest interactive element.
2. That CTA stays reachable (sticky chrome) across the full scroll.
3. **(Density-bearing)** The hero carries more than one real photograph or a grouped image treatment; a single restrained hero image under-represents this shape's real differentiator.
4. **(Density-bearing)** A trust/credibility band (duration in business, brands/suppliers carried, real rating) appears early, ahead of the merchandising sections.
5. Merchandising is grouped by audience or department first, occasion/category second, not a flat, undifferentiated grid and not a priced, filterable catalog.
6. No price, discount graphic, or fake-urgency device appears anywhere on the page.
7. No cart, checkout, account, or search chrome anywhere on the page; none of it exists for the business this shape serves.
8. The conversation CTA recurs at the merchandising level (inside category/audience sections), not only in the hero and footer.
9. Only real, unwatermarked photography is used across every section, including any segment with thinner real material; a genuine content gap is flagged, not filled with stock imagery.
10. A location/hours/contact module exists, distinct from the persuasive trust band, and handles any unverified detail (hours, a legal-entity question) with visible caution rather than false confidence.
11. The real rating or review signal, where one exists, is shown honestly and modestly, with no fabricated testimonial carousel dressing it up as more than it is.
12. The footer repeats the practical trust information (address, hours, brands/suppliers, social profile) and contains no dead or invented links to features the business does not have.

**Threshold.** A build hitting all twelve is at the bar for this shape; conventions 3 and 4 are the density-bearing pair (their absence is what makes an otherwise-honest build read as an under-filled brochure rather than a shop with real depth), and conventions 6, 7, and 9 are the honesty-bearing trio (their violation is what makes a build actively misrepresent a business that has no digital commerce). Missing a density-bearing convention reads as thin; missing an honesty-bearing convention reads as dishonest, a more serious failure than thin, and should block ship rather than wait for a polish pass.

---

## Common positioning wedges in this shape

From the one real case this shape has been built against so far:

- **Real breadth as the wedge against a sparse, single-hero-image treatment.** A shop with genuine multi-brand, multi-audience depth loses its actual differentiator if it is composed as if it were a narrow, single-line premium brand. Showing the real range, grouped with intent, is the position to hold.
- **Honesty about having no online storefront, instead of a thin imitation of one.** A build that fakes a price, a cart, or a stock signal to look more like a "real" ecommerce site is less credible than one that plainly shows real goods and asks the reader to talk to a person, which is how this business actually operates.
- **Duration and brand diversity as the depth signal, in place of a catalog-size figure.** This shape cannot honestly claim "X items in stock"; a founding year and a real brands-carried list do the same credibility work without fabricating a number.

Pick the wedge that matches the specific business's real evidence; do not assume all three apply to every build in this shape.
