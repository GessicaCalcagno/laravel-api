<script>
export default {
  data() {
    return {
      navItems: [
        {
          routeName: "home",
          title: "Home",
        },
        {
          routeName: "projects",
          title: "Projects",
        },
      ],
    };
  },
};
</script>

<template>
  <nav class="navbar navbar-dark bg-dark navbar-expand-lg">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">BOOLFOLIO</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNavAltMarkup"
        aria-controls="navbarNavAltMarkup"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav" v-for="item in navItems">
          <router-link
            :to="{ name: item.routeName }"
            class="nav-link active"
            aria-current="page"
            href="#"
            >{{ item.title }}</router-link
          >
        </div>
      </div>
    </div>
  </nav>
</template>

<style lang="scss" scoped></style>
