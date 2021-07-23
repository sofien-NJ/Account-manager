<template>
  <div style="display: flex;">
    <v-tabs
      v-model="tab"
      dark
      icons-and-text
      vertical
      style="max-width: 120px;"
    >
      <v-tabs-slider></v-tabs-slider>

      <v-tab key="#profile">
        Profile
        <v-icon>mdi-account</v-icon>
      </v-tab>

      <v-tab key="#favorits">
        Favorites
        <v-icon>mdi-heart</v-icon>
      </v-tab>

      <v-tab key="#shipping">
        Shipping
        <v-icon>mdi-google-maps</v-icon>
      </v-tab>
    </v-tabs>

    <v-tabs-items v-model="tab" style="flex-grow: 1;">
      <v-tab-item key="#profile">
        <v-card flat>
          <v-card-text>
            <!-- <v-form ref="form" v-model="valid" lazy-validation> -->
            <v-text-field
              v-model="name"
              :counter="10"
              :rules="nameRules"
              label="Name"
              required
            ></v-text-field>

            <v-text-field
              v-model="email"
              :rules="emailRules"
              label="E-mail"
              required
            ></v-text-field>
            <v-btn
              :disabled="!valid"
              color="success"
              class="mr-4"
              @click="validate"
            >
              Validate
            </v-btn>

            <v-text-field
              v-model="password"
              label="Normal with hint text"
              hint="At least 8 characters"
              required
            ></v-text-field>
            <v-text-field
              v-model="password"
              :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
              label="Normal with hint text"
              hint="At least 8 characters"
              required
            ></v-text-field>

            <v-btn color="error" class="mr-4" @click="reset">
              Reset Form
            </v-btn>
            <!-- </v-form> -->
          </v-card-text>
        </v-card>
      </v-tab-item>
      <v-tab-item key="#favorites">
        <div>
          <v-container>
            <v-row>
              <v-col
                cols="12"
                md="4"
                v-for="product in products"
                :key="product.id"
              >
                <v-card
                  :loading="loading"
                  class="mx-auto my-12"
                  max-width="374"
                >
                  <template slot="progress">
                    <v-progress-linear
                      color="deep-purple"
                      height="10"
                      indeterminate
                    ></v-progress-linear>
                  </template>

                  <v-img height="250" :src="product.image.path"></v-img>
                  <v-btn absolute color="orange" class="white--text" fab right>
                    <v-icon>mdi-cart</v-icon>
                  </v-btn>
                  <v-card-title>{{ product.title }}</v-card-title>

                  <v-card-text>
                    <div class="my-4 text-subtitle-1">
                      {{ product.price }}
                    </div>

                    <p v-html="product.description"></p>
                  </v-card-text>
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </div>
      </v-tab-item>
      <v-tab-item key="#shipping">
        <v-card flat v-for="product in products" :key="product.id">
          <v-card-text>
            <v-card class="mx-auto" max-width="1400" outlined>
              <v-list-item three-line>
                <v-list-item-content>
                  <v-list-item-title class="text-h5 mb-1">
                    {{ product.title }}
                  </v-list-item-title>
                  <v-list-item-title class="text-h5 mb-1">
                    {{ product.type }}
                  </v-list-item-title>
                  <v-list-item-subtitle>
                    <p v-html="product.description"></p>
                  </v-list-item-subtitle>
                </v-list-item-content>

                <v-icon aria-label="My Account" role="img" aria-hidden="false">
                </v-icon>
                <img src="/map.png" style="width: 70px;" />
              </v-list-item>

              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn outlined rounded text>
                  Button
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs-items>
  </div>
</template>

