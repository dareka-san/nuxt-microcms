<template>
  <div>
    <h1>果たしてデプロイされるのか？うぬｎ！下書きは出ておらぬか！？</h1>
    <div v-for="item in items" :key="item.id">
      <nuxt-link :to="'careers/' + item.id">
        <h2>
          {{ item.name }}
          {{ item.id }}
        </h2>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      items: []
    };
  },
  async asyncData() {
    const { data } = await axios.get(
      "https://salisty.microcms.io/api/v1/careers",
      {
        headers: { "X-API-KEY": process.env.API_KEY }
      }
    );
    return {
      items: data.contents
    };
  }
};
</script>