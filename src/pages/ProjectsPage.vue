<script>
import axios from "axios";
import ProjectCard from "../components/ProjectCard.vue";


export default {
  components: {
    ProjectCard,
  },
  data() {
    return {
      projects: [],
      lastPage: 0,
      curPage: 1,
    };
  },
  created() {
    this.getPosts();
  },
  methods: {
    getPosts() {
      axios
        .get(`http://127.0.0.1:8000/api/projects?page=${this.curPage}`)
        .then((resp) => {
          console.log(resp);
          this.projects = resp.data.results.data;
          // this.projects = resp.data.results aggiungo .data per la paginazione;
          this.lastPage = resp.data.results.last_page;
        });
    },
    changePage(newPage) {
      this.curPage = newPage;
      this.getPosts();
    },
    showNext() {
      if (this.curPage < this.lastPage) {
        this.curPage++;
        this.getPosts();
      }
    },
    showPrev() {
      if (this.curPage > 1) {
        this.curPage--;
        this.getPosts();
      }
    },
  },
};
</script>

<template>
  <div class="container">
    <h1>Tutti i miei progetti</h1>
    <div class="row row-cols-4 g-2">
      <div class="col" v-for="project in projects">
        <ProjectCard :project="project" />
      </div>
    </div>

    <div class="mt-5 d-flex justify-content-center">
      <nav aria-label="Page navigation example">
        <ul class="pagination">
          <li class="page-item">
            <a
              class="page-link"
              href="#"
              :class="{ disabled: curPage === 1 }"
              @click.prevent="showPrev()"
              >Previous</a
            >
          </li>
          <li
            class="page-item"
            :class="{ active: page === curPage }"
            v-for="page in lastPage"
          >
            <a class="page-link" href="#" @click.prevent="changePage(page)">{{
              page
            }}</a>
          </li>
          <li class="page-item">
            <a
              class="page-link"
              href="#"
              :class="{ disabled: curPage === lastPage }"
              @click.prevent="showNext()"
              >Next</a
            >
          </li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<style scoped lang="scss"></style>
