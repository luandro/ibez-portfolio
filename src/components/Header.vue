<template>
  <header class="header">
    <nav class="nav">
      <g-link to="/" exact>
        <h1>{{ $static.metaData.siteName }}</h1>
      </g-link>
      <Info />
    </nav>
  </header>
</template>

<script>
import Info from './Info.vue'
export default {
    props: {
        page: {
            type: String,
            required: true
        }
    },
    computed: {
        isInfoPage() {
            return this.page === "info" && true
        },
        infoLink() {
            return this.isInfoPage ? "/" : "/info"
        }, 
    },
    components: {
        Info
    }
}
</script>

<static-query>
    query {
    metaData {
        siteName
    }
    }
</static-query>

<style>
.header h1 {
  margin-bottom: 0;
}

.nav {
  padding: 1.5rem 1.25rem;
  border-bottom: 1px solid #ebebeb;
  /* display: flex; */
  /* justify-content: space-between; */
  /* flex-direction: row; */
  /* align-items: center; */
}

.nav img {
  margin-bottom: 0;
}

@media (min-width: 768px) {
  .header {
    height: 100vh;
    position: fixed;
    left: 0;
    top: 0;
  }

  .nav {
    padding: 2rem;
    width: 30vw;
    height: 100%;
    border-right: 1px solid #ebebeb;
    border-bottom: none;
    flex-direction: column;
    align-items: flex-start;
  }
}
@media print {
  .header {
    min-height: 100vh;
  }
}
</style>