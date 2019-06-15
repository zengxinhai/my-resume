<template>
  <div class="home">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
    <ScrollAppear />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from '@/components/HelloWorld.vue'; 
import ScrollAppear from '@/components/ScrollAppear.vue';

@Component({
  components: {
    HelloWorld,
    ScrollAppear,
  },
})
export default class Home extends Vue {}
</script>
