# 🧑‍💼 API Clients

This module groups together the endpoints linked to customer management (authentication, user info, shopping cart, payments, etc.).

!!! note "Base URL Notice"
    The base URL for these endpoints depends on the subdomain of your store.
    For example, if your store is accessible at **`https://test10.devaito.com`**,
    then your API base URL will be:
    **`https://test10.devaito.com/api`**

---

## 🔐 Customer Authentication

### POST `/login-customer`

Authenticates an existing customer and returns an access token.

!!! info "Token Requirement"
    🔓 **No authentication required**

**Request body:**
```json
{
  "email": "userFalah1@gmail.com",
  "password": "userFalah1@gmail.com"
}
```

**Example response:**
```json
{
  "success": true,
  "token": "325|hrY289rdJ9Y1MvnXVB45lQ9dQkvdlAeWhvt88kBe"
}
```

### POST `/register-customer`

Registers a new customer account and returns a token.

!!! info "Token Requirement"
    🔓 **No authentication required**

**Request body:**
```json
{
  "name": "test",
  "email": "testq1q23q214112234@test.com",
  "phone": "12313123123",
  "password": "test234234",
  "password_confirmation": "test234234"
}
```

**Example response :**
```json
{
  "success": true,
  "user": {
    "image": null,
    "name": "test",
    "email": "testq1q23q214112234@test.com",
    "id": 12,
    "uid": null,
    "phone_with_code": "12313123123",
    "phone_code": null,
    "phone": "12313123123",
    "verified_at": null
  },
  "token": "327|yZGp2fGZcvmdwQNH4Mo29giyEb0fJrPkGHHtE3a9"
}
```

## 📦 Products
!!! info "Token Requirement"
    🔓 **No authentication required For all endpoint related to products**

### GET `/popular-products`


this endpoint will return a list of popular products based on the number of sales

**params**

| Name | Type | Required | Description |
|------|------|-----------|-------------|
| `page` | integer | No | Page number to retrieve (default: `1`) |
| `per_page` | integer | No | Number of items per page (default: `8`) |

```
{
    "success": true,
    "data": [
        {
            "id": 2,
            "name": "Universal Language Translator",
            "permalink": "httpsexamplecomuniversal-language-translator",
            "thumbnail_image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg",
            "orders_count": 0,
            "orders_sum_unit_price": null,
            "orders_sum_quantity": null
        },
        {
            "id": 3,
            "name": "English Grammar Workbook",
            "permalink": "httpsexamplecomenglish-grammar-workbook",
            "thumbnail_image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg",
            "orders_count": 0,
            "orders_sum_unit_price": null,
            "orders_sum_quantity": null
        },
        {
            "id": 4,
            "name": "Interactive English Vocabulary App",
            "permalink": "httpsexamplecominteractive-english-vocabulary-app",
            "thumbnail_image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg",
            "orders_count": 0,
            "orders_sum_unit_price": null,
            "orders_sum_quantity": null
        },
        {
            "id": 5,
            "name": "English Idioms and Phrases Guide",
            "permalink": "httpsexamplecomenglish-idioms-and-phrases-guide",
            "thumbnail_image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg",
            "orders_count": 0,
            "orders_sum_unit_price": null,
            "orders_sum_quantity": null
        },
        {
            "id": 6,
            "name": "Wooden Handle Steel Gardening Tools Small Shovel",
            "permalink": "wooden-handle-steel-gardening-tools-small-shovel",
            "thumbnail_image": "https://treasurex.devaito.com/public/tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/68f744b306031_5f6aac0d-1764-41b4-ac74-601c34ee52f5.jpg",
            "orders_count": 0,
            "orders_sum_unit_price": null,
            "orders_sum_quantity": null
        },
        {
            "id": 7,
            "name": "Trendy Retro Hand Women's Bag Korean Style Niche",
            "permalink": "trendy-retro-hand-womens-bag-korean-style-niche",
            "thumbnail_image": "https://treasurex.devaito.com/public/tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/68f744c974868_6714bb43-bce4-471d-b5b0-24e6e587a6a8.jpg",
            "orders_count": 0,
            "orders_sum_unit_price": null,
            "orders_sum_quantity": null
        },
        {
            "id": 8,
            "name": "Retro Plus Size Loose Sports Knee Length Shorts",
            "permalink": "retro-plus-size-loose-sports-knee-length-shorts",
            "thumbnail_image": "https://treasurex.devaito.com/public/tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/68f7559e8d04d_83428bac-0d0c-42eb-96c0-bbecd5b8a71e.jpg",
            "orders_count": 0,
            "orders_sum_unit_price": null,
            "orders_sum_quantity": null
        },
        {
            "id": 9,
            "name": "pizza",
            "permalink": "pizza",
            "thumbnail_image": "https://treasurex.devaito.com/public//tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/2025/Oct/YYXLfDGHIkqaotWtDNotiujt9P3gNmJvs07pni7P.webp",
            "orders_count": 0,
            "orders_sum_unit_price": null,
            "orders_sum_quantity": null
        }
    ],
    "pagination": {
        "items_per_page": 10,
        "total_items": 8,
        "current_page": 1,
        "total_pages": 1
    }
}
```

