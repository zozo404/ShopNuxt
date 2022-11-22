<template>
  <div>
    <Nav class="sticky top-0" />
    <h1 class="font-bold m-5 md:mx-10">
      {{ currentProduct.attributes.name }}
    </h1>
    <Products :data="currentProduct" />
    <Ads class="mx-auto sm:m-10" />
    <Footer />
  </div>
</template>
    
    <script>
export default {
  async asyncData({ $strapi, $http, route }) {
    const id = route.params.products;
    const response = await this.$strapi.$products.findOne(id, {
      populate: "*",
    });
    const { data: currentProduct } = response;
    return { currentProduct };
  },
  data() {
    return {
      currentProduct: {},
    };
  },
};
</script>
    
    <style scoped>
</style>