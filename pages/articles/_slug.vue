<template>
  <div>
    <h1>{{ article.title }}</h1>
    <dl>
      <dt>Date</dt>
      <dd>{{ article.date }}</dd>
    </dl>
    <div>
      <img :src="article.image" alt="">
    </div>
    <div>
      <p>Tags</p>
      <ul>
        <li v-for="tag in article.tags" :key="tag">{{ tag }}</li>
      </ul>
    </div>
    <nuxt-content :document="article"></nuxt-content>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content('articles', params.slug || 'index').fetch();
    return { article };
  }
};
</script>

<style>

</style>