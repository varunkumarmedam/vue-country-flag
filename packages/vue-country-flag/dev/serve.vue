<script>
import Vue from 'vue';
import CountryFlag from '@/CountryFlag.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    CountryFlag
  }
});
</script>

<template>
  <div id="app">
    <CountryFlag country='it'/>
    <CountryFlag country='sun' size='big'/>
    <CountryFlag country='se' size='small'/>
  </div>
</template>
