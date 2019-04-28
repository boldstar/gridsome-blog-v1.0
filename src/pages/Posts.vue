<template>
  <Layout>
    <div class="posts">
      <div class="posts-content">
        <ul class="post-list">
          <li class="post" v-for="post in $static.posts.edges" :key="post.id">
            <div class="post-details">
                <g-link class="post-link" :to="post.node.path" :class="{'active-link' : post.node.path == $route.path}">{{ post.node.title }}</g-link>
                <span>{{ post.node.category}}</span>
                <p class="post-excerpt">{{ post.node.excerpt}}</p>
                <small class="post-by">{{ post.node.date}} By {{ post.node.author }}</small>
            </div>
            <g-image class="post-image" :src="post.node.featuredImage"></g-image>
          </li>
        </ul>
        </div>
    </div>
  </Layout>
</template>

<static-query>
  query posts {
    posts: allPost {
      edges {
        node {
          id
          title
          path
          category
          excerpt
          date
          author
          featuredImage
        }
      }
    }
  }
</static-query>

<script>
export default {
    name: 'Posts',
    metaInfo: {
    title: 'Blog Roll'
  }
}
</script>

<style scoped>
.posts {
  width: 100%;
}

.posts-content {
  max-width: 1120px;
  margin: 0 auto;
}

.post {
    display: flex;
    box-shadow: 0 1px 5px rgba(0,0,0,500);
    border-radius: 10px;
    margin-bottom: 15px;
    height: 300px;
}

.post-list {
    padding: 35px;
}

.post-link {
    text-decoration: none;
    font-size: 2rem;
}

.post-excerpt {
    margin: 0;
}

.post-details {
    display: flex;
    flex-direction: column;
    width: 75%;
    padding: 10px;
}

.post-image {
    height: 300px;
    width: auto;
    max-width: 35%;
    border-radius: 0 10px 10px 0;
}

.post-by {
    margin-top: auto;
}
</style>

