<template>
  <p>{{counter}}</p>
  <p>{{doubleCounter}}</p>
  <span>{{msg2}}</span>
  <p ref="desc"></p>
</template>

<script>
import {reactive,computed,watch, onMounted, onUnmounted, ref, toRefs} from 'vue'
export default {
  setup(){
    //counter相关
    const {counter,doubleCounter}=useCounter()
    //其他数据
    const msg2=ref('some message')

    const desc = ref(null)
    watch(counter,(val, oldVal)=>{
      const p = desc.value
      p.textContent=`counrer change from ${oldVal} to ${val}`
    })

    return {counter,doubleCounter,msg2,desc}
  }
}
  function useCounter(){
    const data=reactive({
      counter:1,
      doubleCounter:computed(()=>data.counter*2)
    })
    let timer;
    onMounted(()=>{
      timer = setInterval(() => {
        data.counter++
      }, 1000);
    })
    onUnmounted(()=>{
      clearInterval(timer)
    });
    return toRefs(data);
  }
</script>
