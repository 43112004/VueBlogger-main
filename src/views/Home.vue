<template>
  <div>
    <video
     id="comp-k85ppcnz_video"
     class="K8MSra"
     role="presentation"
     crossorigin="anonymous"
     playsinline=""
     preload="auto"
     muted=""
     loop=""
     tabindex="-1"
     autoplay=""
     src="https://video.wixstatic.com/video/375882_9f1a8e8b364946f38b7eb05436e76503/1080p/mp4/file.mp4"
     style="height: 100%; width: 100%; object-fit: cover; object-position: center center;"
     ></video>
    <div class="container">
      <div class="text-center">
        <div class="center">
          <Avatar size="300" home="true" />
        </div>
        <h1>{{ config.name }}</h1>
        <h4 style="color: #666666">{{ config.username }}</h4>
        <p>{{ config.description }}</p>
      </div>
      <h2>Latest Posts</h2>
      <hr/>
      <div class="grid-3_xs-1_sm-2_md-2" v-if="posts.length">
        <div
          :key="index"
          v-for="(post, index) in posts.slice(Math.max(posts.length - 6, 0)).reverse()"
          class="col"
        >
          <PostCard :post="post" class="center" />
        </div>
      </div>
      <Nothing v-else />
    </div>
  </div>
</template>

<script>
import Avatar from '@/components/Avatar.vue'
import PostCard from '@/components/PostCard.vue'
import Nothing from '@/components/Nothing.vue'

export default {
  name: 'Home',
  components: {
    Avatar,
    PostCard,
    Nothing
  },
  data: function () {
    return {
      posts: this.getConfig('posts.json').posts,
      config: this.getConfig().config
    }
  },
  mounted: function () {
    this.changeTitle('Home')
  }
}
</script>
<style lang="scss" scoped>
.K8MSra{
   height: 100%;
    width: 100%;
    object-fit: cover;
    object-position: center center;
    opacity: 0.5;
    position: absolute;
    top: 0;
}
</style>