### GET `/product-details/{slug}`

!!! important "important note"
    This endpoint has two type of response (output):

    - If the product is basic product , it well return product details with a specific format.

    - If the product is customizable product , it well return product details with a specific format.

to know which format you need to use you need to read at first this key in the response `product_type` , how tell you which type of product you have in the example below you well have the response with the format of customizable product and basic product

**Example response of basic product:**
```json
{
    "success": true,
    "product_type": "customizable",
    "product": {
        "id": 103,
        "name": "MENU BOSTON BRGR (SPICY)",
        "thumbnail": "https://picksssss.devaito.com/public/tenant/tenant10e9818b-3e6f-4ae4-aa41-3fd5035d8c0b/2025/08/screenshot-2025-07-23-124317-68907f0ba8053.jpg",
        "gallery": [
            "https://picksssss.devaito.com/public/tenant/tenant10e9818b-3e6f-4ae4-aa41-3fd5035d8c0b/2025/08/screenshot-2025-07-23-124317-68907f0ba8053.jpg"
        ],
        "base_price": 7.5,
        "oldPrice": 0,
        "quantity": 0,
        "description": null,
        "options_groups": [
            {
                "id": 626,
                "group_name": "FAITES VOTRE CHOIX",
                "min_options": 1,
                "max_options": 1,
                "options": [
                    {
                        "id": 4559,
                        "option_name": "FRITES",
                        "price": "0.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4560,
                        "option_name": "POUTINE",
                        "price": "1.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4561,
                        "option_name": "CHEEZY FRIES",
                        "price": "1.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4562,
                        "option_name": "CHICKN POUTINE",
                        "price": "2.00",
                        "stock": 1000,
                        "qty_max": 1
                    }
                ]
            },
            {
                "id": 627,
                "group_name": "BOISSONS",
                "min_options": 1,
                "max_options": 1,
                "options": [
                    {
                        "id": 4563,
                        "option_name": "MILKSHAKE FRAISE",
                        "price": "1.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4564,
                        "option_name": "PEPSI",
                        "price": "0.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4565,
                        "option_name": "MIRINDA ORANGE",
                        "price": "0.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4566,
                        "option_name": "MIRINDA CITRON",
                        "price": "0.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4567,
                        "option_name": "7UP",
                        "price": "0.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4568,
                        "option_name": "MIRINDA TROPICAL",
                        "price": "0.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4569,
                        "option_name": "WATER 33CL",
                        "price": "0.00",
                        "stock": 1000,
                        "qty_max": 1
                    }
                ]
            },
            {
                "id": 628,
                "group_name": "EXTRA",
                "min_options": 0,
                "max_options": 5,
                "options": [
                    {
                        "id": 4570,
                        "option_name": "EXTRA EMMENTAL",
                        "price": "0.50",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4571,
                        "option_name": "EXTRA BOEUF",
                        "price": "1.50",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4572,
                        "option_name": "EXTRA JALAPENOS",
                        "price": "0.50",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4573,
                        "option_name": "EXTRA CRISPY CHICKEN",
                        "price": "1.50",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4574,
                        "option_name": "EXTRA CHEDDAR",
                        "price": "0.50",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4575,
                        "option_name": "EXTRA CHAMPIGNONS SAUTÉS",
                        "price": "0.50",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4576,
                        "option_name": "EXTRA OIGNONS CARAMELISEES",
                        "price": "0.50",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4577,
                        "option_name": "EXTRA ŒUF A CHEVAL",
                        "price": "0.50",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4578,
                        "option_name": "EXTRA BACON HALAL",
                        "price": "1.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4579,
                        "option_name": "EXTRA SAUCE",
                        "price": "0.30",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4580,
                        "option_name": "TOMATE",
                        "price": "0.25",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4581,
                        "option_name": "SALADE",
                        "price": "0.25",
                        "stock": 1000,
                        "qty_max": 1
                    }
                ]
            },
            {
                "id": 629,
                "group_name": "PERSONNALISEZ VOTRE BURGER",
                "min_options": 0,
                "max_options": 5,
                "options": [
                    {
                        "id": 4582,
                        "option_name": "SANS FROMAGE",
                        "price": "0.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4583,
                        "option_name": "SANS OIGNION",
                        "price": "0.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4584,
                        "option_name": "SANS OIGNION",
                        "price": "0.00",
                        "stock": 1000,
                        "qty_max": 1
                    },
                    {
                        "id": 4585,
                        "option_name": "SANS SAUCE",
                        "price": "0.00",
                        "stock": 1000,
                        "qty_max": 1
                    }
                ]
            }
        ],
        "has_options": 1,
        "symbol_devise": "$"
    }
}
```

