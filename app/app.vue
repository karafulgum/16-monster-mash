<template lang="html">
  <div class="app">
    <div class="left-side">
      <p class="left-side__title">Build Your Monster</p>
      <div class="left-side__img-switcher">
        <button class="left-side__btn"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>
        <div class="frame">
          <img src="/monster/body-1.png" alt=""/>
        </div>
        <button class="left-side__btn"><i class="fa fa-chevron-right" aria-hidden="true"></i></button>
      </div>
      <div class="left-side__img-switcher">
        <button class="left-side__btn"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>
        <div class="frame">
          <img src="/monster/eyes-1-crossed.png" alt=""/>
        </div>
        <button class="left-side__btn"><i class="fa fa-chevron-right" aria-hidden="true"></i></button>
      </div>
      <div class="left-side__img-switcher">
        <button class="left-side__btn"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>
        <div class="frame">
          <img src="/monster/mouth-1.png" alt=""/>
        </div>
        <button class="left-side__btn"><i class="fa fa-chevron-right" aria-hidden="true"></i></button>
      </div>
      <form>
        <input type="text" name="name" placeholder="Name Your Creation">
        <button class="form__submit">Save Favorite</button>
      </form>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';

export default Vue.extend({
  data() {
    return {
      monsters: [],
      form: {
        name: 'monster-name'
      },
    };
  },
});
</script>
