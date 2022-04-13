<template>
  <layout>
    <header
      class="masthead"
      :style="{
        backgroundImage: `url(${GRIDSOME_API_URL + blog.background.data.attributes.url})`
      }"
    >
      <div class="container position-relative px-4 px-lg-5">
        <div class="row gx-4 gx-lg-5 justify-content-center">
          <div class="col-md-10 col-lg-8 col-xl-7">
            <div class="site-heading">
              <h1>{{ blog.title }}</h1>
              <span class="subheading">{{ blog.subTitle }}</span>
            </div>
          </div>
        </div>
      </div>
    </header>
    <!-- Main Content-->
    <div class="container px-4 px-lg-5">
      <div class="row gx-4 gx-lg-5 justify-content-center">
        <div class="col-md-10 col-lg-8 col-xl-7">
          <template v-for="edge in $page.posts.edges">
            <!-- Post preview-->
            <div class="post-preview">
              <g-link :to="'/post/' + edge.node.id">
                <h2 class="post-title">{{ edge.node.attributes.title }}</h2>
              </g-link>
              <p class="post-meta">
                Posted by
                <a href="#!">{{ edge.node.attributes.create_by.data.attributes.name }}</a>
                {{ edge.node.attributes.createdAt }}
              </p>
            </div>
            <!-- tag-->
            <span v-for="tag in edge.node.attributes.tags.data" :key="tag.attributes.id">
              <a href="">{{ tag.attributes.title }}</a>&nbsp;&nbsp;
            </span>
            <!-- Divider-->
            <hr class="my-4" />
            <!-- Pager-->
          </template>
          <div class="d-flex justify-content-end mb-4"><a class="btn btn-primary text-uppercase" href="#!">Older Posts →</a></div>
        </div>
      </div>
    </div>
  </layout>
</template>

<page-query>
query{
  posts: allStrapiPost {
    edges {
      node {
        id
        attributes {
          title
          content
          tags {
            data {
              attributes {
                title
              }
            }
          }
          create_by {
            data {
              attributes {
                name
              }
            }
          }
        }
      }
    }
  }
  blogInfo: allStrapiBlogInfo {
    edges {
      node {
        data {
          attributes {
            title
            subTitle
            background {
              data {
                attributes {
                  url
                }
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
  computed: {
    blog () {
      return this.$page.blogInfo.edges[0].node.data.attributes
    },
  },
}
</script>

<style>
</style>