**Example response of basic product:**
```json
{
    "success": true,
    "product_type": "standard",
    "product": {
        "id": 108,
        "name": "PISTACHE FRAMBOISE",
        "brand": null,
        "summary": null,
        "description": null,
        "product_type": 1,
        "supplier": 4,
        "permalink": "pistache-framboise",
        "unit": null,
        "conditions": null,
        "has_variant": 2,
        "discount_type": 2,
        "discount_amount": null,
        "pdf_specifications": null,
        "thumbnail_image": "174",
        "video_link": null,
        "is_featured": 2,
        "max_item_on_purchase": null,
        "min_item_on_purchase": null,
        "low_stock_quantity_alert": null,
        "is_authentic": 2,
        "has_warranty": 2,
        "has_replacement_warranty": 2,
        "warrenty_days": null,
        "is_refundable": 2,
        "shipping_location_type": null,
        "is_active_cod": 1,
        "is_active_free_shipping": 2,
        "cod_location_type": "anywhere",
        "is_active_attatchment": 2,
        "attatchment_name": null,
        "shipping_cost": 0,
        "is_apply_multiple_qty_shipping_cost": 2,
        "is_enable_tax": 1,
        "tax_profile": null,
        "status": 1,
        "id_cj": null,
        "profil_imported_countries": null,
        "has_options": 0,
        "created_at": "2025-07-24 11:51:13",
        "updated_at": "2025-08-09 17:27:11",
        "is_approved": 1,
        "id_lacaisse": null
    },
    "colorImages": [],
    "attributes": [],
    "colorsSectionNew": [],
    "prices": {
        "id": 108,
        "product_id": 108,
        "sku": null,
        "purchase_price": null,
        "unit_price": 8,
        "quantity": 0,
        "created_at": "2025-07-24 11:51:13",
        "updated_at": "2025-08-06 14:29:21"
    },
    "discount_type": 2,
    "amount_discount": null,
    "has_color": false,
    "has_color_photo": false,
    "thumbnail_image": "/tenant/tenant10e9818b-3e6f-4ae4-aa41-3fd5035d8c0b/2025/Jul/G4hKuday2XXOeMr1RBXpWEInStKU1bU1U3k2skWX.webp",
    "galleryImagesLeft": [
        {
            "image_path": "/tenant/tenant10e9818b-3e6f-4ae4-aa41-3fd5035d8c0b/2025/Jul/G4hKuday2XXOeMr1RBXpWEInStKU1bU1U3k2skWX.webp",
            "upload_id": 174
        }
    ],
    "symbol_devise": "$",
    "has_variant": 2,
    "variantsDataNew": null,
    "variantsDataPrice": [],
    "categories": [
        {
            "id": 21,
            "name": "CHOCOLAT"
        }
    ],
    "total_reviews": 0,
    "average_rating": 0
}
```

### GET `/fetch-categories`

Return all product categories

**Query Parameters**

| Name | Type | Required | Description |
|------|------|-----------|-------------|
| `page` | integer | No | Page number to retrieve (default: `1`) |
| `per_page` | integer | No | Number of items per page (default: `10`) |

**Example response:**
```json
{
    "success": true,
    "entities": [
        {
            "id": 9,
            "name": "Home Improvement",
            "url": "home-improvement",
            "slug": "home-improvement",
            "image": "/public/storage/all_files/2023/Mar/img-demo_17.jpg"
        },
        {
            "id": 12,
            "name": "Bags & Shoes",
            "url": "bags-shoes",
            "slug": "bags-shoes",
            "image": "/public/storage/all_files/2023/Mar/img-demo_17.jpg"
        },
        {
            "id": 15,
            "name": "Men's Clothing",
            "url": "mens-clothing",
            "slug": "mens-clothing",
            "image": "/public/storage/all_files/2023/Mar/img-demo_17.jpg"
        },
        {
            "id": 1,
            "name": "Electronics",
            "url": "electronics",
            "slug": "electronics",
            "image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg"
        },
        {
            "id": 2,
            "name": "Home & Garden",
            "url": "home-garden",
            "slug": "home-garden",
            "image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg"
        },
        {
            "id": 3,
            "name": "Fashion",
            "url": "fashion",
            "slug": "fashion",
            "image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg"
        },
        {
            "id": 4,
            "name": "Beauty & Personal Care",
            "url": "beauty-personal-care",
            "slug": "beauty-personal-care",
            "image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg"
        },
        {
            "id": 5,
            "name": "Sports & Outdoors",
            "url": "sports-outdoors",
            "slug": "sports-outdoors",
            "image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg"
        },
        {
            "id": 6,
            "name": "Toys & Games",
            "url": "toys-games",
            "slug": "toys-games",
            "image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg"
        },
        {
            "id": 7,
            "name": "Books & Stationery",
            "url": "books-stationery",
            "slug": "books-stationery",
            "image": "/public/storage/all_files/2023/Mar/img-demo_17.jpg"
        }
    ],
    "items_per_page": 10,
    "total_items": 11,
    "current_page": 1,
    "total_pages": 2
}
```

### GET `/fetch-all-products`

Return all products with a pagination that you can use to fetch more data

To switch between pages , use the `page` query parameter.

example of format :

**`https://picksssss.devaito.com/api/fetch-all-products?page=2`**

**Query Parameters**

| Name | Type | Required | Description |
|------|------|-----------|-------------|
| `page` | integer | No | Page number to retrieve (default: `1`) |
| `per_page` | integer | No | Number of items per page (default: `8`) |

