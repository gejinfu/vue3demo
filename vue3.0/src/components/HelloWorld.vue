<template>
  <h1>{{ msg }}</h1>
  <p>Edit <code>components/HelloWorld.vue</code> to test hot module replacement.</p>
  <p>hello, vite!!!</p>
  <Composition></Composition>
  <ModelButton></ModelButton>
</template>

<script>
import {reactive,computed,watch, onMounted, onUnmounted, ref, toRefs} from 'vue'
import ModelButton from './ModelButton.vue'
import Composition from './Composition.vue'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
    ModelButton,
    Composition
  },
}
</script>
