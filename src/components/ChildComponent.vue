<!--<template>
  <div>
    <button @click="showSlots">show slots</button>
    <InnerChild>
      <template v-for="(_, name) in $slots" #[name]="scope">
        <slot :name="name" v-bind="scope"></slot>
      </template>
    </InnerChild>
  </div>
</template>-->

<script>
import {computed, defineComponent, onUpdated, watch, h, ref, reactive} from "vue";
import InnerChild from "./InnerChild.vue";

export default defineComponent({
  inheritAttrs: false,
  components: {
    InnerChild,
  },
  setup(props, { slots }) {
    const _sl = reactive(slots);

    const slotsComputed = computed(
        () => {
          console.log('slotsComputed', {...slots})
          return {
            slot1: slots.slot1,
            slot2: slots.slot2,
          }
        }
    )

    const showSlots = () => {
      console.log('slots', { ...slots })
    }
    let _slots = slots;

    watch(() => Object.keys(slots).length, (v) => {
      console.log('watch', v)
    }, { immediate: true, deep: true})

    onUpdated(() => {
      console.log('onUpdated', _slots === slots, slots)
      _slots = slots;
    })

    const innerCounter = ref(0);
    const onButtonClick = () => innerCounter.value = innerCounter.value + 1

    return () => h('div', {},[
        h('button', { onClick: onButtonClick }),
        h('div', {}, [innerCounter.value]),
        h(
            InnerChild, {}, slotsComputed.value,
        )
    ])
  }
})
</script>
