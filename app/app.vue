<template lang="html">
  <div class="app">

    <div class="sidebar">
      <p class="sidebar__title">Build Your Monster</p>
      <div class="sidebar__img-switcher">
        <button class="sidebar__btn"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>
        <div class="sidebar__frame">
          <img class="sidebar__img" src="/monster/body-1.png" alt="" />
        </div>
        <button class="sidebar__btn"><i class="fa fa-chevron-right" aria-hidden="true"></i></button>
      </div>
      <div class="sidebar__img-switcher">
        <button class="sidebar__btn"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>
        <div class="sidebar__frame">
          <img class="sidebar__img" src="/monster/mouth-1.png" alt="" />
        </div>
        <button class="sidebar__btn"><i class="fa fa-chevron-right" aria-hidden="true"></i></button>
      </div>
      <div class="sidebar__img-switcher">
        <button class="sidebar__btn"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>
        <div class="sidebar__frame">
          <img class="sidebar__img" src="/monster/eyes-1-crossed.png" alt="" />
        </div>
        <button class="sidebar__btn"><i class="fa fa-chevron-right" aria-hidden="true"></i></button>
      </div>
      <form class="sidebar__form">
        <input class="sidebar__input" type="text" name="name" placeholder="Name Your Creation">
        <button class="sidebar__submit">Save Favorite</button>
      </form>
    </div>

    <div class="app__content">
      <div class="main">
        <div class="monster">
          <img src="/monster/body-1.full.png" alt="" class="monster__img">
          <img src="/monster/eyes-1-crossed.full.png" alt="" class="monster__img">
          <img src="/monster/mouth-1.full.png" alt="" class="monster__img">
        </div>
      </div>

      <div class="favorites">
        <div class="favorites__group">
          <div class="monster">
            <img src="/monster/body-1.full.png" alt="" class="monster__img">
            <img src="/monster/eyes-1.full.png" alt="" class="monster__img">
            <img src="/monster/mouth-1.full.png" alt="" class="monster__img">
          </div>
          <p class="favorites__name">Kara</p>
        </div>
        <div class="favorites__group">
          <div class="monster">
            <img src="/monster/body-1.full.png" alt="" class="monster__img">
            <img src="/monster/eyes-1.full.png" alt="" class="monster__img">
            <img src="/monster/mouth-1.full.png" alt="" class="monster__img">
          </div>
          <p class="favorites__name">Cooper</p>
        </div>
        <div class="favorites__group">
          <div class="monster">
            <img src="/monster/body-1.full.png" alt="" class="monster__img">
            <img src="/monster/eyes-1.full.png" alt="" class="monster__img">
            <img src="/monster/mouth-1.full.png" alt="" class="monster__img">
          </div>
          <p class="favorites__name">Maggie</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';

export default Vue.extend({
    data() {
        return {
            monsterParts: [],
            form: {
                name: 'monster-name'
            },
        };
    },
});
</script>
