<script>
import HelloWorld from './components/HelloWorld.vue';
import { ref, computed, defineComponent } from 'vue';

export default {
  components: {
    HelloWorld,
  },

  provide() {
    return {
      flag: computed(() => this.flag),
    };
  },

  setup() {
    const flag = ref(0);
    const localValue = ref(0);
    return {
      flag,
      localValue,
    };
  },

  methods: {
    onClick() {
      this.localValue++;
    },
  },

  watch: {
    localValue() {
      this.flag++;
    }
  }

}
</script>


<template>
<div>
  <button type="button" :value="'flag: ' + flag" @click="onClick">{{ 'flag: ' + flag}}</button>
</div>
<HelloWorld msg="Vite + Vue" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
