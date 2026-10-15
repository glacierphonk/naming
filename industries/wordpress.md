# WordPress Plugins & Themes

Load this file when the naming brief says the product ships as a WordPress plugin, theme, block, or WooCommerce extension. It collects the platform rules that general naming guidance misses. The core files still apply: [principles.md](../principles.md), [anti-patterns.md](../anti-patterns.md), [availability.md](../availability.md).

One rule shapes everything else here: **on WordPress.org the slug is permanent.** You can change a plugin's display name whenever you like. You can never change its slug after approval.

---

## Platform Constraints

### Plugin slugs

WordPress.org generates the slug from the `Plugin Name:` header in the main plugin file (`Boaty McBoatface` becomes `boaty-mcboatface`). That one string then shows up in five places:

| Where | Example |
| ----- | ------- |
| Directory URL | `wordpress.org/plugins/boaty-mcboatface` |
| Folder on every install | `wp-content/plugins/boaty-mcboatface` |
| SVN repository | `plugins.svn.wordpress.org/boaty-mcboatface` |
| Translation text domain | `__( 'Hello', 'boaty-mcboatface' )` |
| WP-CLI | `wp plugin install boaty-mcboatface` |

Rules from the [Plugin Developer FAQ](https://developer.wordpress.org/plugins/wordpress-org/plugin-developer-faq/):

- English letters and Arabic numerals only. Lowercase, words joined by hyphens.
- No vulgarities, no version numbers, and no "WordPress" or "plugin" except in extreme cases.
- The slug can't start with someone else's trademark or project name unless you officially represent them. The team won't accept written permission from the owner either: if that permission is withdrawn later, the slug can't be changed and the plugin gets closed.
- You can edit the slug once after submitting. After approval it's fixed for good. The team turns down most requests to resubmit a plugin just to get a better slug, because users, reviews and install counts can't be moved over.
- Names can't be reserved. The plugin has to be complete when you submit it, and approved slugs that never get used can be handed to someone else ([guideline 16](https://developer.wordpress.org/plugins/wordpress-org/detailed-plugin-guidelines/#16-a-complete-plugin-must-be-available-at-the-time-of-submission)).
- A slug can clash with a plugin that isn't on WordPress.org at all. Updates are matched by folder name, so the directory blocks any slug that matches a privately distributed plugin with a real user base. Otherwise your code would be pushed to their users as an "update".

The display name is the flexible part: you change it in the main plugin file and `readme.txt`. The FAQ's advice is to make it "memorable and descriptive, while keeping it under 5 words." It also says the slug and display name are weighted equally in search. Ranking comes from a good readme, answering support threads, and reviews.

Since 2025 the Plugins team has used AI to flag duplicate or similar plugin names during review ([Make WordPress Plugins, May 2025](https://make.wordpress.org/plugins/2025/05/21/the-wordpress-ecosystem-is-growing-new-plugin-submissions-have-doubled-in-2025/)). The same post reports submissions up 87% on the previous year. A name one letter away from an existing plugin will probably be flagged before a human reviewer sees it.

### The "WP" prefix

"WP" is not a WordPress trademark, and the WordPress Foundation has said it isn't trying to register it ([WP Tavern, 2021](https://wptavern.com/wordpress-org-experiments-with-rejecting-plugin-submissions-with-the-wp-prefix-to-mitigate-potential-trademark-abuse)). Even so, since 2021 the upload checker has flagged new plugins whose name or slug starts with "WP". The goal is to stop "WP Something" turning into "WordPress Something" after approval. The rule is still disputed ([meta ticket #5868](https://meta.trac.wordpress.org/ticket/5868), [Plugin Check #464](https://github.com/WordPress/plugin-check/issues/464)), so check what the uploader currently does before you build a brand on it. Older names such as WP Mail SMTP (listed 2007) keep their slugs. For a new plugin, plan on a `wp-` slug being rejected.

The Foundation's [trademark policy](https://wordpressfoundation.org/trademark-policy/) also asks people not to use "WP" "in any way that confuses people", and names a hosting company as the example.

### Code prefixes

Your code prefix isn't the product name, but it gets used everywhere the product does. The Plugin Handbook's [best practices](https://developer.wordpress.org/plugins/plugin-basics/best-practices/) ask for a unique prefix on every global function, class, namespace, option and transient. It should be at least 4 letters (5 recommended) and not a common English word. `wp_`, `__`, `_` and `WordPress` are reserved. WooCommerce extensions must also avoid `Woo` and `WooCommerce`. Themes have the same 4-letter minimum ([theme requirements](https://make.wordpress.org/themes/handbook/review/required/)).

A name that shortens to a clean 4-5 letter prefix is easier to live with. The handbook's own example is "Easy Custom Post Types", which gives `ecpt_`.

### Theme names

From the [Theme Directory requirements](https://make.wordpress.org/themes/handbook/review/required/#7-naming-spelling-and-trademarks):

- Theme names can't use "WordPress", "Theme", or "Twenty" (reserved for the default themes).
- The team can turn down a name that's too close to an existing theme or brand.
- The slug is the name in lowercase with hyphens for spaces. It's also the folder name and must be the text domain.
- Theme names can't be reserved for future use.

### Blocks

A block has two names. The machine name in `block.json` is `namespace/block-name`: lowercase letters, digits and dashes, one slash, starting with a letter ([block metadata reference](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-metadata/)). The namespace should be your plugin slug or author name, never `core` or `wordpress`. The `title` is what people see in the inserter, and the docs ask you to keep it short.

Single-block plugins in the Block Directory have stricter rules ([Block Specific Plugin Guidelines](https://developer.wordpress.org/plugins/wordpress-org/block-specific-plugin-guidelines/)). The plugin title and the block title should say what the block does and should match, or nearly. The guidelines give "Rainbow Block", "Sepia Image Grid" and "Business Hours Block" as good names, and "PluginCo Inc Block", "Widget" and "Image Block" as bad ones. "Image Block" fails because nobody can tell it apart from the core Image block. Trademark rules apply to block names the same way they apply to plugin names.

This is the one place in WordPress where a descriptive name is the right call. A block title is a label in a list, not a brand. Save the creativity for the plugin name, and put search aliases in the `keywords` field of `block.json`.

---

## Trademark / Regulatory

| Mark | Owner | What it means for your name |
| ---- | ----- | --------------------------- |
| WordPress, WordCamp, BuddyPress, WP-CLI, Openverse | WordPress Foundation | Keep them out of product, company and domain names. "for WordPress" as a descriptor is fine ([policy](https://wordpressfoundation.org/trademark-policy/)) |
| Woo, WooCommerce and other Woo marks | Automattic | Never in a product, brand or feature name, and never in an ecommerce domain. Use "[Name] for WooCommerce" or "compatible with WooCommerce" ([Woo trademark guidelines](https://woocommerce.com/trademark-guidelines/)) |
| Any other plugin or service brand | Its owner | Your name can't open with it. The FAQ's example: "My Service Integration for Amazorn" passes, "Amazorn – My Service Integration" doesn't |

Workarounds get noticed. The FAQ names misspellings like "WuuCommerce" and "Face-Range" outright: they signal to the team that you'll cause guideline trouble later.

[availability.md](../availability.md#wordpress-naming-restrictions) covers the WordPress mark itself. This table adds the other marks you'll run into.

---

## WooCommerce Extensions

- New plugin slugs can't start with `woo`. The directory makes you use `wc` instead (FAQ, "Why can't I use someone's trademark/brand as my plugin name?"). Some older slugs, such as `woo-variation-swatches`, still start with `woo`.
- The WooCommerce Marketplace requires "Product Name for WooCommerce", not "WooCommerce Product Name" ([content style guide](https://developer.woocommerce.com/docs/woo-marketplace/content-style-guide)).
- That format puts your word first, so your first word has to do the branding work. "Variation Swatches for WooCommerce" follows the rule and is instantly forgettable. CartFlows, from the same top-250 list, shows the alternative: its own name, with WooCommerce pushed into the descriptor ("CartFlows – Funnel Builder & Checkout Plugin for WooCommerce").
- Payment and checkout extensions handle other people's money. A name that borrows a payment brand you don't own breaks the trademark rules and costs you trust in the same move.

---

## Audience Expectations

| Audience | Where they meet the name | What the name has to do |
| -------- | ------------------------ | ----------------------- |
| Site owners | The "Add Plugins" screen in wp-admin, which searches the WordPress.org directory | Name plus descriptor answers "does this do what I searched for?" in one line |
| Developers | Folder names, WP-CLI commands, text domains, function prefixes | Short, easy-to-type slug and a clean prefix |
| Agencies and freelancers | Recommending a stack to a client on a call or in a proposal | Survives being said out loud once |
| Theme buyers | Browsing screenshots | Sets a mood. Function matters less |

The site-owner row is where the tension sits. People search by function, so it's tempting to name by function. [principles.md](../principles.md) already argues against that. The WordPress-specific answer is the display-name descriptor, covered next, which lets you have a brand and still match searches.

---

## Naming Conventions

The figures below come from the 250 most popular plugins in the WordPress.org plugins API, pulled 2026-10-15. The directory listed 71,695 plugins that day.

### Brand plus descriptor is the default display name

119 of the top 250 display names use a separator to attach a descriptor to a short brand, for example "Yoast SEO – Advanced SEO with real-time guidance and built-in AI" and "Wordfence Security – Firewall, Malware Scan, and Login Security". In those 119, the brand part before the separator averages 2.3 words (median 2). It's WordPress's version of name plus tagline, and it's why a distinctive brand doesn't cost you search traffic. The descriptor holds the keywords and can be rewritten any time. The slug never changes.

Keep the descriptor honest. [Guideline 12](https://developer.wordpress.org/plugins/wordpress-org/detailed-plugin-guidelines/#12-public-facing-pages-on-wordpress-org-readmes-must-not-spam) treats keyword stuffing on directory pages as spam, and a descriptor listing twelve features reads exactly like it.

### Saturated patterns

| Pattern | In the top 250 | Note |
| ------- | -------------- | ---- |
| Slug starts with `wp-` | 23 | Mostly older plugins. New ones get flagged at upload |
| "for WooCommerce" in the display name | 10 | Required format for extensions, so it doesn't set anyone apart |
| "Easy" in the display name | 9 | Every one of them claims to be easy |
| "Simple" in the display name | 7 | Same problem |
| "All-in-One" in the display name | 6 | Usually followed by a list of the things it's all of |
| `-press` suffix in the slug | 5 | `tablepress`, `translatepress-multilingual`, `loginpress`, `wp-seopress`, `sg-cachepress` |

### Themes name differently

The most popular themes on WordPress.org (8,707 listed on the same date) use short, evocative words: Astra (Latin for "stars"), Kadence, Neve (Italian for "snow"), Hestia (Greek goddess of the hearth), OceanWP, Blocksy, GeneratePress. Theme naming is closer to fashion than to software, because buyers are picking a look. The exceptions name by relationship instead: default themes (Twenty Twenty-Five), builder companion themes (Hello Elementor), and starter themes from theme shops.

---

## Case Studies

### Yoast SEO: the slug outlives the name

The plugin was first listed in October 2010 as WordPress SEO. It's now Yoast SEO, but the slug is still `wordpress-seo`. "Yoast" is how Joost de Valk's first name sounds in Dutch. Rand Fishkin's shortcut for saying it was "just toast with a Y" ([Yoast history](https://yoast.com/about-us/history/)). The founder's name only worked once it was spelled the way English speakers say it. And when the display name moved off the WordPress mark, the slug couldn't follow. A new plugin couldn't get a `wordpress-` slug today at all.

### Akismet: a portmanteau with a story

Akismet is short for "Automattic kismet" ([WordPress.org history book](https://wordpress.org/book/2015/11/akismet/)). It launched in 2005 and has 5 million+ active installs. Kismet means fate. Our reading, not a documented intent: the name casts the filter as the fate waiting for spam. Either way it looks invented but breaks down into a word people already know. Its display name today, "Akismet Anti-spam: Spam Protection", follows the brand-then-function pattern. Building the parent company into the name only worked because Automattic was the parent.

### Wordfence: a compound that names the job

Wordfence is already in [case-studies.md](../case-studies.md) as a compound name. The WordPress angle: "Word" points at the platform without using the trademark, and "fence" says protection in five letters. 5 million+ active installs, with the display name "Wordfence Security – Firewall, Malware Scan, and Login Security" putting the brand first and the features after.

### Jetpack: a metaphor that stretched

Jetpack launched in 2011 as a bridge that gave self-hosted WordPress sites some WordPress.com features ([TechCrunch, 2011](https://techcrunch.com/2011/03/09/automattic-launches-jetpack-gives-wordpress-org-users-wordpress-com-perks/)). We haven't found a documented origin for the name, so this is analysis rather than history. A jetpack is something you strap on to go further than you could on your own, which fits a plugin that bolts cloud services onto a site. The product has since grown into security, backup and speed ("Jetpack – WP Security, Backup, Speed, & Growth"). A metaphor about extra capability grew with it. A feature name wouldn't have.

### Really Simple SSL and Smush: renamed, slug stuck

Really Simple SSL grew into a general security plugin. Its display name is now "Really Simple Security – Simple and Performant Security (formerly Really Simple SSL)", but the slug is still `really-simple-ssl`. Smush has been "Smush" for years, and its slug is still `wp-smushit` from its 2008 listing. The lesson: pick a slug for the brand you'll be in five years, not the first feature you ship. Putting a feature word in the slug is a bet the product never grows past it.

---

## WordPress Anti-Patterns

- **WP + feature** ("WP Image Optimizer"). Nothing distinctive about it, and a new submission will probably be flagged anyway.
- **[Feature]Press.** TablePress and LoginPress do fine, but the suffix is WordPress's answer to "-ify". It tells people this is a WordPress plugin, which the directory already told them.
- **Opening with someone else's brand** ("Elementor Pricing Tables", "WooCommerce Wishlist"). Blocked as a slug, and it implies a partnership you don't have. Flip it: "[Name] for Elementor".
- **Misspelled trademarks** (WuuCommerce, Face-Range). The FAQ names this exact trick.
- **A feature word in the slug.** See Really Simple SSL. Put the feature in the descriptor, where you can change it.
- **Tier words in the slug** (`-lite`, `-pro`, `-free`). The free directory plugin keeps that slug forever, even after you rethink your packaging.
- **Keyword-chain display names.** "WPForms – AI Form Builder for WordPress – Contact Forms, Payment Forms, Survey Form, Quiz & More" covers a lot of searches and nobody can repeat it. Keep the descriptor to one claim.
- **Generic block titles** ("Image Block", "Widget"). They disappear among the core blocks in the inserter.
- **Version numbers.** Not allowed in slugs at all.

---

## Territory Map

Publishing is the most crowded territory here, because WordPress itself lives in it (Word + Press). Start somewhere else. See [metaphor-mapping.md](../metaphor-mapping.md) for the technique.

| Sub-territory | Concepts | Already taken by |
| ------------- | -------- | ---------------- |
| **Printing and publishing** | press, type, quill, colophon, folio, imprint, galley | Gutenberg, every "-Press" plugin |
| **Building and craft** | scaffold, joist, mortar, keystone, trowel, blueprint | Elementor and the page builders |
| **Protection** | fence, gate, moat, sentry, lock, shield | Wordfence |
| **Lift and speed** | jet, rocket, tailwind, booster, slipstream | Jetpack, WP Rocket |
| **Mail and messengers** | courier, relay, carrier pigeon, dispatch, satchel | Mostly literal use so far (WP Mail SMTP, MailPoet). The metaphors are open |
| **Gardens and growth** | trellis, graft, prune, compost, greenhouse | SeedProd. Otherwise open in the top 250 |
| **Themes: sky, sea, place, myth** | stars, tides, coastlines, hearth gods | Astra, OceanWP, Sydney, Hestia |

---

## Naming Brief Additions

Add these to Step 1 when the product is for WordPress:

1. Plugin, theme, block, or WooCommerce extension? Each one has different rules above.
2. Free on WordPress.org, sold elsewhere, or both? The WordPress.org slug is the one you can never change.
3. Does it extend another plugin or service? Then the name takes the form "[Name] for [Their Brand]".
4. What 4-5 letter code prefix does each candidate give you?
5. Will the first feature still be the whole product in three years? If not, keep it out of the slug.

## Checking Availability

- **Plugin slug:** `curl -s "https://api.wordpress.org/plugins/info/1.2/?action=plugin_information&slug=NAME"` returns `{"error":"Plugin not found."}` when the slug is free. Or run `scripts/check-availability.sh NAME wp`.
- **Theme slug:** `curl -s "https://api.wordpress.org/themes/info/1.2/?action=theme_information&slug=NAME"` returns `{"error":"Theme not found"}` when the slug is free.
- **A free slug doesn't mean approval.** Search the directory for close names, because the similarity check will. Search GitHub for a privately distributed plugin using the same folder name.
