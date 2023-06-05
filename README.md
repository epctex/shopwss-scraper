# Actor - ShopWSS Scraper

## ShopWSS scraper

ShopWSS, also known as Warehouse Shoe Sale, is a U.S.-based retailer that specializes in selling shoes, clothing, and accessories. The company sells a variety of items from numerous brands, including Nike, Adidas, Converse, and Puma. In addition to shoes, ShopWSS also sells clothing items like jackets, t-shirts, and pants, as well as accessories such as hats, socks, and bags.

Since ShopWSS doesn't provide a good and free API, this actor should help you to retrieve data from it.

The ShopWSS data scraper supports the following features:

-   Collections - You can fetch all products from a given collection.

-   Search - You can use the search input and fetch all products for a given keyword

-   Product detail - Fetch all product details including title, descriptio, images, variants, options and many more

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/shopwss-scraper/issues).


## Input Parameters

The input of this scraper should be JSON containing the list of pages on ShopWSS that should be visited. Required fields are:

- `search`: (Optional) (String) Keyword that you want to search on ShopWSS.

- `startUrls`: (Optional) (Array) List of ShopWSS URLs. You should only provide collections, search urls and product detail urls.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as argument and returns object with data.

- `customMapFunction`: (Optional) (String) Function that takes each objects handle as argument and returns object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to have a scrape over a specific list URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detail requests. If actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.01-0.03 compute units.

### ShopWSS Scraper Input example