**Example response:**
```json
{
    "success": true,
    "products": [
        {
            "id": 9,
            "name": "pizza",
            "slug": "pizza",
            "image": "https://treasurex.devaito.com/public//tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/2025/Oct/YYXLfDGHIkqaotWtDNotiujt9P3gNmJvs07pni7P.webp",
            "price": "0.00",
            "devise": "MAD",
            "url": "https://treasurex.devaito.com/product/pizza",
            "discount_type": 2,
            "discount_amount": null,
            "brand_name": null,
            "brand_logo": null,
            "categories": []
        },
        {
            "id": 8,
            "name": "Retro Plus Size Loose Sports Knee Length Shorts",
            "slug": "retro-plus-size-loose-sports-knee-length-shorts",
            "image": "https://treasurex.devaito.com/public/tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/68f7559e8d04d_83428bac-0d0c-42eb-96c0-bbecd5b8a71e.jpg",
            "price": "4.86",
            "devise": "MAD",
            "url": "https://treasurex.devaito.com/product/retro-plus-size-loose-sports-knee-length-shorts",
            "discount_type": 0,
            "discount_amount": 0,
            "brand_name": null,
            "brand_logo": null,
            "categories": [
                {
                    "id": 15,
                    "name": "Men's Clothing"
                },
                {
                    "id": 16,
                    "name": "Bottoms"
                },
                {
                    "id": 17,
                    "name": "Man Shorts"
                }
            ]
        },
        {
            "id": 7,
            "name": "Trendy Retro Hand Women's Bag Korean Style Niche",
            "slug": "trendy-retro-hand-womens-bag-korean-style-niche",
            "image": "https://treasurex.devaito.com/public/tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/68f744c974868_6714bb43-bce4-471d-b5b0-24e6e587a6a8.jpg",
            "price": "4.86",
            "devise": "MAD",
            "url": "https://treasurex.devaito.com/product/trendy-retro-hand-womens-bag-korean-style-niche",
            "discount_type": 0,
            "discount_amount": 0,
            "brand_name": null,
            "brand_logo": null,
            "categories": [
                {
                    "id": 12,
                    "name": "Bags & Shoes"
                },
                {
                    "id": 13,
                    "name": "Women's Luggage & Bags"
                },
                {
                    "id": 14,
                    "name": "Shoulder Bags"
                }
            ]
        },
        {
            "id": 6,
            "name": "Wooden Handle Steel Gardening Tools Small Shovel",
            "slug": "wooden-handle-steel-gardening-tools-small-shovel",
            "image": "https://treasurex.devaito.com/public/tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/68f744b306031_5f6aac0d-1764-41b4-ac74-601c34ee52f5.jpg",
            "price": "12.35",
            "devise": "MAD",
            "url": "https://treasurex.devaito.com/product/wooden-handle-steel-gardening-tools-small-shovel",
            "discount_type": 0,
            "discount_amount": 0,
            "brand_name": null,
            "brand_logo": null,
            "categories": [
                {
                    "id": 10,
                    "name": "Tools"
                },
                {
                    "id": 11,
                    "name": "Garden Tools"
                },
                {
                    "id": 9,
                    "name": "Home Improvement"
                }
            ]
        },
        {
            "id": 2,
            "name": "Universal Language Translator",
            "slug": "httpsexamplecomuniversal-language-translator",
            "image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg",
            "price": "49.99",
            "devise": "MAD",
            "url": "https://treasurex.devaito.com/product/httpsexamplecomuniversal-language-translator",
            "discount_type": 2,
            "discount_amount": null,
            "brand_name": null,
            "brand_logo": null,
            "categories": [
                {
                    "id": 1,
                    "name": "Electronics"
                }
            ]
        },
        {
            "id": 3,
            "name": "English Grammar Workbook",
            "slug": "httpsexamplecomenglish-grammar-workbook",
            "image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg",
            "price": "19.99",
            "devise": "MAD",
            "url": "https://treasurex.devaito.com/product/httpsexamplecomenglish-grammar-workbook",
            "discount_type": 2,
            "discount_amount": null,
            "brand_name": null,
            "brand_logo": null,
            "categories": [
                {
                    "id": 2,
                    "name": "Home & Garden"
                }
            ]
        },
        {
            "id": 4,
            "name": "Interactive English Vocabulary App",
            "slug": "httpsexamplecominteractive-english-vocabulary-app",
            "image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg",
            "price": "9.99",
            "devise": "MAD",
            "url": "https://treasurex.devaito.com/product/httpsexamplecominteractive-english-vocabulary-app",
            "discount_type": 2,
            "discount_amount": null,
            "brand_name": null,
            "brand_logo": null,
            "categories": [
                {
                    "id": 3,
                    "name": "Fashion"
                }
            ]
        },
        {
            "id": 5,
            "name": "English Idioms and Phrases Guide",
            "slug": "httpsexamplecomenglish-idioms-and-phrases-guide",
            "image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg",
            "price": "14.99",
            "devise": "MAD",
            "url": "https://treasurex.devaito.com/product/httpsexamplecomenglish-idioms-and-phrases-guide",
            "discount_type": 2,
            "discount_amount": null,
            "brand_name": null,
            "brand_logo": null,
            "categories": [
                {
                    "id": 4,
                    "name": "Beauty & Personal Care"
                }
            ]
        }
    ],
    "items_per_page": 12,
    "total_items": 8,
    "current_page": 1,
    "total_pages": 1
}
```

