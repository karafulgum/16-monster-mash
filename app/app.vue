<template lang="html">
  <div class="app">

    <div class="sidebar">
      <p class="sidebar__title">Build Your Monster</p>
      <div class="sidebar__img-switcher">
        <button class="sidebar__btn" @click="updatePart('body', -1)"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>
        <div class="sidebar__frame">
          <img class="sidebar__img" :src="'/monster/' + monsterParts.body[selected.body] + '.png'" alt="" />
        </div>
        <button class="sidebar__btn" @click="updatePart('body', 1)"><i class="fa fa-chevron-right" aria-hidden="true"></i></button>
      </div>
      <div class="sidebar__img-switcher">
        <button class="sidebar__btn" @click="updatePart('mouth', -1)"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>
        <div class="sidebar__frame">
          <img class="sidebar__img" :src="'/monster/' + monsterParts.mouth[selected.mouth] + '.png'" alt="" />
        </div>
        <button class="sidebar__btn" @click="updatePart('mouth', 1)"><i class="fa fa-chevron-right" aria-hidden="true"></i></button>
      </div>
      <div class="sidebar__img-switcher">
        <button class="sidebar__btn" @click="updatePart('eyes', -1)"><i class="fa fa-chevron-left" aria-hidden="true"></i></button>
        <div class="sidebar__frame">
          <img class="sidebar__img" :src="'/monster/' + monsterParts.eyes[selected.eyes] + '.png'" alt="" />
        </div>
        <button class="sidebar__btn" @click="updatePart('eyes', 1)"><i class="fa fa-chevron-right" aria-hidden="true"></i></button>
      </div>
      <form class="sidebar__form" @submit.prevent="saveMonster">
        <input class="sidebar__input" type="text" name="name" placeholder="Name Your Creation" v-model="selected.name">
        <button class="sidebar__submit">Save Favorite</button>
      </form>
    </div>

    <div class="app__content">
      <div class="main">
        <div class="monster">
          <img :src="'/monster/' + monsterParts.body[selected.body] + '.full.png'" alt="" class="monster__img">
          <img :src="'/monster/' + monsterParts.mouth[selected.mouth] + '.full.png'" alt="" class="monster__img">
          <img :src="'/monster/' + monsterParts.eyes[selected.eyes] + '.full.png'" alt="" class="monster__img">
        </div>
      </div>

      <div class="favorites">
        <div class="favorites__group" v-for="favorite in favorites">
          <div class="monster">
            <img :src="'/monster/' + monsterParts.body[favorite.body] + '.full.png'" alt="" class="monster__img">
            <img :src="'/monster/' + monsterParts.mouth[favorite.mouth] + '.full.png'" alt="" class="monster__img">
            <img :src="'/monster/' + monsterParts.eyes[favorite.eyes] + '.full.png'" alt="" class="monster__img">
          </div>
          <p class="favorites__name">{{ favorite.name }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue';
import monsterParts from './monster-parts';

export default Vue.extend({
    data() {
        return {
            selected: {
              body: 0,
              mouth: 0,
              eyes: 0,
              name: '',
            },
            monsterParts,
            favorites: [],
        };
    },

    mounted() {
      this.getFavorites();
    },

    methods: {
      getFavorites() {
        fetch('http://tiny-tn.herokuapp.com/collections/kf-monsters')
          .then((r) => r.json())
          .then((favorites) => {
            this.favorites = favorites;
          });
      },

      updatePart(partName, difference = 1) {
        this.selected[partName] = (this.selected[partName] + difference) % this.monsterParts[partName].length;
      },
      saveMonster() {
        fetch(`http://tiny-tn.herokuapp.com/collections/kf-monsters`, {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify(this.selected)
        })
          .then((r) => r.json())
          .then((favorite) => {
            this.favorites = [favorite, ...this.favorites];

            this.selected = {
              name: '',
              body: 0,
              eyes: 0,
              mouth: 0,
            };
          });

      },
    },
});
</script>
