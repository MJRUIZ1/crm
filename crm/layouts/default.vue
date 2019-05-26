<template>
  <div>
    <nav
      class="navbar header has-shadow is-info"
      role="navigation"
      aria-label="main navigation"
    >
      <div class="navbar-brand">
       
      </div>
    </nav>

    <section class="main-content columns">

      

      <div class="container column is-10">
        <nuxt />
      </div>

    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          title: 'Home',
          icon: 'home',
          to: { name: 'index' }
        }
      ]
    }
  }
}
</script>
