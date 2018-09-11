<template>
    <div class="container">
        <div class="row">
            <div v-for="item in data" :key="item.id">
                {{ item.id}}
            </div>
        </div>
    </div>
</template>

<script>
import VueResource from "vue-resource";
export default {
  data() {
    return {
      data: [""]
    };
  },
  created() {
    this.$http
      .get(`https://jsonplaceholder.typicode.com/posts`)
      .then(result => {
        console.log(result.body.id);
        this.data = result.data.title;
      })
      .catch(err => {
        console.log(err);
      });
  }
};
</script>

