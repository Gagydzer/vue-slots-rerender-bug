<template>
  <div>
    <h4>inner child</h4>
    <slot name="test" :foo="'bar'">

    </slot>
  </div>
</template>

<script>
import {computed, defineComponent, onUpdated} from "vue";

export default defineComponent({
  setup() {
    onUpdated(
        () => {
          console.log('inner child updated');
        }
    )
    return {}
  }
})
</script>
