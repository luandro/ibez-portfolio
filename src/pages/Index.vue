<template>
  <Layout page="home">
    <ProjectList :projects="$page.projects.edges" />
  </Layout>
</template>

<script>
import ProjectList from '~/components/ProjectList.vue'

export default {
  metaInfo: {
    title: 'Home'
  },
  components: {
    ProjectList
  }
}
</script>
<page-query>
    query getData {   
        projects: allPortfolio {
            edges {
                node {
                    id
                    title
                    path
                    link
                    date
                    hero_image
                    content
                }
            }
        }
    }
</page-query>