### GET `/search-products`

Return search results of product using the provided query parameters.

To use this endpoint, you need to provide the following query parameters:

**params**

| Name | Type | Required | Description |
|------|------|-----------|-------------|
| `query` | String | yes | key world |
| `limit` | integer | No | Number of items per page (default: `5`) |

example of format :

**`https://picksssss.devaito.com/api/search-products?query=pizza&limit=10`**

**Example response:**
```json
{
    "success": true,
    "data": [
        {
            "product_name": "pizza",
            "score": 0.4137763734340294,
            "id_product": 9,
            "permalink": "pizza",
            "image_url": "https://treasurex.devaito.com/public//tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/2025/Oct/YYXLfDGHIkqaotWtDNotiujt9P3gNmJvs07pni7P.webp",
            "price": 0,
            "devise": "MAD"
        },
        {
            "product_name": "Universal Language Translator",
            "score": 0.3665048622163059,
            "id_product": 2,
            "permalink": "httpsexamplecomuniversal-language-translator",
            "image_url": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg",
            "price": 49.99,
            "devise": "MAD"
        },
        {
            "product_name": "Trendy Retro Hand Women's Bag Korean Style Niche",
            "score": 0.36506165778724786,
            "id_product": 7,
            "permalink": "trendy-retro-hand-womens-bag-korean-style-niche",
            "image_url": "https://treasurex.devaito.com/public/tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/68f744c974868_6714bb43-bce4-471d-b5b0-24e6e587a6a8.jpg",
            "price": 4.86,
            "devise": "MAD"
        },
        {
            "product_name": "English Grammar Workbook",
            "score": 0.3639645343396562,
            "id_product": 3,
            "permalink": "httpsexamplecomenglish-grammar-workbook",
            "image_url": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg",
            "price": 19.99,
            "devise": "MAD"
        },
        {
            "product_name": "English Idioms and Phrases Guide",
            "score": 0.3594667918624297,
            "id_product": 5,
            "permalink": "httpsexamplecomenglish-idioms-and-phrases-guide",
            "image_url": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg",
            "price": 14.99,
            "devise": "MAD"
        }
    ],
    "query": "burger",
    "total_results": 5
}
```

## 👤 User Information

### POST `/log-out-customer`

By using this endpoint, you can log out from the application.

!!! warning "Token Requirement"
    🔒 **Requires authentication**
    Include your token in the `Authorization` header as follows:
    ```
    Authorization: Bearer <token>
    ```

**Response Example**
```
{
    "status": true
}
```

### POST `/update-profile-customer`

By using this endpoint, you can update your profile information.

!!! warning "Token Requirement"
    🔒 **Requires authentication**
    Include your token in the `Authorization` header as follows:
    ```
    Authorization: Bearer <token>
    ```

no params are required

**Request Body**

| Field | Type | Required | Description |
|--------|------|-----------|-------------|
| `name` | string | Yes | user name |
| `phone` | string | Yes | phone number of user |
| `email` | string  | Yes | email user (unique) |
| `image` | binary | no | profile image of the user |

```
{
    "success": true,
    "customer": {
        "image": null,
        "name": "falah test",
        "email": "userFalah1@gmail.com",
        "id": 7,
        "uid": null,
        "phone_with_code": "2342344534545",
        "phone_code": null,
        "phone": "2342344534545",
        "verified_at": null
    }
}
```

### GET `/user-customer`

Returns the details of the currently authenticated customer.

!!! warning "Token Requirement"
    🔒 **Requires authentication**
    Include your token in the `Authorization` header as follows:
    ```
    Authorization: Bearer <token>
    ```

**Example response:**
```json
{
  "success": true,
  "user": {
    "id": 2,
    "uid": null,
    "name": "falah",
    "email": "userFalah1@gmail.com",
    "image": 99,
    "phone_code": null,
    "phone": "2342344534545",
    "reset_password": null,
    "status": 2,
    "verified_at": null,
    "varification_code": null,
    "is_logedin": 2,
    "created_at": "2025-09-05T21:49:51.000000Z",
    "updated_at": "2025-09-05T21:50:12.000000Z"
  }
}
```

## 💳 Payment


### POST `/make-payment` 🟢

Creates a payment intent for an entire shopping cart.

by using this endpoint you well have the ability to get credentials that you need to make a payment using sdk in your app mobile

!!! info "Diffrence between payment methods"

This endpoint handles multiple payments methode:
eache payment methode has a diffrent response , so make sure to handle eache one,
in case of cmi you can't made payment in the app mobile so you need to use the web view to be able to make payment
<!--
- 🔒 **Authenticated User:** Include the `Authorization: Bearer <token>` header. The API will pre-fill user details (email, name) where possible.
- 👤 **Guest User:** Omit the `Authorization` header. You **must** provide fields like `name`, `email`, `phone`, and `address` in the request body if the payment provider (like CMI) requires them.-->

!!! info "You need to know"

