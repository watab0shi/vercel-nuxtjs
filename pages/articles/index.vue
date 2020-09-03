<template>
  <div>
    <h1>Articles</h1>
    <ul>
      <li v-for="a in articles" :key="a.slug">
        <nuxt-link :to="'/articles/' + a.slug">{{ a.date }} : {{ a.title }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const query = await $content('articles' || 'index');
    const articles = await query.fetch();
    return { articles };
  }
};
</script>

<style>

</style>