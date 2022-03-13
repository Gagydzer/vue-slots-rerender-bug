<script>
import InnerChild from "./components/InnerChild.vue";
import {computed, defineComponent, h, ref} from "vue";

export default defineComponent({
  components: {
    InnerChild
  },
  setup(props, { slots }) {
    const innerCounter = ref(0);
    const onButtonClick = () => innerCounter.value = innerCounter.value + 1

    return () => h('div', {},[
      h('button', { onClick: onButtonClick }, ['increment']),
      h('div', {}, [innerCounter.value]),
      h(
          InnerChild, { }, slots,
      )
    ])
  }
})
</script>