By default your store that you are using has no configuration , so you need to configured in the dashboard first by going here "https://YOUR_STORE_NAME.devaito.com/admin/payments/payment-methods"

---

**Required Headers**

| Key | Type | Description |
|-----|------|-------------|
| **store-currency** | string | Optional The currency code the user is browsing in (e.g., MAD, USD, EUR). in case if you don't have a currency code, the API will use the default currency. |
| **Accept** | string | **Required.** Must be `application/json`. |

---

**Request Body (JSON)**

| Key | Type | Description |
|-----|------|-------------|
| **payment_method_id** | integer | **Required.** The ID of the payment method (from `GET /active-payment-methods`). |
| **items** | array | **Required.** An array of objects representing the cart. |
| **items[].id** | integer | **Required.** The product ID. |
| **items[].quantity** | integer | **Required.** The quantity of this item. |
| **items[].color** | string | Optional. The selected color ID. |
| **items[].variant** | object | Optional. The selected variant object (from product details). |
| **name** | string | Optional. Customer's full name. Required for CMI and others if the user is a guest. |
| **email** | string | Optional. Customer's email. Required for CMI and others if the user is a guest. |
| **phone** | string | Optional. Customer's phone number. Required for CMI. |
| **address** | string | Optional. Customer's billing address. Required for CMI. |



!!! info "Requirement"
    🔓 **All the elements (name,email,phone,address) , are not required just in case if you are using the CMI payment method  .**
---

**Example Body 1 (Simple: For Stripe/PayPal)**
```json
{
    "payment_method_id": 3,
    "items": [
        { "id": 6, "quantity": 1 },
        {
            "id": 10,
            "quantity": 2,
            "color": "8",
            "variant": {
                "Size": { "parent_id": 1, "child_id": 7, "child_Name": "1.2X10mm", "parent_name": "Size" }
            }
        }
    ]
}
```

**Example Body 2 (Complete: For CMI)**
```json
{
    "payment_method_id": 4,
    "items": [ { "id": 6, "quantity": 1 } ],
    "name": "John Doe",
    "email": "john.doe@example.com",
    "phone": "+1555123456",
    "address": "123 Main Street"
}
```

---

**Success Response (HTTP 200)**

The response structure depends on the payment provider. Check the `provider` field first.

**Case 1: provider == "stripe" (or gpay)**
Use the `client_secret` and `public_key` with the Stripe SDK.

```json
{
    "provider": "stripe",
    "client_secret": "pi_3SPSr3..._secret_0fs1U0...",
    "public_key": "pk_test_51RiWkY..."
}
```

**Case 2: provider == "paypal"**
Use the `order_id` and `public_key` with the PayPal SDK.

```json
{
    "provider": "paypal",
    "order_id": "2GE8219848...",
    "public_key": "AT_rQlXlQdFi_CSU9V..."
}
```

**Case 3: provider == "cmi"**
Open a WebView and POST the `form_data` to the `gateway_url`.

```json
{
    "provider": "cmi",
    "gateway_url": "https://testpayment.cmi.co.ma/fim/est3Dgate",
    "form_data": {
        "clientid": "600004377",
        "TranType": "PreAuth",
        "amount": "15.50",
        "oid": "CMD-17622...",
        "email": "john.doe@example.com",
        "BillToName": "John Doe",
        "tel": "+1555123456",
        "BillToStreet1": "123 Main Street",
        "okUrl": "https://your-api.com/api/payment/cmi/success",
        "failUrl": "https://your-api.com/api/payment/cmi/fail",
        "CallbackURL": "https://your-api.com/api/payment/cmi/callback",
        "hashAlgorithm": "ver3",
        "HASH": "sRCh9P0ZvD9qrS2AJ8oT..."
    }
}
```

---

**Error Response (HTTP 4xx/5xx)**

**HTTP 422 (Unprocessable Entity)**

Validation error — the message explains what is missing.

```json
{
    "message": "The phone field is required. (and 1 more error)",
    "errors": {
        "phone": ["The phone field is required."],
        "address": ["The address field is required."]
    }
}
```


### GET `/active-payment-methods`

Returns a list of available payment methods for the current store.

!!! warning "Token Requirement"
    🔒 **Requires authentication**

**Example response:**
```json
{
  "success": true,
  "data": {
    "data": [
      {
        "id": 1,
        "name": "Cash On Delivery",
        "logo": "/public/storage/all_files/2023/Apr/cod_971.png",
        "instruction": "Buy this product on Cash On Delivery"
      },
      {
        "id": 2,
        "name": "Paypal",
        "logo": "/public/storage/all_files/2023/Apr/paypal_49.png",
        "instruction": "Pay the amount with Paypal"
      },
      {
        "id": 3,
        "name": "Stripe",
        "logo": "/public/storage/all_files/2023/Apr/stipe_53.png",
        "instruction": "Pay the amount with Stripe"
      }
    ]
  }
}
```

## 🛒 Shopping Cart

### DELETE `/cart/clear`

!!! warning "Token Requirement"
    🔒 **Requires authentication**

By using this endpoint , you can clear the cart of the customer
no params are required

```
{
    "success": true,
    "message": "Panier vidé avec succès"
}
```