<script>
export default {
  name: "AccountManager",

  data: () => ({
    tab: null,
    products: [
      {
        available: true,
        collectionsKeys: ["burgers"],
        created_at: 1618318191164,
        defaultShipping: {
          PickUpInStore: false,
          homeDelivery: false,
          physicalProduct: false,
          weight: null,
        },
        description:
          "<p>Steak 180, galette rosti, jambon de dinde raclette, salade, tomate, oignons.</p>",
        id: "e677e92c-6238-4b0c-af88-9d0378953855",
        imagesIds: ["841bf578-e9f1-4c86-8d26-6f6c67b4ff3a"],
        optionsData: [],
        tags: [],
        title: "LE GOURMAND",
        type: "SIMPLE_PRODUCT",
        updated_at: 1620783905231,
        variantId: "f0e4618c-7e77-4f20-b9b1-a8c5563b4c3a",
        variantsData: [],
        vendorId: null,
        version: "1.0.0",
        images: [
          {
            created_at: 1618318146739,
            id: "841bf578-e9f1-4c86-8d26-6f6c67b4ff3a",
            name: "2021-02-03 (13).png",
            ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
            path:
              "https://cdn.tunisales.com/linstantgourmand/uploads/1618318146129__5131__2021-02-03 (13).png",
            remote: false,
            tag: "picture",
            type: "image/png",
            updated_at: 1618318146739,
            used: false,
            usedIn: [],
            version: "1.0.0",
          },
        ],
        vendor: null,
        variant: {
          barcode: "",
          compare_at_price: "",
          continueOutOfStock: false,
          created_at: 1618318191156,
          id: "f0e4618c-7e77-4f20-b9b1-a8c5563b4c3a",
          imageId: "841bf578-e9f1-4c86-8d26-6f6c67b4ff3a",
          key: "",
          option: null,
          price: "7.50",
          quantity: 0,
          shipping: {},
          sku: "",
          trackQuantity: false,
          updated_at: 1618318191156,
          version: "1.0.0",
          image: {
            created_at: 1618318146739,
            id: "841bf578-e9f1-4c86-8d26-6f6c67b4ff3a",
            name: "2021-02-03 (13).png",
            ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
            path:
              "https://cdn.tunisales.com/linstantgourmand/uploads/1618318146129__5131__2021-02-03 (13).png",
            remote: false,
            tag: "picture",
            type: "image/png",
            updated_at: 1618318146739,
            used: false,
            usedIn: [],
            version: "1.0.0",
          },
          formattedPrice: "€7.50",
        },
        image: {
          path:
            "https://cdn.tunisales.com/linstantgourmand/cache/e677e92c-6238-4b0c-af88-9d0378953855-thumbnail.png",
        },
        collections: [
          {
            color: null,
            created_at: 1618100797579,
            desc: "",
            featured: null,
            icon: null,
            id: "76fd2b67-573a-4c14-99fa-2944ab7677cc",
            imageId: "e5e40e21-442d-495b-8787-7730c9852d5e",
            key: "burgers",
            name: "Burgers",
            order: 0,
            updated_at: 1618438101523,
            version: "1.0.0",
            display: true,
            starred: false,
            coverId: "",
            parentId: null,
            parent: null,
            image: {
              created_at: 1618100460789,
              id: "e5e40e21-442d-495b-8787-7730c9852d5e",
              name: "1612207057284__95793__lamericain.jpg",
              ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
              path:
                "https://cdn.tunisales.com/linstantgourmand/uploads/1618100460523__74557__1612207057284__95793__lamericain.jpg",
              remote: false,
              tag: "picture",
              type: "image/jpeg",
              updated_at: 1618100460789,
              used: false,
              usedIn: [],
              version: "1.0.0",
            },
            cover: { path: "/images/placeholder.png" },
          },
        ],
        _price: 7.5,
        price: "€7.50",
      },
      {
        available: true,
        collectionsKeys: ["pizzas", "burgers"],
        created_at: 1618317831573,
        defaultShipping: {
          PickUpInStore: false,
          homeDelivery: false,
          physicalProduct: false,
          weight: null,
        },
        description:
          "<p>Chicken galette rosti, salade, tomate, oignons, cheddar.</p>",
        id: "24f74077-bfa6-4af4-b331-ef72dc2f53e3",
        imagesIds: ["d331318f-7194-4c29-ad16-0c0be419df78"],
        optionsData: [],
        tags: [],
        title: "LE BAP’S",
        type: "SIMPLE_PRODUCT",
        updated_at: 1620783905270,
        variantId: "e062f038-e55c-45c5-9ee4-8d570e537516",
        variantsData: [],
        vendorId: null,
        version: "1.0.0",
        images: [
          {
            created_at: 1618317983322,
            id: "d331318f-7194-4c29-ad16-0c0be419df78",
            name: "2021-02-03 (7).png",
            ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
            path:
              "https://cdn.tunisales.com/linstantgourmand/uploads/1618317982911__64934__2021-02-03 (7).png",
            remote: false,
            tag: "picture",
            type: "image/png",
            updated_at: 1618317983322,
            used: false,
            usedIn: [],
            version: "1.0.0",
          },
        ],
        vendor: null,
        variant: {
          barcode: "",
          compare_at_price: "",
          continueOutOfStock: false,
          created_at: 1618317831567,
          id: "e062f038-e55c-45c5-9ee4-8d570e537516",
          imageId: "d331318f-7194-4c29-ad16-0c0be419df78",
          key: "",
          option: null,
          price: "6.50",
          quantity: 0,
          shipping: {},
          sku: "",
          trackQuantity: false,
          updated_at: 1618318001347,
          version: "1.0.0",
          image: {
            created_at: 1618317983322,
            id: "d331318f-7194-4c29-ad16-0c0be419df78",
            name: "2021-02-03 (7).png",
            ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
            path:
              "https://cdn.tunisales.com/linstantgourmand/uploads/1618317982911__64934__2021-02-03 (7).png",
            remote: false,
            tag: "picture",
            type: "image/png",
            updated_at: 1618317983322,
            used: false,
            usedIn: [],
            version: "1.0.0",
          },
          formattedPrice: "€6.50",
        },
        image: {
          path:
            "https://cdn.tunisales.com/linstantgourmand/cache/24f74077-bfa6-4af4-b331-ef72dc2f53e3-thumbnail.png",
        },
        collections: [
          {
            color: null,
            created_at: 1618100797579,
            desc: "",
            featured: null,
            icon: null,
            id: "76fd2b67-573a-4c14-99fa-2944ab7677cc",
            imageId: "e5e40e21-442d-495b-8787-7730c9852d5e",
            key: "burgers",
            name: "Burgers",
            order: 0,
            updated_at: 1618438101523,
            version: "1.0.0",
            display: true,
            starred: false,
            coverId: "",
            parentId: null,
            parent: null,
            image: {
              created_at: 1618100460789,
              id: "e5e40e21-442d-495b-8787-7730c9852d5e",
              name: "1612207057284__95793__lamericain.jpg",
              ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
              path:
                "https://cdn.tunisales.com/linstantgourmand/uploads/1618100460523__74557__1612207057284__95793__lamericain.jpg",
              remote: false,
              tag: "picture",
              type: "image/jpeg",
              updated_at: 1618100460789,
              used: false,
              usedIn: [],
              version: "1.0.0",
            },
            cover: { path: "/images/placeholder.png" },
          },
          {
            color: null,
            coverId: "745d1a3d-eaf1-4293-a4a3-06ddd1639159",
            created_at: 1618100752901,
            desc: "",
            featured: null,
            icon: null,
            id: "d6be935c-80c6-4b45-9389-059a935b3663",
            imageId: "dc1838ab-7f35-4c3a-96a2-2a63500dee94",
            key: "pizzas",
            name: "Pizzas",
            order: 0,
            starred: false,
            updated_at: 1623260844653,
            version: "1.0.0",
            display: true,
            parentId: null,
            parent: null,
            image: {
              created_at: 1618318654295,
              id: "dc1838ab-7f35-4c3a-96a2-2a63500dee94",
              name: "2021-02-03 (11).png",
              ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
              path:
                "https://cdn.tunisales.com/linstantgourmand/uploads/1618318653604__24738__2021-02-03 (11).png",
              remote: false,
              tag: "picture",
              type: "image/png",
              updated_at: 1618318654295,
              used: false,
              usedIn: [],
              version: "1.0.0",
            },
            cover: {
              created_at: 1619928658673,
              id: "745d1a3d-eaf1-4293-a4a3-06ddd1639159",
              name: "",
              ownerId: null,
              path: "/images/placeholder.png",
              remote: false,
              tag: "download",
              type: "",
              updated_at: 1619928658673,
              used: false,
              usedIn: [],
              version: "1.0.0",
            },
          },
        ],
        _price: 6.5,
        price: "€6.50",
      },
      {
        available: true,
        created_at: 1618318520805,
        defaultShipping: {
          PickUpInStore: false,
          homeDelivery: false,
          physicalProduct: false,
          weight: null,
        },
        description:
          "<p>Sauce tomate, mozzarella, viande hachée, oignons, oeuf, sauce barbecue.</p>",
        id: "96af54d3-01b7-43b5-9e3a-ba0b2950d544",
        imagesIds: ["a9da3b2d-ec76-480c-9dc3-c89deb550bcb"],
        optionsData: [],
        tags: ["33 cm"],
        title: "La buffalo 33 cm",
        type: "SIMPLE_PRODUCT",
        updated_at: 1620783905296,
        variantId: "68800bfc-472b-4b40-abd6-a1afb5c1fd98",
        variantsData: [],
        vendorId: null,
        version: "1.0.0",
        collectionsKeys: [],
        images: [
          {
            created_at: 1618317632451,
            id: "a9da3b2d-ec76-480c-9dc3-c89deb550bcb",
            name: "2021-02-03 (3).png",
            ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
            path:
              "https://cdn.tunisales.com/linstantgourmand/uploads/1618317631863__18748__2021-02-03 (3).png",
            remote: false,
            tag: "picture",
            type: "image/png",
            updated_at: 1618317632451,
            used: false,
            usedIn: [],
            version: "1.0.0",
          },
        ],
        vendor: null,
        variant: {
          barcode: "",
          compare_at_price: "",
          continueOutOfStock: false,
          created_at: 1618318520794,
          id: "68800bfc-472b-4b40-abd6-a1afb5c1fd98",
          imageId: "a9da3b2d-ec76-480c-9dc3-c89deb550bcb",
          key: "",
          option: null,
          price: "8",
          quantity: 0,
          shipping: {},
          sku: "",
          trackQuantity: false,
          updated_at: 1618318520794,
          version: "1.0.0",
          image: {
            created_at: 1618317632451,
            id: "a9da3b2d-ec76-480c-9dc3-c89deb550bcb",
            name: "2021-02-03 (3).png",
            ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
            path:
              "https://cdn.tunisales.com/linstantgourmand/uploads/1618317631863__18748__2021-02-03 (3).png",
            remote: false,
            tag: "picture",
            type: "image/png",
            updated_at: 1618317632451,
            used: false,
            usedIn: [],
            version: "1.0.0",
          },
          formattedPrice: "€8.00",
        },
        image: {
          path:
            "https://cdn.tunisales.com/linstantgourmand/cache/96af54d3-01b7-43b5-9e3a-ba0b2950d544-thumbnail.png",
        },
        collections: [],
        _price: 8,
        price: "€8.00",
      },
      {
        available: true,
        collectionsKeys: ["pizzas"],
        created_at: 1618318718339,
        defaultShipping: {
          PickUpInStore: false,
          homeDelivery: false,
          physicalProduct: false,
          weight: null,
        },
        description:
          "<p>Crème fraiche, mozzarella, poivrons, escalope de poulet, sauce gruyère.</p>",
        id: "e838a24a-3f1c-437a-8b0e-20fdb2f2de44",
        imagesIds: ["dc1838ab-7f35-4c3a-96a2-2a63500dee94"],
        optionsData: [],
        tags: [],
        title: "La boisée 33 cm",
        type: "SIMPLE_PRODUCT",
        updated_at: 1620783905332,
        variantId: "72ab48e5-f680-4db8-9c37-597c893fbd5f",
        variantsData: [],
        vendorId: null,
        version: "1.0.0",
        images: [
          {
            created_at: 1618318654295,
            id: "dc1838ab-7f35-4c3a-96a2-2a63500dee94",
            name: "2021-02-03 (11).png",
            ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
            path:
              "https://cdn.tunisales.com/linstantgourmand/uploads/1618318653604__24738__2021-02-03 (11).png",
            remote: false,
            tag: "picture",
            type: "image/png",
            updated_at: 1618318654295,
            used: false,
            usedIn: [],
            version: "1.0.0",
          },
        ],
        vendor: null,
        variant: {
          barcode: "",
          compare_at_price: "",
          continueOutOfStock: false,
          created_at: 1618318718332,
          id: "72ab48e5-f680-4db8-9c37-597c893fbd5f",
          imageId: "dc1838ab-7f35-4c3a-96a2-2a63500dee94",
          key: "",
          option: null,
          price: "10",
          quantity: 0,
          shipping: {},
          sku: "",
          trackQuantity: false,
          updated_at: 1618704717374,
          version: "1.0.0",
          image: {
            created_at: 1618318654295,
            id: "dc1838ab-7f35-4c3a-96a2-2a63500dee94",
            name: "2021-02-03 (11).png",
            ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
            path:
              "https://cdn.tunisales.com/linstantgourmand/uploads/1618318653604__24738__2021-02-03 (11).png",
            remote: false,
            tag: "picture",
            type: "image/png",
            updated_at: 1618318654295,
            used: false,
            usedIn: [],
            version: "1.0.0",
          },
          formattedPrice: "€10.00",
        },
        image: {
          path:
            "https://cdn.tunisales.com/linstantgourmand/cache/e838a24a-3f1c-437a-8b0e-20fdb2f2de44-thumbnail.png",
        },
        collections: [
          {
            color: null,
            coverId: "745d1a3d-eaf1-4293-a4a3-06ddd1639159",
            created_at: 1618100752901,
            desc: "",
            featured: null,
            icon: null,
            id: "d6be935c-80c6-4b45-9389-059a935b3663",
            imageId: "dc1838ab-7f35-4c3a-96a2-2a63500dee94",
            key: "pizzas",
            name: "Pizzas",
            order: 0,
            starred: false,
            updated_at: 1623260844653,
            version: "1.0.0",
            display: true,
            parentId: null,
            parent: null,
            image: {
              created_at: 1618318654295,
              id: "dc1838ab-7f35-4c3a-96a2-2a63500dee94",
              name: "2021-02-03 (11).png",
              ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
              path:
                "https://cdn.tunisales.com/linstantgourmand/uploads/1618318653604__24738__2021-02-03 (11).png",
              remote: false,
              tag: "picture",
              type: "image/png",
              updated_at: 1618318654295,
              used: false,
              usedIn: [],
              version: "1.0.0",
            },
            cover: {
              created_at: 1619928658673,
              id: "745d1a3d-eaf1-4293-a4a3-06ddd1639159",
              name: "",
              ownerId: null,
              path: "/images/placeholder.png",
              remote: false,
              tag: "download",
              type: "",
              updated_at: 1619928658673,
              used: false,
              usedIn: [],
              version: "1.0.0",
            },
          },
        ],
        _price: 10,
        price: "€10.00",
      },
      {
        available: true,
        collectionsKeys: ["burgers"],
        created_at: 1618317493257,
        defaultShipping: {
          PickUpInStore: false,
          homeDelivery: false,
          physicalProduct: false,
          weight: null,
        },
        description:
          "<p>Steak 160, oeuf, cheddar, poivre, salade, tomate, oignons.</p>",
        id: "40ee5afd-1784-4f96-8235-1b350687e80c",
        imagesIds: ["4dee7780-9c18-4916-ba55-3a34c309b329"],
        optionsData: [],
        tags: [],
        title: "L’AMÉRICAIN",
        type: "SIMPLE_PRODUCT",
        updated_at: 1620783905360,
        variantId: "b814d031-73ca-44fb-b18b-ca200082e7c2",
        variantsData: [],
        vendorId: null,
        version: "1.0.0",
        images: [
          {
            created_at: 1618317448571,
            id: "4dee7780-9c18-4916-ba55-3a34c309b329",
            name: "2021-02-03 (2).png",
            ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
            path:
              "https://cdn.tunisales.com/linstantgourmand/uploads/1618317448047__24354__2021-02-03 (2).png",
            remote: false,
            tag: "picture",
            type: "image/png",
            updated_at: 1618317448571,
            used: false,
            usedIn: [],
            version: "1.0.0",
          },
        ],
        vendor: null,
        variant: {
          barcode: "",
          compare_at_price: "",
          continueOutOfStock: false,
          created_at: 1618317493251,
          id: "b814d031-73ca-44fb-b18b-ca200082e7c2",
          imageId: "4dee7780-9c18-4916-ba55-3a34c309b329",
          key: "",
          option: null,
          price: "7",
          quantity: 0,
          shipping: {},
          sku: "",
          trackQuantity: false,
          updated_at: 1618317493251,
          version: "1.0.0",
          image: {
            created_at: 1618317448571,
            id: "4dee7780-9c18-4916-ba55-3a34c309b329",
            name: "2021-02-03 (2).png",
            ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
            path:
              "https://cdn.tunisales.com/linstantgourmand/uploads/1618317448047__24354__2021-02-03 (2).png",
            remote: false,
            tag: "picture",
            type: "image/png",
            updated_at: 1618317448571,
            used: false,
            usedIn: [],
            version: "1.0.0",
          },
          formattedPrice: "€7.00",
        },
        image: {
          path:
            "https://cdn.tunisales.com/linstantgourmand/cache/40ee5afd-1784-4f96-8235-1b350687e80c-thumbnail.png",
        },
        collections: [
          {
            color: null,
            created_at: 1618100797579,
            desc: "",
            featured: null,
            icon: null,
            id: "76fd2b67-573a-4c14-99fa-2944ab7677cc",
            imageId: "e5e40e21-442d-495b-8787-7730c9852d5e",
            key: "burgers",
            name: "Burgers",
            order: 0,
            updated_at: 1618438101523,
            version: "1.0.0",
            display: true,
            starred: false,
            coverId: "",
            parentId: null,
            parent: null,
            image: {
              created_at: 1618100460789,
              id: "e5e40e21-442d-495b-8787-7730c9852d5e",
              name: "1612207057284__95793__lamericain.jpg",
              ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
              path:
                "https://cdn.tunisales.com/linstantgourmand/uploads/1618100460523__74557__1612207057284__95793__lamericain.jpg",
              remote: false,
              tag: "picture",
              type: "image/jpeg",
              updated_at: 1618100460789,
              used: false,
              usedIn: [],
              version: "1.0.0",
            },
            cover: { path: "/images/placeholder.png" },
          },
        ],
        _price: 7,
        price: "€7.00",
      },
      {
        available: true,
        collectionsKeys: ["burgers"],
        created_at: 1618317327330,
        defaultShipping: {
          PickUpInStore: false,
          homeDelivery: false,
          physicalProduct: false,
          weight: null,
        },
        description:
          "<p>Chicken, salade, tomate, oignons, cheddar, sauce au choix.</p>",
        id: "9eea71d2-9189-4a6b-97b2-f1d660f4609a",
        imagesIds: ["f576e4bc-8e66-4b42-a8d5-8ccc3097269e"],
        optionsData: [],
        tags: [],
        title: "LE CHICKEN",
        type: "SIMPLE_PRODUCT",
        updated_at: 1620783905388,
        variantId: "588c0e6c-403e-4843-8d2e-b40b3f6e1893",
        variantsData: [],
        vendorId: null,
        version: "1.0.0",
        images: [
          {
            created_at: 1618317894186,
            id: "f576e4bc-8e66-4b42-a8d5-8ccc3097269e",
            name: "2021-02-03 (12).png",
            ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
            path:
              "https://cdn.tunisales.com/linstantgourmand/uploads/1618317893285__15831__2021-02-03 (12).png",
            remote: false,
            tag: "picture",
            type: "image/png",
            updated_at: 1618317894186,
            used: false,
            usedIn: [],
            version: "1.0.0",
          },
        ],
        vendor: null,
        variant: {
          barcode: "",
          compare_at_price: "",
          continueOutOfStock: false,
          created_at: 1618317327324,
          id: "588c0e6c-403e-4843-8d2e-b40b3f6e1893",
          imageId: "f576e4bc-8e66-4b42-a8d5-8ccc3097269e",
          key: "",
          option: null,
          price: "6",
          quantity: 0,
          shipping: {},
          sku: "",
          trackQuantity: false,
          updated_at: 1618317942823,
          version: "1.0.0",
          image: {
            created_at: 1618317894186,
            id: "f576e4bc-8e66-4b42-a8d5-8ccc3097269e",
            name: "2021-02-03 (12).png",
            ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
            path:
              "https://cdn.tunisales.com/linstantgourmand/uploads/1618317893285__15831__2021-02-03 (12).png",
            remote: false,
            tag: "picture",
            type: "image/png",
            updated_at: 1618317894186,
            used: false,
            usedIn: [],
            version: "1.0.0",
          },
          formattedPrice: "€6.00",
        },
        image: {
          path:
            "https://cdn.tunisales.com/linstantgourmand/cache/9eea71d2-9189-4a6b-97b2-f1d660f4609a-thumbnail.png",
        },
        collections: [
          {
            color: null,
            created_at: 1618100797579,
            desc: "",
            featured: null,
            icon: null,
            id: "76fd2b67-573a-4c14-99fa-2944ab7677cc",
            imageId: "e5e40e21-442d-495b-8787-7730c9852d5e",
            key: "burgers",
            name: "Burgers",
            order: 0,
            updated_at: 1618438101523,
            version: "1.0.0",
            display: true,
            starred: false,
            coverId: "",
            parentId: null,
            parent: null,
            image: {
              created_at: 1618100460789,
              id: "e5e40e21-442d-495b-8787-7730c9852d5e",
              name: "1612207057284__95793__lamericain.jpg",
              ownerId: "b3eaf831-b46f-408f-a9e6-4887ea8df62b",
              path:
                "https://cdn.tunisales.com/linstantgourmand/uploads/1618100460523__74557__1612207057284__95793__lamericain.jpg",
              remote: false,
              tag: "picture",
              type: "image/jpeg",
              updated_at: 1618100460789,
              used: false,
              usedIn: [],
              version: "1.0.0",
            },
            cover: { path: "/images/placeholder.png" },
          },
        ],
        _price: 6,
        price: "€6.00",
      },
    ],
  }),
};
</script>
