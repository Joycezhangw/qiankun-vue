# qiankun-vue
one vue plugin power by [qiankun](https://github.com/umijs/qiankun)。

## install
```shell
yarn add qiankun-vue or npm install qiankun-vue --save
```
## use

main.ts
```vuejs
const qiankunVue = new QiankunVue([
  {
    name: 'dashboard',
    entry: '//localhost:5001',
    activeRule: '/dashboard'
  },
  {
    name: 'example',
    entry: '//localhost:5002',
    activeRule: '/example'
  }
])
new Vue({
  router,
  store,
  qiankunVue,
  render: h => h(App)
}).$mount('#main')
```

framework.vue (mounted child app)

```vue
<template>
  <div class="framework">
    <qiankun
      @app-mounted="afterMounted"
      @app-unmounted="afterUnmounted"
    ></qiankun>
  </div>
</template>
<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

  @Component({
    name: 'Framework'
  })
export default class extends Vue {

  afterMounted (app: any) {
    console.log('子应用挂载结束')
  }

  afterUnmounted (app: any) {
    console.log('子应用卸载结束')
  }
}
</script>
<style lang="scss" scoped></style>

```

