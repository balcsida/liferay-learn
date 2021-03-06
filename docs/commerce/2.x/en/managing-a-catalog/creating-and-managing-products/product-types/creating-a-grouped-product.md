# Creating a Grouped Product

A Grouped Product in Liferay Commerce is two or more products from the catalog that are packaged together to be sold as a single item. Grouped Products are tracked in the inventory. The catalog tracks all of the products contained in the group individually. A Grouped Product can contain simple products, other Grouped Products, or virtual products.

## Prerequisites

Before creating a Grouped Product, ensure that the following conditions have been met:

1. The individual products to be sold as a Grouped Product have been created in the catalog.
    * All SKUs have been generated.
    * All prices have been set.
    * The products can be both simple and virtual.
1. The individual products have sufficient quantities in the inventory.

## Create a Grouped Product

To create a grouped product:

1. Go to the _Global Application_ menu &rarr; _Commerce_ &rarr; _Products_.
1. Click the Add (![Add icon](../../../images/icon-add.png)) button then _Grouped_.
1. Enter the following:
    * **Catalog**: Sahara.com
    * **Name**: Brakes Set Combo Kit
1. Click _Submit_ when finished.

Once the Grouped Product entity has been initially created, store administrators will need to associate the individual products to the grouped product entry.

## Associate Products in Group

1. Click the _Grouped_ sub-tab.

   ![Grouped Sub-Tab](./creating-a-grouped-product/images/01.png)

1. Click the (![Add icon](../../../images/icon-add.png)) button to add a Grouped Entry.
1. Select the following products: _Brake Fluid_, _Brake Pads_, and _Brake Rotors_.
1. Click _Add_.

    ![Grouped Sub-Tab](./creating-a-grouped-product/images/02.png)

Next, specify the priority (the order in which they are displayed), and the quantity sold in each package. Click the _3-dot_ icon then _Edit_ next to any of the products.

![Adding a Product to a Grouped Product](./creating-a-grouped-product/images/03.png)

In the image above, the product has been given priority 1.0 which means it will be listed first. Assign incremental values to the other products.

![Grouped Product Priority](./creating-a-grouped-product/images/04.png)

## Apply Product Options

[Product Options](../products/customizing-your-product-with-product-options.md) provide an easy and flexible way to offer products that have a variety of options such as size, quantity, and color. Click the _Options_ sub-tab to add various options to the product.

## Generate SKUs

Once you have applied product options to the product, SKUs have to be generated. For more information about how to generate SKUs, see the article [Adding SKUs to Your Products](../products/adding-skus-to-your-products.md). Click the _SKUs_ sub-tab to generate the SKUs.

## Set Prices and Quantities in the Inventory

After the SKUs have been generated, set the base price and quantities in the inventory for each item. Depending on how many SKUs were generated based on the various product options, each SKU can have its own prices. Some products are sold in bulk quantities while others are sold individually.

1. Click the _SKU_ tab.
1. Click the _3-dot_ icon then _Edit_ next to _default_. (At this point, you can rename the SKU to something more descriptive like _Brakes Set Combo Kit_ on the _Details_ menu.)

    ![Add the Price](./creating-a-grouped-product/images/07.png)

1. Click _Publish_.

To learn more about pricing see: [Introduction to Product Pricing Methods](../../managing-price/introduction-to-product-pricing-methods.md)

To learn how to configure inventory for your product, see: [Setting Inventory by Warehouse](../../managing-inventory/setting-inventory-by-warehouse.md).

### Setting Prices and Quantities on Liferay Commerce 2.0 and Below

To set product prices and quantities for a Grouped product:

1. Click the _SKU_ tab.
1. Click the _3-dot_ icon then _Edit_ next to _default_. (At this point, you can rename the SKU to something more descriptive like _Brakes Set Combo Kit_ on the _Details_ menu.)
1. Click _Pricing_ on the left menu.
1. Enter the following:
    * **Price**: 89.99
    * **Promo Price**: 0.00
    * **Cost**: 0.00

        ![Grouped Product Pricing](./creating-a-grouped-product/images/06.png)

1. Click _Save_. (If Promo Price and Cost fields are left as 0.00, no discounts or promotions are applied at this point.)
1. Click _Price List_ to apply this product to any existing [Price Lists](../../managing-price/adding-products-to-a-price-list.md).

## Configure Product Specifications

[Product specifications](../products/specifications.md) contain useful pieces of product information about the product, such as dimensions, color, weight, capacity, or almost any other attribute. Click the _Specifications_ sub-tab to add specifications.

## Upload Product Images and Attachments

[Product images](../products/product-images.md) help to ensure that customers know what they are buying. Each product variant (SKU) can have their own associated product image. Click the _Images_ sub-tab to add all product images.

Store administrators can also add attachments that are associated with a particular product. Click the _Attachments_ sub-tab to add documents.

## Organize with Categories

[Product Categories](../products/creating-a-new-product-category.md) are used to organize products. Product categories may be used to apply discounts or other offers to a set of products, to assist buyers in finding products, or to promote certain products to a specified account or account group.

## Associate with Related Products

[Product Relations](../products/related-products-up-sells-and-cross-sells.md) can be used to connect products. Once connected, a product displays the links to other products. Every related product must be assigned to a Product Relation Type.

## Selling Grouped Products

The new Grouped Product appears in the catalog. As long as each individual product has enough stock in the inventory, buyers can select the Grouped Product for purchase.

![Dog Grooming Kit](./creating-a-grouped-product/images/05.png)

## Commerce 2.1 and Below

1. Navigate to _Control Panel_ → _Commerce_ → _Products_.
1. Click the Add (![Add icon](../../../images/icon-add.png)) button then _Grouped_.
1. Enter the following:
    * **Catalog**: Sahara.com
    * **Name**: Brakes Set Combo Kit
    * **Short Description**: Brakes Set Combo Kit
    * **Friendly URL**: (auto-generated)
    * **Meta Title**: Brakes Set Combo Kit
1. Click _Publish_.

Once the Grouped Product entity has been initially created, store administrators will need to associate the individual products to the grouped product entry.

### Associate Products in Group

1. Click the _Grouped_ sub-tab.

   ![Grouped Sub-Tab](./creating-a-grouped-product/images/01.png)

1. Click the (![Add icon](../../../images/icon-add.png)) button to add a Grouped Entry.
1. Select the following products: _Brake Fluid_, _Brake Pads_, and _Brake Rotors_.
1. Click _Add_.

    ![Grouped Sub-Tab](./creating-a-grouped-product/images/02.png)

Next, specify the priority (the order in which they are displayed), and the quantity sold in each package. Click the _3-dot_ icon then _Edit_ next to any of the products.

![Adding a Product to a Grouped Product](./creating-a-grouped-product/images/03.png)

In the image above, the product has been given priority 1.0 which means it will be listed first. Assign incremental values to the other products.

![Grouped Product Priority](./creating-a-grouped-product/images/04.png)

Once the products have been grouped, follow the sections above to add Product Options, Generate SKUs, and set the prices. In addition, see the above sections on how to add Product Options, Specifications or upload Product Images.

## Additional Information

* [Introduction to Product Types](./introduction-to-product-types.md)
* [Creating a Simple Product](./creating-a-simple-product.md)
* [Creating a Virtual Product](./creating-a-virtual-product.md)
