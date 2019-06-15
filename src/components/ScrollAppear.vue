<template>
  <div class="scroll-appear-container" :class="{appeared: appearedBefore}" ref="scrollAppearContainer">
    <h1 class="title" :class="{appeared: appearedBefore}">Ice Fox</h1>
    <div class="pic-box">
      <img class="pic" src="../assets/ice-fox.jpg" />
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop } from 'vue-property-decorator';
import { isElementInViewport } from '@/utils/viewPort';

@Component
export default class ScrollAppear extends Vue {
  @Prop() private appearedBefore: Boolean = false; 
  created() {
    window.addEventListener('scroll', this.handleScroll);
  }
  handleScroll() {
    if (isElementInViewport(this.$refs.scrollAppearContainer) && this.appearedBefore === false) {
      this.appearedBefore = true;
    }
  }
}
</script>

<style lang="less" scoped>
.scroll-appear-container {
  height: 40rem;
  opacity: 0;
  transition: opacity 1000ms ease-in-out;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  .title {
    transform: translateY(2rem);
    transition: transform 1000ms ease-in-out;
  }
}

.scroll-appear-container.appeared {
  opacity: 1;
}

.title.appeared {
  transform: translateY(-2rem);
}
</style>
