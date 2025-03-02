# Custom Templates



The Stencil framework allows theme developers and merchants to assign custom layout templates to storefront pages of the following types:

* Brand
* Category
* Product
* Page

<!-- theme: warning -->
> #### Stencil versus blueprint themes
> If you are migrating from BigCommerce's legacy Blueprint themes framework, please keep in mind these differences in how Stencil handles custom templates:
> * The brand option is entirely new in Stencil. If you are running on a Blueprint theme, you will not be able to create a custom template for brand pages.
> * Unlike Blueprint, Stencil does not require that custom template file names start with an underscore.
> * In the current Stencil release, you must create and bundle custom templates using Stencil CLI before you can upload the custom templates to stores. However, once you have created and uploaded templates, authorized store users can assign them to storefront pages through the control panel.


## Authoring a custom template

As a theme developer, you must first create a custom page. Create the custom page by going to **Storefront** > **Web Pages** in the control panel. Then create the custom subdirectory in the `templates/pages` directory, and the four required subdirectories inside of it (brand, category, product, page). Creating these subdirectories will result in the following directory paths:

* templates/pages/custom/brand
* templates/pages/custom/category
* templates/pages/custom/product
* templates/pages/custom/page

Next, create the template HTML files, and then place them in the appropriate `templates/pages/custom/` subdirectories corresponding to the types listed above.

<!-- theme: warning -->
> #### File permissions required
> Be sure to set permission `755 (drwxr-x-r-x)` on any new subdirectories that you add. Also, be sure to set permission `644 (rw-r–r–)` on any new files that you add.
> Without these permissions, running your theme locally will fail with multiple error messages. Bundling your theme will also fail, blocking it's upload to a store.

## Local mapping and testing

To test your custom templates locally, you must edit your `.stencil` or `config.stencil.json` file (if using Stencil V3.1 release or later) to create mappings between each local template and a corresponding URL. Within the `.stencil` file or `config.stencil.json` file, look for the following section:

```json title="customLayouts properties config.stencil.json" lineNumbers
"customLayouts": {
    "product": {},
    "brand": {},
    "category": {},
    "page": {}
  }
```

In this section, you would populate keys to create mappings. As a simple example, assume that you have a product custom template named alternate-product.html, and you want to see that template locally at the URL: http://localhost:3000/test-url/. In this case, you must populate the product key as follows:

```json title="Populate product key" lineNumbers
"product": {
    	"alternate-product.html":"/test-url/"
},
```

### Expanded mapping example

Here is a more-complete example in which the brand, page, and category keys are also populated:

```json title="Populated brand, page, and category keys" lineNumbers
{
  "normalStoreUrl": "http://cornerstone-light-demo.mybigcommerce.com",
  "port": 3000,
  "username": "stencil",
  "token": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "customLayouts": {
    "product": {
      "custom-product.html": "/custom-product/"
    },
    "brand": {
      "custom-brand.html": "/brands/custombrand/"
    },
    "page": {
      "custom-page.html": "/custom-page/"
    },
    "category": {
      "custom-category.html": "/custom-category/"
    }
  }
}
```

### Mapping requirements and options

The requirements and options for the `.stencil` or `config.stencil.json` (if using Stencil V3.1 release or later) mapping examples above are as follows:

* Each mapped URL must be a URL for a brand, category, product, or static page that is already configured in the store. This means that you cannot insert a placeholder URL that is an arbitrary string of letters, such as /abcdefghijklmnop/.

* Each URL’s trailing slash is optional.

* The HTML files must reside in either the brand, category, product, or page subdirectories.

* All brand URLs are nested under the /brands/ parent. Use URL encoding with brand URLs.

* That parent for brand URLs is /brands/ (plural), while the corresponding subdirectory for HTML files is /brand/ (singular).

* After editing your `.stencil` file or `config.stencil.json` files (if using Stencil V3.1 release or later), you must restart stencil to see your changes locally. Enter `stencil start` in the command prompt, appending any appropriate switches for your workflow (e.g.: `stencil start -e -n`).

### Why these URL Requirements?
When you create a local custom template page for products, you expect that page to have access to all Stencil product objects. However, the server cannot readily determine the page type of each local custom template. So we give it a hint by instructing the server to look at the page type of the URL where you mapped the template.

In the above `.stencil` or `config.stencil.json` (if using Stencil V3.1 release or later) configuration example’s final entry, the server will look at the URL `/custom‑category/` within the store, deduce that the page type is category, and return a category context to Stencil CLI. This allows Stencil CLI to properly display the page in the browser when you visit `http://localhost:3000/custom‑category/` locally, or when shoppers visit the corresponding public store page.

### Mapping Multiple URLs
Beyond the single URL mapped to each template in the above examples, you have the option of mapping an array of URLs to each template. This is shown in the following example for the product template:


```json title="Map multiple URLs" lineNumbers
  "customLayouts": {
    "product": {
      "featured-product.html": ["/special-product-one", "/special-product-two"],
      "clearance-product.html": "/clearance-product"
    },
    "brands": {},
    "categories": {},
    "page": {}
  }
```

## Specifying custom front matter

You can specify front matter on a custom template if you only need to render certain resources (such as 'New Products') on that page. Specifying only the attributes you need will reduce page load time. If you don't explicitly specify front matter for your custom template, the front matter for the default page template will be available. See [Using Front Matter](/stencil-docs/storefront-customization/using-front-matter) for more information on using front matter.

## Theme upload

Finally, you must bundle and push the theme to BigCommerce. See [Bundling and Pushing a Theme](/stencil-docs/deploying-a-theme/bundling-and-pushing) for instructions on how to achieve this.

## Troubleshooting template authoring

Here are solutions to some known problems in locally authoring and testing custom templates:

### Viewing Custom Brand Templates Locally

If you are having trouble viewing custom brand templates locally, ensure that the URL used in your `.stencil` or `config.stencil.json` file (if using Stencil V3.1 release or later) is of the form: /brands/brandname. This is necessary because all the brand pages are located under the /brands/ URL path. Also, bear in mind that currently, all brand URLs are Unicode-encoded. So, for example, you should replace a hyphen with: %252d.

### Outdated Stencil CLI

If you have an old version of Stencil CLI installed, it might lack support for custom templates. You can easily update your CLI by executing the following command:

`npm install -g bigcommerce/stencil-cli`

## Applying custom templates to pages

Once the developer has uploaded a theme to BigCommerce, the merchant (or other authorized store user) can assign the custom templates to individual store pages in the BigCommerce Control Panel in order to make it live on the storefront.

If you are ready to apply your custom template to the live BigCommerce storefront, see [Applying a Custom Template](https://support.bigcommerce.com/s/article/Stencil-Themes#custom-template) (BigCommerce Knowledge base).

## Resources

### Related Articles
* [Blueprint Themes](/legacy/blueprint-themes)
* [Applying a Custom Template](https://support.bigcommerce.com/s/article/Stencil-Themes#custom-templates) (BigCommerce Knowledge Base)

### Additional Resources

* [Custom Templates Video Demo](//youtube.com/watch?v=qgaDX7bhmd8) (YouTube)