```json
{
  "startUrls": [
    "https://www.shopwss.com/products/t770_nkwh_nk_xvh?variant=39713821065271",
    "https://www.shopwss.com/collections/classic-womens"
  ],
  "search": "nike",
  "proxy": {
    "useApifyProxy": true
  },
  "endPage": 5,
  "maxItems": 10
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## ShopWSS Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this ShopWSS actor.

## Scraped ShopWSS Properties

The structure of each item in ShopWSS looks like this:

### Item Detail

```json
{
  "type": "product",
  "url": "https://www.shopwss.com/products/a03061c",
  "id": "gid://shopify/Product/6669777535031",
  "slug": "a03061c",
  "availableForSale": true,
  "collections": [
    {
      "id": "gid://shopify/Collection/153375735863",
      "title": "In Stock"
    },
    {
      "id": "gid://shopify/Collection/153375834167",
      "title": "Classic"
    },
    {
      "id": "gid://shopify/Collection/153376260151",
      "title": "Size 3.5"
    },
    {
      "id": "gid://shopify/Collection/153376325687",
      "title": "Converse Shoes"
    },
    {
      "id": "gid://shopify/Collection/153376587831",
      "title": "Size 9.0"
    },
    {
      "id": "gid://shopify/Collection/153377669175",
      "title": "Size 5.5"
    },
    {
      "id": "gid://shopify/Collection/153377800247",
      "title": "Size 10.0"
    },
    {
      "id": "gid://shopify/Collection/153378193463",
      "title": "Shoes"
    },
    {
      "id": "gid://shopify/Collection/153378455607",
      "title": "On Sale"
    },
    {
      "id": "gid://shopify/Collection/153378914359",
      "title": "Size 7.5"
    },
    {
      "id": "gid://shopify/Collection/153380749367",
      "title": "Size 8.5"
    },
    {
      "id": "gid://shopify/Collection/153381568567",
      "title": "Women's Shoes"
    },
    {
      "id": "gid://shopify/Collection/153381797943",
      "title": "womens-shoes-classic"
    },
    {
      "id": "gid://shopify/Collection/153382420535",
      "title": "Women"
    },
    {
      "id": "gid://shopify/Collection/153382682679",
      "title": "Size 6.5"
    },
    {
      "id": "gid://shopify/Collection/153382879287",
      "title": "Size 4.5"
    },
    {
      "id": "gid://shopify/Collection/153383665719",
      "title": "$60 TO $80"
    },
    {
      "id": "gid://shopify/Collection/153384091703",
      "title": "Out of Stock"
    },
    {
      "id": "gid://shopify/Collection/155946745911",
      "title": "Shoes, Clothing, & Accessories"
    },
    {
      "id": "gid://shopify/Collection/261554503735",
      "title": "Women's Shoes, Clothing, & Accessories"
    }
  ],
  "createdAt": "2022-06-20T23:31:18Z",
  "publishedAt": "2023-01-25T00:33:09Z",
  "updatedAt": "2023-06-05T22:43:47Z",
  "description": "CONVERSE RUN STAR HIKE HI-TOP SHOES Upgrade your hi-tops and never look back. Get this chunky platform and jagged rubber sole to put an unexpected twist on your everyday Chucks. Details like a canvas build, rubber toe cap, and Chuck Taylor ankle patch stay true to the original, while a molded platform, two-tone outsole, and rounded heel give off futuristic vibes. Canvas high top platform sneakers. SmartFOAM sockliner for cushioning. Two-tone, exaggerated rubber outsole. Iconic Chuck Taylor ankle patch.",
  "descriptionHTML": "<h2>CONVERSE RUN STAR HIKE HI-TOP SHOES<\/h2><p> <\/p><p>Upgrade your hi-tops and never look back. Get this chunky platform and jagged rubber sole to put an unexpected twist on your everyday Chucks. Details like a canvas build, rubber toe cap, and Chuck Taylor ankle patch stay true to the original, while a molded platform, two-tone outsole, and rounded heel give off futuristic vibes.<\/p><ul>\n<li>Canvas high top platform sneakers.<\/li>\n<li>SmartFOAM sockliner for cushioning.<\/li>\n<li>Two-tone, exaggerated rubber outsole.<\/li>\n<li>Iconic Chuck Taylor ankle patch.<\/li>\n<\/ul>",
  "vendor": "CONVERSE",
  "quantity": 182,
  "tags": [
    "$60 TO $80",
    "A03061C",
    "BROWN",
    "Classic",
    "CONVERSE",
    "eligible-discount",
    "eligible-for-promotions",
    "new-markdown",
    "on-sale",
    "Platform",
    "Run Star Hike Hi",
    "show-all",
    "Womens",
    "womens-canvas",
    "womens-shoes",
    "womens-shoes-classic"
  ],
  "variants": [
    {
      "id": "gid://shopify/ProductVariant/40027207368759",
      "slug": "a03061c",
      "availableForSale": true,
      "barcode": "194434095296",
      "isInStock": true,
      "price": "69.98",
      "availableQuantity": 39,
      "isRequireShipping": true,
      "sku": "11155400021",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "06.0"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207401527",
      "slug": "a03061c",
      "availableForSale": true,
      "barcode": "194434095302",
      "isInStock": true,
      "price": "69.98",
      "availableQuantity": 16,
      "isRequireShipping": true,
      "sku": "11155400022",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "06.5"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207434295",
      "slug": "a03061c",
      "availableForSale": true,
      "barcode": "194434095319",
      "isInStock": true,
      "price": "69.98",
      "availableQuantity": 10,
      "isRequireShipping": true,
      "sku": "11155400023",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "07.0"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207467063",
      "slug": "a03061c",
      "availableForSale": false,
      "barcode": "194434095357",
      "isInStock": false,
      "price": "69.98",
      "availableQuantity": 0,
      "isRequireShipping": true,
      "sku": "11155400024",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "09.0"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207499831",
      "slug": "a03061c",
      "availableForSale": false,
      "barcode": "194434095364",
      "isInStock": false,
      "price": "69.98",
      "availableQuantity": 0,
      "isRequireShipping": true,
      "sku": "11155400025",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "09.5"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207532599",
      "slug": "a03061c",
      "availableForSale": false,
      "barcode": "194434095326",
      "isInStock": false,
      "price": "69.98",
      "availableQuantity": 0,
      "isRequireShipping": true,
      "sku": "11155400026",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "07.5"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207565367",
      "slug": "a03061c",
      "availableForSale": true,
      "barcode": "194434095333",
      "isInStock": true,
      "price": "69.98",
      "availableQuantity": 5,
      "isRequireShipping": true,
      "sku": "11155400027",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "08.0"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207598135",
      "slug": "a03061c",
      "availableForSale": false,
      "barcode": "194434095340",
      "isInStock": false,
      "price": "69.98",
      "availableQuantity": 0,
      "isRequireShipping": true,
      "sku": "11155400028",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "08.5"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207630903",
      "slug": "a03061c",
      "availableForSale": false,
      "barcode": "194434095173",
      "isInStock": false,
      "price": "69.98",
      "availableQuantity": 0,
      "isRequireShipping": true,
      "sku": "11155400029",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "10.0"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207663671",
      "slug": "a03061c",
      "availableForSale": true,
      "barcode": "194434095258",
      "isInStock": true,
      "price": "69.98",
      "availableQuantity": 18,
      "isRequireShipping": true,
      "sku": "11155400077",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "04.0"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207696439",
      "slug": "a03061c",
      "availableForSale": true,
      "barcode": "194434095265",
      "isInStock": true,
      "price": "69.98",
      "availableQuantity": 14,
      "isRequireShipping": true,
      "sku": "11155400078",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "04.5"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207729207",
      "slug": "a03061c",
      "availableForSale": true,
      "barcode": "194434095272",
      "isInStock": true,
      "price": "69.98",
      "availableQuantity": 39,
      "isRequireShipping": true,
      "sku": "11155400079",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "05.0"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207761975",
      "slug": "a03061c",
      "availableForSale": true,
      "barcode": "194434095289",
      "isInStock": true,
      "price": "69.98",
      "availableQuantity": 41,
      "isRequireShipping": true,
      "sku": "11155400080",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "05.5"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    },
    {
      "id": "gid://shopify/ProductVariant/40027207794743",
      "slug": "a03061c",
      "availableForSale": false,
      "barcode": "",
      "isInStock": false,
      "price": "69.98",
      "availableQuantity": 0,
      "isRequireShipping": true,
      "sku": "11155400107",
      "unitPrice": null,
      "unitPriceCurrency": "USD",
      "weight": 0,
      "weightUnit": "POUNDS",
      "option": [
        {
          "name": "Size",
          "value": "03.5"
        },
        {
          "name": "Color",
          "value": "Squirrel Friend/Black/White"
        }
      ]
    }
  ],
  "images": [
    {
      "id": "gid://shopify/ProductImage/30014407999543",
      "src": "https://cdn.shopify.com/s/files/1/0069/3442/9751/products/A03061C_1.jpg?v=1674606399",
      "width": 2754,
      "height": 2754
    },
    {
      "id": "gid://shopify/ProductImage/30014408032311",
      "src": "https://cdn.shopify.com/s/files/1/0069/3442/9751/products/A03061C_2.jpg?v=1674606399",
      "width": 2249,
      "height": 2249
    },
    {
      "id": "gid://shopify/ProductImage/30014408065079",
      "src": "https://cdn.shopify.com/s/files/1/0069/3442/9751/products/A03061C_3.jpg?v=1674606399",
      "width": 2754,
      "height": 2754
    },
    {
      "id": "gid://shopify/ProductImage/30014408097847",
      "src": "https://cdn.shopify.com/s/files/1/0069/3442/9751/products/A03061C_4.jpg?v=1674606399",
      "width": 2754,
      "height": 2754
    },
    {
      "id": "gid://shopify/ProductImage/30014408130615",
      "src": "https://cdn.shopify.com/s/files/1/0069/3442/9751/products/A03061C_5.jpg?v=1674606399",
      "width": 2795,
      "height": 2795
    }
  ],
  "options": [
    {
      "name": "Size",
      "values": [
        "06.0",
        "06.5",
        "07.0",
        "09.0",
        "09.5",
        "07.5",
        "08.0",
        "08.5",
        "10.0",
        "04.0",
        "04.5",
        "05.0",
        "05.5",
        "03.5"
      ]
    },
    {
      "name": "Color",
      "values": [
        "Squirrel Friend/Black/White"
      ]
    }
  ]
}
```

## Contact 
Please visit us through [epctex.com](https://epctex.com) to see all the products that is available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
