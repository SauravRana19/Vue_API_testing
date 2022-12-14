<template>
  <div class="home">
    <HeaderVue />
    <PostApiVue />
    <GetApiVue />
    <FooterVue />
  </div>
</template>
<RouterView />
<script>
import FooterVue from '@/components/Footer_comp.vue';
import HeaderVue from '@/components/Header_comp.vue';
import PostApiVue from '@/components/Post_Api.vue';

export default {
  name: 'home-view',
  components: {FooterVue,HeaderVue,PostApiVue
  }
}
</script>
