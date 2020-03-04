<template>
  <div id="app">
    <keep-alive exclude="Detail">
      <router-view/>
    </keep-alive>
  </div>
</template>

<script>
// exclude作用是取消Detail组件的缓存(上面)
export default {
  name: 'App'
}
</script>

<style>
</style>
