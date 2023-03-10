<template>
  <div class="box">
    <div class="wrapper">
      <img v-lazy="{ nolazy }" :data-src="src" v-bind="$attrs" />
    </div>
  </div>
</template>

<script>
export default {
  inheritAttrs: false,
  props: {
    lazy: {
      type: Boolean,
      default: true,
    },
    src: {
      type: String,
      default: '',
    },
  },
  computed: {
    nolazy() {
      return !this.lazy
    },
  },
  directives: {
    lazy: {
      bind(el, binding) {
        const { nolazy } = binding.value
        if (nolazy) return (el.src = el.dataset.src)
        const obServer = new IntersectionObserver((entries) => {
          // 如果 intersectionRatio 为0，则目标在视野外
          if (entries[0].intersectionRatio <= 0) return
          el.src = el.dataset.src
          obServer.unobserve(el)
        })
        obServer.observe(el)
      },
    },
  },
}
</script>

<style></style>
