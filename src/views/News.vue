<template>
  <div>
    <div class="container">
      <div class="my-5">
        <h1>{{ title }}</h1>
      </div>
      <div class="row">
        <div class="col-md-3" v-for="(data, index) in news" :key="index">
          <div class="card mb-3">
            <img :src="data.urlToImage" class="img-fluid" alt="" />
            <div class="card-body">
              <h5>{{ data.title }}</h5>
              <p class="card-text">
                {{ data.description }}
              </p>
            </div>

            <div class="card-body">
              <a :href="data.url" target="_blank" class="card-link"
                >Read more</a
              >
            </div>
          </div>
        </div>
      </div>
    </div>

    <div>
      <!-- <div v-for="(data, index) in news" :key="index">
        <img :src="data.urlToImage" alt="" />
        <h4>{{ data.title }}</h4>
        <p>{{ data.description }}</p>
        <a :href="data.url" target="_blank">Read more</a>
      </div> -->
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      title: "Welcome to our News",
      news: [],
    };
  },
  mounted() {
    this.fetchNews();
  },
  methods: {
    fetchNews() {
      fetch(
        "https://newsapi.org/v2/everything?q=bitcoin&apiKey=127fc75e6ada467e91789dcc061260b8"
      )
        .then((response) => {
          return response.json();
        })
        .then((response) => {
          this.news = response.articles;
        });
    },
  },
};
</script>