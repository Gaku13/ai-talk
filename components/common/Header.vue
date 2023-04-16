<template lang="pug">
  // headroom
  header
    nuxt-link.logo( to="/" )
      Logo
    nav
      // a.nav-button( href="#" @click="click" )
        | menu
      .nav-container
        // a.nav-close( href="#" @click="close" )
          X
        ul
          li
            nuxt-link( v-scroll-to="feature" to ) できること
          li
            nuxt-link( v-scroll-to="faq" to ) よくある質問
      a.download-button( href="#" target="_blank" rel="noopener noreferrer nofollow" ) ダウンロード
</template>

<script>
import Logo from '~/static/images/logo.svg?inline'
import X from '~/static/images/icon/x.svg?inline'

import { headroom } from 'vue-headroom'

export default {
  components: {
    Logo,
    X,
    headroom,
  },
  data() {
    return {
      feature: {
        el: '#feature',
        offset: -80,
        onStart: function(el) {
          var nav;
          nav = document.querySelector('.nav-container');
          return nav.classList.remove('show');
        }
      },
      faq: {
        el: '#faq',
        offset: -80,
        onStart: function(el) {
          var nav;
          nav = document.querySelector('.nav-container');
          return nav.classList.remove('show');
        }
      }
    };
  },
  methods: {
    click: function() {
      var nav;
      nav = document.querySelector('.nav-container');
      return nav.classList.add('show');
    },
    close: function() {
      var nav;
      nav = document.querySelector('.nav-container');
      return nav.classList.remove('show');
    }
  }
}
</script>

<style lang="stylus">
  header
    position fixed
    top 0
    left 0
    display flex
    align-items center
    width: 100%
    height 64px
    padding 0 24px
    background $white
    transition transform .75s .25s ease, opacity .75s .25s ease, visibility .75s .25s
    box-shadow: 0 1px 10px rgba(0, 0, 0, .1)
    z-index $zindex-header
    @media (max-width: $phone)
      justify-content: space-between
      height 50px
      padding 0 16px
  .logo
    svg
      width 151px
      height auto
      vertical-align bottom
  nav
    display: flex
    align-items: center
    justify-content: space-between
    width: 100%
    @media (max-width: $phone)
      width: auto
    .nav-button
      display none
      line-height 18px
      visibility hidden
      font-weight 700
      letter-spacing .1rem
      @media (max-width: $phone)
        display block
        visibility visible
    .nav-container
      position relative
      margin-left: 24px
      visibility visible
    ul
      display flex
      align-items center
      justify-content center
      list-style none
      margin 0
      padding 0
      li
        padding 0 20px
        a
          color $text
          font-size 14px
          letter-spacing .025rem
          text-decoration none
          transition color .3s
          &:hover
            color $primary
      @media (max-width: $phone)
        display none
    a.download-button
      display: block
      line-height: 20px
      padding: 8px 12px
      color: $white
      font-size: 14px
      font-weight: bold
      text-align: center
      background-color: $primary
      transition: background-color .2s
      border-radius: 4px
      min-width: 130px
      &:hover
        background-color: $space
</style>

