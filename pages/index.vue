<template>
  <div class="md-layout md-aligmnet-center">
    <md-toolbar elevation="2">
      <md-button class="md-icon-button">
        <md-icon>Menu</md-icon>
      </md-button>
      <nuxt-link class="md-primary md-title" to="/">
      Astre App👋
      </nuxt-link>
      <div class="md-toolbar-section-end">
      </div>
    </md-toolbar>

    <div class="md-layout-item md-size-95">
      <md-content class="md-layout md-gutter" style="background:#ccc;padding:5px;">
            <ul v-for="post in posts" :key="post.id" class="md-layout-item md-large-size-25 md-medium-size-33 md-small-size-50 md-xsmall-size-100">
                <md-card md-with-hover style="margin-top:10px">
                
                  <md-card-header>
                    <div class="md-title">
                      <a target="_blank" :href="post.link" :title="post.title.rendered">{{post.title.rendered}}</a>
                    </div>
                    <div class="md-subhead">
                       {{post.title}}
                    </div>
                    <div class="md-subhead">
                       {{post.countries}}
                    </div>

                  </md-card-header>

                  <md-card-content>
                    <div class="md-subhead">
                       {{post.description}}
                    </div>

                    <md-button class="md-icon-button">
                      <md-icon class="small-icon" >favorite</md-icon>
                    </md-button>

                    <md-button class="md-icon-button">
                      <md-icon class="small-icon">visibility</md-icon>
                    </md-button>
                  </md-card-content>
                </md-card>  
            </ul>
      </md-content>
    </div>
    
  </div>
</template>

<script>
export default {
    async asyncData({ app }) {
      const posts = await app.$axios.$get('https://api.nuxtjs.dev/planets?_embed');
      return { posts: posts }
    },
    
  }
</script>

