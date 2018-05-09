<template>
  <div class="main-content">
    <div>
      <i class="btn1">
        <wz-pop-menus @listClick="clickOne" :listdata="data">
          <h2>ceshi</h2>
        </wz-pop-menus>
      </i>
    </div>
    
    <readme></readme>
  </div>
</template>

<script>
import Readme from '../packages/popMenus/README.md'
export default {
  components: {
    Readme
  },
  data(){
    return {
      data: [
        {
          value: 'beijing',
          label: '北京',
          children: [
            {
              value: 'chaoyang',
              label: '朝阳',
              children: [
                {
                  value: 'chaoyang',
                  label: '朝阳'
                },
                {
                  value: 'haidian',
                  label: '海淀'
                },
                {
                  value: 'changping',
                  label: '昌平'
                },
                {
                  value: 'shunyi',
                  label: '顺义'
                }
              ]
            },
            {
              value: 'haidian',
              label: '海淀'
            },
            {
              value: 'changping',
              label: '昌平'
            },
            {
              value: 'shunyi',
              label: '顺义',
              children: [
                {
                  value: 'chaoyang',
                  label: '朝阳'
                },
                {
                  value: 'haidian',
                  label: '海淀'
                },
                {
                  value: 'changping',
                  label: '昌平'
                },
                {
                  value: 'shunyi',
                  label: '顺义'
                }
              ]
            }
          ]
        },
        {
          value: 'shanghai',
          label: '上海',
          children: [
            {
              value: 'baoshan',
              label: '宝山'
            },
            {
              value: 'jiading',
              label: '嘉定'
            }
          ]
        },
        {
          value: '哈哈',
          label: '哈哈'
        }
      ]
    }
  },
  methods: {
    clickOne(obj) {
      console.log(obj)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped rel="stylesheet/less">
.main-content{
  >div{
    width: 100%;
    padding-bottom: 100px;
  }
}
h1 {
  text-align: center;
  padding: 30px;
  overflow: hidden;
}
.wrap {
  width: 100%;
}
.btn1 {
  position: relative;
  float: left;
  width: 30px;
  height: 30px;
  background-color: #42b983;
}
.btn2 {
  background-color: peru;
  float: right;
  margin-right: 130px;
}
.btn3 {
  background-color: palevioletred;
  float: right;
  margin-right: 30px;
}
</style>