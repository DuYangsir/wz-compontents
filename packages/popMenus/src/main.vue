<template>
  <div class="cascader-btn" @click="cascaderShow();" ref="selectBtn">
    <div class="cascader-menus-wrap" ref="selectWrap">
      <ul class="cascader-menus" v-if="isVisible">
        <li v-for="(list, index) in data" :key="index" class="cascader-menu" @mouseleave="mouseleave()" @mouseenter="mouseEnter(index,list)" @click="listClick(list)">
          {{list.label}}
          <i class="el-icon-arrow-right" v-if="list.children && list.children.length > 0">
          </i>
          <ul class="cascader-menus lists" @mouseleave="mouseleave()" v-if="(list.children && list.children.length > 0) && isShowListBox == index">
            <li class="cascader-menu list" v-for="(child, index) in list.children" :key="index" @click="listClick(child)">
              {{child.label}}
            </li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'wz-pop-menus',
  props: ['listdata'],
  //    进阶
  //    props: {
  //      listdata: {
  //        type: Array,
  //        required: true
  //      },
  //      redund: {
  //        required: false
  //      }
  //    },
  watch: {
    listdata: function() {
      // this.data = util.copyObject(this.listdata,this.data)
    }
  },
  data() {
    return {
      isVisible: false,
      isShowListBox: 'none',
      isMarginR: false,
      isMarginRt: false,
      clientRight: 0,
      btnWidth: 0,
      data: []
    }
  },
  methods: {
    cascaderShow: function(e) {
      // this.data = util.copyObject(this.listdata, this.data)
      this.isVisible = true
      e = e || window.event
      //分别兼容ie和chrome
      //兼容火狐和其他浏览器
      let scrollX =
        document.documentElement.scrollLeft || document.body.scrollLeft
      let x = e.pageX || e.clientX + scrollX
      this.clientRight = document.documentElement.clientWidth - x
      let style = window.getComputedStyle(this.$refs.selectBtn, null)
      this.btnWidth = parseInt(style.width) / 2

      if (this.clientRight < 160) {
        this.isMarginR = true
        this.$refs.selectWrap.style.left =
          -(160 - this.clientRight) - this.btnWidth + 'px'
      }
      if (this.clientRight < 320) {
        this.isMarginRt = true
      }
    },
    mouseEnter: function(index, list) {
      this.isShowListBox = index

      if (list.children && list.children.length > 0 && this.isMarginR == true) {
        this.$refs.selectWrap.style.left =
          -320 - this.btnWidth + this.clientRight + 'px'
      }
      if (
        list.children &&
        list.children.length > 0 &&
        this.isMarginRt == true
      ) {
        this.$refs.selectWrap.style.left =
          -(320 - this.clientRight) - this.btnWidth + 'px'
      }
    },
    mouseleave: function() {
      this.isShowListBox = 'none'
    },

    listClick: function(obj) {
      if (!(obj.children && obj.children.length > 0)) {
        this.isVisible = false
      }
      this.$emit('listClick', obj)
      //        进阶
      //        this.$emit('listClick', {value: obj, redund: this.redund})
      event.stopPropagation()
    }
  },
  created: function() {}
}
</script>