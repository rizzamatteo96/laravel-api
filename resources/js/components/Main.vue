<template>
  <div class="container mt-5">
    <div class="row row-cols-3 g-4">
      <div class="col mt-4" v-for="post in posts" :key="post.id"> 
        <div class="card text-dark bg-light">
          <div class="card-body">
            <h3 class="card-title">{{post.title}}</h3>
            <p class="card-text">{{post.description}}</p>
            <p class="card-text"><small class="text-muted">{{post.created_at}}</small></p>
            <button type="button" class="btn btn-outline-dark">Leggi articolo</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: 'Main',
  data(){
    return {
      urlApi: 'http://127.0.0.1:8000/api/posts' ,
      posts: []
    }
  },
  created(){
    this.getPosts();
  },
  methods: {
    getPosts(){
      axios.get(this.urlApi)
            .then(response => {
              // console.log(response.data.results);
              this.posts = response.data.results;
            });
    }
  }
}
</script>


<style lang="scss" scoped>

</style>