<template lang="pug">
  .search-block
    .search-block__header
      h2.search-block__title {{title}}
      a.search-block__more(href="#" @click.prevent="changeTab(id)" v-if="all") Смотреть больше
    .search-block__list
      slot
</template>

<script>
import { mapActions } from 'vuex'
export default {
  name: 'SearchBlock',
  props: {
    title: {
      type: String,
      required: true
    },
    id: {
      type: String,
      required: true
    },
    all: Boolean
  },
  methods: {
    ...mapActions('global/search', ['changeTab'])
  }
}
</script>

<style lang="stylus">
@import '../../assets/stylus/base/vars.styl';

.search-block {
  &+& {
    margin-top: 70px;
  }
}

.search-block__header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 25px;
}

.search-block__title {
  font-family: font-exo;
  font-weight: 200;
  font-size: 30px;
  color: #000000;
}

.search-block__more {
  font-size: 13px;
  text-align: right;
  color: #21A45D;
}
</style>
