<template>
  <div class="card">
    <div class="card-header">
      <h1>{{ projectData.title }}</h1>
      <h3 v-if="projectData.WIP" class="wip-text">[WIP]</h3>
    </div>
    <div class="card-body">
      <img class="bg-img" v-bind:src="projectData.thumbnail" />
      <div class="card-text">
        <p>{{ projectData.description }} </p>
      </div>
    </div>
    <div class="card-footer">
        <ul class="project-lang-list">
          <li v-for="lang in projectData.languages">{{ lang }}</li>
        </ul>
    </div>
  </div>
</template>

<script>

export default {
  props: {
    projectData: Object
  }
}
</script>

<style lang="scss">
@import "~/assets/colours.scss";

.card {
  display: block;
  min-width: 350px;
  width: 45%;
  margin: 1rem auto;
  background-color: $colour-primary-1;
  border-radius: 1rem;
  height: 20rem;
  overflow: hidden;
}

.card-body {
  display: block;
  width: 100%;
  height: 15rem;
  position: relative;
  top: 0;
}

.card-text {
  position: absolute;
  bottom: 0.5rem;
  left: 1rem;
  right: 1rem;
  overflow: hidden;
  padding: 0.5rem;
  display: block;
  margin: 0 auto; 

  background-color: $colour-primary-1;
  color: $colour-primary-0;
  border-radius: 1rem;
}

.wip-text {
  display: inline-block;
  text-align: right;
  width: 20%;
}

.bg-img {
  display: inline-block;
  width: 100%;
  height: 15rem;
  z-index: 1;
  object-fit:cover;
  object-position: center;
}

.card-header {
  text-align: left;
  width: 100%;
  height: 3rem;
  padding-left: 1rem;
  background-color: $colour-primary-0;
  display: inline-block;
  border-top-left-radius: 1rem;
  border-top-right-radius: 1rem;
  color: $colour-primary-1;
}
.card-header h1{
  display: inline-block;
  width: 75%;
}
.card-footer {
  position: relative;
  margin-top: 0;
  display: inline-block;
  // width: 100%;
  min-width: 100%;
  background-color: $colour-primary-0;
  color: $colour-primary-1;
  border-bottom-left-radius: 1rem;
  border-bottom-right-radius: 1rem;

  height: 2rem;
  
  overflow-x: visible;
  overflow-y: hidden;
}

ul.project-lang-list {
  padding-left: 0;
  display: inline;
  overflow: hidden;
  list-style: none;
}

ul.project-lang-list li {
  display:block;
  margin: 0.25rem 1rem;
  float: left;
}



</style>
