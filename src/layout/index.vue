<template>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <component :is="Component" />
    </Suspense>
  </RouterView>
</template>

<script>
  import sxoImplement from './sxoImplement'

  export default {
    name: 'Layout',
    setup () {
      sxoImplement()
    }
  }
</script>
