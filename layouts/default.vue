<template>
    <section class="hero is-info is-fullheight">
        <div class="hero-head">
            <nav class="navbar">
                <div class="container">
                    <div class="navbar-brand">
                        <a class="navbar-item" href="#">
                            <!-- <img src="~assets/buefy.png" alt="Logo">-->
                        </a>
                        <span class="navbar-burger burger" data-target="navbarMenu">
                            <span></span>
                            <span></span>
                            <span></span>
                        </span>
                    </div>
                    <div id="navbarMenu" class="navbar-menu">
                        <div class="navbar-end">
                        <!-- 
                            <span v-for="(item, key) of items" :key="key" class="navbar-item">
                                <NuxtLink :to="item.to" exact-active-class="is-active" class="button is-white is-outlined">
                                    <span class="icon">
                                        <b-icon :icon="item.icon" />
                                    </span>
                                    <span>{{ item.title }}</span>
                                </NuxtLink>
                            </span>
                            -->
                        </div>
                    </div>
                </div>
            </nav>
        </div>

        <div class="hero-body">
            <Nuxt />
        </div>

    </section>
</template>


<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      items: [
        {
          title: 'Home',
          icon: 'home',
          to: { name: 'index' },
        },
        {
          title: 'Inspire',
          icon: 'lightbulb',
          to: { name: 'inspire' },
        },
      ],
    }
  },
}
</script>

<style>
  .hero.is-info {
    background: linear-gradient(
        rgba(0 0 0 / 90%),
        rgba(0 0 0 / 60%)
      ), url('~assets/fb.jpg') no-repeat center center fixed;
    background-size: cover;
  }

</style>
