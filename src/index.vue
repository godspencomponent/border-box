<template>
  <div class="component">
    <component
      class="borderWrap"
      v-if="scriptLoadSuccess&&type"
      :color="[color1, color2]"
      :reverse="reverse"
      :dur="dur"
      :title="title"
      :titleWidth="titleWidth"
      :is="type"
    ></component>
  </div>
</template>

<script>
  import {VueExtend} from 'godspen-lib'
  import {
    borderBox1,
    borderBox2,
    borderBox3,
    borderBox4,
    borderBox5,
    borderBox6,
    borderBox7,
    borderBox8,
    borderBox9,
    borderBox10,
    borderBox11,
    borderBox12,
    borderBox13
  } from '@jiaminghi/data-view'

  export default {
    mixins: [VueExtend.mixin],
    name: 'border-box',
    label: process.env.LABEL,
    style: process.env.STYLE,
    props: {
      type: {
        type: [String],
        default: 'DvBorderBox1',
        editer: {
          ignore: true // 忽略，码良基础在编辑器中不显示
        }
      },
      reverse: {
        type: Boolean,
        default: '是否翻转',
        editer: {
          ignore: true // 忽略，码良基础在编辑器中不显示
        }
      },
      dur: {
        type: Number,
        default: 3,
        editer: {
          ignore: true // 忽略，码良基础在编辑器中不显示
        }
      },
      title: {
        type: String,
        default: '标题',
        editer: {
          ignore: true // 忽略，码良基础在编辑器中不显示
        }
      },
      titleWidth: {
        type: Number,
        default: 250,
        editer: {
          ignore: true // 忽略，码良基础在编辑器中不显示
        }
      },
      comStyle: {
        type: Object,
        default: function () {
          return {
            color1: 'rgb(35, 95, 167)',
            color2: 'rgb(79, 210, 221)'
          }
        },
        editer: {
          ignore: true // 忽略，码良基础在编辑器中不显示
        }
      }
    },
    data () {
      return {
        scriptLoadSuccess: false,
        colors: {
          DvBorderBox1: ['rgb(35, 95, 167)', 'rgb(79, 210, 221)'],
          DvBorderBox2: ['#fff', '#fff'],
          DvBorderBox3: ['rgb(40, 98, 183)', 'rgb(40, 98, 183)'],
          DvBorderBox4: ['red', 'rgba(0, 0, 255, 0.8)'],
          DvBorderBox5: ['rgba(255, 255, 255, 0.2)', 'rgba(255, 255, 255, 0.2)'],
          DvBorderBox6: ['rgba(255, 255, 255, 0.4)', 'rgba(255, 255, 255, 0.4)'],
          DvBorderBox7: ['rgba(255, 255, 255, 0.2)', 'rgba(255, 255, 255, 0.2)'],
          DvBorderBox8: ['rgb(35, 95, 167)', '#53cbd9'],
          DvBorderBox9: ['rgb(0, 120, 210)', 'rgb(0, 120, 210)'],
          DvBorderBox10: ['rgb(29, 72, 196)', 'rgb(211, 225, 248)'],
          DvBorderBox11: ['#8cacf9', '#24316b'],
          DvBorderBox12: ['rgb(46, 96, 153)', 'rgb(124, 231, 253)'],
          DvBorderBox13: ['rgb(46, 96, 153)', 'rgb(124, 231, 253)']
        }
      }
    },
    computed: {
      color1 () {
        return this.comStyle.color1 || this.colors[this.type][0]
      },
      color2 () {
        return this.comStyle.color1 || this.colors[this.type][1]
      }
    },
    async mounted () {
      // 纯属演示异步加载js资源，与本组件无关； loadJs返回一个promise实例 可以用async 或者 then 来处理回调
      window.Vue.use(borderBox1)
      window.Vue.use(borderBox2)
      window.Vue.use(borderBox3)
      window.Vue.use(borderBox4)
      window.Vue.use(borderBox5)
      window.Vue.use(borderBox6)
      window.Vue.use(borderBox7)
      window.Vue.use(borderBox8)
      window.Vue.use(borderBox9)
      window.Vue.use(borderBox10)
      window.Vue.use(borderBox11)
      window.Vue.use(borderBox12)
      window.Vue.use(borderBox13)

      this.scriptLoadSuccess = true
    },
    editorMethods: {
    },
    methods: {
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" type="text/stylus" scoped>
  .component {
    width: 100%;
    height: 100%;

    .borderWrap {
      width: 100%;
      height: 100%;
    }
  }
</style>
