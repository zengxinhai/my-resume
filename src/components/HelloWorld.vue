<template>
  <div class="container">
    <div class="banner">
      <button @click="vibrate">Vibrate!</button>
    </div>
    <div class="skill">1</div>
    <div class="experience">2</div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
  vibrate(): void {
    if (navigator.vibrate) {
      navigator.vibrate(100);
    } else {
      alert('Vibrate not supported');
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.container {
  display: grid;
  height: 50rem;
  grid-template: 
    "banner" 60px
     "skill"
     "experience"
     "experience";
  @media (min-width: 992px){
    grid-template: 
      "banner banner banner" 100px
      "skill experience experience"
  }
}

.banner {
  background: red;
  grid-area: banner;
}

.skill {
  background: blue;
  grid-area: skill;
}

.experience {
  background: yellow;
  grid-area: experience;
}
</style>
