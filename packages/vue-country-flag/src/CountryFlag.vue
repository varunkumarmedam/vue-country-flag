<template>
    <span :class="flagIconClass" v-if="country"></span>
</template>

<script>
import './css/flags/flags.min.css'

export default {
  name: 'CountryFlag',
  props: {
    country: {
      type: String,
      required: true
    },
    rounded: {
      type: Boolean,
      default: false
    },
    size: {
      type: String,
      validator: function(value) {
        return value === 'small' || value === 'normal' || value === 'big'
      },
      default: 'normal'
    }
  },
  computed: {
    flagIconClass () {
      return {
        [`flag ${this.flagIconCountry}`]: true,
        [`rounded`]: this.rounded,
        [this.flagMargin]: true
      }
    },
    flagIconCountry () {
      let country = this.country.toLowerCase() 
      country = (country === 'ad') ? 'andorra' : country
      return `f-${country}`
    },
    flagMargin () {
      switch (this.size) {
        case 'small':
            return 'small-flag' 
        case 'normal':
            return 'normal-flag'
        case 'big':
            return 'big-flag'
        default:
            return 'normal-flag'
      }
    }
  }
}
</script>
<style scoped>
  .small-flag {
    margin: -15px -22.5px;
    transform: scale(0.25);
    -ms-transform: scale(0.25); 
    -webkit-transform: scale(0.25);
    -moz-transform: scale(0.25);
  }
  .normal-flag {
    margin: -10px -15px;
    transform: scale(0.5);
    -ms-transform: scale(0.5); 
    -webkit-transform: scale(0.5);
    -moz-transform: scale(0.5);
  }
  .big-flag {
    margin: 0;
  }
  .small-flag.rounded {
    -moz-border-radius: 15px;
    border-radius: 15px;
  }
  .normal-flag.rounded {
    -moz-border-radius: 10px;
    border-radius: 10px;
  }
  .big-flag.rounded {
    -moz-border-radius: 8px;
    border-radius: 8px;
  }
</style>
