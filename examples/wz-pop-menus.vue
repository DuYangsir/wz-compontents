<template>
  <div class="main-content">
    <i class="btn1">
      <wz-pop-menus @listClick="clickOne" :listdata="data"></wz-pop-menus>
    </i>
    <readme></readme>
  </div>
</template>

<script>
import Readme from '../packages/popMenus/README.md'
export default {
  components: {
    Readme
  }
}
</script>