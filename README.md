# Minimal Liquid Shopify Theme

A small Shopify Online Store 2.0 theme built from Liquid, JSON templates, and plain CSS.

## Project structure

- `assets/products-grid.css` contains shared storefront, product grid, product card, and responsive styles.
- `config/settings_schema.json` defines the accent-color setting and theme metadata.
- `layout/theme.liquid` provides the HTML document, Shopify layout objects, stylesheet, and shared header/footer.
- `sections/products-grid.liquid` renders a merchant-selected collection with configurable heading, desktop columns, and product count.
- `sections/main-product.liquid` and `sections/main-collection.liquid` render product and collection pages from Shopify objects.
- `sections/header.liquid` and `sections/footer.liquid` provide store navigation and copyright.
- `snippets/product-card.liquid` renders one product's image, title, price, sale state, availability, and native add-to-cart form.
- `templates/` contains JSON templates for the homepage, product, and collection.

## Grid and product cards

The homepage JSON template includes `products-grid`. In the Theme Editor, select a collection and configure the heading, desktop columns, and maximum product count. The grid renders each item using `product-card`. The collection template uses the same snippet and provides pagination.

Cards use Shopify's first available variant ID in the native product form. Products without an available variant show a sold-out state instead of an add button. Sale prices appear when the selected variant's compare-at price is higher than its current price.

## Run locally

Install and authenticate with Shopify CLI, then run from this directory:

```sh
shopify theme dev --store shopify.com
```

The CLI prints a preview URL after connecting to the store.

## Assumptions and limitations

- Products, collections, navigation, and cart come from Shopify; there is no sample catalog or external API.
- Select a collection in the homepage grid settings before products can appear there.
- The product page variant selector submits the selected variant, but does not dynamically update the displayed price without JavaScript.
- Advanced filtering, predictive search, and JavaScript cart interactions are intentionally omitted.