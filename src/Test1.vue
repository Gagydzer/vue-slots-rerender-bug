<template>
  <div>
    <button @click="onButtonClick">increment</button>
    <div>
      {{ innerCounter }}
    </div>
    <InnerChild>
      <template #test="scope">
        {{ scope.foo }}
      </template>
    </InnerChild>
  </div>
</template>

<script>
import InnerChild from "./components/InnerChild.vue";
import {computed, defineComponent, h, ref} from "vue";

export default defineComponent({
  components: {
    InnerChild
  },
  setup(props, { slots }) {
    const innerCounter = ref(0);
    const staticCounter = ref(0);
    const onButtonClick = () => innerCounter.value = innerCounter.value + 1

    return {
      innerCounter, onButtonClick
    }
  }
})
</script>
