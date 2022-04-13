<template>
  <layout>
    <header class="masthead" style="background-image: url('/img/home-bg.jpg')">
      <div class="container position-relative px-4 px-lg-5">
        <div class="row gx-4 gx-lg-5 justify-content-center">
          <div class="col-md-10 col-lg-8 col-xl-7">
            <div class="site-heading">
              <h1>Clean Blog</h1>
              <span class="subheading">A Blog Theme by Start Bootstrap</span>
            </div>
          </div>
        </div>
      </div>
    </header>
    <!-- Main Content-->
    <div class="container px-4 px-lg-5">
      <div class="row gx-4 gx-lg-5 justify-content-center">
        <div class="col-md-10 col-lg-8 col-xl-7">
          <template v-for="edge in $page.tags.edges">
            <!-- Post preview-->
            <div class="post-preview">
              <a href="post.html">
                <h2 class="post-title">{{ edge.node.attributes.title }}</h2>
              </a>
            </div>
            <!-- Pager-->
          </template>
          <div class="d-flex justify-content-end mb-4"><a class="btn btn-primary text-uppercase" href="#!">Older Posts →</a></div>
        </div>
      </div>
    </div>
  </layout>
</template>

<page-query>
query {
  tags: allStrapiTag {
    edges {
      node {
        attributes {
          title
          posts {
            data {
              attributes {
                title
              }
            }
          }
        }
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  },
}
</script>

<style>
</style>
