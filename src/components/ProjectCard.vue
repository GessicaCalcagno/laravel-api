<script>
export default {
  props: {
    project: Object,
  },
  // data(){
  //     return {
  //         //   imageBaseUrl:'http://127.0.0.1:8000/storage' -> devo ancora inserire le img lato back end

  //     }
  // }
};
</script>

<template>
  <div class="card h-100">
    <!-- Devo implementarlo lato back end -->
    <!-- <img class="card-image" :src="project.cover_img ? `${imageBaseUrl}/${project.cover_image}` : `https://placehold.co/500x300?text=immagine+non+disponibile` " alt=""> -->

    <img
      class="card-image"
      src="https://placehold.co/500x300?text=immagine+non+disponibile"
      alt=""
    />
    <div class="card-body">
      <h6>{{ project.title }}</h6>
      <!-- Se non inserisci il ternario da errore perchè non tutti i progetti hanno il type -->
      <p>{{ project.type ? project.type.name : "Nessuna tipologia" }}</p>
      <div>
        <span
          class="badge text-bg-primary mx-1"
          v-for="technology in project.technologies"
          >{{ technology.name }}</span
        >
      </div>
    </div>
  </div>

</template>

<style scoped lang="scss"></style>