### DELETE `/cart/remove-item`

!!! warning "Token Requirement"
    🔒 **Requires authentication**

By using this endpoint , you can remove a specifique item from cart customer

**Request body**

| Name | Type | Required | Description |
|------|------|-----------|-------------|
| `cart_item_id` | integer | yes | the id of the product in the cart |

```
{
    "success": true,
    "message": "Item has been removed"
}
```

### GET `/cart/list`

!!! warning "Token Requirement"
    🔒 **Requires authentication**

By using this endpoint , you well get the list of products in theshopping cart.

**params**

| Name | Type | Required | Description |
|------|------|-----------|-------------|
| `page` | integer | No | Page number to retrieve (default: `1`) |
| `per_page` | integer | No | Number of items per page (default: `8`) |

```
{
    "success": true,
    "cartItems": [
        {
            "cart_item_id": 17,
            "product_id": 8,
            "name": "Retro Plus Size Loose Sports Knee Length Shorts",
            "permalink": "retro-plus-size-loose-sports-knee-length-shorts",
            "image": "https://treasurex.devaito.com/public/tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/68f7559e8d04d_83428bac-0d0c-42eb-96c0-bbecd5b8a71e.jpg",
            "variant": "Size:XL/color:Pink",
            "variant_code": "1:5/color:4",
            "unitPrice": 4.86,
            "oldPrice": 4.86,
            "quantity": 2,
            "attachment": null,
            "max_item": 1000,
            "min_item": 0
        },
        {
            "cart_item_id": 16,
            "product_id": 8,
            "name": "Retro Plus Size Loose Sports Knee Length Shorts",
            "permalink": "retro-plus-size-loose-sports-knee-length-shorts",
            "image": "https://treasurex.devaito.com/public/tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/68f7559e8d04d_83428bac-0d0c-42eb-96c0-bbecd5b8a71e.jpg",
            "variant": "Size:L/color:Pink",
            "variant_code": "1:4/color:4",
            "unitPrice": 4.86,
            "oldPrice": 4.86,
            "quantity": 1,
            "attachment": null,
            "max_item": 1000,
            "min_item": 0
        },
        {
            "cart_item_id": 15,
            "product_id": 6,
            "name": "Wooden Handle Steel Gardening Tools Small Shovel",
            "permalink": "wooden-handle-steel-gardening-tools-small-shovel",
            "image": "https://treasurex.devaito.com/public/tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/68f744b306031_5f6aac0d-1764-41b4-ac74-601c34ee52f5.jpg",
            "variant": "",
            "variant_code": "color:",
            "unitPrice": 12.35,
            "oldPrice": 12.35,
            "quantity": 1,
            "attachment": null,
            "max_item": 1,
            "min_item": 0
        },
        {
            "cart_item_id": 14,
            "product_id": 6,
            "name": "Wooden Handle Steel Gardening Tools Small Shovel",
            "permalink": "wooden-handle-steel-gardening-tools-small-shovel",
            "image": "https://treasurex.devaito.com/public/tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/68f744b306031_5f6aac0d-1764-41b4-ac74-601c34ee52f5.jpg",
            "variant": "",
            "variant_code": "",
            "unitPrice": 12.35,
            "oldPrice": 12.35,
            "quantity": 7,
            "attachment": null,
            "max_item": 1,
            "min_item": 0
        },
        {
            "cart_item_id": 13,
            "product_id": 2,
            "name": "Universal Language Translator",
            "permalink": "httpsexamplecomuniversal-language-translator",
            "image": "https://treasurex.devaito.com/public/storage/all_files/2023/Mar/img-demo_17.jpg",
            "variant": "",
            "variant_code": "",
            "unitPrice": 49.99,
            "oldPrice": 49.99,
            "quantity": 1,
            "attachment": null,
            "max_item": 49,
            "min_item": 1
        }
    ],
    "items_per_page": 10,
    "total_items": 5,
    "current_page": 1,
    "total_pages": 1
}
```

### POST `/cart/add`

Adds a product to the authenticated customer's shopping cart.

!!! warning "Token Requirement"
    🔒 **Requires authentication**

**Request body:**

| Name | Type | Required | Description |
|------|------|-----------|-------------|
| `product_id` | String / integer | Yes | this is the product id |
| `quantity` | integer | Yes | quantity of items |
| `color` | integer | No | color id |
| `colorText` | String | No | color name (ex: red) |
| `variant` | Object(JSON) | No | variants that has been selected (ex:{"Size":{"parent_id":1,"child_id":4,"child_Name":"L","parent_name":"Size"}}) |

**Example response:**
```json
{
    "success": true,
    "data": {
        "productId": "6",
        "productName": "Wooden Handle Steel Gardening Tools Small Shovel",
        "productPermalink": "wooden-handle-steel-gardening-tools-small-shovel",
        "productImage": "https://treasurex.devaito.com/public/tenant/tenantd74de1f0-e8cc-40e7-954f-b6a6429fc1e8/68f744b306031_5f6aac0d-1764-41b4-ac74-601c34ee52f5.jpg",
        "paramsVariantText": "",
        "paramsVariant": "",
        "unitPrice": "12.35",
        "oldPrice": 12.35,
        "quantity": "1",
        "min_item": 0,
        "max_item": 1,
        "seller": null,
        "shopName": null,
        "shopSlug": null,
        "brand_id": null,
        "attachment": null,
        "attributes_added": [],
        "colors_added": [],
        "product_cj": 1
    }
}
```

## 🛍️ Checkout

### POST `/get-state`

By using this endpoint you will get all states that a city have by passing the city id

**Request Body**

| Name | Type | Required | Description |
|------|------|-----------|-------------|
| `city_id` | integer | Yes | city id ex(2504)|

```
{
    "success": true,
    "data": [
        {
            "id": 29576,
            "name": "Agadir"
        }
    ]
}
```

### POST `/get-cities-of-state`

By using this endpoint you will get all cities that a country have by passing the country id

**Request Body**

| Name | Type | Required | Description |
|------|------|-----------|-------------|
| `country_id` | integer | Yes | country id ex(148)|

```
{
    "success": true,
    "data": [
        {
            "id": 2504,
            "name": "Agadir",
            "code": null
        },
        {
            "id": 2505,
            "name": "Casablanca",
            "code": null
        },
        {
            "id": 2506,
            "name": "Chaouia-Ouardigha",
            "code": null
        },
        {
            "id": 2507,
            "name": "Doukkala-Abda",
            "code": null
        },
        {
            "id": 2508,
            "name": "Fes-Boulemane",
            "code": null
        },
        {
            "id": 2509,
            "name": "Gharb-Chrarda-Beni Hssen",
            "code": null
        },
        {
            "id": 2510,
            "name": "Guelmim",
            "code": null
        },
        {
            "id": 2511,
            "name": "Kenitra",
            "code": null
        },
        {
            "id": 2512,
            "name": "Marrakech-Tensift-Al Haouz",
            "code": null
        },
        {
            "id": 2513,
            "name": "Meknes-Tafilalet",
            "code": null
        },
        {
            "id": 2514,
            "name": "Oriental",
            "code": null
        },
        {
            "id": 2515,
            "name": "Oujda",
            "code": null
        },
        {
            "id": 2516,
            "name": "Province de Tanger",
            "code": null
        },
        {
            "id": 2517,
            "name": "Rabat-Sale-Zammour-Zaer",
            "code": null
        },
        {
            "id": 2518,
            "name": "Sala Al Jadida",
            "code": null
        },
        {
            "id": 2519,
            "name": "Settat",
            "code": null
        },
        {
            "id": 2520,
            "name": "Souss Massa-Draa",
            "code": null
        },
        {
            "id": 2521,
            "name": "Tadla-Azilal",
            "code": null
        },
        {
            "id": 2522,
            "name": "Tangier-Tetouan",
            "code": null
        },
        {
            "id": 2523,
            "name": "Taza-Al Hoceima-Taounate",
            "code": null
        },
        {
            "id": 2524,
            "name": "Wilaya de Casablanca",
            "code": null
        },
        {
            "id": 2525,
            "name": "Wilaya de Rabat-Sale",
            "code": null
        }
    ]
}
```

### GET `/get-countries`

By using this endpoint you will get the list of countries with their respective codes , to get more countries you need to go to you admin panel and activated

```
{
    "success": true,
    "data": [
        {
            "id": 148,
            "name": "Morocco",
            "code": "MA"
        }
    ]
}
```

### POST `/get-shipping-options`

By using this endpoint you well get the coast of shipping delivery address specified from the user in the admin panel (by the admin user)

**Request Body**

!!! info "Token Requirement"
    🔓 **All the elements in the request body , you can get it from the checkout form**

| Name | Type | Required | Description |
|------|------|-----------|-------------|
| `country_id` | integer | yes | Page number to retrieve (default: `1`) |
| `location` | integer | no | location id |
| `post_code` | string | no | postal code of the user |
| `products` | string (JSON) | yes | all data related of the product  |
| `shipping_type` | string | yes | shipping type (ex:'home_delivery')  |
| `state_id` | integer | yes | state id |
| `state_name` | string | no | state name |
| `zone` | string | no | zone name |

```
{
    "success": true,
    "shipping_available": true,
    "options": [
        {
            "id": 1760951929254,
            "product": "https://treasurex.devaito.com/public/tenant/tenant9075b507-8538-4d3e-8db8-d7affee7e55b/68bb5a715ec82_image__1593617139550380.jpg",
            "options": {
                "id": null,
                "title": "Home Delivery",
                "shipping_cost": 0,
                "shipping_time": null,
                "shipping_from": null,
                "by": null
            },
            "default_option": {
                "id": null,
                "title": "Home Delivery",
                "shipping_cost": 0,
                "shipping_time": null,
                "shipping_from": null,
                "by": null
            },
            "tax": 0
        }
    ]
}
```

## ⚠️ Common Issues / Tips

!!! tip "Troubleshooting"
    - Ensure you use the correct **subdomain** for your store when calling the API.
    - Always include the `Authorization: Bearer <token>` header for authenticated endpoints.
    - Use `Content-Type: application/json` for all POST requests.
    - If you receive a `401 Unauthorized` response, your token may have expired.
